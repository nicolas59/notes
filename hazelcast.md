Introduction
===================
Cache distribué en mémoire (HazelCast IMDG (In-Memory Data Grid) ).


Fonctionnalités 
===================
- Offre un cache mutualisé en mettant à disposition un cluster hazelcast
- Peut être utilisé en mode depot
- Peut être utilisé comme une queue
- Cache pouvant être utilisé par divers programmes codés dans des langages différents


Configuration 
==================

Le serveur est initialisé en code Java. Lors du lancement, le serveur verifie les ports disponibles et s'execute sur un de ces ports. Le relancement du main va entrainer la mise à disposition d'un serveur hazelcast sur un autre port.

Une replication automatique est effecutée entre les serveurs. Les données sont repliquées entre les noeuds en réalisant du sharding. Les données sont recopiées entre chaque noeuds, des ensembles de données sont marqués comme données maitre sur chaque serveur et d'autres ensembles sont taggués comme données backup.

Le client se connecte à un des serveurs et recupére les données via l'API. 

La configuration de la connexion (ou de l'initialisation du serveur ) est réalisées :
- via du code
    ```java
     Config cfg = new Config();

     cfg.getNetworkConfig().getJoin().getTcpIpConfig().addMember("127.0.0.1").setEnabled(true);
	 
     cfg.getNetworkConfig().getJoin().getMulticastConfig().setEnabled(false);

- via des fichiers XML
   ```java
   Config cfg = new ClasspathXmlConfig(file);

Pour le client, la classe `ClientConfig` permet d'intiialiser la configuration au cluster Hazelcast. 
   ```java
   ClientConfig clientConfig = new ClientConfig();

   clientConfig.getNetworkConfig().addAddress("127.0.0.1");
   clientConfig.getNetworkConfig().setConnectionTimeout(5000);
   ```


`La version des jar client et serveur doivent être en conformtée. Sur mac, une différence de version entraine des interruption de la connexion par le client`


Liens
=============
* Documentation : http://docs.hazelcast.org/docs/3.8/manual/html-single/index.html
* Initialiser Hazelcast https://hazelcast.org/getting-started-with-hazelcast/
* Chargement par configuration : http://docs.hazelcast.org/docs/3.3/manual/html/config.html
* Repot github : https://github.com/hazelcast
* Console d'administration : http://docs.hazelcast.org/docs/2.2/manual/html/ch17.html
* Presentation de divers solutions de cache & Hazelcast : https://fr.slideshare.net/tmatyashovsky/from-cache-to-in-memory-data-grid-introduction-to-hazelcast




