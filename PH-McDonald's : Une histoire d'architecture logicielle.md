# McDonald's : Une histoire d'architecture logicielle

Au début, il y avait un petit restaurant à San Bernardino, Californie. Les frères McDonald venaient de créer un système de restauration rapide. Leur code était comme leur cuisine - un espace unique où tout se passait. Les commandes, la préparation, le service... tout était entremêlé. C'était l'époque du monolithe.

Dans cette première cuisine, un seul cuisinier pouvait s'occuper de tout. Il n'y avait pas de séparation claire des responsabilités. Comme un fichier `RestaurantService.ts` qui contenait toutes les fonctions imaginables - depuis la prise de commande jusqu'à la gestion des stocks, en passant par la préparation des frites.

Puis Ray Kroc est arrivé. Il a vu le potentiel de standardisation. C'est à ce moment que McDonald's a commencé à diviser ses opérations en stations distinctes. La station burger ne s'occupait que des burgers. La station frites ne faisait que des frites. Les caissiers ne faisaient que prendre les commandes.

Notre code a suivi la même évolution. Le monolithe s'est transformé en modules. Un dossier `orders/` pour tout ce qui concernait les commandes. Un dossier `menu/` pour la gestion des produits. Un dossier `users/` pour les clients et employés. C'était encore une seule application, mais avec des frontières plus claires. Comme un restaurant unique avec des zones de travail bien définies.

Au fur et à mesure que McDonald's grandissait, il est devenu impossible de tout gérer depuis un seul restaurant. Le système de franchise est né. Chaque restaurant était autonome, mais suivait les mêmes recettes, les mêmes procédures, la même marque.

Notre architecture a emprunté le même chemin. Les modules sont devenus des microservices indépendants. `order-service`, `menu-service`, `user-service`... Chacun avec sa propre base de code, sa propre base de données, son propre cycle de déploiement. Ils communiquaient entre eux via des API bien définies, comme les restaurants McDonald's qui communiquent via des procédures standardisées.

Et comme McDonald's a son siège qui définit les règles globales, nous avons ajouté une API Gateway pour diriger le trafic et un Event Bus pour partager les événements importants entre services.

Finalement, McDonald's a atteint une maturité où chaque restaurant est organisé selon les mêmes principes - la zone cliente (interface), la zone des managers (application), la cuisine (domaine) et les systèmes de support (infrastructure).

Notre architecture a suivi cette évolution jusqu'à une implémentation DDD complète. Chaque microservice a maintenant sa propre structure en couches, avec un domaine riche au centre, protégé par les couches application et infrastructure.

Comme McDonald's qui a transformé un simple stand de hamburgers en un empire mondial de restauration rapide, notre architecture a évolué d'un simple fichier à un écosystème complet et sophistiqué - sans jamais perdre de vue ce qui compte vraiment : servir efficacement les besoins des utilisateurs.

Et tout comme on reconnaît immédiatement un McDonald's n'importe où dans le monde, notre architecture est devenue reconnaissable, prévisible et fiable - parce qu'elle a été conçue avec les mêmes principes que ceux qui ont fait le succès de la chaîne : standardisation, séparation des préoccupations, et focus sur l'expérience client.


Dans cette évolution de l'architecture McDonald's, vous pourriez intégrer les schémas en arbre précédents pour illustrer chaque étape de maturité. Voici comment les incorporer dans le récit:

# McDonald's : Une histoire d'architecture logicielle

## Phase 1 : Le monolithe initial (1955)

Au début, il y avait un petit restaurant à San Bernardino, Californie. Les frères McDonald venaient de créer un système de restauration rapide. Leur code était comme leur cuisine - un espace unique où tout se passait.

```
mcdonalds-app/
├── src/
│   ├── controllers/
│   │   └── AppController.ts       # Gère toutes les requêtes
│   ├── services/
│   │   └── RestaurantService.ts   # Toute la logique métier mélangée
│   ├── models/
│   │   ├── Order.ts
│   │   ├── Menu.ts
│   │   └── User.ts
│   ├── utils/
│   │   └── helpers.ts
│   └── app.ts                     # Point d'entrée unique
├── package.json
└── tsconfig.json
```

## Phase 2 : Le monolithe modulaire (1970-1980)

Puis Ray Kroc est arrivé. Il a vu le potentiel de standardisation. McDonald's a commencé à diviser ses opérations en stations distinctes, comme notre code s'est transformé en modules.

```
mcdonalds-app/
├── src/
│   ├── orders/
│   │   ├── controllers/
│   │   │   └── OrderController.ts
│   │   ├── services/
│   │   │   └── OrderService.ts
│   │   └── models/
│   │       └── Order.ts
│   ├── menu/
│   │   ├── controllers/
│   │   │   └── MenuController.ts
│   │   ├── services/
│   │   │   └── MenuService.ts
│   │   └── models/
│   │       └── MenuItem.ts
│   ├── users/
│   │   ├── controllers/
│   │   │   └── UserController.ts
│   │   ├── services/
│   │   │   └── UserService.ts
│   │   └── models/
│   │       └── User.ts
│   ├── shared/
│   │   ├── database/
│   │   │   └── Database.ts
│   │   └── utils/
│   │       └── helpers.ts
│   └── app.ts
├── package.json
└── tsconfig.json
```

