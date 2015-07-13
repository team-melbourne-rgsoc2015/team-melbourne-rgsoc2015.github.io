---
layout: post
title: The Learning Curve
---

![](https://googledrive.com/host/0BzxRUlDjwAFec3VGdXdJNGZQSVU)

Vi: A lifetime ago, when I was doing work as an accountant, I had a fantastic boss name Reynold
who was talking about learning being a bunch of dots that, with time, gets linked together.
I'm starting to feel that the dots are still very apart but hopefully slowly coming together.

Today, I:

* Learnt more about the Ember framework (more in detail about that below).
* Found a shortcut - to comment things out in a text editor, highlight and then command + forward slash (/).
* Played around with the inspector on Chome to create a break and also to check out routes on Ember sites (check out the pics below).

![](https://googledrive.com/host/0BzxRUlDjwAFed1gwWUNuOWlxQjg)

This is a screenshot of a website that uses the current adsense plugin done by DiscourseHosting.  Yes - I've been browsing Shopbop lately to see what new clothes they have...
Anyway, in that pic, you can see in their code adbygoogle.push({}); which looks like it's pushing an empty object.

Our lovely mentor, Dane, from RedBubble, suggested we try creating a break.  In the inspect elements thinggo in Chrome, you can also view sources, and create a break which can show you what happens at certain points.

I put a break in line 29 and reloaded (refreshed) the site and the ad didn't load (see below).
I'm looking forward to using this more...

![](https://googledrive.com/host/0BzxRUlDjwAFec3VGdXdJNGZQSVU)

### Ember Time...

While we've been going through the mechanics of the plugin, I'm feeling rather deficient in the basics, so today went through Videos 1 - 20 of Mastering Ember.js by CodeLogical - you can watch it on youtube.  Thanks also to Sarah for referring me to this great source.  The source uses the old Ember (not Ember CLI), but it's great for understanding the framework.

Here's what I learnt:

#### 1. Create a route.

The route name doesn't need to be exactly what it is in the URL.

**app.js**

```
App.Router.map(function() {
	this.route('first-route' (this is just the name), {path: '/first-router-in-url'}) < for convention keep it similar.	
	}
)

```

#### 2. Render the Route - that means to show it.  

Create a template relating to the route.  The template will be a handlebars template.  I suspect with Ember CLI that would be in the templates folder and a separate hbs file.

**index.html**

```
<script type="text/x-handlebars" id="ADD the ROUTE NAME">
	<h2>Add what's in the route</h2>
</script>

```

#### 3. Add in a Click Action.  

Created an action called headerClicked that creates an alert box.

**index.html**

```
<script type="text/x-handlebars" id="ADD the ROUTE NAME">
	<h2{{action 'headerClicked'}} > Add what's in the route</h2>
	<p>{{firstName}}<<lastName>></p>
</script>
```

**App.js**

```
App.FirstRouteRoute = Ember.Route.extend({
	actions: {
		headerClicked: function() {
				alert('Header Clicked');
		}
	}
	model: function() {
		return ['first item', 'second item'];  >> //This would be passed to the controller.  Then the 
		// controlller checks and then it would load everything in the template (index.html or whichever template)
		// has been set for this route.
	}
})
```

#### 4. Creating the first controller

Controllers take precedence over the router and can store data. One can put the action here instead of putting it in the router.

**app.js**

```
App.FirstRouteController = Ember.Controller.extend({
	firstName: 'Harry'
	lastName: 'Hart'
});
```

#### 5. Databinding

Adding data for a person - in the handlebars template, you can then do: {{person.age}} {{person.height}}.  If you bind to a property that doesn't exist, there's no error, it just doesn't show.

**app.js**

```
App.DatabindingController = Ember.Controller.extend({
	firstName: 'Richmond',
	lastName: 'Valentine',
	person: {
		age: 40,
		height: '1.9m'
		status: 'megamaniac'
	}
})
```

This post will be updated later today with more stuff...
