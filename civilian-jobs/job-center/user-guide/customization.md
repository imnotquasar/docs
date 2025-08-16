# Customization

This section explains how to visually and functionally customize **Quasar Job Center** to fit your server’s branding and design preferences.

***

## Logo Replacement

You can replace the default logo with your own branding:

* Navigate to: `html/assets/logo.png`
* Replace the file with your server’s logo image
* **Recommended size:** `200x60px`
* **Supported formats:** `.png` or `.webp` with transparency for best results

***

### Color Scheme

To modify the color palette used in the interface, edit the following values in: `html/css/style.css`

```css
:root {
    --primary-color: #00a3ff;
    --primary-gradient: radial-gradient(50% 50% at 50% 50%, #006299 0%, #00a3ff 100%);
    --secondary-gradient: radial-gradient(49.48% 49.48% at 50.52% 50.52%, rgba(25, 63, 85, 0.35) 0%, rgba(14, 21, 27, 0.8) 100%);
    --main-gradient: radial-gradient(49.48% 49.48% at 50.52% 50.52%, #28343c 0%, rgba(14, 21, 27, 0.9) 100%);
    --border-gradient: linear-gradient(180deg, rgba(52, 68, 82, 0) 0%, #2d2d2d 100%);
    --border-radius: 1vh;
    --border-radius-sm: 0.5vh;
    --spacing-xs: 0.5vh;
    --spacing-sm: 1vh;
    --spacing-md: 1.5vh;
    --spacing-lg: 2vh;
    --spacing-xl: 3vh;
}
```

Feel free to update the values to match your server’s branding, theme, or seasonal events.

***

### Job Images

Each job card supports a custom preview image. Use attractive, high-resolution visuals to improve immersion:

* **Recommended size:** `600x300px`
* **Formats:** `.jpg` or `.png`
* **Suggested sources:**
  * [Unsplash](https://unsplash.com) for royalty-free photography
  * Screenshots from your server
  * Custom renders or artwork

Use consistent styles and dimensions across all job cards to keep the UI clean and professional.

***

### Icon Customization

Quasar Job Center uses FontAwesome icons for job cards and categories. You can assign any valid FontAwesome class to your jobs or categories in `shared/config.lua`.

Here are some popular options:

| Icon | Usage              | Class                   |
| ---- | ------------------ | ----------------------- |
| 🛡️  | Police / Security  | `fas fa-shield-alt`     |
| 🚑   | Medical / EMS      | `fas fa-ambulance`      |
| 🚗   | Automotive         | `fas fa-car`            |
| 💼   | Business / Office  | `fas fa-briefcase`      |
| 🛠️  | Technical / Repair | `fas fa-tools`          |
| 🎓   | Education          | `fas fa-graduation-cap` |
| ⚖️   | Legal              | `fas fa-gavel`          |
| 🍽️  | Food Service       | `fas fa-utensils`       |
| 🎵   | Entertainment      | `fas fa-music`          |

To apply, simply assign the class in the job or category config like this:

```lua
icon = "fas fa-ambulance"
```