## Phase 3 : Vers les microservices (2000+)

Au fur et à mesure que McDonald's grandissait, le système de franchise est né. Notre architecture a suivi le même chemin vers des services indépendants.

```
mcdonalds-ecosystem/
├── order-service/
│   ├── src/
│   │   ├── controllers/
│   │   ├── services/
│   │   ├── models/
│   │   └── app.ts
│   ├── package.json
│   └── Dockerfile
├── menu-service/
│   ├── src/
│   │   ├── controllers/
│   │   ├── services/
│   │   ├── models/
│   │   └── app.ts
│   ├── package.json
│   └── Dockerfile
├── user-service/
│   ├── src/
│   │   ├── controllers/
│   │   ├── services/
│   │   ├── models/
│   │   └── app.ts
│   ├── package.json
│   └── Dockerfile
├── api-gateway/
│   ├── src/
│   │   └── routes/
│   ├── package.json
│   └── Dockerfile
├── event-bus/
│   ├── src/
│   ├── package.json
│   └── Dockerfile
└── docker-compose.yml
```

## Phase 4 : L'architecture DDD mature (présent)

Finalement, chaque restaurant McDonald's a atteint une organisation en couches sophistiquée. Notre architecture a évolué vers une implémentation DDD complète où chaque service est structuré selon ces mêmes principes.

### Couche Interface (Le Comptoir)

```
interface/
├── controllers/
│   ├── BurgerController.ts
│   ├── OrderController.ts
│   └── CustomerController.ts
├── routes/
│   ├── api.routes.ts
│   ├── burger.routes.ts
│   ├── order.routes.ts
│   └── customer.routes.ts
├── validation/
│   ├── ValidBurgerRequest.ts
│   ├── OrderValidator.ts
│   └── CustomerValidator.ts
├── events/
│   ├── OrderEvents.ts
│   ├── EventEmitter.ts
│   └── EventHandlers.ts
├── adapters/
│   ├── OrderAdapter.ts
│   ├── BurgerAdapter.ts
│   └── CustomerAdapter.ts
├── transformers/
│   ├── OrderTransformer.ts
│   ├── BurgerTransformer.ts
│   └── ResponseTransformer.ts
├── middlewares/
│   ├── AuthenticationMiddleware.ts
│   ├── LoggingMiddleware.ts
│   ├── ErrorHandlingMiddleware.ts
│   └── ValidationMiddleware.ts
├── errors/
│   ├── HttpErrors.ts
│   ├── ErrorFormatter.ts
│   └── ErrorResponses.ts
└── index.ts
```

### Couche Application (Les Managers & La Cuisine)

```
application/
├── services/
│   ├── OrderService.ts
│   ├── MenuService.ts
│   └── CustomerService.ts
├── commands/
│   ├── burger/
│   │   ├── CreateBurgerCommand.ts
│   │   └── UpdateBurgerStatusCommand.ts
│   ├── order/
│   │   ├── CreateOrderCommand.ts
│   │   └── MergeFriesAndDrinkCommand.ts
│   └── menu/
│       ├── CreateMenuCommand.ts
│       └── AddSauceToMenuCommand.ts
├── handlers/
│   ├── burger/
│   │   ├── CreateBurgerCommandHandler.ts
│   │   └── UpdateBurgerStatusCommandHandler.ts
│   ├── order/
│   │   ├── CreateOrderCommandHandler.ts
│   │   └── MergeFriesAndDrinkCommandHandler.ts
│   └── menu/
│       ├── CreateMenuCommandHandler.ts
│       └── AddSauceToMenuCommandHandler.ts
├── queries/
│   ├── burger/
│   │   ├── FindBurgerByRecipeQuery.ts
│   │   └── GetBurgerQuery.ts
│   ├── order/
│   │   ├── GetOrderQuery.ts
│   │   └── GetOrdersPaginatorQuery.ts
│   └── menu/
│       └── GetMenuQuery.ts
├── queryHandlers/
│   ├── burger/
│   │   ├── FindBurgerByRecipeQueryHandler.ts
│   │   └── GetBurgerQueryHandler.ts
│   ├── order/
│   │   ├── GetOrderQueryHandler.ts
│   │   └── GetOrdersPaginatorQueryHandler.ts
│   └── menu/
│       └── GetMenuQueryHandler.ts
├── dtos/
│   ├── BurgerDTO.ts
│   ├── OrderDTO.ts
│   └── MenuDTO.ts
├── events/
│   ├── order/
│   │   ├── OrderCreatedEvent.ts
│   │   └── OrderCompletedEvent.ts
│   ├── burger/
│   │   ├── BurgerFinishedEvent.ts
│   │   └── BurgerStatusChangedEvent.ts
│   ├── inventory/
│   │   ├── OutOfStockEvent.ts
│   │   └── LowStockEvent.ts
│   └── EventBus.ts
├── transactions/
│   ├── TransactionManager.ts
│   ├── OrderTransaction.ts
│   └── MenuTransaction.ts
└── index.ts
```

