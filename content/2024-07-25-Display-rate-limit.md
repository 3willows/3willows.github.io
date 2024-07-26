---
categories: ["meta"]
date: "2024-07-25"
title: "Display rate limit in Official Next + Supabase Quick Start"
---

I need to familiarise myself with Next + Supabase, so used this (generally) very engaging [official tutorial](https://www.youtube.com/watch?v=WdA6b0jPNv4) to get me started.

However, I quickly ran into a problem.

The "Log in" page has two buttons: "Sign In" and "Sign Up".

![Login page with sign in and sign up buttons](/Dual-page.png)

Because the "Sign in" button is green, I clicked on it without much thought.  

But, with no signed up, no one can sign in.  A sensible error message, "Could not authenticate user", appears.

So far, so good.  A quick back paddle to "sign up" solves the problem.

But very soon, even the "sign up" button fails, returning the exact same error, "Could not authenticate user".

I was baffled.  Is it the password security policy?  Something to do with my earlier steps?  My having put parentheses around the Supabase URL and API key?

None of these seems to explain the problem.  I was further confused when, creating everything afresh (including destroying and creating a new Supabase project), the sign up function worked again.

I looked through the code more closely and added a console.log around the relevant error object.  It turns out the error message in fact says,

```js
{
  __isAuthError: true,
  status: 429,
  code: 'over_email_send_rate_limit'
}
```

And the email send rate limit?  *3* emails per hour.

![Rate limit](/Rate-limit.png)

This is not hard to exceed at all.  

To make this a true quick start experience, the rate limit should be displayed for the developer to see how quickly it gets used up.