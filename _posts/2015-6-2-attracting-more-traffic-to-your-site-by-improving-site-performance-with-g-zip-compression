---
layout: post
title: Attracting more traffic to your site by improving site performance with g zip compression
---

A few days ago, I noticed in my Google Adsense dashboard that the health of my site had gone down mainly due to its speed.  It was
previously at 4/5 and had gone down to 3/5.  As Google now ranks page speed, that is, how fast your website appears to people as a search ranking factor, I decided to fix it.

People often think that to get on the web now, all you need is a website.  While that's true and there are many website builders out 
there that can put a site up in a matter of minutes (e.g. wix.com and weebly.com), having an online presence requires traffic.
This means your site needs to be sympatico with the search engine that's going to be bringing in the most traffic for your site, this 
will most likely be Google.

Page speed insights does actually give you great insight into what to fix.  It said that if I used gzip compression, that it would improve
my load time by 70%.

So I searched around for gzip compression and found the below code.  I added this in the .htaccess file within my wordpress files.
It worked perfectly (which is always a good sign) and there was no need to use a plugin.
You should try it too!

```
<IfModule deflate_module>
    <IfModule filter_module>
        AddOutputFilterByType DEFLATE text/plain text/html
        AddOutputFilterByType DEFLATE text/xml application/xml application/xhtml+xml application/xml-dtd
        AddOutputFilterByType DEFLATE application/rdf+xml application/rss+xml application/atom+xml image/svg+xml
        AddOutputFilterByType DEFLATE text/css text/javascript application/javascript application/x-javascript
        AddOutputFilterByType DEFLATE font/otf font/opentype application/font-otf application/x-font-otf
        AddOutputFilterByType DEFLATE font/ttf font/truetype application/font-ttf application/x-font-ttf
    </IfModule>
</IfModule>
```

It worked.  My site had improved from 3/5 to 4/5.  Yay!  I also noticed slightly more impressions.

I know this post is a bit off the topic of our Rails Girls Summer of Code plugin creation but it just highlights that even
if someone invests a lot of time with their blog in terms of content, you need still web infrastructure to perform well.
**Good web infrastructure** generates **more traffic** which leads to (if everything goes well) **more conversions for your advertising
campaign**.

By @ladydanger.

