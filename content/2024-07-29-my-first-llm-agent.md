---
categories: ["meta"]
date: "2024-07-29"
title: "My first LLM agent"
---

I was recently invited to try [PromptBro](https://promptbros.ai/)'s LLM agent function.

While I occasionally use [Perplexity.ai](https://www.perplexity.ai/) for debugging, my exposure to LLM agents was limited to the very amusing [Bertie Wooster bot](https://poe.com/BertieWooster) on Poe.

The sign-up experience is smooth.  One of the first things I tried is the DALL-E integration, and I was impressed by the quality of the image generated.

I entered the following text prompt.

> Give me a tutor who teaches a web dev (who is familiar with the usual tools) how to use the framework Next.js with Typescript and Supabase.

Which was then apparently expanded into this longer description.

> A scene showing a web development tutor and a student immersed in a learning session. The tutor who belongs to a Black descent is carefully guiding his Hispanic student through the intricacies of using the Next.js framework with Typescript and Supabase. The tutor is demonstrating on a large screen, showing codes and functionalities. The student looks on, focused and thoughtful, his fingers flying over his laptop keyboard as he implements the new learnings. Around them, the room is filled with the usually used web development tools such as a text editor, browser, and console terminal.

And in turn this image.

![Next.js tutor](/Next.js-tutor.png)

Which was impressive.

This image came in handy when I was creating my agent, with a view of feeding it my (then unsolved) [SO question](https://stackoverflow.com/questions/78812601/env-file-in-next-js-changes-the-behaviour-of-mailgun-js-solved).  The image is already there for selection when I was asked to give an image to my agent.

There was a slight hiccup in the set-up, however.  I was asked to select a prompt for the agent, but could not find any.  A quick Google later, I back-paddled and created [my first prompt](https://promptbros.ai/prompt/clz8p5epr00018t79pgio3y4z) first and used it to create [my first agent](https://promptbros.ai/prompt/clz8p5epr00018t79pgio3y4z).

After creating the agent, I copied and patsted my SO question to see if it could provide an answer.

The experience is quite different from the generic LLMs I use online.  The agent suggested two areas of investigation:

- the .env file being read at run time, not the compile time.
- problems with the instantiation of the Mailgun instance.

For each area, it gave detailed reasons, with the design principles behind the tools, as requested by the Prompt.

However, a moment's thoughts revealed that neither of these suggestions can be right.  The environmental variables were logged out correctly when the Mailgun instances were created.  So the problem must be elsewhere.

I moved on to asking how I can try to elicit a more detailed error message from the code.  This time, the answers were in the right direction: I got an ```MailgunAPIError``` error message, which I had seen but not thought about much earlier.

Even though at first sight obscure, this helped me realise nature of the error: a [typo] to my API key.  It dawned on me as I was reading the ```mailgun.js``` docs that the reason why no further detailed error message was given is (likely) because nothing more could be said: the error was beyond the module and is instead due to the wrong API key.

While the Next.js tutor (the agent in question) did not help me debug my code in any direct way, the discursive nature of the answers did help me get to the root of the problem quicker: by being discursive with its reasoning, I could more quickly spot that I was being taken down the wrong road and back-paddle more quickly.

I have not decided how much I will continue the use LLM agents in my work flow, but this first encounter is certainly very encouraging.