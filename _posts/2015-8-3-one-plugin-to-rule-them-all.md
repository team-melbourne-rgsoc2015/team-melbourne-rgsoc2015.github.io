---
layout: post
title: One Plugin to Rule them All...Only if it Works Though
---

<a href="http://www.youtube.com/watch?feature=player_embedded&v=fJlz6nEOT7w
" target="_blank"><img src="http://img.youtube.com/vi/fJlz6nEOT7w/0.jpg" 
alt="IMAGE ALT TEXT HERE" width="240" height="180" border="10" /></a>

Today was a productive day because we have now completed the initial working build of the Adsense plugin.  This plugin allows adsense ads to be displayed in Discourse.  Adsense is where you let Google display ads in your blog/website and then when they get clicked by someone in the world, you get paid a share by Google.  A plugin is something people install on top of their software to allow some special functionality e.g. displaying ads.
The reason plugins exist is because some features/functions are needed by some and not by others and it doesn't make sense to build it into the core of the software if only certina people need it and others done.

But our ambitions are bigger, we want to build **one plugin to rule them all**.  What does this mean?  Well people can use different ad platforms such as Google Adsense, Google Double Click for Publishers, Amazon Affiliates and more.
We want to make one plugin that people can install that will allow people to choose which platform they want to use.
Click on the picture above, it'll take you to a surprise movie that may delight or disappoint you, depending on your likes/dislikes.

So we used Balsamiq (a wireframing tool) to draw out what we wanted our plugin to look like and how it would work for users.  
You can check out our documentation and a video [here](https://github.com/team-melbourne-rgsoc2015/Roadmap/blob/master/ad-plugin-interface.md).  Kudos to Sarah for the great voiceover!

Balsamiq is a fantastic tool which you can use if you want to do pictures (mock-ups) of what your website would look like and how things piece together.  
We used Quicktime to do a video of the screen.  It's software that comes with most mac computers.

Other learning that we'd like to share with you:

### Adsense Plugin Build Using Components and Not Initializers in Ember
The original adsense plugin created by Discourse Hosting used initializers.  In our plugin, we've used Ember components.
Check it out [here](https://github.com/team-melbourne-rgsoc2015/discourse-adsense-test).

### Build from Bottom Up is Much Better  (in our case) than Refactoring
We had a few sources to help us build the adsense plugin - we refactored the existing adsense plugin that used initializers, we refactored adsense code into the existing dfp plugin but our progress was really achieved when we built:

1. A simple plugin that would display a container.
2. Substituting the adsense code (with hardcoded figures) to see if it would display.  We just added it in a template component and it did - yay!
3. Edited the code to accept inputs from users for things like publisher ID and ad code.

Building from the bottom up in this case taught us more and also helped us make a cleaner more bare bones plugin.


### Figuring How to Test Adsense - Where There is a Will there is a Way
Adsense cannot and probably shouldn't be tested locally but with some lateral thinking we found a way.  Tweet us a private message and we will be happy to share.


### Debugging code in Javascript using Debugger; and using the Console.
In your js.es6 file you can place ```debugger;``` anywhere and that will run some sort of debugger that you can then see in your console.
This helps you find our where errors are in your code, so that you can fix it.
To get to the console using Google Chrome:

1. Right click anywhere on a web page
2. Click Inspect Element
3. On the header of the Inspect Element, click Console.
4. Now you are at your console and you can then see the debugger.

### Pairing is Effective & Efficient
Pairing is when you sit with someone, a partner, and work through a problem together.  Ideally, you'd sit together on one computer and plug in your keyboard and mouse (hopefully the computer has enough USB holes.
I had heard of pairing before starting RGSoC but I didn't think much of it because it reminds you of something you do at primary school and I was burnt from group work at University, but.... it is so effective (with the right pair).
Why?  Here are three reasons:

1. Stops you from wasting time and forces you to focus.  It's easy to start ebay-ing and wasting your time on the internet, browsing through things that will never enhance your life and never getting back that time.  Pairing stops you from doing that, because seriously, why would anyone read 'Mariah Carey gets gold necklace from James Packer' in front of their partner while you are supposed to be doing work?
2. Sounding board.  On Sunday night, I was trying to refactor the adsense plugin and took forever... and got nowhere.  I should have just gone to sleep, it would have resulted in the same thing.  However, with my pair, we finished it in a day using a different approach.
3. Sharing knowledge.  Shortcuts on the computer that each of us know and are able to share make it easier for work to be done.  I also now know what idk stands for.

That's a wrap...
