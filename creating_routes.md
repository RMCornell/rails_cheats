# ===== Creating Routes =====

Routes are what define the http CRUD functions that will take place as the user interacts with various parts of the web app.  There are two ways to create routes, manually and automatically within Rails. 

## Manually Creating Routes
You can manually create your own routes in the routes.rb file without using the Rails resources helper.  

    Inside app_root/config/routes.rb:
    get '<path_1/path_2>' => <controller>#<method>
    
    Example:
    get 'products/:id' => 'catalog#view'

This route tells rails that when the url 'blah/products/1' is visited, Rails will go to the catalog controller and find the 'view' method to execute when generating the view for this url.

You can write POST, PATCH, PUT and DELETE routes and actions the same way by just replacing the word 'get' with the action you are writing the route for. 

## Automatically Create Routes
Rails is capable of automatically creating all necessary default routes with one line of code. 

    Inside the app_root/config/routes.rb
    resources :<model_name>(plural)
    
    Example:
    resources:users
    
Resources will automatically map the HTTP avers to the actions in the appropriate controller. 

Resources will generate the following standard routes:

    prefix          Verb        URI Pattern                  Controller/Action(controller Method)
    <model>         GET         /users(.:format)                users#index
    <model>         POST        /users(.:format)                users#create
    <new_model>     GET         /users/new(.:format)            users#new
    <edit_model>    GET         /users/:id/edit(.:format)       users#edit
    <model>         GET         /users/:id(.:format)            users#show
    <model>         PATCH       /users/:id(.:format)            users#update
    <model>         PUT         /users/:id(.:format)            users#update
    <model>         DELETE      /users/:id(.:format)            users#destroy
    
## Limiting Route Creation
You can limit the routes created by telling Rails to 'only' create certain routes instead of the eight standard routes it creates. 

    Inside app_root/config/routes.rb
    resources :<model_name>, only: [:<route_one, :<route_two>]
    
    Example:
    resources :users, only: [:new, :create, :show]
    
## Nested Routes
You can create nested routes by defining resources for additional routes inside of a 'do' block for existing routes

    Inside app_root/config/routes.rb
    resources :<model_one> do
        resources :<model_two>
    end
    
    Example:
    
    resources :users do
        resources :songs
    end
    
This will do two things.  First it will create the eight standard routes for users as outlined above.  Additionally, it will create eight additional routes for songs that will be nested under users.  They will look like this:

    Prefix              Verb    URI                         Controller#Action
    user_songs          GET     /users/:user_id/songs       songs#index
    user_songs          POST    /users/:user_id/songs       songs#create
    new_user_song       GET     /users/:user_id/songs/new   songs#new
    
And so on and so forth with each route being nested within the first resourced routes.
    
## Namespaced Routes
Namespacing is used when you are running a multitenant application that has different levels of authencicated users.  As in the case of having an application administrator.

    Inside app_root/config/routes.rb
    namespace :<title_of_namespaced_route> do
        resources <object>
    end
    
    Example:
    namespace :admin do 
        resources :songs
    end
    
This will be similar to nested routes with one significant difference.  Because of the namespacing, when the application looks for a controller associated with this route, it will first look for a controller with the name of the namespace. 

It will direct admin/songs to Admin::SongsController which is a different controller than SongsController (See guide on multitenancy authorization for more indepth information on this)

Additonally, namespacing will change the way the route helpers look when generating resources for the namespaced routes. 
   
