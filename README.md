Shorthand stuff
======================

BASIC SHORTHAND NOTES FOR PUBLISHING ON SPECIALS.STATESMAN.COM ARE ON THE [STATESMAN WIKI](http://wiki.statesman.com/doku.php?id=web_content_help:shorthand_tips).

## Publishing Shorthand on projects.statesman.com

There are a couple of differences that need to be applied if you are publishing a shorthand to projects.statesman.com.

### Logo

Logos are added at the top fo the free template.

#### Try SVG
I haven't tried them yet
* For Statesman, use the `statesman.svg`, which just says Statesman. You can download it from this repo. (I NEED TO TEST THE SVG. Might use logo-short-black-ia.png if it doesn't work.)

#### Fallback pngs

* For Statesman, use the logo-short-black-ia.png, which just says Statesman. You can download it from this repo. (It has been run through a program called ImageAlpha to clean it up, based on Shorthand recommendations.)
* For Austin360, use the `austin360.png` logo, which is available in this repo. Also run through ImageAlpha.
* `logo-ia.png` is the full Austin American-Statesman logo, which has been run through ImageAlpha. It is too wide for phones, but we'll retain it in case we want to use it some time in the future.
* Sponsored content may have a different logo.

### THEMES

* There is a CMG - Free Sites theme that can be used.
* The Shorthand - Combined theme also has a nice font combination

That's basically the only difference.

### SETTINGS

* Same as others, but note the Author/S field doesn't really get stuff into metrics. That happens under Add JS.

### SHARING

* For the full URL:
  - For editorial, your published url will be `http://projects.statesman.com/[section]/[projectname]` as appropriate. We might come up with a special place for them if we do more of them.
  - For sponsored content, for now the published url will be `http://host.coxnewsweb.com/aas/advertising/sponsored/[path-to-your-project]/`
* The Facebook App ID for projects.statesman.com is: 1019142718149176

(That said, I don't think the FB id actually works. We get linter errors.)

### ADD CSS

There isn't anything required here.

### ADD JS

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

MyStatesman (I like the black one for projects)
```
<link rel="shortcut icon" href="//mystatesman.com/r/PortalConfig/np-paid/assets/mystatesman/images/favicon.ico" />
```


Statesman
``` html
<link rel="shortcut icon" href="//statesman.com/r/PortalConfig/np-free/assets/statesman/images/favicon.ico"/>
```


Austin360
``` html
<link rel="shortcut icon" href="//austin360.com/r/PortalConfig/np-free/assets/austin360/images/favicon.ico"/>
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



