---
categories: ['meta']
date: "2024-07-15"
title: "Hugo deploy: struggle v choice"
---

Given my familiarity with Vercel, I initially wanted to deploy my Hugo blog there.

But the process was just too difficult.  Following the [official guide](https://vercel.com/guides/deploying-hugo-with-vercel) led to a webpage that displayed some, but not all, features of my ```theme```.  

I tried a few troubleshooting tips from various sources, but without a deep understanding of how Vercel works, couldn't find a fix.  

Online discussions seem to put the finger of blame on which Hugo version is used by Vercel: but without knowing the full context it was hard to get a feel for whether that is right.

I then changed tracks to starting from a [Hugo starter](https://vercel.com/templates/hugo/hugo) provided by Vercel itself.  It worked perfectly well with the default theme, but once agin, the moment I switched to other themes, problems would surface.

It only occurred to me 1-2 hours in that there is another way of doing things.

I chose Vercel in the first place because I thought I could save time with my familiarity with Vercel in general.  

But given it is a hobby project I don't have any solid reason to choose Vercel over anything else.  The time I had spent on finding various fixes for the Vercel deployment already outweighs any time savings from familiarity.  Time to give up the struggle and start afresh.

[Hugo](https://gohugo.io/hosting-and-deployment/hugo-deploy/) lists a wide range of options for deployment, each with its own dedicated tutorial.  After trying Gitlab and finding the set-up too complex, I settled on Netlify and the process went very smoothy from there.

Overall, in this situation, I think I struggled slightly too much.  The desire to stick to a well-known deployment strategy is understandable. 

But there must be a point where the costs outweighs the benefits: especially if (as in my case) main goal is just to get a website up-and-running, as opposed to learning anything very deep about the process of deployment as such.