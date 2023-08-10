# 🎨 Strapi Admin Tailwind Theme
Create your favorite theme for Strapi admin panel using Tailwind colors.

`109,751,747,072` possible combinations!

*Plaese don't forget to give it a star if you liked it 🙂⭐*


# 📷 Examples
| | | |
| --- | --- | --- |
| ![image](https://github.com/ShahriarKh/strapi-admin-tailwind-theme/assets/31452340/e9f38822-15d5-4f4e-99d7-3e3dac10c836) | ![image](https://github.com/ShahriarKh/strapi-admin-tailwind-theme/assets/31452340/e9d49559-e82d-4c5d-8f76-5c88c386f2ea)
| ![image](https://github.com/ShahriarKh/strapi-admin-tailwind-theme/assets/31452340/d8cad609-0049-48c5-9795-dd1be2345be1) | ![image](https://github.com/ShahriarKh/strapi-admin-tailwind-theme/assets/31452340/19dd5103-4f85-4530-9fba-f82bda34ee09)
| ![image](https://github.com/ShahriarKh/strapi-admin-tailwind-theme/assets/31452340/71fcd76d-1d96-4328-b6e1-60bea13fcb0b) | ![image](https://github.com/ShahriarKh/strapi-admin-tailwind-theme/assets/31452340/4577ab9b-dfec-4310-b732-066686024acf) 
| ![image](https://github.com/ShahriarKh/strapi-admin-tailwind-theme/assets/31452340/526d17a0-5940-45ee-87a4-3c5bfa6b0ecd) | ![image](https://github.com/ShahriarKh/strapi-admin-tailwind-theme/assets/31452340/209e9841-1137-485b-99e4-99879b0f6b2b)




---

# 🔨 Installation

1. Go to `src/admin` and create `app.js` if you haven't already done that.
2. Create `extensions` folder inside `src/admin`.
3. Copy `theme.js` file  from repo and paste it in `src/admin/extensions`.
   your folder structure should be like this:
    ```
    📁 src
    └── 📁 admin
        ├── 📁 extensions
        │   ├── theme.js
        │   └── ...
        ├── app.js
        └── ...
    ```
4. Open `app.js`, import `darkTheme` and `lightTheme` from `theme.js` and update the config:
    ```js
    import { darkTheme, lightTheme } from "./extensions/theme";
    
    export default {
      config: {
        theme: {
          dark: {
            colors: darkTheme,
          },
          light: {
            colors: lightTheme,
          },
        },
      },
    };
    ``` 
6. Rebuild admin panel.
7. Enjoy!

---

# 🖌 Customization

This extension replaces [Strapi Design System colors](https://design-system-git-main-strapijs.vercel.app/?path=/story/design-system-components-theme--dark-colors) with [Tailwind colors](https://tailwindcss.com/docs/customizing-colors).

Inside `theme.js` you'll see a bunch of colors plus some functions. At the end of the file, there are two exported objects: `darkTheme` and `lightTheme`. Each object contains other objects (say "color sets") that replace colors of different parts of strapi colors; for example, `darkWarning` will replace all `warning` colors in dark mode and `lightSuccess` will replace all `success` colors in light mode.  
But how are these defined at the first place?

Every color set can be defined with the following syntax:
```js
const colorSetName = createColors(tailwindColorName, strapiDesignSystemName, isDarkTheme) // isDarkTheme is true by default and can be omitted
```
For example, the code below will replace primary colors (`primary100`, `primary200`, `primary500`, `primary600` and `primary700`) with pink variants:
```js
const darkPrimary = createColors(pink, "primary")
```
Notice that tailwind color name is a js object and doesn't need quotes!

To create your desired theme, you just need to change the name of the colors. For example, if you want to make all primary colors 'lime' in light mode, look for the `lightPrimary` and change the color name passed to `createColors` function:
```js
// before
const lightPrimary = createColors(blue, "primary", false);

//after
const lightPrimary = createColors(lime, "primary", false);
```

---

# 🤔 Questions

- ***Can I have different colors for light and dark mode?***  
   For sure! `lightTheme` and `darkTheme` are two separate objects and you can customize them however you want.
  
- ***Can I prevent some colors from being changed and use Strapi colors?***  
   Of Course! just omit the color set from theme object and you are good to go:
  ```js
  export const darkTheme = {
    // ...darkNeutral, neutral colors are not included in the object, so the admin panel will use strapi original colors.
    ...darkPrimary,
    ...darkSecondary,
    ...darkAlternative,
    ...darkWarning,
    ...darkSuccess,
    ...darkDanger,
    ...darkButtons,
  };
  ```
  ![image](https://github.com/ShahriarKh/strapi-admin-tailwind-theme/assets/31452340/7f7b4f91-456d-4f18-ba5a-ef2a30ad8a9e)

  
- ***Can I have dark menus in light theme and vice versa?***  
   Certainly! You can do it by calling the `createColors` function with `isDarkTrue: true` for light colors and the other way round:
  ```js
  const lightPrimary = createColors(rose, "primary", true);
  ```
   ![image](https://github.com/ShahriarKh/strapi-admin-tailwind-theme/assets/31452340/a19b9065-c9d3-427c-9cb7-893d42f1055c)
  ```js
  const lightPrimary = createColors(rose, "primary", false);
  ```
   ![image](https://github.com/ShahriarKh/strapi-admin-tailwind-theme/assets/31452340/caa3f600-4f18-4feb-a255-67826e8864b7)

- ***Does it support plugins in admin panel?***  
  Yes! Albeit if the plugin follows the strapi guidlines and uses the strapi design system for its interface.
  
  ![image](https://github.com/ShahriarKh/strapi-admin-tailwind-theme/assets/31452340/7ddca923-2474-44be-95bf-9de6ea405163)
  👆 The screenshot above is for my Strapi plugin, Content-type Explorer. Check it out on [GitHub](https://github.com/ShahriarKh/strapi-content-type-explorer) or [Strapi Marketplace](https://market.strapi.io/plugins/strapi-content-type-explorer)!


