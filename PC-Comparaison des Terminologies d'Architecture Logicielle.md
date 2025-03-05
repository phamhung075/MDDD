# Comparaison des Terminologies d'Architecture Logicielle

Ce document compare les différentes terminologies utilisées dans l'architecture logicielle, notamment entre le Domain-Driven Design (DDD) tel que présenté dans l'analogie McDonald's et d'autres approches courantes dans le développement frontend moderne.

## Niveau 1: Architecture Globale

```
DDD (McDonald's)                | Frontend Moderne                | Autres Appellations
--------------------------------|---------------------------------|-------------------------
Interface Layer (Comptoir)      | Presentation Layer              | View Layer / UI Layer
Application Layer (Managers)    | Application Layer               | State Management / Controller Layer
Domain Layer (Recettes)         | Business Logic Layer            | Core / Model Layer
Infrastructure Layer (Fondation)| Services Layer                  | API / External Services Layer
```

## Niveau 2: Couche Interface/Présentation

```
DDD (McDonald's)                | Frontend Moderne                | Autres Appellations
--------------------------------|---------------------------------|-------------------------
Controllers                     | Components                      | Views / Screens
Routes                          | Router                          | Navigation
Validation                      | Form Validation                 | Validators / Schemas
Events                          | Event Handlers                  | Listeners
Adapters                        | Adapters / HOCs                 | Wrappers / Decorators
Transformers                    | Mappers / Transformers          | Converters / Formatters
Middlewares                     | Middleware                      | Interceptors
Errors                          | Error Boundaries                | Exception Handlers
```

## Niveau 3: Couche Application/State Management

```
DDD (McDonald's)                | Frontend Moderne                | Autres Appellations
--------------------------------|---------------------------------|-------------------------
Services                        | Services / Store                | Managers / Providers
Commands                        | Actions                         | Mutations (Vuex) / Dispatchers
Handlers                        | Reducers                        | Effects (NgRx) / Sagas (Redux-Saga)
Queries                         | Selectors                       | Getters / Computed (Vue)
QueryHandlers                   | Query Hooks                     | Custom Hooks / Composables (Vue)
DTOs                            | Interfaces / Types              | Models / Schemas
Events                          | Events / Signals                | Observables / Streams
Transactions                    | Batch Updates                   | Atomic Operations
```

## Niveau 4: Couche Domaine/Business Logic

```
DDD (McDonald's)                | Frontend Moderne                | Autres Appellations
--------------------------------|---------------------------------|-------------------------
Entities                        | Models                          | Records / Data Classes
Aggregates                      | Composite Models                | Compound Objects
Value Objects                   | Immutable Objects               | Props / ReadOnly Types
Domain Events                   | Domain Signals                  | Business Events
Repositories                    | Data Access Objects             | Stores / Model Managers
Domain Services                 | Business Logic Services         | Use Cases / Interactors
Factories                       | Factory Functions               | Creators / Constructors
Specifications                  | Predicates / Validators         | Rules / Conditions
```

## Niveau 5: Couche Infrastructure/Services

```
DDD (McDonald's)                | Frontend Moderne                | Autres Appellations
--------------------------------|---------------------------------|-------------------------
Persistence                     | API Clients / Storage           | Data Sources / Clients
Repository Implementations      | API Services                    | Data Providers / Connectors
Services                        | External Services               | Utilities / Helpers
Adapters                        | Service Adapters                | Wrappers / Clients
Config                          | Environment Config              | Settings / Constants
Jobs                            | Background Tasks                | Workers / Processes
External                        | Third-party Integrations        | External APIs / SDKs
```

## Approches Spécifiques dans le Frontend Moderne

### React

```
├── components/           # Équivalent à Interface Layer
│   ├── ui/               # Composants réutilisables
│   └── pages/            # Composants de pages
├── hooks/                # Logic partagée (Application Layer)
├── context/              # State management global
├── store/                # Redux/Zustand (Application Layer)
│   ├── actions/          # Équivalent à Commands
│   ├── reducers/         # Équivalent à Handlers
│   └── selectors/        # Équivalent à Queries
├── services/             # API et services externes (Infrastructure)
├── utils/                # Fonctions utilitaires
└── types/                # TypeScript types/interfaces
```

### Angular

```
├── components/           # Équivalent à Interface Layer
│   ├── ui/               # Composants réutilisables
│   └── pages/            # Composants de pages
├── services/             # Services Angular (Application + Infrastructure)
├── state/                # NgRx/Signals (Application Layer)
│   ├── actions/          # Équivalent à Commands
│   ├── reducers/         # Équivalent à Handlers
│   ├── effects/          # Équivalent à Effects/Side-effects
│   └── selectors/        # Équivalent à Queries
├── models/               # Interfaces/Classes (Domain Layer)
├── interceptors/         # HTTP Interceptors (Infrastructure)
└── guards/               # Route Guards (Infrastructure)
```

### Vue

```
├── components/           # Équivalent à Interface Layer
│   ├── ui/               # Composants réutilisables
│   └── views/            # Composants de pages
├── composables/          # Composition API functions (Application Layer)
├── store/                # Pinia/Vuex (Application Layer)
│   ├── actions/          # Équivalent à Commands
│   ├── mutations/        # Équivalent à Handlers
│   └── getters/          # Équivalent à Queries
├── services/             # API et services externes (Infrastructure)
├── utils/                # Fonctions utilitaires
└── types/                # TypeScript types/interfaces
```

## Feature-First vs Layer-First

### Organisation par Couche (Layer-First)

```
src/
├── interface/            # Tous les éléments d'interface
├── application/          # Toute la logique d'application
├── domain/               # Tous les modèles et règles métier
└── infrastructure/       # Tous les services externes et config
```

### Organisation par Fonctionnalité (Feature-First)

```
src/
├── features/
│   ├── auth/             # Fonctionnalité d'authentification
│   │   ├── components/   # Interface (UI)
│   │   ├── store/        # Application (State)
│   │   ├── models/       # Domain (Business Logic)
│   │   └── services/     # Infrastructure (API)
│   ├── orders/           # Fonctionnalité de commandes
│   │   ├── components/
│   │   ├── store/
│   │   ├── models/
│   │   └── services/
│   └── ...
├── shared/               # Éléments partagés entre fonctionnalités
└── core/                 # Éléments fondamentaux de l'application
```

## Modèles de Communication

### Flux Unidirectionnel (One-way Data Flow)

```
Action → Dispatcher → Store → View
   ↑                            |
   └----------------------------↓
```

### DDD Communication

```
Interface → Application → Domain ← Infrastructure
```

### Component Communication in Component-based architectures

```
Props Down → Components → Events Up
```

### Flux & Redux

```
Actions → Reducers → Store → Components
```

### Reactive Programming

```
Sources → Operators → Subscribers 
```
