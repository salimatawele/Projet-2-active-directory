# Configuration du Service DNS

Le service DNS est hébergé directement sur le contrôleur de domaine (`SRV-DC01`).

## Paramètres principaux
* **Zone de recherche directe :** `entreprise.local`
* **Intégration Active Directory :** Activée (les enregistrements sont stockés et répliqués de manière sécurisée via l'annuaire).
* **Rôle :** Résolution des noms d'hôtes du domaine en adresses IP et localisation des contrôleurs de domaine (enregistrements SRV).
