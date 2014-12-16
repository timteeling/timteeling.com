---
layout: post
title:  "Peek Through Background Effect"
date:   2014-03-11 21:00:00
published: true
style: |
  h1, footer {
    background: #425363;
    font-family: 'Tungsten A', 'Tungsten B', sans-serif;
  }

  h1 {
    font-weight: 300;
    font-size: 4em;
    padding: 1.25em .125em .35em;
    text-transform: uppercase;
    color: #263645;
  }

  @media (min-width: 64.5em) {
    h1 { 
        font-size: 6em;
        padding: 1em .125em .35em;
    }
  }

  .char14,
  .char15,
  .char16,
  .char17,
  .char18,
  .char19,
  .char20,
  .char21,
  .char22,
  .char23 {
    color: rgba(255, 131, 0, .75);

    -webkit-animation: flash 5s linear infinite;
    animation: flash 5s linear infinite;
    -webkit-animation-fill-mode: both;
    animation-fill-mode: both;
  }

  h2 {
      color: #263645;
  }

  a {
    color: #3498db;
  }
---

<span class="scaps">I recently came across</span> the [CodeKit 2.0](http://incident57.com/codekit) landing page and really like the  animations used throughout. Some animations were so subtle that I didn't realize them until looking through a few times.

One that I really like that I wanted to try to replicate was in the Source Maps and Minifiers Section:

<img src="/img/codekit-source-maps.png" alt="CodeKit 2.0 Source Maps">

The subtle animation with the background pattern has a cool effect that makes the pattern look like its being filled up. I had to try to recreate this myself but I wanted to put my own spin on it.

## Top Layer
Instead of the circuit board looking graphic, I used this hexagon nextwork  graphic that is repeatable. The trick here is to use a positive foreground and whatever cuts you want to show through should be transparent. Also, you'll have more flexibility and sharper results if you use SVG (especially if you only support IE9+). This will be used as a CSS background image.

<img src="http://timteeling.com/dev/img/network.svg" alt="Network Image" />

<pre>
<code class="language-css">
.container {
  background-image: url('http://timteeling.com/dev/img/network.svg');
}
</code>
</pre>

## Bottom Layer
I'm going to get to the middle layer in a moment, but our base layer will be a background color. The color set here will be what shows through the clipped image. I set it to #263645.

<pre>
<code class="language-css">
.container {
  background-color: #263645;
  background-image: url('http://timteeling.com/dev/img/network.svg');
}
</code>
</pre>

## Fancy Middle Layer
Now the fun part. I want parts of the hexagons to light up orange like they are parts of a network being scanned. We can have multiple background images by separating them with commas and in this case we are going to add a gradient to go with the image we already have.

Here is what we see below the image.

<div style="margin-bottom: 2em; background-color: #263645; background-image: radial-gradient(200px 500px at center, #ff8300 0%, transparent 50%, transparent); height: 300px;"></div>

<pre>
<code class="language-css">
.container {
  background-color: #263645;
  background-image: url('http://timteeling.com/dev/img/network.svg'),
  radial-gradient(200px 500px at center, #ff8300 0%, transparent 50%, transparent);
  background-size: 125%, 50% 100%;
  background-position: 0 60%, 0 100%;
}
</code>
</pre>

## Adding Animation
Now we want the orange gradient to move across the screen, we can do this by animating our background-position. Note that we need to account for both background images. We only want to animate the second image so our background-positions need to be comma separated.

<pre>
<code class="language-css">
@keyframes move {
    0% { 
        background-position: 0 60%, 0 50%;
    }
    100% { 
        background-position: 0 60%, 100% 50%;
    }
}

.container {
  background-color: #263645;
  background-image: url('http://timteeling.com/dev/img/network.svg'),
  radial-gradient(200px 500px at center, #ff8300 0%, transparent 50%, transparent);
  background-size: 125%, 50% 100%;
  background-position: 0 60%, 0 100%;
  animation: move 5s linear infinite;
}
</code>
</pre>


## Final Effect

Now that we have all three layers on top of one another, we can animate the middle layer to get the spotlight or moving fill effect. The final effect can be seen on CodePen.

<p data-height="268" data-theme-id="0" data-slug-hash="KDlCd" data-default-tab="result" class='codepen'>See the Pen <a href='http://codepen.io/timteeling/pen/KDlCd'>Peeking Through the Background</a> by Tim Teeling (<a href='http://codepen.io/timteeling'>@timteeling</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
<script async src="//codepen.io/assets/embed/ei.js"></script>
