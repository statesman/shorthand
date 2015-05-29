Shorthand stuff
======================

## Shorthand help docs

Shorthand has a website for [Guidelines and help](http://www.shorthand.happyfox.com/home), including [Media sizes](http://www.shorthand.happyfox.com/kb/section/5/).

## Logo

* Thought is as of 5/29/2015 to use the `logo-short-black-ia.png`, which just says Statesman. It has been run through a program called [ImageAlpha](http://pngmini.com) to clean it up, based on Shorthand recommendations.
* `logo-ia.png` is the full Austin American-Statesman logo, which has been run through ImageAlpha. It is too wide for phones, but we'll retain it in case we want to use it some time in the future.

## Favicon

Add this to the `<head>`.

``` html
<link rel="shortcut icon" href="http://media.cmgdigital.com/shared/theme-assets/242014/www.statesman.com_5126cb2068bd43d1ab4e17660ac48255.ico" />
```

## Metrics

To get metrics on a shorthad project, we need to do the following:

* Rename `index.html` to `index.php`
* Drop copies of the two files into the root of the project:
  * `metrics-head-inc`
  * `metrics.inc`
* Take the following code and drop it into `index.php` AFTER the opening `<head>` tag:

``` php
<!-- cmg metrics -->
<?php include "metrics-head.inc";?>
```

* Take the following code and drop it BEFORE the closing `</body>` tag:

``` php
<!-- cmg footer metrics -->
<script type="text/javascript">
  var projectSite = "statesman";
  var projectChannel = "news"; // Medley Category
  var projectCategory = "local"; // Medley subCategory
  var projectSubCategory = "blanco-river-flooding"; // project name
</script>

<?php include "metrics.inc";?>
```

* Edit the `project[X]` vars above. Make sure you use actual Medley category and subcategory names, spelled correctly. Look at the source of an existing page with that category/subcategory and copy/paste it.

## CSS changes

The CSS window has some example targeting like the `story-title` and `story-heading`.

Here is an example pulling in a Google font and then applying it to those styles. (They are snips, not the entire CSS file.):

``` css
<link href='http://fonts.googleapis.com/css?family=Merriweather:400,400italic,900|Merriweather+Sans:400,400italic,800' rel='stylesheet' type='text/css'>

/* Title Section */
.section-title .story-title {
    font-family: 'Merriweather', Arial, serif; font-weight: 900; 
}
.section-title .story-heading {
    font-family: 'Merriweather', Arial, serif; font-weight: 400; 
}

/* Text Over Media */
.section-text-over-media .text-over-media-inner {
    font-family: 'Merriweather', Arial, serif; font-weight: 900;
}
```

## Soundcite

We've tried using the [Knight Center SoundCiteJS](http://soundcite.knightlab.com/) project in Shorthand, and it is possible, with some caveats.

* The paragraph of text where you want to us the span tag with the sound reference must in an HTML block. Only those with Developer status (Christian & Andrew) can add them.
* The SoundCiteJS code can be added outside the `<script>` tags in the JAVASCRIPT section in Shorthand (again, by a developer).

```
<link href='//cdn.knightlab.com/libs/soundcite/latest/css/player.css' rel='stylesheet' type='text/css'><script type='text/javascript' src='//cdn.knightlab.com/libs/soundcite/latest/js/soundcite.min.js'></script>
```

You can also drop a regular Soundcloud embed player in as an HTML block.
