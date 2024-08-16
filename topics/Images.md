# Images

##### What are images?

Images define a server type to use for a server. An image consists of the following components:

- Name, Author
- Update URL, Donate URL
- A startup and stop command
- Online detection via regex matches
- Automatic config file parsing configuration
- Variables to configure the server's behavior
- A selection of Docker images the server can use
- A installation script for server data and software

If you want to learn more about the configuration of images and/or want to create your own images, have a look at the [details](Configuration-Details.md)

##### Find images:

> Disclaimer: We do **not** support third party images. If you have issues with a third-party developer, contact them.

Links:
- [Official github repository](https://github.com/Moonlight-Panel/Images)
- [Moonlight Discord #images](https://discord.gg/TJaspT7A8p)

##### Import images

You can import images in the image admin menu

_Sidebar => Servers (Admin) => Images_

Click on the "Import" button. A file dialog will open where you need to select the image JSON file. After selecting one, the image will be imported.

##### Pterodactyl Eggs

Moonlight offers a import tool for pterodactyl eggs, which allows you to automatically convert images from the pterodactyl egg format to the moonlight image format. The import works on most eggs, some might need some adjustments. To import a pterodactyl egg click on "Import Egg" in the same menu as described above and select the egg json file you want to import.