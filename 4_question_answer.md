1. This is an explanation of how to use "singular" and "plural" properly in Rails.

**For example, "posts" is specified for parameters when creating a controller, and "post" is specified for parameters when creating a model. It seems that various variables are automatically created based on that, so I think it makes sense to use "posts" and "post" properly, but it is still confusing because there is no description anywhere.**  

Here it is Database tables use user. Table names are plural.=> this will be users as Table name.
But Column names in the database use user, but are generally singular.

Eg:

users | Id
------------ | -------------
Name | STRING
Email | STRING
post_id | FOREIGN KEY


posts | Id
------------ | -------------
name  | STRING
content | TEXT


Model class names use CamelCase. These are singular, and will map automatically to the plural database table name.Model attributes and methods use user and match the column names in the database.Model files go in app/models/#{singular_model_name}.rb

Eg:
# app/models/post.rb
```
class Post < ActiveRecord::Base
  # This class will have these attributes: id, name, content
end
```
Controller class names use CamelCase and have Controller as a suffix. The Controller suffix is always singular. The name of the resource is usually plural.
```
Posts Controller < ApplicationController
  `def index`
    # ...
  `end`
  `def show`
    # ...
  `end`
  # etc
end
```
Route names are user, and usually match the controller. Most of the time routes are plural and use the plural resources.
```route.rb
resources :posts
```

Views
View file names, by default, match the controller and action that they are tied to.

```Views go in app/views/#{resource_name}/#{action_name}.html.erb.```

Examples:

app/views/posts/show.html.erb


1. Even if I try "rake routes", there are "post" "new_post" "posts" and "confirm_posts" in Prefix. I don't understand why this is happening at all.

Thank you for asking, now we are going to look together how Rails routing configurations are kept in config/routes.rb file. And Taking parameters depends on many things. rake routes will show with routes take parameters. Member actions will take parameters.
## Routing 
*The Rails router recognizes URLs and dispatches them to a controller's action, or to a Rack application. It can also generate paths and URLs, avoiding the need to hardcode strings in your views.*
 When your Rails application receives an incoming request for:
`GET /posts/new`
it asks the router to match it to a controller action. If the first matching route is:

`get '/posts/:new', to: 'posts#create'`

and your application contains this code in the controller:

`@post = post.new(params[:post])`
and this in the corresponding view:
`<%= link_to 'New post', post_path(@post) %>`



```posts    GET        /posts(.:format)          posts#index
         post       /posts(.:format)          posts#create
edit_post GET       /posts/:id/edit(.:format) posts#new
```

*Hope you have got something, thank you for your attention.*

