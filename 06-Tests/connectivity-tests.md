# Tests de Connexion au Domaine (Poste Client)

* **Machine testée :** Poste client Windows (ex: PC-RH01)
* **Action :** Jonction au domaine `entreprise.local` effectuée avec succès à l'aide des privilèges administrateur.
* **Test d'authentification :** Connexion réussie sur la session de l'utilisateur `adupont` (RH) depuis le poste client.
* **Statut :** Validé avec succès.

## Objectif
Vérifier la bonne communication IP entre le poste client et le contrôleur de domaine.

## Commandes exécutées
```cmd
ping 192.168.1.10
