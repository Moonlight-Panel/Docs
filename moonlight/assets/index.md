# Asset Management

In Moonlight, a feature can add assets to to moonlight, like JavaScript files, Images and Stylesheets. This documentation article will cover how developers can add assets to their features and how panel administrator can override assets.

## How to Override Assets in Moonlight

**Introduction:**
In Moonlight, you can customize various assets like logos and styles to tailor your system to your preferences. This guide will walk you through the process of overriding assets, allowing you to replace default assets with your own custom ones.

**Understanding Asset Storage:**
Moonlight stores its assets using a structured approach. When you inspect the source file for an asset, such as the favicon, you'll notice a path like `/api/core/asset/Core/svg/logo.svg`. This path reveals how assets are accessed through Moonlight's API.

**API Structure:**
Assets are served via Moonlight's API, specifically the `core` API, with the path `/api/core/`. Assets are accessed through the `/asset/` route on the API.

**Identifying Asset Features:**
The next part of the asset path, such as `/Core/`, indicates the name of the feature to which the asset belongs. This name may vary depending on the specific feature.

**Locating the Desired Asset:**
The remaining part of the path, such as `/svg/logo.svg`, specifies the exact location of the desired asset within its feature.

**Overriding Process:**
To override an asset, open Moonlight in your web browser and navigate to _System => Files_. Here, you'll find the file manager. Open the `assetOverride` folder.

**Replacing Assets:**
Suppose you want to replace the asset `/api/core/asset/Core/images/image.png`. Start by creating a folder with the name of the asset's feature, such as `/Core`. Within this folder, create a folder named `images` to match the original asset's directory structure. Now, upload your desired replacement file (e.g., a `.png` file) into this folder. It's crucial that the replacement file has the same name as the original asset for the override to work properly.

**Examples:**
The table below illustrates examples of how asset paths map to their override paths.

| Api Path                                   | Asset Override path        |
| ------------------------------------------ | -------------------------- |
| `/api/core/asset/Servers/styles/style.css` | `Servers/styles/style.css` |
| `/api/core/asset/Core/img/logo.png`        | `Core/img/logo.png`        |

**Conclusion:**
By following this guide, you can easily override default assets in Moonlight, enabling you to personalize your system's appearance to better suit your needs and preferences.

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
