### Moonlight CLI

The moonlight cli is a usefull tool for installing, updating and administrating moonlight instances.
It loads the scripts from our script server in order to ensure you are up to date.
The cli has multiple modules. For managing moonlight you have the `moonlight` module. You can call a module by executing
```
mlcli <module name> <parameters>
```


#### Module: Moonlight
This module helps with the installation and administration of the panel.
It has the following commands:

| Subcommand | Description |
|------------|-------------|
| install | Installs the panel to the current maschine. Used by the web configurator |
| uninstall | Removes the moonlight installation from the current maschine|
| config | Opens the core.json config file in the nano text editor. Requires nano to be installed |
| logs | Shows the logs of the moonlight container if installed |
| restart | Restarts the moonlight and the integrated database container if installed |