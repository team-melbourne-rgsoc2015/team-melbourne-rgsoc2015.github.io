---
layout: post
title: Part 2 with another 5 Basic Notes on how Ember.js Works
---

Vi: Continued from the previous blog post...

#### 11. Ember Helpers - The Already Given Ember Helpers and Make Your Own!

Helpers help you reduce the need to repeat long pieces of code in many different places.  In Ember, these are called Ember helpers and you can use them in a Handlebars template - that's the file that has a .hbs extension.

These are examples of already produced Ember helpers:

```
{{#link-to 'route'}} {{/link-to}}
{{input}}
{{input type='radio'}} > radio button
Action helper

<a href="" {{action 'someAction'}}</a> - make an HTML element clickable
<button {{action 'expand'}}>Show More...</button>
```

or you can definitely create your own by doing...

In **app.js** you set up the below. See the Handlebars helper called makeShorter being created.

```
App.IndexController = Ember.ArrayController.extend({
key_name: 'value_of_key'
});

Ember.Handlebars.helper('makeShorter', function(value, option) {
return value.substr(0, 5);
)};
```

The in the Handlebars template:

```
{{name_of_helper key_name_here}} - will apply the helper method to the value of the key.
```


#### 12. Databinding Part 2 - Binding and Pushing New Objects through an Action

This means to create data (info) and put it into a variable type thing that already exists.
For example, the below code will make a little input box and then whatever goes in that input box will then be (or bind) to whatever that variable name is.  So, if the firstName was Cate and lastName Blanche and if you had an input form that binded to the firstName variable, and you then put in Carte, the firstName would now be Carte and you'd end up with firstName + lastName = Carte Blanche.


In the **index.html** template

```
{{firstName}}
{{input value=firstName}} // Binding the value into the input.  Changing the input will change the first name.
	<button {{action 'addNewItem' }}>update model</button>
```

The below code pushes a new item into the existing model through an action... (
In the controller...

```
actions: {
		addNewItem: function(){
			this.get('model').pushObject('new item');
		}
}
```


#### 13. Ember Data for Defining, Creating and Using Models

> Model is a class that defines the properties and behavior of the data that you present to the user. 

In Ember, every route has an associated model, the model is something that defines properties and behaviour of data.  
So for example, just say there's a boy, 'Little Johnny', he has the following properties of being: male.
So you have a model, called Little Johnny, who has 1 property and that's of gender: male.  The data can only be male or female.
One of the two only.  That's behaviour of data.

In Ember, you can get data by not going to the server and instead using the Fixture Adapter - which is really neat!

So, this is how you create person model in with a Fixture Adapter (we're using Ember-data here btw).

```
App.PersonAdapter = DS.FixtureAdapter.extend ({});  // Anytime a person is requested, don't go to the server but go to the fixture and then return the people.

// Behind the scenes, the RESTAdapter is working and it's the overall thinggo, so for each model, you must write fixture adapter to use the fixtures thinggo.

App.ApplicationAdapter = DS.RESTAdapter.extend({}); // I am the REST adapter.

// Here's the Person model.
App.Person = DS.Model.extend({
	firstName: DS.attr(),
	lastName: DS.attr('string'),
	age: DS.attr()
});

// Creating people using fixtures.
App.Person.FIXTURES = [
	{
		id: 1,
		firstName: 'Prince',
		lastName: 'Eric',
		age: 18
	},
	{
		id: 2,
		firstName: 'Ariel',
		lastName: 'Triton',
		age: 16
	}
]

// Here, the model is returning details from the Fixtures.
model: function() {
	return this.store.find('person');
}

// We're displaying this in the index.html
{{#each item in model}}
	<li>{{item.firstName}} - {{item.lastName}} is of age {{item.age}}</li>
{{/each}}
```


#### 14. When Variable Values Change and You Want to Bind this to Another Variable

In short the proper names for this is **computer properties** and **observers**.

* Computed properties is when a variable has values from other variables and you do this in a controller.  Use .property
* Observers are different from computed properties as a value is not set for them.  It looks at the variable, and only if the variables that it derives its value from changes, then the observer runs.  It uses the SET whereas computed properties uses a GET.  Use .observes

Here's an example of computed properties being used.

```
{{firstName}} {{input value=firstName}}
{{lastName}} {{input value=lastName}}
{{fullName}} // we want to bind this to the first and last name.


All.IndexController = Ember.ArrayController.extend({
	lastName: 'ang',
	lastName: 'jo',
	fullName: function() {
		return this.get('firstName') + ' ' +this.get('lastName')
	}.property('firstName','lastName')  

//You need property to automatically update.  This is special Ember magic.  This function depends on first and lastname so if these things change, then you'll update the cache for the change.

})
```

Here's an example of observers being used.

```
// Observers - anytime this property changes, then run this function.  This property depends on other properties.

All.IndexController = Ember.ArrayController.extend({
	lastName: 'ang',
	lastName: 'jo',
	fullName: '',
	adjustFullName: function() {
		this.set('fullName', this.get('firstName')+ ' '+this.get('lastName'));
	}.observes('firstName', 'lastName')  
})
```

#### 15. Model Relationships

You can put relationships between different models.  For example, if you created a blog.  You'd need a model for the blog posts and a separate model for the comments.  You'd then need to establish some form of link or relationship between these two different models.  For example, if you have a post, you'll have certain comments that are related to a post and not another post.  So the relationship you'd have from the persepctive of:

* The post is that the post will have many comments.  That's a 'hasMany' relationship.
* The comment is that the comment will belong to one post.  That's a 'belongsTo' relationship.

Relationships are also called associations.  In Rails, which is another framework (Ember is a framework), there are more advanced associations called Polymorphic Associations.  The name sounds scary but it means that one model can be associated with many models.  Kind of like if you have a sweater that can be used for winter and summer - the transitional piece of clothing.  @winter.sweater, @summer.sweater.

Anyway, let's see how we can make model relationships in Ember.js

```
// in app.js

App.ArticleAdapter = DS.FixtureAdapter.extend();

App.BlogRoute = Ember.Route.extend({
	model: function() {
		return this.store.find('article');
	}
});


// in index.html under blog handlebars

{{#each}}
	<p>{{#link-to 'article' this}}{{title}}{{/link-to}}</p>
{{/each}}


// article path: in app.js

this.route('article', {path: 'articles/:article_id'});


// New handlebars template for article show.

{{title}}
{{body}}


// Associating articles with comments - see we're doing it in the MODEL.

App.Article = DS.Model.extend({
	title: DS.attr(),
	body: DS.attr(),
	comments: DS.hasMany('comment', {async: true})  // remember the async to true.
});

App.Comment = DS.Model.extend({
	text: DS.attr(),
	atricle: DS.belongsTo('article')
});

// In the fixtures, you then need to allocate.

App.Article.FIXTURES = [
comments: [2,3] < being the ID, uses an array because it is a HasMany
]

App.Comment.FIXTURES = [
	article: 2 < single ID due to belongsTo
]

// To display in template.

{{#each comments}}
	{{text}}
{{/each}}

// Because of the association, for each blog post, it will display the comments that belong to that particular blog post.
```

Here is a pic of Gazelle, from Kingsman Secret Service... just because... (It's a good movie).

![](https://googledrive.com/host/0BzxRUlDjwAFebHZ0cXhqNVFOTWM)

Part 3 to follow tomorrow on Ember... It'll be the last part
