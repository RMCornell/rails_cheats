# Rails Authentication

## Create new_user path
-add routes in routes file in root/config/routes

        resources :user, only [:new]
        
-Rake routes to confirm creation

## Create Users Controller
-Create user controller with rails generator 
    
    From Terminal
        rails g controller Users
            
-Or create user controller manually

    create root/app/controllers/users_controller.rb and add:
    
    class UsersController < ApplicationController
    
    end
        
## Create template for users inside view folder

    create directory root/app/views/users
    create file root/app/views/users/show.html.erb
    
    Inside file add:
        <h1>Create a new account</h1>
            <%= form_for(@user) do |f| %> (Define variable in UsersController with @user = User.new
                <%= f.label :username %>
                <%= f.text_field :username %>
            
                <%= f.label :password %>
                <%= f.text_field :password %>
            
                <%= f.submit "Create Account %>
            <% end %>
            
## Create User Model
