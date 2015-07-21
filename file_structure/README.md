# Theme Files

- This document will outline all of the major files in a Theme set, as well as provide some basic information on their usages.


## Pages

- **TODO**: Make teh awesome content here!


## Emails (a.k.a. Notifications)

- These files are found in the _Notifications_ folder. They represent the layout and content of emails that are sent to registrants on an event-by-event basis.
- This folder _does not_ contain any system emails that get sent directly to Stakeholders.
- Any files whose names begin with an underscore (`_`) character are _template files_ which are either extended or dynamically inserted into other non-template files. All other files are the bases off of which the actual email content is built.
- Any files that are intended to be dynamically inserted into another file will be referred to as 'drop-ins' below. They can be inserted into any other template using Liquid's `include` syntax, e.g.:
  + `{% include 'event_details_panel' %}`
  + **important:** when including a file in another file, the leading underscore and file extension are automatically added, so they _must not_ be included in the `include` call.


##### Templates and Drop-ins

  - `_attend_panel.liquid`
    + drop-in panel containing instructions for attending the meeting, including a link to join the web meeting
  - `_browser_test_panel.liquid`
    + drop-in panel containing a link to test browser compatibility for the meeting's selected web platform
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
    + drop-in containing full support information, including Q&A and un-registration link
  - `_support_panel_min.liquid`
    + drop-in containing minimal support information--NO unregister link


##### Base-Level Emails

  - `confirmation.liquid`
    + sent to a registrant as soon as he/she completes the registration process; contains all necessary information for attending the event.
  - `default.liquid`
  - `eventcanceled.liquid`
    + sent to registrants when an event has been cancelled
  - `eventrecording.liquid`
    + sent to registrants when the event's recording is available (including a link to said recording)
  - `eventrescheduled.liquid`
    + sent to registrants when an event has been rescheduled; contains the updated information for the event
  - `forgotpassword.liquid`
  - `receipt.liquid`
    + sent to registrants after successfully registering _and paying_ for an event; this email is sent in addition to the `confirmation.liquid` email
  - `reminder.liquid`
    + sent to registrants in advance of a meeting, providing a recap to all registrants of all meeting information
  - `sorry.liquid`
    + sent to registrants who _did not_ attend an event once the event has ended; includes a link to the recording for the event
  - `thanks.liquid`
    + sent to registrants who _did_ attend an event once the event has ended; includes a link to the recording for the event
  - `thankyou.liquid`
    + sent to registrants who _did_ attend an event once the event has ended; includes a link to the recording for the event
  - `unregistration.liquid`
    + sent to registrants after they have been _un-registered_ for an event
  - `venuechanged.liquid`
    + sent to registrants of offline events when the event's venue has changed; provides information for the updated venue
  - `waitlistadd.liquid`
    + sent to a registrant who has been added to the waitlist; if/when more registration spots open up, the registrant will be automatically moved out of the waitlist, and will receive a follow-up confirmation email
