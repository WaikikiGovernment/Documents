# Export 

## Blazor export
* Publish to folder from VisualStudio.
* Copy wwwroot to the app folder.
* Rename wwwroot to the name of the app.
* Delete appsettings.Development.json. (Optionally change url in appsettings.json)
* In index.html change base hrf to "/Webpage/app/APPNAME/".
* In 404.html change pathSegmentsToKeep to 3.

## Muse export
* Publish Muse files.
* Copy assets folder and service-worker.js to root.
* Replace webpro.js file in scripts folder.

## Manual edits
### Delete lines with regex
* Links: <.*"http://widgets-musethemes.businesscatalyst.com.*>
* Comments: <!--(.*?)-->
* Crc: ?crc=[0-9]*

### Format document
* Cmd + D
* Cmd + Y

### Remove duplicate widget styles and scripts
* Stats animator
* Donut charts

### Optimize css styles:
* http://css.github.io/csso/csso.html

### Direct include scripts
```
<script type="text/javascript">
    document.documentElement.className = document.documentElement.className.replace('nojs', 'js');
    $.browser = { webkit: true, version: '605.1.15', safari: true, msie: false, Features: {} };
</script>
<script src="scripts/museutils.js"></script>
<script src="scripts/whatinput.js"></script>
<script src="scripts/jquery.musemenu.js"></script>
<script src="scripts/webpro.js"></script>
<script src="scripts/musewpdisclosure.js"></script>
<script src="scripts/jquery.watch.js"></script>
<script src="scripts/musewpslideshow.js"></script>
<script src="scripts/jquery.museoverlay.js"></script>
<script src="scripts/touchswipe.js"></script>
<script src="scripts/jquery.musepolyfill.bgsize.js"></script>
<script type="text/javascript">
    $(document).ready(function () {
        try {
        ...
        });
</script>
```

<img width="1879" alt="Képernyőfotó 2023-01-15 - 18 13 06" src="https://user-images.githubusercontent.com/43353335/212556186-f587fd71-52ca-4572-b83d-de2a70368490.png">

### Scroll position fixes
Search for
```
scrollTop()
```

Replace with
```
var startPosition = u26604span.offset().top + 80;
var scrollPosition = $(window).scrollTop() + $(window).height();
if (scrollPosition > startPosition) {
```