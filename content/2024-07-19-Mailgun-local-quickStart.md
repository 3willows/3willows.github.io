---
categories: ["meta"]
date: "2024-07-19"
title: "Mailgun quick start: with Express on local machine"
---

After attending a meet-up, I was told of a volunteering opportunity to improve the group website.

Specifically, at present, there was no functionality for the website to send out a confirmation email after someone signs up.

The tech lead who put the website together in a few hours says that a good tool for this feature would be [Mailgun](https://www.mailgun.com/).

So I decided to give Mailgun a quick spin, to see if I am up for the task.

### 1 Signing up for a free plan

The first hurdle was whether a free tier is available as of July 2024. The non-obvious answer is "yes": you just need to sign up using [this page](https://www.mailgun.com/pricing/) as opposed to the more obvious `Get Started for Free` button on the [homepage](https://www.mailgun.com/).

### 2 Quick start example for Node: the hurdle

The "Getting Started" guide on the Mailgun website is easy to follow, until I reached the stage of the quick start example for Node.

As of 19 July 2024, these are the instructions and the example code.

> Sandbox domains are restricted to authorized recipients only.

(There is a box on the right of the screen allowing you to add authorized recipients to the sandbox.)

> Here's the basic code you need. Plug in your API info from above and modify the from address, to address, and other content to give Mailgun a good old test drive.

```js
const formData = require("form-data")
const Mailgun = require("mailgun.js")
const mailgun = new Mailgun(formData)
const mg = mailgun.client({
  username: "api",
  key: process.env.MAILGUN_API_KEY || "key-yourkeyhere",
})

mg.messages
  .create("sandbox-123.mailgun.org", {
    from: "Excited User <mailgun@sandbox9bbf6d0dbdd14a1aac25af6db05fc464.mailgun.org>",
    to: ["test@example.com"],
    subject: "Hello",
    text: "Testing some Mailgun awesomeness!",
    html: "<h1>Testing some Mailgun awesomeness!</h1>",
  })
  .then((msg) => console.log(msg)) // logs response data
  .catch((err) => console.log(err)) // logs any error
```

The difficulty (as explained by [this SO question](https://stackoverflow.com/questions/78754430/unauthorized-error-by-mailgun-using-node-js-and-mailgun-js-package/78766954#78766954)) is knowing exactly what "other content" needs to be changed. I was stuck on that for 10-20 minutes myself.

### 2 Quick start example for CURL

To troubleshoot, I took a detour and tried the CURL example (below) instead,

```bash
curl -s --user 'api:YOUR_API_KEY' \
  	https://api.mailgun.net/v3/sandbox9bbf6d0dbdd14a1aac25af6db05fc464.mailgun.org/messages \
  	-F from='Excited User <mailgun@sandbox9bbf6d0dbdd14a1aac25af6db05fc464.mailgun.org>' \
  	-F to=YOU@sandbox9bbf6d0dbdd14a1aac25af6db05fc464.mailgun.org \
  	-F to=bar@example.com \
  	-F subject='Hello' \
  	-F text='Testing some Mailgun awesomeness!'
```

For `curl`, I only had to change "YOUR_API_KEY" and the "to address" to send out an email. This gave me comfort that Mailgun was working as expected.

### 3 Quick start example for Node: the solution

As I explain in my [SO answer](https://stackoverflow.com/a/78766954/19767032), the first parameter to `mg.messages.create` is the `domain` as per [mailgun.js docs](https://github.com/mailgun/mailgun.js/?tab=readme-ov-file#create).

So that needs to be changed to the sandbox domain as well.

Incidentally, to access the api key from `.env`, I ran `node --env-file=.env index.js`: I used to require the `dotenv` module instead in `index.js`, but this seems to have fallen out of favour.

### 4 Wiring up to a webpage with Express

The next step after the Node quickstart example is to wire Mailgun up to an Express App.

There is an [official Mailgun tutorial](https://www.mailgun.com/blog/email/how-to-send-transactional-email-in-a-nodejs-app-using-the-mailgun-api/) for this, albeit from 2022.

I was disappointed by the lack of recent update and github repo. But given its official status I decided to stick with the tutorial.

A rookie error I made (due to the lack of a repo) was to have the wrong directory structure: placing `js` within `views`. In many ways this betrays my lack of familiarity of the Express system, since of course nothing unrelated to the display of the web page should live in `views`.

In any case, I cut down the tutorial to its bare essentials: removing these 3 features that I do not need for the moment.

- Sending a newsletter to an email list
- Adding email addresses to a list
- Sending an invoice to a single email address

I then did the following (not in chronological order):

- install and require `mailgun.js` in preference to the deprecated `mailgun-js`.
- ```console.log(process.env.MAILGUN_API_KEY)``` to make sure the .env file is correctly wired up.
- change the callback function within `/submit/:mail` to the Node quick start example, given the syntax for `mailgun.js` is different from `mailgun-js`.

With these tweaks, I got the send mail feature to work with the address bar (i.e. by typing "http://localhost:3030/submit/[email address]" to send a get request to `/submit/:mail`).

### 5 Fixing jade/pug

I turn then to fixing jade/pug page (jade has been renamed to pug after the Mailgun tutorial was published in 2022).

The original example code was a bit convoluted to me, so I removed the separate js file and did this instead to start with.

```pug
doctype html
html
  head
    title Mailgun Transactional demo in NodeJS
  body
    p Welcome to a Mailgun form
    form(action="/submit/email", method="GET")
      label(for="mail") Email
      //- not wired up yet
      input(type="text", id="emailAddress", value="verified email address")
      button(type="submit") Send email
```

My focus at this point is on Mailgun, not the ins and outs of pug.  So I used perplexity.ai to quickly wire up the text input bar to the form ```action```, so that the user sends a GET request to "/submit/[email input by user]".

```pug
doctype html
html
  head
    title Mailgun quick start
    script.
      document.addEventListener('DOMContentLoaded', function() {
        const form = document.getElementById('emailForm')
        form.addEventListener('submit', function(e) {
          e.preventDefault(); // Prevent the default form submission
          const emailAddress = document.getElementById('emailAddress').value;
          window.location.href  = `/submit/${encodeURIComponent(emailAddress)}`;
        });
      });
  body
    p Welcome to a Mailgun form
    form#emailForm(action="/submit/:emailAddress", method="GET")
      label(for="emailAddress") Email
      input(type="text", id="emailAddress", placeholder="your email")
      button(type="submit") Send email``
```

Finally, tweaking ```app.js``` so that it reads ```req.params.mail``` from the GET request to "/submit/:mail", I complete the bare-bones skeleton for getting up Mailgun working on my local machine.

The next step will be deploying Mailgun on a small wesbite: but if my recent experience is any guide, that will be another kind of beast entirely (requiring different materials and a different mind set).  Another day!