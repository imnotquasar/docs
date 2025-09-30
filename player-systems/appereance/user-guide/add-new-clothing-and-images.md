# Add New Clothing & Images

Adding new clothing to your server is simple and fully automated with the built-in image capture system included in `qs-appearance`. This system generates visual previews of all clothing items, allowing players to browse items with images instead of blank slots.

***

## How It Works <a href="#basic-use-of-crafting" id="basic-use-of-crafting"></a>

{% hint style="danger" %}
#### **IMPORTANT**&#x20;

After running the `/save-images` command, the system will capture images of all clothing items based on your selection (either all at once or in fragments, depending on your configuration in the menu). Once the process is complete and all images have been generated, you **must restart your server or script** to ensure they are properly indexed and displayed in the wardrobe and store interfaces.
{% endhint %}

Quasar Appearance includes an automatic image generation tool that captures preview images of every clothing item in your server. This means you don’t need to manually upload or configure image files.

If you add custom clothing packs or new DLC content, simply use the following command in-game:

```
/save-images
```

Once executed, the system will begin capturing images of **all clothing items**, including new and existing ones. This process ensures that every item is visualized correctly in the wardrobe and store interfaces.

***

## No Server Storage Required

All generated images are **hosted externally by Quasar Store through FiveManage.com**, so this feature **only uses your FiveManage token** for image saving.\
This means it does **not consume any storage or bandwidth from your server**. Everything is stored and served securely through our CDN, keeping performance high and maintenance minimal.

***

## How to use Fivemanage token

When you finish generating and saving clothing images, you **must disable** the option:

```lua
Config.ImageSaver.enable = false
```

If you leave it enabled, your **FiveManage token** could be exposed and players may steal it.

Your token must be placed here:

```lua
-- qs-appearance/config/fivemanage.lua  
Config.FiveManageToken = "your_token_here"
```

Always make sure to keep your token private and disable the image saver once the process is complete.
