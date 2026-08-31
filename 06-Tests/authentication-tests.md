# Tests d'Authentification

## Objectif
Vérifier que les utilisateurs créés dans l'Active Directory peuvent ouvrir une session sur les postes clients du domaine.

## Résultat du test
* **Compte testé :** `entreprise.local\adupont` (Alice Dupont)
* **Poste client :** `PC-RH01`
* **Résultat :** Connexion réussie au domaine après authentification valide auprès du contrôleur de domaine (`SRV-DC01`).
