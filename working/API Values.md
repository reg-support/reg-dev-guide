# API Return Values

##### Coupon check  

  - `_links [object]`
  - `code [string]`: the coupon code in use
  - `type [string]`: the coupon type; either `fixed` or `percentage`
  - `value [number]`: the static value of the coupon (i.e. unrelated to the price of the current event)
  - `value_display [number]`: the value formatted for currency

##### Registrant

- `_links [object]`
  - `details [url]`: URL for the event's `details` API
  - `detailsPage [url]`: URL for the event's `details` page
  - `unregister [url]`: URL to the API to cancel registration
  - `unregisterPage [url]`: URL to the `unregister` page
- `attendance_end [UTC string]`: date/time of the end of the attendence window
- `attendance_start [UTC string]`: date/time of the start of the attendence window
- `attended [boolean]`: whether the registrant has already attended the event
- `been_on_waitlist [boolean]`: whether the registrant has been waitlisted for the event
- `email_address [string]`: registrant's email address (if any)
- `first_name [string]`: registrant's first name
- `last_name [string]`: registrant's last name
- `on_waitlist [boolean]`: whether registrant is currently on the waitlist
- `properties [object]`: values for custom registration fields (if any)
- `timezone [object]`
  - `id [string]`: timezone identifier, e.g. `America/Los_Angeles`
  - `abbreviation [string]`: timezone suffix, e.g. `PST`
  - `offset [number]`: timezone numeric offset, e.g. `-480`
  - `name [string]`: full name of the timezone, e.g. `(UTC-08:00) Pacific Time (US & Canada)`
- `unregistered [boolean]`: whether registrant has been unregistered

##### Venue

- `_links [object]`
- `address [object]`
  - `address1 [string]`: e.g. `2525 SW 1st Ave`
  - `locality [string]`: e.g. `Portland`
  - `region [string]`: e.g. `Oregon`
  - `country_code [string]`: e.g. `US`
  - `postal_code [string]`: e.g. `97205`
- `latitude [number]`: e.g. `45.504211`
- `longitude [number]`: e.g. `-122.679771`
- `name [string]`: the name assigned to the venue, e.g. `InterCall Portland`
