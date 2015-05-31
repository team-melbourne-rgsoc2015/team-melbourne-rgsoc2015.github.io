---
layout: post
title: Finally, after 3 hours, the Team Melbourne Rails Girls Summer of Code 2015 Blog is Up.
---
Edited 31 May 2015 for grammar, spelling, relevance and reliability.

Finally, after 3 hours (edited: plus a few more hours), the Team Melbourne Rails Girls Summer of Code 2015 Blog is Up

So the plan was a simple one - to create a blog so that Sarah and I could start making posts on what we were learning before and while rails girls summer of code 2015.  The whole process took about 3 hours this morning.  

First, we had to decide what platform to use.  The platform had to:
* Enable blogging but it didn't need to be full blown blogging software - just enough to post with.
* It had to be free now and for ongoing maintenance - we looked at Wordpress on Heroku and it required connect with Amazon AWS for media upload, so that wasn't going to work.
* Allow us to add images and media file via links to other places where we would host it.  E.g. dropbox.
 
Given this, we chose github pages.  It seemed sensible since we're going to work on open source.  There are two types of github pages - users/organisations and projects.  I initially set up a project page (because that was easy to set up) but then found that it linked to my personal github page as a project (as it should) but that's not want we wanted, we wanted a blog for our team.  

So... I created an organisation account so that our url would be our team name (which looks like team_name.github.io as opposed to username.github.io/project_name).  Once that organisation account was set up, I followed github's instructions to set up a page from the terminal which led to a plain "Hello World" page which functioned but looked ugly.  That was scrapped.

Then... I used github's automatic page generator with the minimal theme - that worked fine and was pretty but the problem was that it didn't have the blog scaffolding that we needed.  Scrapped that too.  At this stage, I deleted the whole repo and started again as my github commits were going bonkers.  In my searches, I found this fantastic post from [Jekyll](http://jekyllbootstrap.com/usage/jekyll-quick-start.html) that outlined how I could set up the github page directly from my terminal with the blog scaffolding.  It was fantastic!  It was easy to set up - I guess the only thing was their instructions still had .com, whereas now the pages on github end with a .io.  So... after 3 hours, here's the start of our blogging journey. (btw - images etc... will be uploaded and prettier formatting will happen once we get used to Jekyll).  

The thing that I've noticed that's different with this blog scaffold compared to a database is that you post content after the section enclosed by the three hypenated lines.  Was so confused because usually in a blog with a database, you would put the content within the description.  Maybe it was just a syntax thing.

Oh well... you learn something new everyday and this static scaffolding system is quite interesting.

Update: Kudos to @snjqi188 who pushed the current blog (what you're seeing now).  The jekyllbootstrap one I used originally had issues with the terminal and she used jekyll-now, forked from @barryclark, which allows updated from github.  The solution's easy and simple.  Which is how things should be.  
