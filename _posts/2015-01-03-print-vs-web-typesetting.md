---
layout: post
title:  "Print vs Web Typesetting"
date:   2015-01-03 21:00:00
published: true
---

<p class="lede">Why haven't more typesetting conventions from print spilled over to the web?</p>

I've been reading more print magazines lately in an effort to escape all the screens around me. I read *Wired* and *Fast Company* every month and I've noticed there are several practices and tricks employed by print designers that are not used on the web. I'm going to try wrapping my head around each of these and rationalize why or why aren't they used on the web.

### What print can get away with
Designing for print obviously has some advantages over designing for the web. Print designers have the luxury of knowing the page dimensions and have centuries of work to reference. Here are some concepts of what print can do but the web can't seem to pull off:

##### Using bold weights for longer passages
I don't really know how common this is but *Wired* uses Brandon text at a bold weight for certain sidebar articles. I didn't notice it at first but once I realized it, I question how that is able to work.

##### Shorter measures
Print traditionally has a shorter measure that what is seen on the web since overlowing column layouts are typically used on the page. 45-75 characters is the ideal line length but some columns in print use less than 20 characters.Short measures on the web are odd enough since longer than ideal measures are normally seen.

##### Designing out of the box
Responsive design with a focus on performance has inhibited designers from creating experiences that flow beyond the box. It is called the *box* model after all. I think this is also a symptom of us designing in the browser. Lots of sites are very rectangular. This is in stark contrast to *Wired* and *Businessweek* features in print. [*Bloomberg Politics*](http://bloomberg.com/politics) has shown this is possible on the web and I hope that more sites take after them

### What isn't common on the web
I'm not saying that all of the following is not possible on the web, but the usage of the following things is not common. Some is due to technical reasons while others just seem to be cultural.

##### Pilcrow Usage
The pilcrow ( ¶ ), also known as the paragraph symbol, is used in print to combine the first few paragraphs into one larger block of text to fit the design of a layout. There is nothing keeping this convention from being used on the web, it is probably not used since it would not be semantic to combine multiple paragraphs for the sake of design.

##### Sidebars within articles
There is nothing technical limiting this. Hell, the `aside` element was supposed to be used for this but I rarely see sidebars within articles on the web. *Vox* has recently started to [experiment](http://www.vox.com/2014/11/12/7186667/office-fitness-exercises-stretches) with sidebar information in features but this is the only example that I could find.

##### Hyphenation and Justification
Text on the web is rarely justified because there is a lack of proper hyphenation support in browsers. Progress has been made getting hyphenation into web browsers but Chrome still does not support it and the hyphenation in IE and Firefox are still not as powerful or as smart as what you find in InDesign. They break words in awkward places.
    
    p {
        hyphens: auto; /* Works in Firefox, Safari, IE10+ */
    }

##### Indented paragraphs
This is probably due to browser defaults to give paragraphs margins between one another and to not indent, but seldom do you see paragraphs indented and without any margin in between them.

    p {
        margin: 0;
    }

    p + p {
        text-indent: 1em;
    }

##### Small caps
Dropcaps have caught on in editorial design with the `:first-letter` pseudo selector (although it behaves differently across browsers) but small caps have not caught on as much. Typically, drop caps or small caps are used to begin an article. I think the usage of small caps isn't as widespread due to a combination of performance considerations of including another font weight and also that there are not a lot of small cap fonts widely available by font providers. When they are present, they are not easily findable in services like Typekit and Google Fonts.

    abbr {
        font-variant: small-caps;
    }

##### Hanging punctuation
Looks like there is a [proposal](http://css-tricks.com/almanac/properties/h/hanging-punctuation/) for this but browsers have yet to implement it anywhere. It can kind of be faked by using `text-indent` but only on a first and you have to account for character widths.

    p {
        hanging-punctuation: first;
    }

### Will anything catch on?
As time passes browsers will implement and make possible most of today's limitations. Other new developments like Flexbox, CSS Shapes, and CSS Regions will further make layouts on the web more like print. Each new redesign brings print and web closer together.
