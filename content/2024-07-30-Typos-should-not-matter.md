---
categories: ["meta"]
date: "2024-07-30"
title: "Reflections on a typo"
---

Much of my day was spent working on a bug described in this [SO question](https://stackoverflow.com/questions/78812601/env-file-in-next-js-changes-the-behaviour-of-mailgun-js-solved).

In a narrow sense, it was caused by a careless error: it was a hanging " in one of my environment variables.

But in the broader sense, the problem wasn't the typo.  It is my unfamiliarity with Next.js, which made me look and double-check all these areas:-

- client/server components
- different .env file settings for each
- the concept of components itself
- Next directory structure
- mailgun create method

Had I known the eco-system better, I wouldn't have looked so widely: the typo would have been spotted sooner.