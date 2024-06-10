---
categories: ['meta']
date: "2024-06-10"
title: "Migrating to Hugo"
---

What eventually gave me the push to migrate to Hugo from Jekyll was not technical superiority; but difficulty of getting support online.

I wanted to remove the "Subscribe via RSS" line at the footer of my Jekyll webpage.  But the only information I could find about this was [this discussion from 2019](https://github.com/jekyll/minima/issues/375). Too many things have changed since then and the solution doesn't work easily (or possibly at all).

Contrast Hugo: the only difficulty I ran into was when I was deploying on Github pages (via Action), and I forgot to include the "workflows" folder within the ".github" folder.  Otherwise everything was fine: there was a plethora of up-to-date materials to help with every step of the process.