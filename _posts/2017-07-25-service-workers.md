---
layout: post
title:  "Service Workers Are More Work Than They First Appear"
date:   2017-07-25 18:00:00
published: true
---

<p class="lede">It's not as simple as specifying which files to cache offline</p>

I've been trying to learn how to build progressive web apps recently and have come across [several](https://ethanmarcotte.com/wrote/going-offline/) [blog](https://csswizardry.com/2017/01/moving-css-wizardry-onto-https-and-http-2/) [posts](https://www.smashingmagazine.com/2016/02/making-a-service-worker/) outlining how to implement a "simple" service worker. I've followed along and the root of most of these tutorials stems from [Google's Web Fundamentals](https://developers.google.com/web/fundamentals/getting-started/primers/service-workers) article on the subject.

I've followed along to add a service worker for this site to make pages, posts and CSS cached for offline use. However, what I'm running into issues with is what to do after you deploy your first changes using the service worker.

The Google article briefly talks about how you need to bump the version number or name of your cache and to delete the old version. This makes sense but this seems like a very manual thing to do that needs to be taken care of by some sort of build step.

Another thing that's bugging me that I need to figure out is the service worker's cache getting in the way of me working on the site when I'm running it locally. It looks like Dev Tools has a way to pause it but you have to keep the Applications tab open. Another unintended consequence of the cache is when I tried building another Jekyll site and running it on port 4000 and got this site still!

In the end I'm reminded of the old adage about cache invalidation being one of the hardest things in computer science... It looks like I'm stuck bringing in [a package](https://github.com/GoogleChrome/sw-precache) and configuring some build scripts to determine when to use the cache, when not to use the cache and when to bump the cache.

Service workers are supposed to be the next big thing (once WebKit gets onboard) but them needing to rely on external steps and tools for continued use just reminds me that [the tools we use](the-tools-we-use) are not as friendly as the websites we make.
