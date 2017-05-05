Commande de base pour mysql
================

- Afficher les schemas 

`show databases;`

- Lister les utilisateurs

`select host, user, password from mysql.user`

- Création d'un utilisateur

`create user '<user>'@'%' identified by 'password'`

- droit de lecture
`GRANT SELECT ON db2.* TO '<user>'@'%'`

