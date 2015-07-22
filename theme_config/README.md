# Theme.config

- Theme.config is an XML-based file that allows us to add a variety of customizations to a theme.


##### Locales

- for localized sites, we can specify which locale files are available to the site in the `<locales>` element, near the top of the page; for example, the following block specifies that US English, German, and Spanish are available, with US English being the default:

  ```xml
  <locales default="en-US">
    <add name="en-US"/>
    <add name="de"/>
    <add name="es"/>
  </locales>
  ```

- the actual localization is specified in `loc.po` files within the **Locales** folder in the theme package
- these `name` attributes correspond to to the name of the folder that holds the associated `loc.po` file; for example, using 'de' for localization would look for the translation map at **Locales/de/loc.po**
