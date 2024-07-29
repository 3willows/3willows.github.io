---
categories: ["meta"]
date: "2024-07-29"
title: "Next, Supabase, Mailgun"
---

My aim is simple: on my deployed website, when a user enters her email to sign up for something, my website needs to send her a confirmation email, and also log it into a database.

So, how to go about it?

It is not hard to get a Next.js and Supabase working together on a local machine or when deployed.  There is an official tutorial which is good but [for a minor flaw](https://3willows.github.io/2024-07-25-display-rate-limit/).

It is also not hard to deploy [Mailgun on a local machine](https://3willows.github.io/2024-07-19-mailgun-local-quickstart/).

But snags begin to appear when I put everything together.

When I modified the Next.js and Supabase repo to incorporate Mailgun, a mysterious difference appeared between the local environment and the deployed version.  It didn't help that the only tutorials I could find on a quick Google were using the older "mailgun-js" npm module, which is subtly different from the current  "mailgun.js" module: so there were 30-40 minutes where I just had to bat away error messages one-by-one.

(This was however a good introduction to the importance of "use server": something my eyes glazed over before.)

I could dig into it and find out more, but  [Vercel's documentation](https://vercel.com/guides/sending-emails-from-an-application-on-vercel) does not mention Mailgun as one of the recommended providers.  Which made me wonder at one point whether I should jump ship altogether.

Fortunately, [this tutorial](https://www.youtube.com/watch?v=Te4ESNxq_xU) came to the rescue.  The [source code](https://github.com/3willows/lets-build-contact-form) works out of the box, and holds up when deployed.

My plan is now to combine the "let's build contact form" repo and the Next + Supabase starter repo into a single deployed website.  

This will give me most of the functionalities I need: there will still be a further issue of getting permission to send emails to different email holders (every provider takes steps to prevent their services being abused for sending out spam email), but that is a conceptually separate step that can wait.