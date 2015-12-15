## CSS changes

These are optional. With the newer Shorthand template, we don't **have** to change this.

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