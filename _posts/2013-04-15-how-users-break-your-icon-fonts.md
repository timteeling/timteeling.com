---
layout: post
title:  "How Users Kill Your Icon Fonts"
date:   2013-04-15 10:46:41
categories: 'icon fonts'
---

<p><span class="scaps">I remember reading</span> Alex Limi's post, <a href="http://limi.net/checkboxes-that-kill">Checkboxes that kill your product</a> a couple of weeks ago and found out that icon fonts can be added to his list.</p>

<p>I came across this a few days ago at work.  We were using <a href="http://fortawesome.github.io/Font-Awesome/">Font Awesome</a> in some development builds of two of our products. After some testing, I had heard that we received some feedback from Firefox users complaining about broken images in the UI. I thought that was strange since there were barely any images in the UI in question but once we received screenshots of the errors it was obvious.</p>

<p>The users were overriding the fonts we had specified in the UI, including the icon font so it looked like an empty glyph not supported by the font. The product in question is used mainly by members of the security community. Members of this community are known for being fans of custom stylesheets, user scripts, and never allow HTML in their emails.</p>

<p>After some searching I found that it's surprisingly easy to block icon fonts from rendering in your browser. Here's how to do it:</p>

<h3>Firefox</h3>
<p>Go to Firefox -> Preferences and click on the Content tab. There is a section called Fonts &amp; Colors and if you click the Advanced button, a window will drop in and give you the option change the default fonts in Firefox as well as giving you the option to disable "Allow pages to choose their own fonts, instead of my selections above."</p>

<p>If you uncheck this, then all fonts that are loaded via @font-face, TypeKit, Google Web Fonts, and icon fonts will no longer work.</p>

<h3>Chrome</h3>
<p>Type in <code>about:version</code> into the omnibar in Chrome and find the Profile Path. Go to that path. For Mac the path is:</p>

<pre><code>/Users/tteeling/Library/Application Support/Google/Chrome/Default</code></pre>

<p>Once inside that folder find the User StyleSheets folder and there will be a custom.css file in there. Add this (or something similar) to the file and save.</p>

<pre class="language-css"><code>* { font-family: 'comic sans ms'; }</code></pre>

<p>Some elements of your site will be overtaken by the user specified style but not all.  To get <em>everything</em> to obey the custom stylesheet we can add important to the declaration:</p>

<pre class="language-css"><code>* { font-family: 'comic sans ms' !important; }</code></pre>

<h2>Is there a Solution to Prevent this?</h2>

<p>Icon fonts have blown up in popularity over the past year and I can't think of a solution to this problem. SVG and PNG fallbacks come to mind but I have no idea how you can detect if an icon font is being overridden even if it is loading.</p>

<p>Should we care that a user can wreck their own experience? I understand that the situation I described is what most people would call an edge case but as front end developers, isn't our job to cater to all users the best we can regardless of device, browser, or scenario?</p>

<p>This encounter made me realize that even though icon fonts have a lot of great benefits, they do not degrade gracefully. In the meantime, we discontinued using icon fonts in our product and went back to using image sprites instead.</p>