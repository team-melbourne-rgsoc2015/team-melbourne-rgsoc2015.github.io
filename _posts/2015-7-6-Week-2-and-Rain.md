---
layout: post
title: Week 2 and Rain
---

Vi: Today, again, was a cold and rainy day.  Sarah is off to yoga now and I’m on a new diet.  Have lost a few kilos being in Japan for the last few weeks and I like it, but being in Melbourne and especially in Redbubble is very tempting.  There are cupcakes, biscuits and heaps of food.  Today was a good day, I only ate one cupcake.  Will continue trying my best to avoid eating all 4 cupcakes in one day.  Redbubble is the company that keeps on giving, aside for providing us with an awesome place to work from, they provide breakfast and lunch.  Actually… they should be on BRW’s Best Workplaces.  A nomination is in order…
Ok, now that the scene is set… let’s go through what happened today in dottish point form.

##### Eloquent Javascript Chapter 3 Activity on Recursion

The 2nd eloquent javascript wanted us to write some code that would provide a true if a number was even and false if a number was not even using N-2.

Here’s the solution:

```
function isEven(n) {
  if (n == 0)
    return true;
  else if (n == 1)
    return false;
  else if (n < 0)
    return isEven(-n);
  else
    return isEven(n - 2);
}
```

I like this because any positive number is reduced to its the base case of n==0 or n==1 where there is a true/false designation based on the repeating -2 pattern.  This is different to using a remainder to determine if a number is even e.g.  number % 2 == 0.  Using the remainder way means that it will take the instance of the number there and apply that divisible property of that number and if it is divisible by 2, then it would be an even number and if it doesn’t meet this case then it would be false.  Whereas this isEven function, takes a number, say 9 as a point in a line and reduces it by -2 (9, 7, 5, 3, 1) until it reaches 0 or 1 and then it would be true/false.  So here, evenness is determined by reduction by pattern to either 0 or 1 and a number is just a figure in a continuum.

Anyway, I find this neat - and that’s my non-sensicle two-bob worth for today. 

##### From Rails to Ember

I found this the most interesting difference from Rails to Ember.

> In any server rendered framework, page reloads clear state. Your app might have sections that contain a lot of AJAX, but for the most part you start with a fresh state every time a user clicks a link. Not so with a client-side framework.

I think this might affect an advertising plugin… (more to follow in a few months time).
Also getting used to the idea of ‘hooks’ in ember as opposed to the Rails controller handling a lot of the things that routes in Ember is managing.

##### Installing an Adsense Plugin
Tonight, we want to look at how an adsense plugin works and followed instructions found [here](https://github.com/discoursehosting/discourse-adsense) for the non-docker installation.  Installed it and have pushed these changes to github on a separate branch.
More updates to follow tomorrow...


Sarah: 4 things I did today

###1. 15 minutes with Git and Reading up on Git

Rational: Lessening the chances of me breaking anything when pushing, pulling and merging to Github

![](https://googledrive.com/host/0B0MprGf2iwLoWlBVdXh1bHZOUWM)

Fun fact: [The difference between git pull, git fetch, git clone and git rebase](http://blog.mikepearce.net/2010/05/18/the-difference-between-git-pull-git-fetch-and-git-clone-and-git-rebase/)

![](https://googledrive.com/host/0B0MprGf2iwLoeHhKMzQ3NEh3UnM/)

![](https://googledrive.com/host/0B0MprGf2iwLoakx3eEIxdmZPN1k/)

*http://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell*

When you realise that understanding code is simply the same as reading a good story.

###2. Fiddling around more with the Mac

Rational: This was unintentional. But I had to find out if double downloading NodeJS on different versions would be detrimental. As I explored further, I realised it probably wouldn't. The latest installation seemed to overwrite my first one. 

Fun fact: You know Mac is great when even the Terminal line looks beautiful. It's always a horror story with my Windows - but that being said, both are great. [Here's to check what's been installed on your mac.](http://applehelpwriter.com/2013/05/21/how-to-check-whats-been-installed-on-your-mac/)

###3. Meeting Jo for the first time!

Rational: Kick-off Meet-up!

Fun fact: This was my first time meeting our female coach, Jo. (All the girl power) She brought up topics such as unit testing and suggested we try Jasmine. Pretty cool to have a coach with these areas of expertise. 

*- Reminder: Take a photo with her!*

### 4. More about Ember

We tried to install Node.js but there're some administrative issues. Hoping to get it settled because I am itching to create a [ToDoMVC](https://todomvc.com/examples/emberjs/) app. I know, we should have done this a long time ago. But we've got a new laptop to work with - thus more things to install!

Signing Off,
Vi and Sarah

