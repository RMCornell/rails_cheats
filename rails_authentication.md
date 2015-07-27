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
-Use rails generate model or create by hand
-Use password_digest for b_crypt gem
-migrate database after creation of model and confirmation that the migration file has been set up correctly. 

## Create users_path in routes

    In routes.rb file:
    
        add [:create]
        
## Specify in user.rb model
   
    has_secure_comment
    
    uncomment bcrypt in Gemfile and bundle
    
## Add Create method to UsersController.rb

    in users_controller.rb:
    
        def create
            @user = User.new(user_params)
            
            if @user.save
                session[:user_id] = @user.id
                redirect to @user
            else
                #add error conditions and rerender new view if validations do not pass.
        end
        
## Specify Strong Params inside a private method in UsersController

    inside of users_controller.rb
    
    private
    
    def user_params
        params.require(:user).permit(:username, :password)
    end
    
## Define user_path [:show]

## Add show Method to UsersController

## Add show.html.erby in user_view directory

## In UserControllers#show

    def show
        @user = current_user
        
## Create Helper Method

    helper_method :current_user
    
    def current_user
        @current_user ||= User.find(session[:user_id]) if session[:user_id]
    end
    
## In show.html.erb

    <h2>User Show Page</h2>
    
    Welcome <%= @user.username %>
    
## In Application_layout

    <body>
        <% if current_user %>
            Welcome <%= current_user.username %> (This will only work if current_user exists
        <% end %>
            <%= yeild %>
    </body>
    
## Reset session between tests

    In test_helper.rb
    
    class ActionDispatch::IntegrationTest
        def teardown
            reset_session!
        end
    end
    
    
    