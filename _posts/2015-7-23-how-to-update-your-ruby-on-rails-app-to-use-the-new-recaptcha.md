---
layout: post
title: How to Update Your Ruby on Rails App to Use the New Recaptcha using the recaptcha gem in 2 Steps
---

It's been a while since I blogged, mainly because Sarah & I have been busy working on the advertising plugin for discourse.
Today, we also did a presentation to Redbubble.com (our coaching company) to explain what we're working on.  Meanwhile, Redbubble
has some fantastic and unique stuff you can get for yourself or someone special - highly recommend (but then I'm biased).
You should though at least [check it out](www.redbubble.com).

Anyway, during the team showcase (where every team presents), one of the teams spoke in passing of the new google recaptcha tag.
I made a mental note because I use recaptcha in my rails app to ward away spam.  It's that thing which asks you to type in some really 
blurry words before you can send an email.  It looked like this:

![](https://dl.dropboxusercontent.com/u/101847371/old-recaptcha.png)

Google have replaced in now with a prettier, younger and smarter thing where you just have to tick a box and it 
can detect whether you are a bot sending out spam or human.  I'm always amazed by google magic.

![](https://dl.dropboxusercontent.com/u/101847371/sexy-new-recaptca.png)

Funnily enough, in checking my mail at home, there are a 'to-do' that I flagged from the 1st of this month and it was to update recaptcha.

So tonight, I decided to do so. At night time I like to so relaxing stuff - like look at pics in fashion magazines, catch up on Quora, watch tv shows like
the Batchelor... in fact the trashier the better.  Sometimes, though a lot of the time lately, it's doing little tweaks on my website.
The reason I'm not keen on doing these things at night is because often the timeframe for doing something new (even an update) may take
hours.  Anyway, enough bantering here's how I updated my ruby on rails app to use the new recaptcha if you are:

* Already using the recaptcha gem before Dec 2014 and had it functioning (e.g. you've already got your private & public key).  Here's the [gem](https://github.com/ambethia/recaptcha/) although now it's been updated.

So here are the steps:

1. You'll need to update that single gem.  Do 'bundle update recaptcha' on your terminal.
2. Go into config/initializers/recaptcha.rb and add ```config.api_version = 'v2'``` so that your code in that file looks like:

```
Recaptcha.configure do |config|
  config.public_key  = ENV['RECAPTCHA_PUBLIC_KEY']
  config.private_key = ENV['RECAPTCHA_PRIVATE_KEY']
  config.api_version = 'v2'
  #config.proxy = 'http://myproxy.com.au:8080'
end
```

Then just git push to your remote (if you have one) and then git push heroku master to deploy it to the internet so real spam bots and 
of course, people can see it.

Then you're done!

Phew!  It was a relatively painless and short process.  On the upside, I even had time to backup my database and find out that they
are screening Madame Bovary at the Kino (again, it was out since July 9!) - must book a time to see that.  I did like the novel.  Madame Bovary is
a great story by Gustave Flaubert and inspired the term [bovarism](https://www.google.com.au/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=bovarism).
If anyone else is interested in french literature, les liaisons dangereuses is also a good read and also Les Mots by JP Sartre.  

Sweet dreams all...

