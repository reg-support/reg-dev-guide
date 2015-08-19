# Theme Files

- This document will outline all of the major files in a Theme set, as well as provide some basic information on their usages.


## Views

- These files are found under the **Views** parent folder. They represent the actual web pages that will be displayed to a user visiting any page on the Site.
- The files in the **Pages** folder are the base-level files that are rendered by the server to provide the page to the browser.
- The files in the **Shared** folder are are _template files_ which are either extended or dynamically inserted into other non-template files.
- Except where otherwise noted, the URL for a page will contain the name of the file (e.g. the registration page for an event will include `/register/` in the URL, which is the rendered version of `register.liquid`). This will let you know which file you need to look at if you need to update anything.

##### /Pages

- `attend.liquid`
  + the primary landing page for all information pertinent to an individual event; a link to this page is included in the `confirmation.liquid` notification that is sent to a registrant after successfully registering for an event
- `cart.liquid`
- `catalog.liquid`
  + the base page for a Site; displays all Events currently scheduled under the parent Site
  + **Note:** this is the default page, so if the site's URL is entered with no page URL included, this will be the page displayed. It is identical to including `/catalog/` in the URL.
- `confirm.liquid`
  + the page on which a registrant's supplied registration information is displayed back to them; once the registrant confirms this information, their registration is completed, and they are redirected to `thanks.liquid`
  + **Note:** for events that have payments required, this is the same page on which a registrant will submit payment information. In this case, the URL will show `/payment/`, rather than `/confirm/`.
- `event.liquid`
  + **Note:** the URL for this page shows `/details/`, rather than `/event/`
- `login.liquid`
  + this is the attendee login page. It is activated only if IER Profile mode has been turned on.
- `register.liquid`
  + the page from which an attendee can register for an event; `event.liquid` links directly to this page from its "Register" button
- `reset-password.liquid`
  + the page from a registered user can request an update for his/her account password
- `support.liquid`
  + **Note:** this page is currently not in use, since our support link redirects to our Freshdesk portal
- `thanks.liquid`
  + the page that is displayed after registration (and/or payment) has been completed
- `topic.liquid`
  + this page shows all of the events scheduled under a pre-defined topic
- `unregister.liquid`
  + the page on which a registrant can un-register for an event; the link to this page is sent to the registrant in the `confirmation.liquid` email

##### /Shared

- `_additionalfields.liquid`
  + drop-in containing additional templates for registration fields, beyond what is defined in `_registrationfields.liquid`
- `_eventmaster.liquid`
  + the top-level page that is extended by all pages that pertain to an individual event, including: `attend.liquid`, `confirm.liquid`, `event.liquid`, `register.liquid`, `thanks.liquid`, and `unregister.liquid`
  + **Note:** this file also extends `_homemaster.liquid`, so any changes you make to _either_ of these files will be reflected in all of the files listed above.
- `_homemaster.liquid`
  + the absolute top-level template for all pages; it includes the basic structure shared by all pages and the HTML `<head>` section
  + **Note:** this page is extended by all others, so any changes made to this page _will be reflected in all pages_
- `_registrationfields.liquid`
  + drop-in containing templates for building all necessary fields for a registration form, including default values (e.g. pre-populated drop-down menu of U.S. states)
- `_themecss.liquid`
  + `themecss.liquid` houses additonal CSS code for the theme. It overrides the Bootstrap CSS.


## <a name="email"></a>Emails (a.k.a. Notifications)

- These files are found in the **Notifications** folder. They represent the layout and content of emails that are sent to registrants on an event-by-event basis.
- This folder _does not_ contain any system emails that get sent directly to Stakeholders.
- Any files whose names begin with an underscore (`_`) character are _template files_ which are either extended or dynamically inserted into other non-template files. All other files are the bases off of which the actual email content is built.
- Any files that are intended to be dynamically inserted into another file will be referred to below as 'drop-ins'. They can be inserted into any other template using Liquid's `include` syntax, e.g.:
  + `{% include 'event_details_panel' %}`
  + **important:** when including a file in another file, the leading underscore and file extension are automatically added, so they _must not_ be included in the `include` call.


##### Templates and Drop-ins

- `_attend_panel.liquid`
  + drop-in panel containing instructions for attending the meeting, including a link to join the web meeting
- `_browser_test_panel.liquid`
  + drop-in panel containing a link to test browser compatibility for the meeting's selected web platform
- `_de-audio.liquid`
  + drop-in panel containing audio details for Direct Event audio
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
  + drop-in panel containing audio details for a generic audio provider (e.g. Reservationless Plus)
- `_inline_styles.liquid`
  + drop-in containing some of the vital styles defined as liquid strings; we are using this to force inline styles on some elements for better compatibility among various mail clients; think of this file as a 'hacked stylesheet'
- `_op-assist-audio.liquid`
  + drop-in panel containing audio details for Operator Assisted audio
- `_support_panel_full.liquid`
  + drop-in containing full support information, including Q&A and un-registration link
- `_support_panel_min.liquid`
  + drop-in containing minimal support information--NO unregister link


##### Base-Level Emails

- `confirmation.liquid`
  + sent to a registrant as soon as he/she completes the registration process; contains all necessary information for attending the event.
- `default.liquid`
  + the fallback/default email that will be sent when the expected email is not present
- `eventcanceled.liquid`
  + sent to registrants when an event has been cancelled
- `eventrecording.liquid`
  + sent to registrants when the event's recording is available (including a link to said recording)
- `eventrescheduled.liquid`
  + sent to registrants when an event has been rescheduled; contains the updated information for the event
- `forgotpassword.liquid`
  + sent to a registrant who has requested a password reset
- `receipt.liquid`
  + sent to registrants after successfully registering _and paying_ for an event; this email is sent _in addition to_ the `confirmation.liquid` email
- `reminder.liquid`
  + sent to registrants in advance of a meeting, providing a recap to all registrants of all meeting information
- `sorry.liquid`
  + sent to registrants who _did not_ attend an event once the event has ended; includes a link to the recording for the event
- `thanks.liquid`
  + sent to registrants who _did_ attend an event once the event has ended; includes a link to the recording for the event
- `thankyou.liquid`
  + sent to registrants who _did_ attend an event once the event has ended; includes a link to the recording for the event
- `unregistration.liquid`
  + sent to registrants after they have been successfully un-registered for an event
- `venuechanged.liquid`
  + sent to registrants of offline events when the event's venue has changed; provides information for the updated venue
- `waitlistadd.liquid`
  + sent to a registrant who has been added to the waitlist; if/when more registration spots open up, the registrant will be automatically moved out of the waitlist, and will receive a follow-up confirmation email
