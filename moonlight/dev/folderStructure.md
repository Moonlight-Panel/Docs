#### Moonlights folder structure

```
Moonlight
├───Core // The place for all of moonlights core stuff
│   ├───Configuration // The models for the config files used by the core
│   ├───Database
│   │   ├───Entities // Database entities
│   │   └───Migrations // Database migrations
│   ├───Extensions
│   │   └───Attributes
│   ├───Helpers
│   ├───Http // All http endpoint (mostly api) related stuff
│   │   ├───Controllers
│   │   ├───Middleware
│   │   ├───Requests
│   │   └───Resources
│   ├───Models // Just model classes ig
│   │   ├───Abstractions
│   │   ├───Enums
│   │   └───Forms
│   ├───Repositories // All repos for saving data
│   ├───Services // All core services
│   └───UI
│       ├───Components // Core ui components
│       │   ├───Alerts
│       │   └───Partials
│       ├───Layouts
│       └───Views // Pages
|
├───Features // All features of moonlight are contained here
├───Pages // For asp.net
├───Styles // Contains the default theme .scss
└───wwwroot 
    ├───css // Add custom css files here (e.g. for libraries)
    ├───editor // ACE Editor, probably irrelevant for you
    ├───fonts // Add custom fonts here
    ├───img // Add custom images here
    ├───js // Add custom javascript here (e.g. for libraries)
    └───svg // Add custom svgs here
```

#### Plugin/Feature folder structure

```
└───Features // Put all your features here
    └───Dummy
        ├───DummyFeature.cs // The class defining the feature
        ├───Configuration // All config models go here
        ├───Entities // All database entities should be placed here
        ├───Helpers
        ├───Http // Http api stuff
        │   ├───Controllers
        │   ├───Middleware
        │   ├───Requests
        │   └───Resources
        ├───Models
        │   ├───Abstractions
        │   ├───Enums
        │   └───Forms
        ├───Services // Put your services here
        └───UI // UI stuff
            ├───Components
            └───Views
```