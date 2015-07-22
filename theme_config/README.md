# Theme.config

[Return to Main Page](https://github.com/reg-support/reg-dev-guide/blob/master/README.md)

## <a name="top">Table of Contents

- [Basic Information](#1)
- [Locales](#2)
- [Pages](#3)
- [Settings & Groups](#4)


## <a name="1"></a>Basic Information

- Theme.config is an XML-based file that allows us to add a variety of customizations to a theme.
- This guide is written assuming the reader has a basic understanding of the usage and terminology of XML.


[Back to Top](#top)
## <a name="2"></a>Locales

- for localized sites, we can specify which locale files are available to the site in the `<locales>` element, near the top of the page; e.g. the following block specifies that US English, German, and Spanish are available, with US English being the default:

  ```xml
<locales default="en-US">
  <add name="en-US"/>
  <add name="de"/>
  <add name="es"/>
</locales>
  ```

- the actual localization maps are specified in `loc.po` files within the **Locales** folder in the theme package
- the `name` attributes above correspond to to the name of the folder that holds the associated `loc.po` file; for example, using 'de' for localization would cause the site to look for the translation map at **Locales/de/loc.po**
- a localized version of the Site can be requested with a GET param named `locale` with a value matching the name; e.g. the following URL would request the German/DE version of a site:
  + `[...]/?locale=de`


[Back to Top](#top)
## <a name=#3></a>Pages

[Back to Top](#top)
## <a name=#4></a>Settings & Groups

- We can define custom settings within the `<settings>` element. Anything we define here will show up under the "Theme Details" page in a Site's back-end, and can be edited directly from the back-end by clicking on the "Configure Theme" link on the right side of the page.
- Similar to adding locales, we can add custom settings here by inserting an `<add>` element
- There are 4 _attributes_ that are of interest when adding a custom setting:
  + `name` - this is the name of the setting as it will be passed from the server into our template pages; since we will be accessing as a variable in code, it should be a single camel-case word, like `siteTitle`
  + `title` - this is the "pretty print" version, as it will show up in the back-end; it can be mostly anything you want, but generally speaking, title-case is probably the best, like `Site Title`
  + `type` - this is the data type you are defining; most custom settings will be of "Text" type, but we have a few options available to us:
    - `Text` - a plain text string; use this for creating a custom text field (e.g. for displaying custom copyright information)
    - `Image` - a digital image; using this type will allow the user to upload an image to the back-end in their site
    - `Color` - a color in hexadecimal format; use this when you want to define customizable colors (you do generally want to define a default value for this data type)
  + `default` (optional) - as the name suggests, this will be the default value of the custom setting; it can be omitted altogether if not default value is needed
- putting this all together, we might end up with a settings group that looks something like the following:

  ```xml
<group name="Base Settings">
  <add name="siteTitle" title="Site Title" type="Text"/>
  <add name="siteLogo" title="Site Logo" type="Image"/>
  <add name="siteThemeColor" title="Site Theme Color" type="Color" default="#428BCA"/>
</group>
  ```

[Back to Top](#top)

[Return to Main Page](https://github.com/reg-support/reg-dev-guide/blob/master/README.md)

- a
- a
- a
- a
- a
- a
- a
- a
- a
- a
- a
- a
- a
- a
- a
