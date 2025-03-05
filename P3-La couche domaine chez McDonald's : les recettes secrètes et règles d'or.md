# La couche domaine chez McDonald's : les recettes secrètes et règles d'or

Nous voilà maintenant dans le cœur battant de McDonald's - bien au-delà du comptoir accueillant et des managers affairés. Bienvenue dans cette cuisine sacrée où les règles fondamentales ne se négocient pas, où les recettes originales sont jalousement gardées, où l'essence même du Big Mac prend forme. Bienvenue dans la couche domaine.

## Les entités : les produits iconiques

Regardez ce Big Mac. Ce n'est pas simplement un sandwich - c'est une entité emblématique avec sa propre identité, ses règles de composition, son intégrité à préserver. Le Big Mac possède un état (ses ingrédients), un comportement (comment il doit être assemblé) et une identité unique (ce qui le distingue du McChicken).

Dans votre architecture, `BurgerEntity.ts` représente précisément cela - une entité riche avec un cycle de vie, des règles et une identité propre. Comme le Big Mac ne serait pas authentique sans sa sauce spéciale, une entité domaine n'est pas complète sans ses comportements encapsulés.

Les entités sont les centres de gravité de votre modèle, gouvernant leur propre monde avec autorité. Elles ne s'inquiètent pas de la persistance ou de l'interface utilisateur - elles se concentrent uniquement sur l'expression fidèle des règles métier fondamentales, comme un chef McDonald's se concentre sur la perfection de chaque hamburger sans se soucier du marketing.

## Les événements de domaine : les moments de vérité

"Le steak vient d'atteindre sa cuisson parfaite." "La recette du Big Mac a été mise à jour au niveau mondial." Ces moments critiques dans l'univers McDonald's sont l'équivalent de vos événements de domaine.

Dans votre dossier `domain-events`, `BurgerCreatedEvent.ts` ou `MealStatusChangedEvent.ts` capturent ces moments de vérité - des faits immuables qui se sont produits dans le domaine et qui peuvent déclencher d'autres actions en cascade.

Contrairement aux simples notifications, ces événements sont des éléments de première classe dans votre modèle. Ils enregistrent l'histoire de votre domaine comme le livre des recettes McDonald's enregistre l'évolution de ses créations culinaires.

## Les value objects : les ingrédients précis

La sauce spéciale du Big Mac n'a pas d'identité propre - c'est sa composition exacte qui compte. Une portion de sauce est parfaitement interchangeable avec une autre portion identique.

Vos `AddressValueObject.ts`, `IngredientValueObject.ts` ou `RecipeValueObject.ts` incarnent cette même philosophie - des objets immuables définis uniquement par leurs attributs, sans identité propre. Une adresse est une adresse, un ingrédient est un ingrédient - peu importe leur instance spécifique tant que les valeurs sont identiques.

Ces objets sont les gardiens de l'intégrité des données. Comme McDonald's ne tolère pas la moindre variation dans la composition de sa sauce spéciale, vos value objects garantissent que certaines structures de données respectent rigoureusement leurs règles de validation.

## Les agrégats : les menus complets

Un Happy Meal n'est pas simplement la somme de ses composants - c'est un concept cohérent qui regroupe burger, frites, boisson et jouet sous une entité logique unique.

Vos agrégats fonctionnent de la même manière - ils regroupent des entités et value objects connexes sous un gardien unique qui maintient leur cohérence collective. L'agrégat `Order` peut contenir plusieurs `MenuItem`, mais c'est `Order` qui garantit la cohérence de l'ensemble.

Comme le manager qui vérifie qu'un Happy Meal est complet avant de le servir, l'agrégat est le garant des invariants qui s'appliquent à un groupe d'objets plutôt qu'à des éléments individuels.

## Les repositories : les gestionnaires de stock

Dans les coulisses de McDonald's, des systèmes sophistiqués gèrent le stock d'ingrédients sans que les cuisiniers aient à se préoccuper des détails de stockage.

De même, vos `BurgerRepository.ts` ou `OrderRepository.ts` permettent au domaine de rester pur, en abstraisant les mécanismes de persistance. Ils offrent l'illusion que les entités sont simplement stockées et récupérées en mémoire, tout comme un cuisinier McDonald's peut se concentrer sur la préparation des hamburgers sans penser aux systèmes logistiques complexes qui assurent la disponibilité des ingrédients.

## Les domain services : les procédures spéciales inter-produits

Certaines opérations chez McDonald's ne concernent pas un produit unique mais plusieurs éléments - comme la coordination entre la préparation des burgers et des frites pour qu'ils soient prêts simultanément.

Vos `DomainService.ts` ou `MenuPlannerService.ts` gèrent précisément ce type de logique qui traverse plusieurs entités ou agrégats. Ce ne sont pas des coordinateurs d'application - ils contiennent une véritable logique métier qui ne trouve naturellement sa place dans aucune entité individuelle.

## Les specifications : les critères de qualité

"Un hamburger est considéré parfaitement cuit lorsque..." McDonald's dispose de spécifications précises pour chaque aspect de ses produits.

En code, vos spécifications sont des objets qui encapsulent des critères métier particuliers. `FreshBurgerSpecification.ts` ou `ValidOrderSpecification.ts` pourraient définir exactement ce qui constitue un burger frais ou une commande valide, permettant d'évaluer ces conditions de manière cohérente à travers l'application.

## Les factories : les stations d'assemblage

Dans un McDonald's efficace, certaines stations sont dédiées à l'assemblage de produits spécifiques selon des procédures standardisées.

Vos `BurgerFactory.ts` ou `MealFactory.ts` jouent ce rôle - ils encapsulent la logique de création d'entités ou d'agrégats complexes, garantissant que tous les objets sont correctement initialisés et que les règles métier sont respectées dès la création.

## Le langage omniprésent : parler McDonald's

Remarquez comment, dans un McDonald's, tout le monde - du caissier au manager - utilise le même vocabulaire spécifique : "Happy Meal", "BigMac", "McNuggets". Ce langage partagé est le ciment qui unit toutes les équipes.

Dans votre domaine, ce langage omniprésent se reflète dans chaque classe, méthode et propriété. Le code devient une traduction directe des concepts métier, créant un pont naturel entre les experts du domaine et les développeurs.

## En résumé : l'essence inaltérable

La couche domaine de McDonald's est ce qui reste constant à travers le temps et l'espace. Que vous soyez à Tokyo ou à Paris, que vous commandiez via une borne tactile ou au comptoir, l'essence d'un Big Mac reste la même.

De même, votre couche domaine représente le cœur inaltérable de votre système - indépendant des mécanismes de persistance, des interfaces utilisateur ou des protocoles de communication. Elle exprime ce que votre entreprise EST, pas simplement ce qu'elle FAIT.

Comme McDonald's a construit son empire global sur la consistance inébranlable de ses produits fondamentaux, une architecture DDD bien conçue repose sur un domaine solide qui capture fidèlement les règles essentielles de l'entreprise - ces vérités qui resteraient vraies même si vous changiez complètement de technologie ou d'infrastructure.

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

![CDomain](<https://github.com/phamhung075/MDDD/blob/main/CDomain.png>)