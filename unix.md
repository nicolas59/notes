Commandes UNIX 
===================

Liste des utilisateurs : 
    cat /etc/passwd | awk -F: '{print $ 1}'

Afficher les groupes : 
    cat /etc/group | awk -F: '{print $ 1}'

Changer le mot de passe
    passwd <user>


Astuces 
====================
Modifier les régles d'authentification en editant le fichier /etc/ssh/sshd_config.


Créer un service 
====================
* Réaliser un script contenant les informations suivantes

    `# chkconfig: <levels> <start> <stop>`

    `# description: <some description>`

* Ajouter ce script dans le repertoire `/etc/init.d``
* Executer la commande :    
    `sudo chkconfig --level 345 <service> on` 
