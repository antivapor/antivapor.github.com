Title: Instagram Tag
Date: 2014-06-10
Modified: 2014-01-13
Slug: instagram-tag
Category: code
Tags: instagram, python, pelican, plugins, liquid
Author: Tom Spalding

Hello world! I had to say that. ;) Today, I want to show you my addition to the [liquid tags](https://github.com/getpelican/pelican-plugins/tree/master/liquid_tags) plugin.

I recently converted from the Ruby-based static site generator [Jekyll](http://jekyllrb.com/) to the Python-based [Pelican](http://blog.getpelican.com/) when I helped the [ACM at my school](http://sfsu.acm.org) do a similar conversion from Wordpress to Pelican (see [my post about the process](http://sfsu.acm.org/blogging-about-blogs.html) if you wish). The only thing I was hesitant about was whether I'd be able to use something akin to inline [Liquid](http://liquidmarkup.org/) tags in my [Markdown](http://daringfireball.net/projects/markdown/) but for [Jinja](http://jinja.pocoo.org/docs/) templates. My inner scientist was thrilled when I saw the Python [notebook](https://github.com/getpelican/pelican-plugins/blob/master/liquid_tags/notebook.py) and the other helpful capabilities in the [liquid tags](https://github.com/getpelican/pelican-plugins/blob/master/liquid_tags/) plugin.

Here's my [small addition](https://github.com/getpelican/pelican-plugins/pull/402); you can use Instagram shortcodes like the Liquid [image tag](https://github.com/getpelican/pelican-plugins/blob/master/liquid_tags/img.py), and also specify the resolution retrieved[^1]. It also warns about any shortcodes that 404.

[^1]: The only caveat is that you don't want to *not* set a size (t/m/l) or width and then expect to use a class called t, m, or l as the first listed class. However, I know you wouldnt do that anyway. I just wanted to say something in a footnote.

Enable this in your code by adding `liquid_tags.gram` to your plugins: `PLUGINS = ['liquid_tags.gram']`.

###Syntax
<s>Heads up, full syntax isn't yet implemented.</s> Full syntax is implemented!

```
{% gram shortcode [size] [width] [class name(s)] [title text | "title text" ["alt text"]] %}
```

###Examples
{% gram pFG7naIZkr t %}

```
{% gram pFG7naIZkr t %}
```

You can specify a size with `t`, `m`, or `l`. This is a coral fungus we found near a <a href="#" alt="SF-89L" title="SF-89L">Nike missile silo</a>  and dangerously amongst a poison oak field!

{% gram pFJE11IZnx %}

```
{% gram pFJE11IZnx %}
```

Or, if no size, it lets `m` be used, which the Instagram API does itself by [default](http://instagram.com/developer/embedding/#media_redirect).

{% gram pFI0CAIZna l 400 figure 'pretty turkey tail fungus' %}

Resolution-size set, width, class, and text.

```
{% gram pFI0CAIZna l 400 figure 'pretty turkey tail fungus' %}
```

{% gram rOru21oZpe l 450 test_class instagram 'warehouse window title' 'alt text' %}

This is the full syntax.

```
{% gram rOru21oZpe l 450 test_class instagram 'warehouse window title' 'alt text' %}
```

Output:

```
<img src="http://photos-c.ak.instagram.com/hphotos-ak-xaf1/t51.2885-15/917172_604907902963826_254280879_n.jpg" width="450" title="warehouse window title" alt="alt text" class="test_class instagram">
```

View the pull request at [github.com/getpelican/pelican-plugins/pull/402](https://github.com/getpelican/pelican-plugins/pull/402).

Idea: If you use the [Better Images and Figures](http://duncanlock.net/blog/2013/05/29/better-figures-images-plugin-for-pelican/) plugin and the CSS [[Duncan Lock](http://duncanlock.net/)] uses, it would make these photos look like [Polaroid](https://en.wikipedia.org/wiki/Polaroid_film) film!
