### Getting started
***This project still in development, changes may occur***

Start hosting servers with moonlight in a few simple steps.

Requirements:
- An Ubuntu Linux server
- The ability to run Docker
- 4 GB of memory (recommended; can work with less)
- 20GB of disk space
- 2 Cores

**Step 1: Install moonlight panel**

Login into the server you want to install the panel on and run the following command

```bash
bash <(curl https://get-moonlight.app)
```

and select the "Moonlight Panel" and then "Install". It will guide you through the installation.

**Step 2: Login into the panel**

Open the panel with the URL shown by the installer, execute the following command, and login with the credentials shown:
```
mlcli moonlight login
```

**Step 3: Add a node**

Go to Servers => Nodes and add a new node. After adding a node, go to the setup page and follow the instructions.

*NOTE: If you are installing the panel and the node on the same server and you are using https with the panel, add the `--skip-lets-encrypt` option to the generated command shown by moonlight*

After the installation is finished, you should see information about the node in the information page of the node. If it shows data, the node has been successfully installed.

> Please note that your have an File in ``/etc/moonlight/config.json`` you must Delete the File to Run the Deamon Command.

**Deamon Error Error**:

If you Deamon can't install and you get this error:
```
E: Unable to locate package dotnet-sdk-7.0
E: Couldn't find any package by glob 'dotnet-sdk-7.0'
```
Then you need to install the Dotnet SDK 7.0 
> ### Link to microsoft: 
> - https://learn.microsoft.com/de-de/dotnet/core/install/linux-ubuntu-install?pivots=os-linux-ubuntu-2204&tabs=dotnet7
> - https://learn.microsoft.com/de-de/dotnet/core/install/linux-ubuntu-install?pivots=os-linux-ubuntu-2204&tabs=dotnet7#ubuntu-2204

#### Command - Copy Paste:<br>
*(Work on Ubuntu 22.4)*
```
sudo apt-get update && sudo apt-get install -y dotnet-sdk-7.0
```


**Step 4: Add allocations**

Go to the allocations tab of the node you added in the previous step and use the quick adder to add some allocations. Please keep in mind moonlight will **not** adjust the filewall rules for the node when adding allocations.

**Step 5: Import a pterodactyl egg**

Go and find your favorite pterodactyl egg. If you dont know any, you can use [this](https://github.com/parkervcp/eggs/blob/master/game_eggs/minecraft/java/purpur/egg-purpur.json) egg

Then go to Servers => Images and press "Import Egg". After importing, you should see the image in your list. For more information about images (and eggs) have a look [here](/moonlight/images)

**Step 6: Create your first server**

Go to Servers and create a new server. Select your user and the imported image and submit it. Then go to the user server list and the server should appear in your list. Click on it to manage it.