---
layout: post
title:  "Lightboxes & Pseudo Elements"
date:   2013-07-08 20:35:41
style: |
  body, h1 {
    font-family: 'Mercury SSm A', 'Mercury SSm B';
  }

  h1 {
    background: #fff;
    color: #444;
    padding-bottom: .125em;
    border-bottom: 3px solid tomato;
    margin-bottom: .5em;
    padding-bottom: .75em;
  }
  
  h3 {
  border-bottom: 3px solid tomato;
  }
  
  .entry {
  text-align: center;
  }
  
  .entry .container {
  text-align: left;
  }

  header[role=banner] {
    background: transparent;
    border-bottom: 3px solid tomato;
    
  }

  header[role=banner] a {
    color: tomato;
  }

---
<p>How can we better indicate a lightbox to a user?</p>

<p>A large number of visuals that I have to use in my day to day are product screen shots. Thumbnail versions of these are usually quite worthless so you usually have to resort to using some sort of lightbox plugin to display the image larger.  Here's a quick little trick to tell the user that the image is a lightbox.</p>

<p>First, let's look at some basic markup from what you'd find with most lightbox plugins:</p>

<h3>HTML</h3>

<pre class="language-markup"><code>&lt;a href="/path/to/image.jpg" class="lightbox">
  &lt;img src="thumbnail.jpg">
&lt;/a>
</code></pre>


<p>If we can hook onto that lightbox class in CSS, we can use pseudo elements to signify to click to enlarge.</p>

<h3>CSS</h3>

<pre class="language-css"><code>.lightbox {
  position: relative;
}

.lightbox:after {
  content: 'Click to Enlarge'; 
  position: absolute;
  left: 0;
  bottom: -1.5em;
}
</code></pre>


<p>This will give us linked text below our thumbnail image. You may ask why do it this way if I can just write a caption or something like that? The real power behind this trick is the ability to integrate icon fonts with it.</p>

<p>If we slightly tweak the CSS in our <code>after</code> pseudo element, and include a reference to a unicode character for a magnifying glass (I'll use <a href="http://fontawesome.io">Font Awesome's</a> as an example), then we get a much nicer result.</p>

<h3>CSS</h3>

<pre class="language-css"><code>.lightbox:after {
  content: '\f002 Click to Enlarge'; 
  font-family: 'FontAwesome', 'proxima nova', sans-serif;
  position: absolute;
  left: 0;
  bottom: -1.5em;
}
</code></pre>


<p>Specifying a fallback font that is inline with the rest of your font stack allows you to mix the icon font character along with regular text, however, you will run into issues if you use normal letters, numbers, or symbols to map your icon fonts.</p>