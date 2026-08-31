# Tests des Partages Réseau et Permissions NTFS

## Objectif
Vérifier l'étanchéité des dossiers partagés selon les départements (cloisonnement des accès).

## Scénario de test
* **Utilisateur :** Alice Dupont (Membre du groupe `GRP-RH`)
* **Test 1 (`\\SRV-DC01\PartagesEntreprise\RH`) :** Accès en lecture/écriture autorisé.
* **Test 2 (`\\SRV-DC01\PartagesEntreprise\IT`) :** Tentative d'accès -> Refus d'accès (*Access Denied*) conformément à la matrice de sécurité.
