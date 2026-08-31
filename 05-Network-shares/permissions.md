# Matrice des Permissions NTFS

La sécurité des dossiers partagés repose sur un cloisonnement strict basé sur les groupes de sécurité Active Directory créés au Jour 2.

| Dossier Partagé | Groupe AD Autorisé | Droits NTFS Attribués |
| :--- | :--- | :--- |
| `...\PartagesEntreprise\RH` | GRP-RH | Modification / Lecture / Écriture |
| `...\PartagesEntreprise\IT` | GRP-IT | Modification / Lecture / Écriture |
| `...\PartagesEntreprise\Direction` | GRP-Direction | Modification / Lecture / Écriture |
