# La couche infrastructure chez McDonald's : les fondations invisibles qui soutiennent l'empire

Descendons maintenant dans les sous-sols de McDonald's, là où les clients et même certains employés ne mettent jamais les pieds. C'est ici que se cachent les systèmes de réfrigération, les générateurs électriques, les réseaux d'approvisionnement en eau et les câblages complexes. Bienvenue dans la couche infrastructure - ces fondations invisibles sans lesquelles même le Big Mac le plus parfaitement conçu ne pourrait jamais atteindre votre plateau.

## La persistence : les entrepôts frigorifiques

Regardez ces imposantes chambres froides à l'arrière de chaque McDonald's. Elles ne créent pas les aliments, elles ne définissent pas les recettes, mais sans elles, rien ne serait possible. Elles préservent l'état du système entre deux services, maintiennent les ingrédients dans des conditions optimales, et garantissent la continuité des opérations.

Votre dossier `persistence` joue exactement ce rôle crucial. Il ne contient pas la logique métier, mais assure que vos précieuses données survivent aux redémarrages du système. Ici se trouvent vos adaptateurs de base de données, vos mappeurs ORM, vos scripts de migration - tout ce qui touche à la sauvegarde et à la récupération de l'état de votre application.

Comme McDonald's peut changer de fournisseur de systèmes de réfrigération sans modifier ses recettes de burgers, votre application peut migrer d'une base de données SQL vers MongoDB sans que le domaine ne s'en aperçoive. C'est l'essence même d'une bonne séparation des préoccupations.

## Les repositories d'infrastructure : les traducteurs de commandes

Dans l'arrière-cuisine de McDonald's, il existe des systèmes sophistiqués pour transformer les commandes abstraites ("deux Happy Meals") en instructions concrètes pour les systèmes d'inventaire ("retirer deux jouets, deux boîtes, quatre pains à burger...").

Vos implémentations concrètes de repositories dans `infrastructure/repositories` sont ces traducteurs essentiels. Alors que les interfaces de repository définies dans le domaine parlent le langage métier, leurs implémentations dans l'infrastructure parlent SQL, MongoDB, ou tout autre dialecte technique nécessaire.

`BurgerRepositoryImpl.ts` ou `OrderRepositoryMongo.ts` savent comment transformer une entité domaine pure en une structure adaptée à la persistance, puis comment reconstituer cette entité à partir des données brutes récupérées. Ils masquent tous les détails techniques désagréables - les connexions, les transactions, les index - exactement comme le système logistique de McDonald's masque aux cuisiniers les complexités de la chaîne d'approvisionnement.

## Les services d'infrastructure : les utilitaires indispensables

Un McDonald's moderne dépend d'une multitude de services techniques : système de paiement électronique, surveillance vidéo, climatisation, connexion Internet pour les bornes de commande...

Dans votre dossier `infrastructure/services`, on trouve les équivalents numériques : services d'envoi d'emails, clients d'API externes, gestionnaires de cache, services de génération de PDF... Ces éléments ne sont pas au cœur de votre logique métier, mais ils fournissent des capacités techniques indispensables au fonctionnement global.

Le `EmailService.ts` ne sait rien des règles qui déterminent quand envoyer une confirmation de commande - il sait simplement comment envoyer un email de manière fiable. Le `PaymentGatewayService.ts` ne connaît pas les règles de tarification, mais il sait comment communiquer sécuritairement avec le processeur de paiement.

## Les adaptateurs : les prises universelles

McDonald's opère dans des dizaines de pays avec des standards électriques différents, des réglementations diverses, des fournisseurs locaux variés. Pour maintenir une expérience cohérente, ils utilisent des adaptateurs qui standardisent ces variations.

Vos adaptateurs dans l'infrastructure jouent le même rôle. Le `MongoDBAdapter.ts` ou le `RedisAdapter.ts` normalisent les interactions avec ces technologies spécifiques, offrant une interface cohérente au reste de l'application. Si vous décidez de changer de fournisseur de cache ou de file d'attente, seul l'adaptateur correspondant doit être modifié.

## La configuration : le manuel d'ouverture du restaurant

Chaque matin, le premier manager de McDonald's suit un protocole précis pour mettre en route le restaurant : allumer les équipements dans un ordre spécifique, vérifier les températures, initialiser les caisses...

Dans votre infrastructure, les fichiers de configuration jouent ce rôle d'initialisation. Ils définissent comment votre application se connecte aux bases de données, quels ports elle utilise, comment elle s'authentifie auprès des services externes, et quels paramétrages spécifiques à l'environnement (développement, test, production) doivent être appliqués.

## La journalisation et le monitoring : les caméras de surveillance

Un McDonald's bien géré dispose de systèmes pour surveiller constamment ses opérations : caméras de sécurité, capteurs de température, compteurs de clients...

