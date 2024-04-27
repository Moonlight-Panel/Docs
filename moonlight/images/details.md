### Details about images and their configuration

#### Donate URL
The donate url is a way to link a website of your choice in an image to allow the community to thank you for your work. If a donate url is set, it will display a donate button in the image overview, linking to the website.

#### Update URL
The update URL provides an easy way to keep images up-to-date. When updating an image, this url will be fetched, and the result will be interpreted as the new image configuration in a JSON format. An example usage would be to set the update url to the `raw.githubusercontent.com` raw link of the image json in your github repo. With this, the users of your image will be able to fetch the latest version without the need to lookup your github repo.

#### Startup Command
The startup command defines the command that will be executed at the start of a server lifecycle. Variables in this command need to be handled by the Docker image of the moonlight image. Moonlight does **not** parse the startup command in any way (yet).

#### Stop Command
The stop command can be either a text you want to send to the server's standard input or a SIG command. To specify a text, just type it. If you want to specify a SIG command, put a `^` before the name of the SIG command. For example, to send a SIGKILL when a user requests the stop of a server, write `^SIGKILL` into the stop command. `^C` will emit a `SIGINT` signal.

#### Parse configurations
The parse configuration defines how moonlight will parse defined configuration files.

To start, add a new configuration and specify a relative file path. Then specify a type, which will define what parser to use.

Current implemented types:
- file
- properties

After that, add a new key-value definition by pressing the plus button.
Specify the key and the value. To use variables, write the variable in double brackets. So for a variable called `MINECRAFT_VERSION` you would write `{{MINECRAFT_VERSION}}`.

#### Variables

Variables allow users and admins to define the server's behavior, e.g., specify the Minecraft version you want to use on a Minecraft image.
Variables will be passed as environment variables to the server container. There are also default and unmodifiable variables you can use.

Default variables:
- `SERVER_PORT`: The default allocation port
- `ML_PORT_X`: Where the X stands for the index of the allocation. So if you want to use the second allocation of a server, use `ML_PORT_1`.
- `SERVER_MEMORY`: The amount of memory the server has allocated in megabytes.

Variable options:
- **Key**: Defines the environment variable name
- **Default value**: The default value to set the variable to when a server is created
- **Display name**: This is the display name of the variable, which will be shown to the user if enabled to edit/view the variable
- **Description**: This text should describe what the variable does for the user if allowed to view and/or change
- **Allow edit**: Allow the user to edit the variable. Won't work if view is disabled
- **Allow view**: Allow the user to view the variable but not edit it unless specified otherwise
- **Type**: Specifies the type of the variable. This specifies what ui the user will see for the variable. You can also specify the options that are available using the filter field.
- **Filter**: The behavior of this field depends on the type. See below

Filter behavior:
- Text: The user's input will be checked against the filter value, which is interpreted as a regex expression
- Toggle: If the filter is set to `boolean` the value of the toggle will be written as `true` or `false`. If not, it will be saved as `1` or `0`
- Select; The filter value represents the available options for the select separated by a `;`
- Number: *None*

#### Docker images:
This defines the available Docker images to use for the server container. You are also able to select the default Docker image that will be used if a new server is going to be created. It's also possible to allow the user to change the image himself.

A Docker image definition has multiple options:
- **Name**: This is the name of the Docker image. E.g. moonlightpanel/moonlight:canary
- **Display Name**: This will be shown if the user is able to change the Docker image as the image name
- **Auto Pull**: Specifies if the Docker image should be pulled/updated when creating a server instance. Disable this for only local existing Docker images


#### Installation

The installation section defines what to do when a server is going to be created. Install the required software and download files using this section.

The **Install Shell** property defines what shell to pass the install script to. The install Docker image defines what Docker image to use when running the installer. This is a good way to use dependencies without installing them in the install script.

Then there is a script editor that contains the install script, which will be executed when a server is reinstalled or created. You have two mounts to use when working in the install script:
- `/mnt/install`: A temporary storage for the installation process
- `/mnt/server`: The server volume (or virtual disk) is mounted at this point, so you are able to copy and download files in order for your server to be able to run here

The variables described a few sections above are also available here to use as environment variables. The output of the install script will be printed to the server console and, as such, is visible to the user, so make sure no sensitive data is printed in the install process