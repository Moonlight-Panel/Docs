# Asset Management

In Moonlight, a feature can add assets to to moonlight, like JavaScript files, Images and Stylesheets. This documentation article will cover how developers can add assets to their features and how panel administrator can override assets.

## Overiding assets

To understand how to override assets, we need to understand how assets are stored by moonlight. If you open the browser devtools, and look for the source file for the favicon, you will see the path `/api/core/asset/Core/svg/logo.svg`.

We can see that moonlight is providing its assets via an api, to be exact, the `core` api (path is `/api/core/`). Assets are served over the `/asset/` route on the api.

The next part of the path is `/Core/`, which represents the name of the assets feature. This name varies for different features.

`/svg/logo.svg` represents the actual path of the wanted ressource. **This text is relevant for overriding ressources with Moonlight.**

To override an asset, open Moonlight in your preferred browser and navigate to _System => Files_. You will now see a filemanager, open the `assetOverride` folder.

Lets now say you want to override the asset `/images/image.png`. As the file is in the `/images` folder, you create a folder named `images` (the same name is important, otherwise it wont work). Now, you can upload your desired file (in this case a `.png` file) you want to replace the original asset with. It **must** have the same name as the original asset, otherwise it won't work.

### Here are some more examples how asset overriding works

| Api Path                                   | Asset Override path |
| ------------------------------------------ | ------------------- |
| `/api/core/asset/Servers/styles/style.css` | `/styles/style.css` |
| `/api/core/asset/Core/img/logo.png`        | `/img/logo.png`     |

## For feature developers

**This step by step guide will show you how you can add custom assets to your feature.**
Lets say you wanted to create an image for your feature

1. Create a folder in the `/Assets` Folder, which represents your features name (it don't has to be your exact features name, you it just has a representative purpose), for example `/Assets/Test`.

2. Create a folder or the folders, where your image should be saved, lets say you want to save it in `/images/test/image.png`, so you create this folder.

_(We are now in `/Assets/Test/images/test`)_

3. Save your image in this folder, the path to the image in our example would now be `/Assets/Test/images/test/image.png`.

4. Navigate to your `Feature.cs` file, and go to your `OnPreInitialized` Task. There you can add your asset to the assets api. Use `context.AddAsset("{FEATURE_NAME}", "{FILEPATH}");` to add an asset. **The feature name must be the same name as the folder you created in step 1.** The file path is the path is the same as the path for the asset in step 2.

5. You can now access your asset via this api url: `/api/core/assets/Test/images/test/image.png`

**Here are some more examples:**

| Feature Name | Path in `/Assets` folder             | AddAsset function                                    | Api url for your asset                        |
| ------------ | ------------------------------------ | ---------------------------------------------------- | --------------------------------------------- |
| `Support`    | `/Assets/Support/styles/styles.css`  | `context.AddAsset("Support", "styles/styles.css");`  | `/api/core/assets/Support/styles/styles.css`  |
| `Billing`    | `/Assets/Billing/images/success.png` | `context.AddAsset("Billing", "images/success.png");` | `/api/core/assets/Billing/images/success.png` |