### Couche Domaine (Les Recettes & Règles)

```
domain/
├── entities/
│   ├── BurgerEntity.ts
│   ├── OrderEntity.ts
│   ├── MenuItemEntity.ts
│   └── CustomerEntity.ts
├── aggregates/
│   ├── menu/
│   │   ├── MenuAggregate.ts
│   │   └── MenuAggregateRoot.ts
│   └── order/
│       ├── OrderAggregate.ts
│       └── OrderAggregateRoot.ts
├── value-objects/
│   ├── common/
│   │   ├── AddressValueObject.ts
│   │   ├── PriceValueObject.ts
│   │   └── IdentifierValueObject.ts
│   ├── menu/
│   │   ├── RecipeValueObject.ts
│   │   └── IngredientValueObject.ts
│   └── order/
│       ├── OrderStatusValueObject.ts
│       └── OrderTimeValueObject.ts
├── domain-events/
│   ├── burger/
│   │   ├── BurgerCreatedEvent.ts
│   │   └── BurgerCookedEvent.ts
│   ├── menu/
│   │   ├── MenuCreatedEvent.ts
│   │   └── RecipeUpdatedEvent.ts
│   └── order/
│       ├── OrderPlacedEvent.ts
│       └── MealStatusChangedEvent.ts
├── repositories/
│   ├── BurgerRepository.ts
│   ├── OrderRepository.ts
│   ├── MenuRepository.ts
│   └── IRepository.ts
├── services/
│   ├── MenuPlannerService.ts
│   ├── QualityControlService.ts
│   ├── InventoryDomainService.ts
│   └── OrderProcessingService.ts
├── factories/
│   ├── BurgerFactory.ts
│   ├── MealFactory.ts
│   ├── OrderFactory.ts
│   └── MenuFactory.ts
├── specifications/
│   ├── FreshBurgerSpecification.ts
│   ├── ValidOrderSpecification.ts
│   ├── CompleteMenuSpecification.ts
│   └── ISpecification.ts
├── interfaces/
│   ├── IEntity.ts
│   ├── IAggregateRoot.ts
│   ├── IValueObject.ts
│   └── IDomainEvent.ts
├── exceptions/
│   ├── InvalidOrderException.ts
│   ├── MenuConfigurationException.ts
│   └── DomainException.ts
├── rules/
│   ├── GoldenRules.ts
│   ├── BurgerRules.ts
│   └── OrderRules.ts
└── index.ts
```

### Couche Infrastructure (Les Fondations Invisibles)

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

Et finalement, pour les projets en démarrage qui souhaitent adopter ces principes mais avec une structure plus légère, voici la version MVP qui permet de commencer rapidement tout en préservant les principes DDD :

```
mcdonalds-ddd/
├── interface/
│   ├── controllers/
│   │   ├── OrderController.ts
│   │   └── MenuController.ts
│   ├── routes/
│   │   └── api.routes.ts
│   ├── middlewares/
│   │   ├── AuthenticationMiddleware.ts
│   │   └── ErrorHandlingMiddleware.ts
│   └── dtos/
│       ├── OrderDTO.ts
│       └── MenuDTO.ts
├── application/
│   ├── services/
│   │   ├── OrderService.ts
│   │   └── MenuService.ts
│   ├── commands/
│   │   ├── CreateOrderCommand.ts
│   │   └── CreateMenuCommand.ts
│   ├── handlers/
│   │   ├── CreateOrderCommandHandler.ts
│   │   └── CreateMenuCommandHandler.ts
│   ├── queries/
│   │   ├── GetOrderQuery.ts
│   │   └── GetMenuQuery.ts
│   ├── queryHandlers/
│   │   ├── GetOrderQueryHandler.ts
│   │   └── GetMenuQueryHandler.ts
│   └── events/
│       ├── OrderCreatedEvent.ts
│       └── EventBus.ts
├── domain/
│   ├── entities/
│   │   ├── BurgerEntity.ts
│   │   └── OrderEntity.ts
│   ├── aggregates/
│   │   └── order/
│   │       └── OrderAggregate.ts
│   ├── value-objects/
│   │   ├── PriceValueObject.ts
│   │   └── IngredientValueObject.ts
│   ├── repositories/
│   │   ├── OrderRepository.ts
│   │   └── MenuRepository.ts
│   ├── services/
│   │   └── MenuPlannerService.ts
│   └── events/
│       └── BurgerCreatedEvent.ts
├── infrastructure/
│   ├── persistence/
│   │   ├── database/
│   │   │   └── DatabaseConnection.ts
│   │   └── orm/
│   │       └── EntityMappers.ts
│   ├── repositories/
│   │   ├── OrderRepositoryImpl.ts
│   │   └── MenuRepositoryImpl.ts
│   ├── services/
│   │   └── LoggingService.ts
│   └── config/
│       └── AppConfig.ts
└── index.ts
```

Comme McDonald's qui a transformé un simple stand de hamburgers en un empire mondial, cette architecture évolutive permet de grandir tout en préservant les principes fondamentaux qui font son succès.