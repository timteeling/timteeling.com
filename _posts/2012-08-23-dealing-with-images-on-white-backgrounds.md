---
layout: post
title:  "Dealing with Images on White Backgrounds"
date:   2012-08-23 15:51:41
style: |
  .demo {
    margin-top: 1em;
  }

  .demo figure {
    position: relative;
    margin: 0 auto;
  }

  .demo figure:before {
    -webkit-box-shadow: inset 0 0 25px rgba(0,0,0,0.1);
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    content: "";
  }

  .demo img {
    display: block;
    margin: 0 auto;
    max-width: 100%;
  }

  @media screen and (min-width: 980px) {
    .demo figure:before {
      -webkit-box-shadow: inset 0 0 50px rgba(0,0,0,0.1);
    }
  }
---

I read a lot of tech blogs and the majority of images feature a product or graphic on a plain white background. Since a vast majority of sites feature white backgrounds, these images can cause some odd illusions to a layout since the amount of white space around the product or graphic varies.

<figure>
  <img src="/img/msft.jpg" alt="Microsoft Logo" title="Microsoft Logo" class="aligncenter" />
</figure>

I like how <a href="http://theverge.com">The Verge</a> has dealt with this problem.  They overlay a subtle inset box shadow over all of their images.  It's so subtle that you don't notice it on images with darker backgrounds.  On white backgrounds, it adds a nice vignette effect and defines the boundaries of the image.

<div class="demo">
<figure>
  <img src="/img/msft.jpg" alt="Microsoft Logo" title="Microsoft Logo" class="aligncenter" />
</figure>
</div>

The markup and styling behind it is surprisingly simple.  They use a <code>div</code> to wrap their images but I'll use the more semantic <code>figure</code> element.

<h3 class="code-title">HTML</h3>
<pre class="language-markup">
<code>
&lt;figure>
  &lt;img src="path/to/image.jpg" alt="Image" />
&lt;/figure>
</code>
</pre>

We'll use the <code>:before</code> pseudo element to apply our inset box shadow by absolutely positioning it within the relatively positioned <code>figure</code> element.

Note that with a larger blur value, the background appears more gray when the image is scaled down. We can use media queries for smaller viewports to make the box shadow blur smaller to preserve the vignette effect. 

<h3 class="code-title">CSS</h3>
<pre class="language-css">
<code>
figure {
  position: relative;
  margin: 0 auto;
}

figure:before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  -webkit-box-shadow: inset 0 0 50px rgba(0,0,0,0.1);
  -moz-box-shadow: inset 0 0 50px rgba(0,0,0,0.1);
  box-shadow: inset 0 0 50px rgba(0,0,0,0.1);
}

img {
  display: block;
  margin: 0 auto;
  max-width: 100%;
}
</code>
</pre>

There is one issue that I'm coming across with making this scale down to mobile devices.  For some reason, there is a disparity between the height of the <code>figure</code> element and the <code>img</code> element when the site is under 600px wide.  I haven't been able to simulate it in another environment outside of this site so I'm wondering what my theme and reset is doing to it.