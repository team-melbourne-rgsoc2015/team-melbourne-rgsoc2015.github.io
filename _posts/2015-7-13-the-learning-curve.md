---
layout: post
title: The Learning Curve + Part 1: 10 Basic Notes on how Ember.js Works
---

![](https://googledrive.com/host/0BzxRUlDjwAFec3VGdXdJNGZQSVU)

Vi: A lifetime ago, when I was doing work as an accountant, I had a fantastic boss named Reynold
who was talking about learning being a bunch of dots that, with time, gets linked together.
I'm starting to feel that the dots are still very apart but hopefully they'll soon come together.

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

Before we start, here's a common translation to terms.
*Render* means to show or display something.
*Template* is the view of something, it's the file that display the view.
*Route* is a path, it's supposed to create the URL.
*URL* is the thing that appears in the box in the browser (when you open up to go on the internet) and it has the website name e.g. www.ember.js is a URL.
*Link* is something that links you to another thing.  You can embed links within buttons aswell.  

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

#### 6. Models

> In Ember, every route has an associated model. This model is set by implementing a route's model hook

Models in Ember store data.  In the Ember CLI, this has it's own folder.  Things called fixtures are in here - fixtures
are like set data that come up when first loading something.  A model hook is created within a route - see...

**app.js** (Route)

```
export default Ember.Route.extend({
    model: function() {
        return this.store.find('todo');
    },
```

**model.js** within the model folder if using CLI.  It holds the fixtures and gets data from the data store.  The title is a string and isCompleted is a true/false.

```
import DS from 'ember-data';

export default DS.Model.extend({
  title: DS.attr('string'),
  isCompleted: DS.attr('boolean')
}).reopenClass({
  FIXTURES: [
      {
          id: 1,
          title: "Complete Ember.js Tutorial",
          isCompleted: false
      },
      {
          id: 2,
          title: "Checkout some more ember stuff",
          isCompleted: true
      },
      {
          id: 3,
          title: "Solve world hunger (with Ember)",
          isCompleted: false
      }
  ]
});
```

**template.hbs** - you can show your items here.

```
Template for all the first model
{{#each item in model}}
	<li>{{item.title}}</li>
{{/each}}
```

#### 7. Redirecting and Linking

You might need to redirect routes.  There are two ways:

* Redirect function in route.

```
App.IndexRoute = Ember.Route.extend({
	redirect: function() {  //The redirect is a HOOK.
		this.transitionTo('link to name of route');
	}
})
```

* Redirect in a controller

```
App.IndexController = Ember.ObjectController.extend({
	actions: {
		linkClicked: function() {
			this.transitionToRoute('about');
		}
	}
});
```

To create links in Ember, use {{#link-to}}, kinda like the link_to in Rails.  For example {{#link-to 'name_of_route}}Text_that_ppl see{{/link-to}}.


#### 8. Application template and outlet

What is {{outlet}}?  It pretty much renders (or shows) all the subpages within the js application.
So you have your application, then the individual routes that show beneath this.  It means that the application doesn't have to reload.


#### 9. Using a different template without create a new route.

This is possible in Ember through the use of renderTemplate hook.  A hook in Ember is the thing in a Route that is before the expression of function().

```
App.AboutRoute = Ember.Route.extend({
	renderTemplate: function() {
		this.render('PUT_THE_NAME_OF_THE_TEMPLATE_YOU_WANT_TO_RENDER');
	}
});
```

This is not normally used in this way but rather with another outlet (see below)

```
{{outlet}}
	{{outlet outlet2}} // You'd render something here.
```

```
	this.render();
	this.render('aboutme', {}); // this would render in the 2nd outlet.
```

#### 10. GET and SET in Ember.js

If you want to get properties in a controller inside a method use GET and if you want to set new properties, then use SET.

```
actions: {
	showAlert: function() {
		var actor = this.get('firstName') + ' ' + this.get('lastName');
		alert('The actor is '+ actor);
	}
	setAnotherActor: function() {
		this.set('firstName', 'Michael');
		this.set('lastName', 'Schofield'); // This might have been changed in the new version.
		var newActor = this.get('firstName') + ' ' + this.get('lastName');
		alert('The new actor is ' + newActor);
	}
}
```

In your template, you can create a link to do the action which will then GET the firstName and lastName properties.
For example:

```
<a href ="" {{action: showAlert'}} show actor</a >.
```

There's more... but that's it for today.... Part 2 of Basic Notes on how Ember.js Works will come tomorrow.

Noche...

