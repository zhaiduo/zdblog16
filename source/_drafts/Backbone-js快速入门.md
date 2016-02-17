---
title: Backbone.js快速入门
tags:
  - MVC
id: 1792
categories:
  - javascript
---

js files needed:
underscore.js, jquery.js, backbone.js

创建Models
> var Todo = Backbone.Model.extend({
>   initialize: function(){
>     this.on('change', function(){
>         console.log('- Values for this model have changed.');
>     });
>   },
>   defaults: {
>     title: '',
>     completed: false
>   }
> });
> Todo.validate = function(attrs) {
>   if (!attrs.title) {
>     return 'I need your title';
>   }
> };
> var todo = new Todo({
> title: 'Check the attributes of both model instances in the console.',
> completed: true
> });
> 
> console.log(todo.get('title'));
> todo.set("title", "Title attribute set through Model.set().");
> Todo.unset('title', {validate: true});

创建Views
> var TodoView = Backbone.View.extend({
>   tagName:  'li',// required, but defaults to 'div' if not set
>   className: 'container', // optional, you can assign multiple classes to this property like so: 'container homepage'
>   id: 'todos', // optional
>   // Cache the template function for a single item.
>   todoTpl: _.template( "An example template" ),
>   //An event takes the form of a key-value pair 'eventName selector': 'callbackFunction'
>   events: {
>     'dblclick label': 'edit',
>     'keypress .edit': 'updateOnEnter',
>     'blur .edit':   'close'
>   },
>   // Re-render the titles of the todo item.
>   render: function() {
>     this.$el.html( this.todoTpl( this.model.toJSON() ) );
>     this.input = this.$('.edit');
>     return this;
>   },
>   edit: function() {
>     // executed when todo label is double clicked
>   },
>   close: function() {
>     // executed when todo loses focus
>   },
>   updateOnEnter: function( e ) {
>     // executed on each keypress when in todo edit mode,
>     // but we'll wait for enter to get in action
>   },
>   events: {
>         click: function(e) {
>           console.log(view.el === e.target);
>         }
>   }
> });
> var todoView = new TodoView({el: '#footer'});//you can set el to an existing element when creating the view:
> console.log(todosView.el); // logs 
> 
> todoView.setElement($(someid));//setElement: If you need to apply an existing Backbone view to a different DOM element
> 
> ////////////////////////////////////////////
> 关于Render:
> var ItemView = Backbone.View.extend({
>   events: {},
>   render: function(){
>     this.$el.html(this.model.toJSON());
>     return this;
>   }
> });
> var ListView = Backbone.View.extend({
>   render: function(){
>     var items = this.model.get('items');
>     _.each(items, function(item){
>       var itemView = new ItemView({ model: item });
>       this.$el.append( itemView.render().el );
>     }, this);
>   }
> });
> 
> //Collections are sets of Models and are created by extending Backbone.Collection.
> var TodosCollection = Backbone.Collection.extend({
>   model: Todo,
>   url: '/todos'
> });
> 
> var todos = new TodosCollection();
> todos.fetch(); // sends HTTP GET to /todos
> var todo2 = todos.get(2);
> todo2.set('title', 'go fishing');
> todo2.save(); // sends HTTP PUT to /todos/2
> 
> todos.create({title: 'Try out code samples'}); // sends HTTP POST to /todos and adds to collection
> todo2.destroy(); // sends HTTP DELETE to /todos/2 and removes from collection
> 
> //Each RESTful API method accepts a variety of options.
> model.save({b: 2, d: 4}, {patch: true});
> console.log(this.syncArgs.method);
> // 'patch'

The Backbone.history.start() method will simply tell Backbone that it’s okay to begin monitoring all hashchange events as follows:
var myTodoRouter = new TodoRouter();
Backbone.history.start();

参考网址：
[http://addyosmani.github.io/backbone-fundamentals/](http://addyosmani.github.io/backbone-fundamentals/)
[http://ricostacruz.com/backbone-patterns/](http://ricostacruz.com/backbone-patterns/)