# Plan d'adressage IP - Infrastructure Active Directory

Ce document répertorie la configuration IP de l'infrastructure réseau de l'entreprise.

## Contrôleur de Domaine (SRV-DC01)
* **Nom de la machine :** SRV-DC01
* **Adresse IP fixe :** 192.168.1.10
* **Masque de sous-réseau :** 255.255.255.0
* **Passerelle par défaut :** 192.168.1.1
* **Serveur DNS préféré :** 127.0.0.1 (Pointant vers lui-même pour l'annuaire Active Directory)
* **Nom de domaine complet (FQDN) :** entreprise.local
* **Nom NetBIOS :** ENTREPRISE
