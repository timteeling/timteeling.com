---
layout: post
title:  "Display Top Content from Google Analytics with Status&nbsp;Board"
date:   2013-04-19 10:07:41
style: |
  h1 {
    background: #3fae29;
    font-family: 'Tungsten A', 'Tungsten B';
    font-weight: 400;
    text-transform: uppercase;
    padding-left: .25em;
    padding-right: .25em;
  }
  
  h2 {
    font-family: 'Tungsten A', 'Tungsten B';
    font-weight: 400;
    text-transform: uppercase;
    }
  
  a {
  color: #3fae29;
  }
  
  footer {
  background: #3fae29;
  }
---

<p>I bit the bullet and bought <a href="http://panic.com/statusboard">Status Board</a> last night and it's gorgeous but I needed to find more ways to display my data.</p>

<p>I was rummaging around for data to pull in and came across Carl Franzon's <a href="http://www.carlfranzon.com/2013/04/google-analytics-panel-for-status-board/">PHP script</a> for Google Analytics to display a week's worth of visits and pageviews as a line graph. The script is based off of the g-api library so there is an immense amount of data you can pull from it.</p>

<img src="/img/status-board-top-pages.png" alt="Status Board - Google Analytics Top Content" width="1536" height="1024" class="aligncenter size-full wp-image-426" />
<h2>Displaying Top Content</h2>
<p>I forked Carl's GitHub repo and hacked together another file called toppages.php that displays the top URLs with their corresponding number of pageviews from the past seven days. Please follow the instructions in the readme file to add it to your Status Board.</p>

<h2>Warning: I suck at PHP</h2>
<p>Please feel free to add/change anything to the repo as I don't have any knowledge of PHP beyond the basics. I'm certain that what I hacked together can be improved.</p>

<p>Thanks Carl and thanks Panic!</p>

<a class="btn" href="https://github.com/timteeling/SBAnalytics" onclick="_gaq.push(['_trackEvent', 'Download', 'Click', 'Google Analytics Status Board Download']);">Download from GitHub</a>