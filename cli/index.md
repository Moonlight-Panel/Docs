### Moonlight CLI

The moonlight cli is a usefull tool for installing, updating and administrating moonlight instances.
It loads the scripts from our script server in order to ensure you are up to date.
The cli has multiple modules. For managing moonlight you have the `moonlight` module. You can call a module by executing
```
mlcli <module name> <subcommand> <parameters>
```

#### Module: Installer
This module helps with the installation of the panel and the daemon.
It has the following commands:

```
mlcli install <subcommand> <parameters>
```

| Subcommand | Description |
|------------|-------------|
| run | Runs the current installed version of the installer (located in the /tmp directory). If no local version exists, it fetches the latest one from our servers |
| update | Replaces the current installed version of the installer with the latest one from our servers |


#### Module: Moonlight
This module helps with the administration of the panel.
It has the following commands:

```
mlcli moonlight <subcommand> <parameters>
```

| Subcommand | Description |
|------------|-------------|
| config | Opens the core.json config file in the nano text editor. Requires nano to be installed |
| logs | Shows the logs of the moonlight container if installed |
| restart | Restarts the moonlight and the integrated database container if installed |
| login | Searches through the logs of moonlight to find the default login credentials |

#### Module: Daemon
This module helps with the administration of the daemon.
It has the following commands:

```
mlcli daemon <subcommand> <parameters>
```

| Subcommand | Description |
|------------|-------------|
| config | Opens the config.json config file in the nano text editor. Requires nano to be installed |
| logs | Shows the logs of the daemon |
| restart | Restarts the daemon |
| status | Shows the status of the daemon |