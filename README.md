# XOXO fax send

This is a basic system that uses Twilio's Fax API to send faxes. To set it up for yourself or your own friend group, you'll need a developer account from Twilio, which is out of scope of this document.

Once you have a funded Twilio account, you'll need a phone number, and two codes from the Twilio Developer Console.

Click "Show" to get started!

# Your Project

On the front-end,
* `views/index.html` is the app's UI
* `public/client.js` has the JavaScript to set up International Telephone Input, the phone number validator and formatter
* `public/style.css` has the page styling
* `views/setup.html` and `public/setup.js` are for the setup helper flow.

On the back-end,
* `server.js` is run when the project starts
* `package.json` contains the app's dependencies
* `.env` contains variables custom to the app we don't want other users to see

# Security/Privacy

Uploaded faxes are stored in Glitch's `/tmp` storage, which is deleted soon after the application spins down.  Uploaded faxes are given temporary, generated filenames.

Twilio is set to not store sent faxes, although metadata about the send is kept for 180 days.

The uploaded faxes are only served to requests presenting a valid Twilio signature, which (in theory) only Twilio should be able to generate.

# Alternatives

Twilio has its own serverless hosted code service called Twilio Functions, but as of April 2020 [you can't `POST` `multipart/form-data` content to it](https://www.twilio.com/docs/runtime/functions/request-flow) (typically what you'd use to upload a potentially large binary file like a PDF).

Most online fax tools with free trials either don't allow you to send faxes, or limit your total number of pages.  Most want monthly subscriptions rather than offer pay-as-you-go.

🚨 Twilio has sunset its Programmable Fax API, which this code uses.  It will cease to work as of **December 17, 2021**.  You shouldn't use this as the basis for any new projects!  See the [Phaxio fax send](https://glitch.com/~phaxio-fax-send) sister project, or read [Twilio's migration guide to learn how to use Documo instead](https://support.twilio.com/hc/en-us/articles/1260800821230-Programmable-Fax-Migration-Guide-for-Documo-mFax).

# More Info

* [Glitch Twilio SMS demo](https://glitch.com/~basic-twilio-sms)
* [Twilio Fax blog post](https://www.twilio.com/blog/2017/04/faxing-ascii-images-using-node-and-twilio-programmable-fax.html)
* [International Telephone Input library](https://intl-tel-input.com)
* [Emoji Favicon generator](https://favicon.io/emoji-favicons/)

Made with [Glitch](https://glitch.com) and [Twilio](https://www.twilio.com) by [Vitorio](http://vitor.io) for the [XOXO](https://xoxofest.com/) Slack.
