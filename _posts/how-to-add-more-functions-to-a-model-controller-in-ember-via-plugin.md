---
layout: post
title: How to Add More Functions to a Model/Controller in Ember via a Plugin in 4 Steps
---

This post aims to show you how to extend the functionality for a model or controller in a plugin.  A plugin hooks into the core code to deliver to users some kind of functionality e.g. displaying ads.
This post will be useful if you have an Ember App, or a Rails App using Ember as the front end.  

Hopefully it'll work for you as it works for us.  Thanks also to the amazing [Robin](https://twitter.com/eviltrout) for providing this guidance that we can share with you.

### Step 1: Import Your Model/Controller into Your Initializer file.

You're in your plugin folders.
Create an initializers folder and then within that, create a file called **some-initializer-file.js.es6** and add import.

```
import NameofController from 'path';

For example:

import PostModel from 'discourse/models/post';
import ComposerController from 'discourse/controllers/composer';
```

### Step 2: Reopen the Model or Controller That You Imported & Add Whatever you Wanted to Add

So, in the same initializer file you can add that function or whatever you wanted to add to extend that model or controller.
The ```export default, name and initialize``` just get the thing going and so that it can display it's parts.

```
export default {
  name: 'extend-something',
  initialize() {
    NameofController.reopen({
      nameOfFunction: function() {
        write what it does...
      }.property(something)
    });
  }
}

An Example:

export default {
  name: 'extend-post-model',
  initialize() {
  	PostModel.reopen({
  	  postSpecificCount: function() {
   	    return this.get('post_number') % 2 === 0; 
  	  }.property('post_number')
  	});
  }
};

```

### Step 3: Put it Altogether

Your initializer file should look like this when putting everything together (using the post example):

```
import PostModel from 'discourse/models/post';

export default {
  name: 'extend-post-model',
  initialize() {
  	PostModel.reopen({
  	  postSpecificCount: function() {
   	    return this.get('post_number') % 2 === 0; 
  	  }.property('post_number')
  	});
  }
};
```

### Step 4: Apply Your Function that is Extended from A Model or Controller in Ember to A Handlebars Thinggo.

Using handlebars, just put an if statement around whatever you want to apply the function to.

For example, in Discourse > Templates > Connectors > post-bottom.hbs, we did:

```
{{#if postSpecificCount}}
  {{google-dfp-ad placement="post-bottom"}}
 {{/if}}
```

This piece of code means that, we'll display the ad if it meets the function requirements.  So display the ad after every 2nd post.

I don't know why but doing certain things add to your propensity to do other things.

For example, when I was working in a journalist's bureau, I started drinking wine at home nearly every night.
Now, everytime that I'm coding but not in a pair, I'm listening to early 2000s hip hop and r&b.  Last night, I even listened to Peter Andre, what the?

Meanwhile, I really want to be one of those token girls in those videos (Nelly, if you somehow are reading this coding blog post, please... please... choose me if you're doing another music video!  I don't look anything like the girls in your videos but I make up for it in Australian humor and coding skills) <3

Anyway, hope this helps some aspiring plugin author somewhere...

xox Ladydanger