Votre infrastructure inclut des équivalents numériques : services de journalisation qui enregistrent chaque action significative, systèmes de monitoring qui surveillent la santé de l'application, alertes qui se déclenchent lorsque des seuils critiques sont dépassés. Ces systèmes ne participent pas directement à la préparation des hamburgers (la logique métier), mais ils sont essentiels pour garantir que tout fonctionne comme prévu.

## Les tâches planifiées : l'équipe de nettoyage nocturne

La nuit, quand les clients sont partis, McDonald's entre dans un autre mode : nettoyage profond, maintenance des équipements, préparation pour le lendemain...

Vos jobs planifiés dans l'infrastructure fonctionnent sur le même principe : nettoyage des données temporaires, génération de rapports quotidiens, sauvegardes de bases de données, synchronisation avec des systèmes externes... Ces tâches discrètes mais cruciales s'exécutent souvent quand l'activité principale est au ralenti.

## Les migrations : les rénovations de restaurant

Périodiquement, McDonald's rénove ses restaurants - mettant à jour l'agencement, remplaçant les équipements vieillissants, adaptant l'espace aux nouvelles offres...

Dans votre code, les scripts de migration de base de données accomplissent cette même fonction d'évolution contrôlée. Ils permettent à votre schéma de données de s'adapter aux nouveaux besoins sans perturber le service, tout en préservant les données existantes.

## En résumé : l'infrastructure invisible mais essentielle

La magie de McDonald's réside dans cette capacité à masquer une complexité technique impressionnante derrière une façade de simplicité. Les clients ne voient que les arches dorées et les hamburgers, jamais les kilomètres de câblage électrique ou les systèmes sophistiqués de gestion de la chaîne du froid.

De même, une bonne couche infrastructure dans votre architecture DDD devrait être comme la plomberie d'un grand restaurant : invisible pour l'utilisateur final et même pour la plupart des développeurs travaillant sur les fonctionnalités métier, mais impeccablement conçue, robuste et prête à évoluer sans perturber l'ensemble.

Comme McDonald's n'a pas réinventé ses recettes emblématiques quand il est passé des années 1950 aux années 2020, votre domaine ne devrait pas changer quand vous passez de MySQL à PostgreSQL ou d'un serveur local au cloud. C'est la promesse d'une infrastructure bien conçue - elle porte le domaine sans jamais le contraindre.

``` 
infrastructure/
├── persistence/
│   ├── database/
│   │   ├── MongoDB.ts
│   │   ├── PostgreSQL.ts
│   │   └── DatabaseConnection.ts
│   ├── orm/
│   │   ├── TypeORM.ts
│   │   ├── Mongoose.ts
│   │   └── EntityMappers.ts
│   ├── migrations/
│   │   ├── MigrationRunner.ts
│   │   └── scripts/
│   │       ├── 001-initial-schema.ts
│   │       ├── 002-add-order-status.ts
│   │       └── 003-customer-preferences.ts
│   └── cache/
│       ├── Redis.ts
│       ├── Memcached.ts
│       └── CacheManager.ts
├── repositories/
│   ├── BurgerRepositoryImpl.ts
│   ├── OrderRepositoryMongo.ts
│   ├── MenuRepositorySQL.ts
│   └── CustomerRepositoryImpl.ts
├── services/
│   ├── email/
│   │   ├── EmailService.ts
│   │   └── EmailTemplates.ts
│   ├── payment/
│   │   ├── PaymentGatewayService.ts
│   │   └── PaymentProviders/
│   │       ├── StripeAdapter.ts
│   │       └── PayPalAdapter.ts
│   ├── logging/
│   │   ├── LoggingService.ts
│   │   └── LoggerFactory.ts
│   ├── storage/
│   │   ├── FileStorageService.ts
│   │   └── StorageProviders/
│   │       ├── S3Adapter.ts
│   │       └── LocalStorageAdapter.ts
│   └── monitoring/
│       ├── HealthCheckService.ts
│       └── MetricsService.ts
├── adapters/
│   ├── MongoAdapter.ts
│   ├── RedisAdapter.ts
│   ├── S3Adapter.ts
│   └── APIAdapter.ts
├── config/
│   ├── AppConfig.ts
│   ├── DatabaseConfig.ts
│   ├── environment/
│   │   ├── Development.ts
│   │   ├── Production.ts
│   │   └── Testing.ts
│   └── secrets/
│       └── SecretsManager.ts
├── jobs/
│   ├── scheduler/
│   │   ├── CronJobManager.ts
│   │   └── JobRegistry.ts
│   └── tasks/
│       ├── DatabaseCleanupJob.ts
│       ├── ReportGenerationJob.ts
│       └── DataSyncJob.ts
├── external/
│   ├── api-clients/
│   │   ├── ExternalServiceClient.ts
│   │   └── ThirdPartyAPIClient.ts
│   └── integrations/
│       ├── PaymentProviderIntegration.ts
│       └── SupplierSystemIntegration.ts
└── index.ts
```
![alt text](<https://github.com/phamhung075/MDDD/blob/main/CInfrastructure.png>)