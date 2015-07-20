# Theme Files

- This document will outline all of the major files in a Theme set, as well as provide some basic information on their usages.

## Pages

- **TODO**: Make teh awesome content here!

## Emails (a.k.a. Notifications)

- These files are found in the _Notifications_ folder. They represent the layout and content of emails that are sent to registrants on and event-by-event basis.
- This folder _does not_ contain any system emails that get sent directly to Stakeholders.
- Any files whose names begin with an underscore (`_`) character are _template files_ which are either extended or dynamically inserted into other non-template files. All other files are the bases off of which the actual email content is built.
- Any files that are intended to be dynamically inserted into another file will be referred to as 'drop-ins' below. They can be inserted into any other template using Liquid's `include` syntax, e.g.:
  + `{% include 'event_details_panel' %}`
  + **important:** when including a file in another file, the leading underscore and file extension are automatically added, so they _must not_ be included in the `include` call.


##### Templates and Drop-ins

  - `_attend_panel.liquid`
  - `_browser_test_panel.liquid`
  - `_de-audio.liquid`
  - `_emailmaster.liquid`
    + this is the top-level template for all emails; all of the other email files extend this one, so any changes made here will be reflected in ALL emails
  - `_event_details_panel.liquid`
    + drop-in containing title, date, etc. for the event
    + while the title of this panel defaults to "Event Info", you can actually inject your own title by declaring a variable called `event_details_title` before you include the template. for example:
      ```
      {% assign event_details_title = 'New Date and Time!'; %}
      {% include 'event_details_panel' %}
      ```
  - `_footer.liquid`
    + drop-in containing contact info, copyright, etc.
  - `_generic-audio.liquid`
  - `_inline_styles.liquid`
    + drop-in containing some of the vital styles defined as liquid strings; we are using this to force inline styles on some elements for better compatibility among various mail clients; think of this file as a 'hacked stylesheet'
  - `_op-assist-audio.liquid`
  - `_support_panel_full.liquid`
    + drop-in containing full support information, including Q&A and unregistration link
  - `_support_panel_min.liquid`
    + drop-in containing minimal support information--NO unregister link


##### Base-Level Emails

  - `confirmation.liquid`
  - `default.liquid`
  - `eventcanceled.liquid`
  - `eventrecording.liquid`
  - `eventrescheduled.liquid`
  - `forgotpassword.liquid`
  - `receipt.liquid`
  - `reminder.liquid`
  - `sorry.liquid`
  - `thanks.liquid`
  - `thankyou.liquid`
  - `unregistration.liquid`
  - `venuechanged.liquid`
  - `waitlistadd.liquid`
