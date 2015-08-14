Shorthand stuff
======================

## Shorthand help docs

Shorthand has a website for [Guidelines and help](http://www.shorthand.happyfox.com/home), including [Media sizes](http://www.shorthand.happyfox.com/kb/section/5/).

## Sharing setup

* User our atxne.ws bitly account in Passpack.
* VIA is is just the account: "statesman" or "austin360"
* Facebook App ID: 881505665256530

## Adding Brightcove video

* You'll need this site [www.embedresponsively.com](www.embedresponsively.com), then click on the tab **Generic iFrame**.
* Go into Brightcove and find your video
* On the right under Quick Video Publish, go under "Select a player" and choose **JANUS Chromeless Single**.
* Copy the JavaScript code into the Embed Responsively site and click **Embed**.
* Go below the video shown and copy the Embed code listed there.
* Go into Shorthand and create a New Section and pick **Custom HTML**
* Remove the dummy H1 line and replace it with your embed code.

Note, on Embed Responsibly they suggest taking out any parameters with sizes in the original embed. We haven't at this point, but it might be worth considering if we see sizing problems on some platforms.

## Soundcite

We've tried using the [Knight Center SoundCiteJS](http://soundcite.knightlab.com/) project in Shorthand, and it is possible, with some caveats.

* The paragraph of text where you want to us the span tag with the sound reference must in an HTML block. Only those with Developer status (Christian & Andrew) can add them.
* The SoundCiteJS code can be added outside the `<script>` tags in the JAVASCRIPT section in Shorthand (again, by a developer).

```
<link href='//cdn.knightlab.com/libs/soundcite/latest/css/player.css' rel='stylesheet' type='text/css'><script type='text/javascript' src='//cdn.knightlab.com/libs/soundcite/latest/js/soundcite.min.js'></script>
```

You can also drop a regular Soundcloud embed player in as an HTML block.

## Getting Shorthand projects wrapped by CMG

We've been sending the index.html file to Jon Robison or Maysam H. to get the minimalist wrap applied to stories. All you have to send them is the index.html file.

Thos wrapped files don't currently have Chartbeat, so we need to manually add it until they do.


### In the head

The `<head>` tag is in some weird-ass script tag. Search for `/head` to find the end of it and put this code after their `minmalist.js` call.

``` javascript
<!-- chartbeat head -->
<script type="text/javascript">var _sf_startpt=(new Date()).getTime()</script>
```


### In the body

Same deal as the head, search for `/body` and add this on new lines right before the close tag.

MAKE SURE YOU CHECK THE `chartbeatdoman` FIELD AND UPDATE WITH THE CORRECT DOMAIN AS NECESSARY.

``` javascript
<!--  Chartbeat code -->

<script type="text/javascript">
  var chartbeatdomain = 'mystatesman' + '.com'
  var _sf_async_config = { uid: 31585, domain: chartbeatdomain, useCanonical: true };
  (function() {
    function loadChartbeat() {
      window._sf_endpt = (new Date()).getTime();
      var e = document.createElement('script');
      e.setAttribute('language', 'javascript');
      e.setAttribute('type', 'text/javascript');
      e.setAttribute('src','//static.chartbeat.com/js/chartbeat.js');
     document.body.appendChild(e);
    };
    var oldonload = window.onload;
    window.onload = (typeof window.onload != 'function') ?
      loadChartbeat : function() { oldonload(); loadChartbeat(); };
  })();
</script>
```

### Publishing

We are currently putting these on the projects server. Make sure you've worked with the designer of the project to use the write directory location based on the URL they've put in the sharing setup of the Shorthand project.

## Metrics if not wrapped by CMG

I've moved this from a php-based include system to putting it all in the index.html file. I've left the old `metrics-head.inc` and `metrics.inc` files for posterity.

### Logo

* Thought is as of 5/29/2015 to use the `logo-short-black-ia.png`, which just says Statesman. It has been run through a program called [ImageAlpha](http://pngmini.com) to clean it up, based on Shorthand recommendations.
* `logo-ia.png` is the full Austin American-Statesman logo, which has been run through ImageAlpha. It is too wide for phones, but we'll retain it in case we want to use it some time in the future.

### In the head

Place the following code right after the open `<head>` tag:

``` javascript
<!-- Quantcast Tag, part 1 -->
<script type="text/javascript">
  var _qevents = _qevents || [];
  (function() {
   var elem = document.createElement('script');
   elem.src = (document.location.protocol == "https:" ? "https://secure" : "http://edge")
               + ".quantserve.com/quant.js";
   elem.async = true;
   elem.type = "text/javascript";
   var scpt = document.getElementsByTagName('script')[0];
   scpt.parentNode.insertBefore(elem, scpt);  
  })();
</script>

<!-- chartbeat head -->
<script type="text/javascript">var _sf_startpt=(new Date()).getTime()</script>

<!-- favicon -->
<link rel="shortcut icon" href="http://media.cmgdigital.com/shared/theme-assets/242014/www.statesman.com_5126cb2068bd43d1ab4e17660ac48255.ico" />
```


### In the body

* Place the following just before the closing `</body>` tag
* Update the projectSite, projectChannel, projectCategory and projectSubCategory values.


``` javascript

<!-- cmg footer metrics -->
<script type="text/javascript">
  var projectSite = "statesman";
  var projectChannel = "news"; // Medley Category
  var projectCategory = "local"; // Medley subCategory
  var projectSubCategory = "shorthand-project-name"; // project name
</script>

<!-- statesman sitecatalyst to test blanks -->
<script language="JavaScript" type="text/javascript"><!--
if (projectCategory == "") {
	projectHier3 = projectChannel
}
else if (projectSubCategory == "" && projectCategory != "") {
	projectHier3 = projectChannel + "|" + projectCategory
}
else {
	projectHier3 = projectChannel + "|" + projectCategory + "|" + projectSubCategory
}
--></script>

<!-- SiteCatalyst code version: H.25.5.
Copyright 1996-2013 Adobe, Inc. All Rights Reserved
More info available at http://www.omniture.com -->
<script language="JavaScript" type="text/javascript" src="http://media.cmgdigital.com/shared/news/documents/2013/08/07/sitecatalyst_statesmanv25.js"></script>
<script language="JavaScript" type="text/javascript"><!--

/* You may give each page an identifying name, server, and channel on
the next lines. */

s.pageName=location.host + location.pathname
s.server=window.location.host
s.channel=projectChannel
s.pageType=""
s.prop9=window.location.host
s.prop13=document.title.toLowerCase()
s.prop14=projectCategory
s.prop16="non-mobile site"
s.prop17=""
s.prop18=""
s.prop19=""
s.prop20=""
s.prop21=projectSite
s.prop22="flat pages"
s.prop23=""
s.prop42=projectSite
s.prop43="newspaper"
s.prop57=document.referrer
s.prop63=document.location.href
/* Conversion Variables */
s.hier1="tx: austin|newspaper|" + projectSite
s.hier2="newspaper|tx: austin|" + projectSite
s.hier3=projectHier3
s.campaign=""
s.state=""
s.zip=""
s.events="event1"
s.products=""
s.purchaseID=""
s.eVar9=s.prop9
s.eVar13=s.prop13
s.eVar14=s.prop14
s.eVar15=""
s.eVar16="non-mobile site"
s.eVar17=""
s.eVar18=""
s.eVar19=""
s.eVar20=""
s.eVar21=s.prop21
s.eVar22="flat pages"
s.eVar23=""
s.eVar42=s.prop42
s.eVar43="newspaper"
s.eVar55=s.pageName
s.eVar56=s.channel
s.eVar57=document.referrer
s.eVar63=document.location.href


/************* DO NOT ALTER ANYTHING BELOW THIS LINE ! **************/
var s_code=s.t();if(s_code)document.write(s_code)//--></script>
<script language="JavaScript" type="text/javascript"><!--
if(navigator.appVersion.indexOf('MSIE')>=0)document.write(unescape('%3C')+'\!-'+'-')
//--></script><noscript><img src="http://coxnet.112.2o7.net/b/ss/coxstatesman/1/H.25.5--NS/0"
height="1" width="1" border="0" alt="" /></noscript><!--/DO NOT REMOVE/-->
<!-- End SiteCatalyst code version: H.25.5. -->

<!-- Quantcast Tag, part 2 -->
<script type="text/javascript">
    _qevents.push( { qacct:"p-38KriKc8Foyx-"} );
</script>
<noscript>
<div style="display: none;">
    <img src="http://pixel.quantserve.com/pixel/p-test123.gif" height="1" width="1" alt="Quantcast"/>
</div>
</noscript>

<!--  Chartbeat code -->

<script type="text/javascript">
  var chartbeatdomain = projectSite + '.com'
  var _sf_async_config = { uid: 31585, domain: chartbeatdomain, useCanonical: true };
  (function() {
    function loadChartbeat() {
      window._sf_endpt = (new Date()).getTime();
      var e = document.createElement('script');
      e.setAttribute('language', 'javascript');
      e.setAttribute('type', 'text/javascript');
      e.setAttribute('src','//static.chartbeat.com/js/chartbeat.js');
     document.body.appendChild(e);
    };
    var oldonload = window.onload;
    window.onload = (typeof window.onload != 'function') ?
      loadChartbeat : function() { oldonload(); loadChartbeat(); };
  })();
</script>

```

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
