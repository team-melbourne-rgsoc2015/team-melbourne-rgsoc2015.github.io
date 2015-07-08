---
layout: post
title: Delving Deeper into Ember
---

![](https://googledrive.com/host/0BzxRUlDjwAFeOVUza3JMR2V5UlE)

Vi: Today, I was not well so I worked from home.  Working from home has its upsides.  I’ve been in bed on the computer the whole day (although I don’t think that’s something to brag about) and it’s super comfy in PJ.  The downside of working from home is that I’ve been eating biscuits, rice crackers etc… pretty much anything that I can find at home… and the temptation to internet browse is great.  Meanwhile, how cute is Ember’s Tomster - wonder if he’s a guinea pig.  My fav is the Fishy Tomster - so adorable!

Today, I went to create a todoapp MVC using the ember framework, however, using the cuticleapp didn’t exactly work for me, so I found this great blog post from [brownie3003](http://www.thetechcofounder.com/getting-started-with-ember-js-using-ember-cli/).  The main reason why this worked for me and the others didn’t was:

This was written in May/June - so recent
It used Ember CLI which created the scaffold - using the Ember guides didn’t work with this and we had spend all of yesterday creating the dependencies…. and why waste something if it works...

This activity was fantastic… while there’s still a fair way to go… it was good in getting some form of understanding.  Here’s stuff that I learnt and found interesting (mainly quoted from brownie3003’s website).

> Ember Data is a library for robustly managing model data in Ember.js applications. We'll often see ES6 import statements like import DS from 'ember-data'; that signals the usage of Ember Data.

> A model is represented by an object that stores persistent state (long term living data).

> Fixtures are used to define sample data without the need of querying a backend server.

> In Ember Data, the logic for communicating with a backend data store lives in the Adapter. If the set of backend rules is consistent, we can set up an application-wide adapter, called ApplicationAdapter.

Here’s other stuff I found interesting about Ember:

#### No. 1 Naming convention in Ember and Rails
I also found the way they set up names is kinda similar to **Rails**.  In Rails, say you wanted to create a thing to handle Posts.
*You’d have a Post model, a Posts controller, and a Posts view that would have the relevant view pages like index, create and show.*
In **Ember**, you have the:
*Todos template which is a handlebars file, the Todos route which was defined in the Router (which manages Routes and Resources) and the Model is a singular: Todo.*
I also found it neat how in the route, there will be a hook that returns **all the records** of a type.  It looks like this...

```
import Ember from 'ember';
export default Ember.Route.extend({
    model: function() {
        return this.modelFor('todos');
    }
});
```
#### No. 2 No ‘Else If’ in Handlebars
In Javascript, you have an if, else if etc.. and else.  I’m used to the elsif in Ruby.  But… in handlebars, there is no ‘else if’ or ‘elsif’….

#### No. 3 The way the loop looks in Handlebars…
The #each is used… in long form, this is: {{#each todo in model}} ... 

```
  <section id="main">
    <ul id="todo-list">
      {{#each}}
        <li>
          <input type="checkbox" class="toggle">
          <label>{{title}}</label></button class="destroy"></button>
        </li>
      {{/each}}
    </ul>
```
#### No. 4 Adapters and handling data
I like how with Ember there is no ‘database’ per se in its tradition.  I see a lot of the below code and think that it might be importing data from the library into the backend store and exporting sample data from the application via the fixture?... 

In app > adapters > application.js
```
import DS from 'ember-data'; 
export default DS.FixtureAdapter.extend();
```
It took pretty much the whole day (it’s 10:36pm now… but it’s so easy for time to fly by when you do this stuff… and also if you’re in a comfy bed).

At the beginning (which was yesterday), I didn’t like Ember that much, mainly because I didn’t understand it, but I’m starting to really appreciate what a great framework it is… how neat is it that one can create an app without a controller and manage a lot of it with the routes.  It’s very clever.

I’m starting to feel that Ember’s kind of girl that travels with everything they need (in their handbag) where they can retrieve what they need instead of going back to a closet (database).  Now… if only I could find that uber handbag...
