# Registrant API

[Return to API Main Page](../README.md)

##### Basic Info

- The Registrant API returns information about the current user's registration status, including their answers to individual registration fields.
- Note that in order for this URL to be present, IER must recognize the current user as a registrant, which means they must either be logged in with an IER identity or still have the IER cookie in their browser from a previous registration.
- The URL for this API is provided in the `_links` object of the `event/details` API under the `registrant` property (i.e. `event/details API response -> _links.registrant.href`).

##### Returned Data

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
