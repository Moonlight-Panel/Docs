# Features

To start developing your feature, you need to add a new feature class. So add a class in the folder of your feature (for the folder structure, see here [folder structure](Folder-structure.md). After that, add the following methods to the class and make it a subclass of `MoonlightFeature`. Also, don't forget to modify the constructor.

```C#
public class DummyFeature : MoonlightFeature
{
    public DummyFeature()
    {
        Name = "Dummy";
        Author = "MasuOwO";
        IssueTracker = "your issue tracker url";
    }
    
    public override async Task OnPreInitialized(PreInitContext context)
    {
    
    }
    
    public override async Task OnInitialized(InitContext context)
    {
    
    }
    
    public override async Task OnUiInitialized(UiInitContext context)
    {
    
    }
}
```

#### Initialization
Features have three different stages of initialization

##### 1. Pre-Init
In this stage, services should be added to the service collection and the Kestrel web server config if needed. The context object passed into the `OnPreInitialized` function, which you need to override in order to process it, you have two objects. One is the `WebApplicationBuilder` which can be used to configure services, and the asp.net Kestrel web server. The other is a list of assemblies which will be scanned for services. You should not modify this list at all as it may break other features and/or moonlight's core

##### 2. Init
This stage is invoked after the web application has been built and the service collection has been constructed. The context object of this handler which is passed into the `OnInitialized` method contains the `WebApplication` object. With this object, you are able to load services from the dependency injection, configure the mapping, and more Kestrel options

##### 3. Ui-Init
The third and last main feature stage is the UI init stage. In this stage, you can enable the Blazor page routing and add sidebar items using the provided `UiInitContext` in the `OnUiInitialized`.

To enable the page routing, just add the following method call in the `OnUiInitialized` method.

```C#
context.EnablePages<YourFeatureClass>();
```

YourFeatureClass is the name of the class defining the feature.

To add a sidebar item, just add the following call to the `OnUiInitialized` method:

```C#
context.AddSidebarItem("Dashboard", "bxs-dashboard", "/admin", needsExactMatch: true, isAdmin: true, index: 10324);
```

Parameters:
1. Name of the sidebar item
2. The icon of the sidebar item (see [https://boxicons.com/](https://boxicons.com/) for a reference)
3. The target of your sidebar item

Optional parameters
- needsExactMatch: This defines the behavior of the active page detection. If this is true, the url of the user needs to be exactly the same as the target url to be detected as active. If it is set to false (default), it will check if the user's url starts with the target.
- isAdmin: This defines whether to show the sidebar item only to admins or not. This also moves the item to the admin section of the sidebar.
- index: The higher this number is, the lower it will be in the sidebar. This will help you adjust the position of the sidebar.