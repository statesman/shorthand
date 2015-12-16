Shorthand stuff
======================

## Shorthand help docs

Shorthand has a website for [Guidelines and help](http://www.shorthand.happyfox.com/home), including [Media sizes](http://www.shorthand.happyfox.com/kb/section/5/).

## Sharing setup

* User our atxne.ws bitly account in Passpack.
* VIA is is just the account: "statesman" or "austin360"
* specials.mystatesman.com Facebook App ID: 881505665256530
* projects.statesman.com Facebook App ID: 1019142718149176

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

## Shorthand for mystatesman.com

There is a process to upload shorthand projects wrapped for mystatesman.com that adds the meter modals and such.

Those wrapped files don't currently have Chartbeat, so we need to manually add it until they do.


### Add Chartbeat code

In the **Add JS** button in your project, add the following code:


``` javascript
<!-- chartbeat head -->
<script type="text/javascript">var _sf_startpt=(new Date()).getTime()</script>

<!--  Chartbeat body -->

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

MyStatesman.com projects are uploaded to Amazon AWS. Each user has their own login to the upload site.

* To download your project from shorthand, go to **Publish**, then click **Download ZIP**.
* Rename the zip file to the last part of the url string you want to publish at, like `/seasonal-serenades/`.
* Go to [the console](https://cmg-dst.signin.aws.amazon.com/console).
* Click on S3.
* Click on the link for `staging-specials.mystatesman.com`
* Click **Upload**.
* Drag and drop the zip file to the window as indicated.
* Click the **Start Upload** button.

The file will upload, and then will get processed after a bit, moving to the `specials.mystatesman.com` folder, where it is available at `http://specials.mystatesman.com/whatever-you-called-your-file/`


## Free shorthands on the projects server

Since the AWS process wraps shorthands with metrics code, we have to publish free shorthands on the projects server.

* Under **Themes**, choose *CMG - Free Sites*.
* Do all the other sharing and such that you'll need.
  - For editorial, your published url will be `http://projects.statesman.com/[section]/[projectname]` where the seciton 
  - For sponsored content, for now the published url will be `http://host.coxnewsweb.com/aas/advertising/sponsored/[path-to-your-project]/`
* In the **Add JS** screen, you will need to add some metrics code. See "In Add JS" below.

### Logo

Logos are added at the top fo the free template.

* For Statesman, use the `logo-short-black-ia.png`, which just says Statesman. You can download it from this repo. (It has been run through a program called [ImageAlpha](http://pngmini.com) to clean it up, based on Shorthand recommendations.)
* For Austin360, use the `austin360.png` logo, which is available in this repo. Also run through ImageAlpha.
* `logo-ia.png` is the full Austin American-Statesman logo, which has been run through ImageAlpha. It is too wide for phones, but we'll retain it in case we want to use it some time in the future.
* Sponsored content may have a different logo.

### In Add JS

The following needs to be added in **Add JS**. Note the first several of lines need configuration. For guidance, I usually look at the source code of an existing page and look at their metrics to decide what to put here.

* projectSite: should be "statesman" or "austin360"
* projectChannel: The Medley channel. Usually "news" or "sports". Loo for .channel.
* projectCategory: Medley subcategory. Look at .prop14
* projectSubCategory: About your project. Usually the url like `seasonal-serenades`. Don't use spaces.
* projectByline: lower case names, separated by commas if more than one. Look at s_coxnews.prop23.


``` javascript

<!-- cmg footer metrics -->
<script type="text/javascript">
  var projectSite = "statesman";
  var projectChannel = "news"; // Medley Category
  var projectCategory = "local"; // Medley subCategory
  var projectSubCategory = "shorthand-project-name"; // project directory no spaces
  var projectByline = ""; //lower case names of authors
</script>

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
s.prop22=""
s.prop23="projectByline"
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
s.eVar22=""
s.eVar23="projectByline"
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


### Favicons

The only way to update the favicon is to do it after you have downloaded it. You'll add this to index.html. I would add it just after the `<title>` tag.

Statesman
``` html
<link rel="shortcut icon" href="http://media.cmgdigital.com/shared/theme-assets/162015/www.statesman.com_bf77ed61f1f94479978e65af7cc32071.ico" />
```

Austin360
``` html
<link rel="shortcut icon" href="http://media.cmgdigital.com/shared/theme-assets/162015/www.austin360.com_22903be6a1284aafae1b0ed32b32c102.ico" />
```


### Publishing

Very rough steps:

* Download the zipped project from Shorthand.
* Unzip the project
* Rename the folder the project directory name, like `seasonal-serenades`
* Add favicon to index.html if you want.
* FTP into the host.coxmediagroup.com server.
  - For editorial, go into `prod_aas/projects/[channel name]/`
  - For sponsored content, the ftp username/password should take you the right directory, which is `prod_aas/advertising/sponsored/`.



