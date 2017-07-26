---
layout: post
title:  "The Tools We Use Are Not As Friendly As the Websites We Make"
date:   2015-08-27 15:00:00
published: true
---

<p class="lede">My struggle to find a mobile device friendly workflow for writing and creating on the web</p>

I recently moved across country from Baltimore to Portland. I made a [travel blog](http://bootscootin2pdx.com) to chronicle the trip but building it proved to be a challenge. While I'm used to using Jekyll, Grunt, and Sass for most projects now, I realized  if I was looking to maintain the site primarily from my phone (while in the car or at a rest stop), I wouldn't be able to easily update it if the site was built with Jekyll.

I ended up going with WordPress and using their mobile app. That worked well for the most part to write posts but I still felt constrained in what I could do with the site.

Image uploads worked surprisingly well within the post but setting a featured image doesn't allow you to resize or edit the image. Uploading large files without being to resize thrashed my data plan quite a bit since I was only able to be on Wi-Fi periodically over the course of 16 days.

### The tools don't match the workflow
I learned as I went along and when I went to make changes, I found myself trying to tweak CSS (that meant ditching Sass) and some template files through the WordPress admin and then remembered to use with Coda for iOS directly on the server. I had the site's code in a [GitHub repo](https://github.com/timteeling/pdx) but there was no easy way to commit the changes I made to it.

Panic's recent release of [Coda for iOS](http://panic.com/coda-ios) (née Diet Coda) is an amazing piece of software, but it drives me insane that it doesn't fit into the common web worker's workflow today. There's no easy way to run a grunt task, make a git commit, or compile some Sass. It's focused on the older workflow of being an FTP ninja directly modifying files on a server. I am by no means blaming Panic, I just don't think there's a good solution to these problems yet. Solving this would include having to checkout code from a git repo, run a local web server, and compile code with Node or Ruby. I bet some if not all of this wouldn't fit Apple's sandboxing rules for the App Store, so what are we left to do?

### Not just a mobile device problem

I'm glad to finally get this out of my head since I moved in June. Seeing Dave Rupert write about his ongoing pains with his [switch to Windows](http://daverupert.com/2015/08/developing-on-windows/) sure helped. It's so similar and at the same time you'd never think that it would be so difficult to make a switch like that. He really struck a chord with saying that the HTML, CSS, and JavaScript we painstakingly write to work in all sorts of browsers and devices, however the tools and workflows we use are not universal. How can you update your responsive Jekyll site from your phone? Can an author make changes and create new content to your site regardless of device?

We really take our tools for granted. We need to better account for how our authors will be using and modifying the sites we build. Echoing Brad Frost, the solution is not as simple as ["just..."](https://the-pastry-box-project.net/brad-frost/2014-january-28)
