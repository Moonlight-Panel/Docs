# Diagnose

Adding custom entries to the diagnose file

**Methods**

```C#
Task GenerateReport(ZipArchive archive, IServiceProvider serviceProvider)
```

These functions will be async called and provide access to the in-memory zip archive and the current depedency injection provider. With these two, you are able to resolve any service and add text, files, and more to the diagnose zip archive, which will be returned to the user after all diagnose actions have been called. If you want to consume scoped services, you need to create a scope via the serviceProvider first, as it is a root service provider.

Example:
```C#
public class PluginsDiagnoseAction : IDiagnoseAction
{
    public async Task GenerateReport(ZipArchive archive, IServiceProvider serviceProvider)
    {
        var pluginService = serviceProvider.GetRequiredService<PluginService>();
        
        var content = "Loaded plugins:\n\n";
        
        foreach (var plugin in await pluginService.GetLoadedPlugins())
        {
            content += $"Name: {plugin.Name}\n";
            content += $"Author: {plugin.Author}\n";
            content += $"Issue Tracker: {plugin.IssueTracker}\n";
            content += $"Assembly name: {plugin.GetType().FullName}\n";
            content += "\n";
        }
        
        await archive.AddText("plugins.txt", content);
    }
}
```