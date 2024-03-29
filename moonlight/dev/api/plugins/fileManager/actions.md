#### IFileManagerAction

> Adding custom context menu actions for the file manager

**Properties**

```public string Name { get; }```

The name which will be shown in the context menu

```public string Icon { get; }```

The boxicons icon which will be shown next to the name

```public string Color { get; }```

The bootstrap color to use for the icon

```public Func<FileEntry, bool> Filter { get; }```

A filter function which will determin if the context action you are adding will show on the current file

**Methods**

```Task Execute(BaseFileAccess access, FileView view, FileEntry entry, IServiceProvider provider)```

This function will be called when the user has clicked on your context menu action. It provides the current file access, the file view which you need to refresh if anything has changed, the file entry the context menu has been called on and a scoped service provider to access services like the ToastService for displaying information

Example:
```
public class DeleteFileManagerAction : IFileManagerAction
{
    public string Name => "Delete";
    public string Icon => "bxs-trash";
    public string Color => "danger";
    public Func<FileEntry, bool> Filter => _ => true; // Results in being shown for every file

    public async Task Execute(BaseFileAccess access, FileView view, FileEntry entry, IServiceProvider serviceProvider)
    {
        await access.Delete(entry);

        await view.Refresh();

        var toastService = serviceProvider.GetRequiredService<ToastService>();
        await toastService.Success("Successfully deleted item");
    }
}
```