---
categories: CSS
date: "2024-04-11T00:00:00Z"
title: Fundamentals in CSS
---

Kevin Powell points out that people (certainly me!) tend to be too impatient with CSS.  

They assume it is a “simple” technology and just resort to looking up answers on Google as they go along, without trying to understand the undelrying principles.

But paradoxically in CSS more than in (say) Javascript, fundamentals matter even more.  

The layout of a web page differs from device to device and from browser to browser.  It has more moving parts than most programming environments.  Errors (and glitches) are context-specific and hard to replicate.  It is not as easy asking about it compared with asking about environments that operate mainly on numbers and letters.

So just "getting your hands dirty" without thinking may not be a good approach for the CSS novice.

For example,  I was doing a React project recently using Tailwind, and got frustrated that somehow a <div> element wasn’t filling out the screen as it should.  

I flailed around for an answer within React/Tailwind.  But after a while, I realised the issue probably lies not with the Tailwind, but with the background colour set on the index.html file.  

Fixing this did not require  extra knowledge online: all I needed was to slow down and think through how the CSS is applies to the html displayed via React.

More from Kevin Powell:
- [Video on good learning resources](https://www.youtube.com/watch?v=2GeMknXoGaA&t=605s)

Games recommended in the video:
- [Flexbox Froggy](https://flexboxfroggy.com/)
- [Grid Garden](https://cssgridgarden.com/)

- [CSS dinner](https://flukeout.github.io/)

See also:
- [Code pip](https://codepip.com/) by the author of Flexbox Froggy and Grid Garden
- [2022 List of CSS games](https://dev.to/dailydevtips1/10-amazing-games-to-learn-css-382i)