Shorthand stuff
======================

## Logo

We're still working out what logo will work best. Christian has a note out asking Rachel at Shorthand about it.

* `logo-320.png` works, but it is too long for phones.
* `logo-240.png` gets blown out because it isn't big enough.

## Metrics

To get metrics on a shorthad project, we need to do the following:

* Rename `index.html` to `index.php`
* Drop copies of the two files into the root of the project:
  * `metrics-head-inc`
  * `metrics.inc`
* Take the following code and drop it into `index.php` AFTER the opening `<head>` tag:

```
<!-- cmg metrics -->
<?php include "metrics-head.inc";?>
```

* Take the following code and drop it BEFORE the closing `</body>` tag:

```
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

* The entire paragraph you have that uses the span tage with the sound reference must in an HTML block. Only those with Developer status (Christian & Andrew) can add them.
* The SoundCiteJS code can be added outside the `<script>` tags in the JAVASCRIPT section in Shorthand (again, by a developer).

```
<link href='//cdn.knightlab.com/libs/soundcite/latest/css/player.css' rel='stylesheet' type='text/css'><script type='text/javascript' src='//cdn.knightlab.com/libs/soundcite/latest/js/soundcite.min.js'></script>
```
