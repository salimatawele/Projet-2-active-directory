# RAPPORT DE PROJET : Mise en place d'une Infrastructure d'Entreprise Centralisée (Windows Server & Active Directory)

## 1. Introduction et Scénario du Projet

Dans le cadre de la croissance de l'entreprise (faisant suite au Projet 1), l'infrastructure informatique nécessite une centralisation et une sécurisation accrues des ressources. L'objectif de ce projet est de déployer un environnement de type **Active Directory (AD DS)** complet sous Windows Server, permettant de gérer de manière unifiée les identités, les postes de travail, les politiques de sécurité (GPO) et le partage de documents cloisonnés par département.

---

## 2. Architecture de l'Infrastructure

L'infrastructure repose sur un modèle client-serveur virtualisé comprenant :
* **Un Contrôleur de Domaine (`SRV-DC01`) :** Hébergeant les services Active Directory, le DNS et le serveur DHCP, configuré avec une adresse IP fixe (`192.168.1.10`).
* **Un Poste Client Windows (`PC-RH01`) :** Intégré au domaine `entreprise.local`, simulant un poste de travail utilisateur.

```text
                    Windows Server (SRV-DC01)
                              │
               ┌──────────────┴──────────────┐
               │                             │
        Active Directory                    DNS
               │
       ┌───────┼────────┐
       │       │        │
      RH      IT    Direction
       │       │        │
     Users   Users    Users
       │       │        │
      PC      PC       PC

## 3. Suivi du Déploiement par Jour (Planning Réalisé)

### Jour 1 — Infrastructure de Base
* **Objectif :** Poser les fondations du réseau d'entreprise et installer le rôle central de l'annuaire.
* **Réalisations :**
  * Installation de Windows Server.
  * Configuration d'une adresse IP fixe (`192.168.1.10`) et d'un masque de sous-réseau adapté.
  * Installation du rôle **Active Directory Domain Services (AD DS)** et promotion du serveur en contrôleur de domaine.
  * Création de la forêt et du domaine racine : `entreprise.local`.

### Jour 2 — Annuaire Active Directory & Organisation
* **Objectif :** Structurer l'entreprise de manière logique en fonction des départements métiers.
* **Réalisations :**
  * Création des **Unités Organisationnelles (OU)** principales : *RH*, *IT*, et *Direction*.
  * Création des comptes utilisateurs (ex : *Alice Dupont* pour le département RH).
  * Création des groupes de sécurité associés (ex : `GRP-RH`, `GRP-IT`, `GRP-Direction`) pour faciliter l'attribution des droits.

### Jour 3 — Réseau, DNS et Jonction des Clients
* **Objectif :** Assurer la communication et la résolution de noms entre les postes clients et le serveur.
* **Réalisations :**
  * Vérification de la résolution des noms de domaine via le service **DNS** interne.
  * Configuration des paramètres réseau sur les postes clients (pointage du DNS primaire vers l'IP du serveur `192.168.1.10`).
  * Jonction réussie du poste client (`PC-RH01`) au domaine `entreprise.local`.
  * Résolution des profils réseau (passage en mode *Réseau Privé*) pour autoriser les flux Active Directory.   

## Jour 4 — Sécurisation par GPO (Group Policy Objects)
* **Objectif :** Imposer des règles de sécurité et unifier l'expérience utilisateur à distance.
* **Réalisations :**
  * Création d'une GPO de politique de mots de passe (`GPO-Politique-MotsDePasse`) imposant la complexité et une longueur minimale.
  * Création de GPO départementales ciblées (ex : `GPO-Parametres-RH`) liées à l'OU correspondante pour restreindre ou configurer l'environnement de travail.
  * Application et vérification des stratégies via la commande `gpupdate /force`.

## Jour 5 — Partages Réseau, Permissions et Tests Finaux
* **Objectif :** Mettre en place un espace de stockage mutualisé et cloisonné de manière sécurisée.
* **Réalisations :**
  * Création d'un dossier racine `C:\PartagesEntreprise` sur le serveur contenant les sous-dossiers : RH, IT, et Direction.
  * Configuration des partages réseau (SMB) et application rigoureuse des permissions NTFS (dissociation de l'héritage, attribution exclusive des dossiers aux groupes AD respectifs : `GRP-RH`, etc.).
  * Validation des accès par des tests pratiques (ex : accès autorisé pour Alice Dupont sur son dossier RH, refus d'accès aux autres départements).

## 4. Synthèse des Tests et Validation

| Type de Test | Cible / Outil | Résultat Observé | Statut |
| :--- | :--- | :--- | :--- |
| **Connectivité Réseau** | `ping 192.168.1.10` | 0% de perte, temps < 1ms | ✅ Succès |
| **Résolution DNS** | `nslookup entreprise.local` | Résolution correcte vers l'IP du DC | ✅ Succès |
| **Authentification** | Connexion `entreprise.local\adupont` | Ouverture de session effective sur le poste client | ✅ Succès |
| **Sécurité (GPO)** | `gpupdate /force` | Application des stratégies de mot de passe et de bureau | ✅ Succès |
| **Cloisonnement** | Accès aux dossiers partagés | Accès autorisé pour le groupe concerné / Refus pour les autres | ✅ Succès |

## 5. Conclusion
Le déploiement de cette infrastructure Active Directory sous Windows Server est un succès complet. L'entreprise dispose désormais d'un système d'information robuste, centralisé, sécurisé par des stratégies de groupe (GPO) et cloisonné grâce à une gestion fine des permissions NTFS et des groupes de sécurité. Ce projet valide l'ensemble des compétences fondamentales en administration système et réseaux d'entreprise.
  
