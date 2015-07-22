# Theme.config

[Return to Main Page](https://github.com/reg-support/reg-dev-guide/blob/master/README.md)

### <a name="top">Table of Contents

- [Basic Information](#1)
- [Locales](#2)


##### <a name="1"></a>Basic Information

- Theme.config is an XML-based file that allows us to add a variety of customizations to a theme.

[Back to Top](#top)
##### <a name="2"></a>Locales

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
