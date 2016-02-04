# <a name="top">Theme.config

[Return to Main Page](https://github.com/reg-support/reg-dev-guide/blob/master/README.md)

## Table of Contents

- [Basic Information](#1)
- [Locales](#2)
- [Pages](#3)
- [Settings & Groups](#4)
- [Connecting Settings & Views](#5)


## <a name="1"></a>Basic Information

- Theme.config is an XML-based file that allows us to add a variety of customizations to a theme.
- This guide is written assuming the reader has a basic understanding of the usage and terminology of XML.
- The following settings do not have any effect on the functionality of the theme--they are purely for informational use.
  + `<title>` - the title for the theme; this will not appear anywhere on the public Site--only in the back-end.
  + `<description>` - a simple description for the theme; again, this will not appear on the public Site, so it can be used to display any useful information (e.g. a version number for the theme)


[Back to Top](#top)
## <a name="2"></a>Locales

- For localized sites, we can specify which locale files are available to the site in the `<locales>` element, near the top of the page; e.g. the following block specifies that US English, German, and Spanish are available, with US English being the default:

  ```xml
  <locales default="en-US">
    <add name="en-US"/>
    <add name="de"/>
    <add name="es"/>
  </locales>
  ```

- The actual localization maps are specified in `loc.po` files within the **Locales** folder in the theme package
- The `name` attributes above correspond to the name of the folder that holds the associated `loc.po` file; for example, using 'de' for localization would cause the site to look for the translation map at **Locales/de/loc.po**
- A localized version of the Site can be requested with a GET param named `locale` with a value matching the name; e.g. the following URL would request the German/DE version of a site:
  + `[...]/?locale=de`


[Back to Top](#top)
## <a name="3"></a>Pages

- The `Pages` section is where you tell IER that you have added a new page to your `Views`. It is also where the default landing page of your site is set.
- Here is the code that determines the default landing page: `<pages default="catalog" login="login">`.
- To change the default landing page, just change the string in the `default` attribute to one of the other page names.  

[Back to Top](#top)
## <a name="4"></a>Settings & Groups

- We can define custom settings within the `<settings>` element. Anything we define here will show up under the "Theme Details" page in a Site's back-end, and can be edited directly from the back-end by clicking on the "Configure Theme" link on the right side of the page.
- Similar to adding locales, we can add custom settings here by inserting an `<add>` element

##### Attributes
- There are 4 attributes that are of interest when adding a custom setting:
  + `name` - this is the name of the setting as it will be passed from the server into our template pages; since we will be accessing this as a variable in code, it should be a single camel-case word, like `siteTitle`
  + `title` - this is the "pretty print" version, as it will show up in the back-end; it can be mostly anything you want, but generally speaking, title-case is probably the best, like `Site Title`
  + `type` - this is the data type you are defining; most custom settings will be of "Text" type, but we have a few options available to us:
    - `Text` - a plain text string; use this for creating a custom text field (e.g. for displaying custom copyright information). Returns a plain string.
    - `Image` - a digital image; using this type will allow the user to upload an image to the back-end in their site. Returns a partial URL `/ier/content/0ef33c2968a34e8cb0c2828320aa06ba.JPG`.
    - `Color` - a color in hexadecimal format; use this when you want to define customizable colors (you do generally want to define a default value for this data type). Returns a string but in hexadecimal format. 
    - `Toggle` - a simple toggle switch. Returns a value of True or False.
    - `File` - Works much like image. Allows a user to upload a file to IER. Returns a partial URL `/ier/content/b75e9e4d70814234b5eddb09358d7267.pdf`.
    - `Markdown` - Allows you to add Markdown in the admin. Returns markdown. Don't forget to use the `markdown` pipe! `{{ theme.settings.markdown | markdown }}`
    - `Dropdown` - Allows you to add a dropdown menu to the theme configuration settings. Value is a plain string but requires a little extra setup in the Theme.Config.
    
      ```
      <add name="dropdown" title="Dropdown" type="Options" default="yep">
        <option title="Yep" value="yep" />
        <option title="Nope" value="nope" />
      </add>
      ```
      
  + `default` (optional) - as the name suggests, this will be the default value of the custom setting; it can be omitted altogether if no default value is needed. 

##### Grouping
- We can group similar settings together by nesting them within a `<group>` element, and providing a `name` attribute. When accessed from the back-end, grouped settings will be grouped together in a collapsable panel.
- We can put as many or as few settings into a group as necessary, and use as many separate groups as necessary.

##### Example
- Putting this all together, we might end up with a settings group that looks something like the following:

  ```xml
  <group name="Base Settings">
    <add name="siteTitle" title="Site Title" type="Text"/>
    <add name="siteLogo" title="Site Logo" type="Image"/>
    <add name="siteThemeColor" title="Site Theme Color" type="Color" default="#428BCA"/>
    <add name="siteHeaderColor" title="Site Header Color" type="Color" default="#000000"/>
  </group>
  ```

[Back to Top](#top)

## <a name="5"></a>Connecting Settings & Views

- After you have created your new group and/or setting, it's time to connect it to the registrant view.
- Remember the `name` attribute that you declared in your `<add>` element above? You can use the attribute within a liquid tag like so: `{{theme.settings.siteHeaderColor}}`.
- This tag can then be placed throughout the CSS or the HTML to render the item you added as a setting.
- Here's an example of what the final product looks like:

```css
h1, h2 {
  color: {{theme.settings.siteHeaderColor}}
}
```

- In the above example, we have applied the Site Header Color style that we declared in Theme.config to both the `h1` and `h2` tags. In this way, we use Liquid to create CSS variables just like we would with LESS or SASS.
- Liquid can also be used to add text blocks or images to your HTML.
- For more information on Liquid, [check out this link](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers).

[Back to Top](#top)
