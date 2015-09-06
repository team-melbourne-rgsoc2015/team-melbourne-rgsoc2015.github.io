---
layout: post
title: How to See if You've Put in Your Google DoubleClick for Publisher's GPT Tag in Properly
---

Google DoubleClick for Publishers (DFP) Small Business is a free ad management solution that helps growing publishers sell, schedule, deliver, and measure all of their digital ad inventory.

All you have to do to get your ad to display is generate a tag (google publisher tag or GPT) and paste it a html page of your site.  In the example below, we've pasted the tag in the head and body tags of the layout html page of this blog.  

There are two parts to GPT tag.

The first part is within the head tags and it makes a call to Google to push the ads.  It looks kind of like this:

```
<!DOCTYPE html>
<html>
  <head>
    <title>{% if page.title %}{{ page.title }} – {% endif %}{{ site.name }} – {{ site.description }}</title>

    {% include meta.html %}

    <!--[if lt IE 9]>
      <script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script>
    <![endif]-->

    <link rel="stylesheet" type="text/css" href="{{ site.baseurl }}/style.css" />
    <link rel="alternate" type="application/rss+xml" title="{{ site.name }} - {{ site.description }}" href="{{ site.baseurl }}/feed.xml" />

    <!-- This is the beginning of the GPT -->
    <script type='text/javascript'>
      var googletag = googletag || {};
      googletag.cmd = googletag.cmd || [];
      (function() {
        var gads = document.createElement('script');
        gads.async = true;
        gads.type = 'text/javascript';
        var useSSL = 'https:' == document.location.protocol;
        gads.src = (useSSL ? 'https:' : 'http:') +
          '//www.googletagservices.com/tag/js/gpt.js';
        var node = document.getElementsByTagName('script')[0];
        node.parentNode.insertBefore(gads, node);
      })();
    </script>
    
    <script type='text/javascript'>
      googletag.cmd.push(function() {
        googletag.defineSlot('/publisher_id/ad_id', [728, 90], 'div-gpt-ad-1441363470466-0').addService(googletag.pubads());
        googletag.pubads().enableSingleRequest();
        googletag.enableServices();
      });
    </script> 
    <!-- This is the end of the GPT -->
    
  </head>
```

The second part is the location of the ad and you can put there anywhere in the body tags of the page.  It could look like this:

```
  <body>
    
    <div id="main" role="main" class="container">
      {{ content }}
      <!-- This is the start of the second part of the GPT ad -->
      <div id='div-gpt-ad-1441363470466-0' style='height:90px; width:728px;'>
        <script type='text/javascript'>
        googletag.cmd.push(function() { googletag.display('div-gpt-ad-1441363470466-0'); });
        </script>
      </div>
      <!-- This is the end of the second part of the GPT ad -->
    </div>

    <div class="wrapper-footer">
      <div class="container">
        <footer class="footer">
          {% include svg-icons.html %}
        </footer>
      </div>
    </div>

    {% include analytics.html %}
  </body>
</html>
```

The thing is there is **substantial waiting time when you put your ad tag in before your DFP ad is served or displayed**, it's just a DFP thing.  The time lag can vary as once, it took nearly overnight for my ads to start serving.

But there is one thing you can do during that waiting time.  That is to check that you've put your GPT (that's the tag that's provided by DFP) in correctly.  Because, if you've put in your GPT in correctly, you just have to wait until your ads start serving from DFP's side.  The other thing is that if you don't know if your tag is in correctly, you may be waiting and the serving of the ad is due to a problem on your side.

So... one way to check if you've put your GPT Ad in correctly is to use ```?google_force_console```.  Here's how to use it (with screenshot pictures):

#### Step 1 - Add ?google_force_console to the page where your ad is expected to display.

After adding your google tag to the right places, navigate to the page where you ad is expected to display and put ```?google_force_console``` at the end of the URL.  The URL is the website's address (see the picture below).

![](https://www.dropbox.com/s/4c4vr57sc8490f9/google_force_console.png?dl=1)

#### Step 2 - Check the Page Request to see if Your Page has been Tagged Properly

The google console should appear.  Click on Page Request and the green tick means that you've put in the GPT correctly.

![](https://www.dropbox.com/s/995n9xou98se4kj/page-request-dfp.png?dl=1)

#### Step 3 - Check the Details of the Ad Slot

Here you've making sure that the publisher ID is correct, the ad slot name matches that in your DFP console and all the other details are there.
When you first start you should see an empty container (and after 2-8 hours that should fill with an ad).

![](https://www.dropbox.com/s/l7nme5kx6yijujc/ad-slots-dfp.png?dl=1)

Another way to check if your ad is just waiting on google to display as opposed to being an error on your part is to:

1. Check on the page and there should be some white empty space where the ad is supposed to go.
2. Right click on the empty space and choose "Inspect Element"
3. You should see something like the below image - if you see a "div-gpt-ad-...", it means that the code is running (see below image).
4. Navigate to the 'console' in the same window and you should see a blank with no errors (see below image)


**Inspect Element and Look Out for the GPT**

![](https://www.dropbox.com/s/q5xfni1c49gj8nb/inspect-elements.png?dl=1)

**Navigate to the 'console' and Make Sure There Are No Errors**

![](https://www.dropbox.com/s/wterh5ecnq5gg9f/console-no-errors.png?dl=1)

These are two ways to check if your code is fine and set up properly.  Now all that's waiting for now is for DFP to serve the ad.

by @ladydanger





