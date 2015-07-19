# ===== Creating Routes =====

Routes are what define the http CRUD functions that will take place as the user interacts with various parts of the web app.  There are two ways to create routes, manually and automatically within Rails. 

## Automatically Create Routes
Rails is capable of automatically creating all necessary default routes with one line of code. 

    Inside the routes file (located app_root/config/routes.rb
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
    
    
    



