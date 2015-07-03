---
layout: post
title: It’s Git…ting Crazy!
---

![](https://googledrive.com/host/0B0MprGf2iwLoeHhKMzQ3NEh3UnM/)

0800 - Kick-off Supervisor Call with Sara. We were delighted to have Adel and Jo with us this Friday on Hangout. 

Throughout the rest of the day:

**1. Eloquent Javascript and WatchAndCode suggestion via Twitter**

Sarah: I started working on Eloquent Javascript: Chapter 4 Exercises. Here are 3 interesting takeaways for today:

**Founder** of WatchAndCode, Gordan, tweeted us last night suggesting that we try out the annotated version of Eloquent Javascript. 

As such, I've been using the site alongside the original EJs for a more thorough understanding of the ways to approach and tackle coding problems.

**It** becomes more difficult from Chapter 4 onwards.
That seems to be the consensus.

**Use Eloquent Javascript** to heighten your understanding of JS (>CodeAcademy)
Thank you to our coach, Adel for this recommendation! Vi and I have found this particularly useful and much more comprehensive than CodeAcademy. 

Definitely, the latter is great for absolute beginners, but EJ covers more functions, methods and poses more of a challenge than the former.

**2. More, more, more administration work**

We're packed for Week 2! It seems that we're scheduled to meet at least one person everyday starting next week. Anticipate awesome developments in Week 2, World.

**3. Created a basic plugin**

![](https://googledrive.com/host/0B0MprGf2iwLobXFVS2ZYcWM4X2s/)

This was relatively straightforward, thanks to a simple and effective write-up by Robin. We had a couple of questions to ask along the way, and managed them by compiling the list of queries on Google Doc.

The main issues that cropped up were in the last step. 

![](https://googledrive.com/host/0B0MprGf2iwLoNnZmSWo3Z2xValU)

What worked for us: plugins/basic-plugin/assets/javascripts/initializers/alert.js.es6
(*refrain from creating a discourse folder*)

And it worked. 

**4. Git Masters in Training**

Vi: Today was a lesson in git… in Q&A format.  

**What happened?**  We tried to create a basic discourse plugin, just to understand how it worked using Robin’s guide [here](https://meta.discourse.org/t/beginners-guide-to-creating-discourse-plugins/30515).  If you’re a budding discourse developer, try it out - it’s an excellent guide.  Long story short, Sarah’s plugin worked and mine didn’t.  We were both working on our local environment.

**Problem 1 - Pushing Changes to the Repo Ain’t Working** We tried to push our changes to the repo and it didn’t work.  Mine you, our changes were in the plugin directory.  After a bit of too-ing and fro-ing, we looked in gitignore and the plugin directory was in there, so with !/plugin/basic-plugin which mean our plugin was now able to be ‘gitted’.  the “!” symbol means “Not”.  So… !Happy(Jan).

**Problem 2 - Sarah’s Alert Plugin Worked and Mine Didn’t**  We decided to push our code to our github repo so that we could see changes and commits.  Putting it up on a remote branch could mean that I could pull that code to replace my existing (non-working code).  In dot point form:

* Sarah forked from her personal Discourse repo to the Team Melbourne Discourse repo.  This was a new repo I could pull from. 
* My original remote branches were all messed up - see below.  So I needed to fix it.  The origin and upstream should be set to the new forked repo and then a pull made from there to my local.

```
git remote -v
origin	git@github.com:team-melbourne-rgsoc2015/discourse (fetch)
origin	git@github.com:team-melbourne-rgsoc2015/discourse (push)
other	https://github.com/snjqi188/discourse.git (fetch)
other	https://github.com/snjqi188/discourse.git (push)
upstream	git@github.com:team-melbourne-rgsoc2015/discourse-ad-plugin.git (fetch)
upstream	git@github.com:team-melbourne-rgsoc2015/discourse-ad-plugin.git (push)
```

Here are the commands I used in the terminal to clean it up:


```
git remote set-url upstream git@github.com:team-melbourne-rgsoc2015/discourse.git
git remote set-url origin git@github.com:team-melbourne-rgsoc2015/discourse.git

git remote -v \\this checks the status

origin	git@github.com:team-melbourne-rgsoc2015/discourse.git (fetch)
origin	git@github.com:team-melbourne-rgsoc2015/discourse.git (push)
other	https://github.com/snjqi188/discourse.git (fetch)
other	https://github.com/snjqi188/discourse.git (push)
upstream	git@github.com:team-melbourne-rgsoc2015/discourse.git (fetch)
upstream	git@github.com:team-melbourne-rgsoc2015/discourse.git (push)

\\all good, except, the ‘other’ that’s there.

git remote rm other \\Removing the other remote branch that was not needed.

git remote -v \\again, a final check and it’s fine!
origin	git@github.com:team-melbourne-rgsoc2015/discourse.git (fetch)
origin	git@github.com:team-melbourne-rgsoc2015/discourse.git (push)
upstream	git@github.com:team-melbourne-rgsoc2015/discourse.git (fetch)
upstream	git@github.com:team-melbourne-rgsoc2015/discourse.git (push)
```

Next… I did a git pull.  This means, my local code would pull from the team-melbourne-rgsoc2015/discourse.git and then replace my code with what’s in the remote code (which is the one that works).


```
Your branch and 'upstream/master' have diverged,
and have 43 and 2 different commits each, respectively.
  (use "git pull" to merge the remote branch into yours)
nothing to commit, working directory clean
```

Unfortunately, I got this after doing the **git pull**

```
error: The following untracked working tree files would be overwritten by merge:
	plugins/lazyYT/assets/javascripts/.DS_Store
	plugins/lazyYT/assets/javascripts/initializers/.DS_Store
Please move or remove them before you can merge.
Aborting
```

I couldn’t find these files.  This is what google returned on DS store:

>.DS_Store is the name of a file in the Apple OS X operating system for
>storing custom attributes of a folder such as the position of icons or the
>choice of a background image. The name is an abbreviation of Desktop
>Services Store, reflecting its purpose. 

Figure, it’s nothing important and a stack overflow result said I should do this:

```
git clean -d -fx ""
```

Git clean removes untracked files (which is what DS store is… isn’t there a real online store by this name…?)  Can’t find what the -fx stands for.

Doing the above returned this:

```
Removing .DS_Store
Removing app/.DS_Store
Removing app/assets/.DS_Store
Removing app/assets/javascripts/.DS_Store
Removing app/assets/javascripts/discourse/.DS_Store
Removing app/assets/javascripts/discourse/initializers/.DS_Store
Removing config/.DS_Store
Removing config/initializers/.DS_Store
Removing db/structure.sql
Removing log/development.log
Removing log/test.log
Removing plugins/.DS_Store
Removing plugins/basic-plugin/assets/javascripts/.DS_Store
Removing plugins/basic-plugin/assets/javascripts/initializers/.DS_Store
Removing plugins/lazyYT/assets/javascripts/.DS_Store
Removing plugins/lazyYT/assets/javascripts/initializers/.DS_Store
Removing public/backups/
Removing public/tombstone/
Removing public/uploads/
Removing spec/fixtures/plugins/my_plugin/auto_generated/
Removing tmp/

```

Then, now that this was done, the git pull worked and I pull, committed and pushed!

But…

Should have checked first that the code worked locally - it did.  The !End…


**5. Other things worth mentioning about**

Photoshopping a black-and-white photo into a coloured collage and trying to make it blend in.

Despite it being a Friday, we stayed in the office for pretty much the whole duration. We promise to make future Fridays more exciting than this! Vi was especially hardworking in git-ing everything. So kudos to her for this particularly fulfilling day!

1700 - Off and out. Happy Weekend, World!


Signing Off, 
Sarah and Vi
