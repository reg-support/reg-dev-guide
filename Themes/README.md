# Themes

### Overview

- A theme controls the front end or customer facing view of IER.

- The technology that exposes the various APIs that IER uses is called Knockout JS. You can read more about it [here](http://knockoutjs.com/).

- The templating language that is used is called Liquid. You can read more about it [here](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers).

- The front end framework used for the layout and design is Bootstrap. You can read more about it [here](http://getbootstrap.com/).

- As a designer, any front end framework can be used such as Bootstrap, HTML Boilerplate, Ivory, Gumby, Zurb Foundation, Skeleton...the list goes on.

- It is up to _you_ as the designer to ensure that the APIs that IER uses are exposed and all the directory dependencies remain intact.

- That being said, themes are extremely versatile from a design standpoint. As long as the KnockoutJS has been added to your views, you can turn IER into anything from a simple, single-page app to a multi-page, ecommerce driven website.

### Liquid Tags

The following Liquid tags are used throughout the Views:

- Catalog page URL - `siteurl catalog`
- Identity Authenticated - `identity.authenticated`
- Identity Provider - `identity.provider`
- Identity User Name - `identity.user_name`
- Login page URL - `siteurl login`
- Logout URL - `logout_url`
- Main site URL - `siteurl`
- Site Google Urchin - `siteGoogleUrchin`
- Site Hostname - `site.hostname `
- Theme Locales - `theme.locales`
- Theme Locales Code - `locale.code`
- Theme Locales Current - `locale.current`
- Theme Locales Name - `locale.name`
- Theme Settings - `theme.settings.setting_name` (note the use of plural '_settings_')

#### Social Medial Tags

- Facebook URL - `facebook.connect_url`
- Google URL - `google.connect_url `
- Microsoft URL - `microsoft.connect_url`
