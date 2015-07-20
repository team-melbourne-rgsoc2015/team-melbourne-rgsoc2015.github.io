---
layout: post
title: Ember, Node, Handlebars and Broccoli
---

Sarah: I’m once again very thankful towards Redbubble for providing us a proper workspace. The Macbook is coming in very handy. The disk is relatively uncluttered, which leaves much room for us to download and install the programs, dependencies, applications and gems we need. 

Downloads made today:
- Node.js
- Ember.js
- Bower dependencies
- Broccoli dependencies (yes, you heard right)
- Rack up gems

That’s pretty scary considering it’s only Day 5 and it seems to be a daily affair to download something new onto Macintosh.

###Getting into the world of Ember
I read the first 5 pages of the [guide](guides.emberjs.com) and fell asleep. Truly, the best way to learn is just to get down and break things. Unlike CodeAcademy, Eloquent Javascript or Codeschool, there’s a serious lack of updated material for Ember.js and EmberCLI for the recent version control. So here’s how we did it:

**What You Need**

- Google (this is vital - we want to minimise asking coaches basic questions that can be easily found on google)
- Ability to parse through content pronto (don’t waste time on information that gets you nowhere)
- Courage (to use what you’ve read and shove it onto the terminal)

I quote Mark Zuckerberg on this one:

![alt text](https://www.dropbox.com/sc/fguf9avgs41dibe/AAAUXcARKXXEFiCXFPzFhhYJa?dl=1)

*I do not own this quote or picture, as you can see, startup quote made [this site](http://startupquote.com/post/1624569753)*

#####Installing Ember.js

Story of how (supposedly) [3 lines of setup](http://guides.emberjs.com/v1.11.0/ember-cli/) turned into a whirlwind adventure booted with multiple commands and anxious fury.

Why so: Discrepencies between Ember.js’s latest version, EmberCLI and Macintosh.

Note: Seems to work fine even though the *Could not find watchman, falling back to Nodewatcher for file system events* warning pops up.

> npm install -g ember-cli

Error: Please try running this command again as root/Administrator

Solution: (Plow through Google) found this [site](https://aralbalkan.com/scribbles/npm-install-g-please-try-running-this-command-again-as-root-administrator/) and change the permissions: sudo chown -R $USER /usr/local
> ember new my-app

Error: Future versions of Ember CLI will not support v0.10.36. Please update to Node 0.12 or io.js.

Solution: Install the latest version from ember.js

> At this point, *ember server* still doesn’t work!

> brew install pcre

> npm install -g phantomjs

Error: Cannot find module ‘ember-cli/lib/broccoli/ember-app’

Solution: npm install ember-cli --save

> ember server

Error: Missing template processor

Solution: npm install -g bower *and* bower install

> ember serve still fails

Solution: bower cache clean && npm cache clean && npm install -g ember-cli

and/or

npm uninstall --save-dev broccoli-ember-hbs-template-compiler

and

npm install --save-dev ember-cli-htmlbars@0.6.0

[Source code](https://gist.github.com/abuiles/11130700)

> aaaand it works! “Serving on http://localhost:4200/”

Disclaimer: With updates on either platform, there are bound to be errors. Perhaps that’s why searching for a solid guide to setting up Ember peacefully is so difficult. Hopefully this’ll be of some help. If anything, always remember that Google is your best friend!

Second Note: If you’re told that rails commands can’t run on your ruby, get ready, [this](http://stackoverflow.com/questions/29803099/cant-run-rails-commands-your-ruby-version-is-2-2-1-but-your-gemfile-specified) might help.

#####Creating the ToDoMVC App

![alt text](https://www.dropbox.com/sc/68r13320ubu2oj9/AADomTSZYEnqCD4-1t2vfQDka?dl=1)

Thank you [CubicleApps](http://www.cubicleapps.com/articles/todo-mvc-with-ember-cli-part-1#) for such a good guide that is compatible with my current version of EmberCLI.

It’s confusing to have to refer back-and-forth with the official EmberJS guides and the above site. The first is the original but the second seems to have a better outcome where I am able to see the ToDoApp static page.

Suggestions if you get stuck at create a template and your first route: fiddle around with everything. Something will work out.

> It is optional, but I suggest installing Ember Inspector (I did mine through Chrome Web Store).

#####Check out this Rock n Roll App!

Spent some time looking at the insides of [this](http://www.toptal.com/javascript/a-step-by-step-guide-to-building-your-first-ember-js-app).

And that’s how I ended up downloading [rack](http://rack.github.io/) just to get the rock n roll app to serve locally.

I’ve made it a point to not spend more than 15 minutes on creating blog content. This one however, took slightly longer because of the complications. It would be preferable to spend time in the office to code and learn as much as I can, **but it is crucial to strike a balance and reflect on what I’ve done today**. Maybe someone out there might find this content beneficial to them! That’s what keeps me motivated to improve my speed of blogging and reviewing what I’ve done today.

More to come, tomorrow. 


Vi:
Today, I also played around with the Ember todoApp until I went home sick.  Anyway, before that we also looked into an existing adsense
plugin and look at each of the files and tried to understand what each did.

Here's the screenshot of my text editor with the files...

![](https://www.dropbox.com/sc/vhgan5omkqrlgae/AAA50iGoXy8rqg2Sg2TI712ra?dl=1)

Here's what (I think) each of the files does in the Adsense plugin:

* License - licence stuff
* Readme.md - markdown file with instructions for users on installing the plugin in development and production environment (production is in docker). 
* Plugin.rb - details about the plugin and there’s what looks like some custom css.

Assets:
Initializers
* Adsense.js.es6 - where it all happens.  I can’t understand much of it, but will try to put into English what I think is happening in this file:
Container function, if the current user has a trust level that is matches the settings, we’ll display ads. Otherwise, don’t display ads.
Variable for position - and this also considers the mobile part of it.  There's a function to push ads and a function to reload something?
That’s as much as I understand at this stage… will go an play around with Ember some more….

* Discourse > Templates > Connectors
* Discovery-List-Container-Top / Topic-above-post-stream / Topic-above-suggest
* Adsense.hbs - it appears there is an if statement that places the ad block based on whether it ticks the condition of being a mobile view.  This is a handlebars template, which according to [this website](http://fileinfo.com/extension/hbs) contains a template written in HTML code and embedded with handlebars expressions.  Assuming this is part of Ember - Yikes! Ember.js uses the Handlebars templating library to power your app's user interface.  At least, there’s only 7 lines of code and it’s an if statement…
E.g. {{#if site.mobileView}} {{adsenseBlock "320" "50" "topiclist_top_mobile"}} is a property from the controller? jsapp controller - application.js.es6?
This would look up the property from the controller, insert them into the HTML described in the template, then put them into the DOM - Ember Docs

In Config > Locales
* Client.en.yml - this looks like it puts the adsense plugin in the site settings so that the admin of Discourse can then click on it.
* Server.en.yml - this looks like a form within the site settings. 

* Settings.yml - this looks like a listing of the form inputs - i.e. what people have to put into discourse.

Signing off for today...
