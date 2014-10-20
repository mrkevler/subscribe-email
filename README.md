Subscribe Email is a UMD JavaScript module for rendering a mailing list sign up form quickly on a webpage.

It allows developers to quickly include an email collection form on a page without being concerned with the implementation details of a specific mailing list platform. We're currently aiming to support mailing lists on SendGrid, MailChimp and Universe.

# Getting the Module
You can get the module in any one of the following ways;
- Download [the latest release](https://github.com/blocks/subscribe-email/releases) from GitHub
- Or install with npm; `npm install subscribe-email`
- Or install with Bower; `bower install subscribe-email`

# Quick Start
To get started, you'll need to include the script on your page, create a `<form>` element, and initialize the module. Here's some minimal code you can use to get started quickly;

```
<script src="subscribe-email.js">
```


```
<form id="subscribe-form"></form>
```


```
<script>
new SubscribeEmail({
  element: '#subscribe-form',
  service: 'universe',
  key: 'your-api-key-here'
});
</script>
```

At a minimum, you'll need to change the `service` and `key` parameters to match your needs.

# Advanced Usage

## Options
The module can be configured with several optional parameters passed to it's constructor. Here is the full list of options:

### `element`
**(Required)** A DOM element, jQuery element, or selector string to refer to the placeholder element.

### `prependMessagesTo`
A selector string that refers to the element that should receive response messages. Defaults to the same value set for `element`.

### `service`
**(Required)** The mailing list platform you are using. Available options are `mailchimp`, `sendgrid` and `universe`.

### `key`
**(Required)** A string of the API key for your mailing list platform.

### `submitText`
A string to be used on the form's submit button (defaults to "Subscribe").

### `template`
Out of the box, the module will generate BEM markup with the namespace `subscribe-email` that contains all of the markup needed to display the alert. If you want to customize the markup, you can pass in a *compiled* handlebars template using this option. (Defaults to `false`).

### `responseElement`
A selector string for the element you want to display response (validation, errors, confirmation) messages from your platform's API (defaults to `'.subscribe-email__response'`).

## Events
Some mailing list platforms may send response messages for things like confirmation or validation errors. The default template will display these messages along-side the form, but alternatively you can easily integrate the messages into other parts of your page by listening for the following events to be emitted from the SubscribeEmail instance;

### `subscriptionMessage`
Fires whenever the mailing list provider returns a response (both success and failure).

### `subscriptionError`
This event will fire if the mailing list provider returns an error. Specific details about the error will be included in a payload object when available.

### `subscriptionSuccess`
This event will fire if the mailing list provider returns a confirmation that the email address has been added to the list. Specific details will be included in a payload object when available.