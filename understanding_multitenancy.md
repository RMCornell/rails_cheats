# Understanding Multitenancy
    Notes from Understanding Multitenancy Lesson - Turing Cohort 1502
    www.vimeo.com/128198524

## What is Multitenancy
One instance of an app serving many tenants instead of each tenant having their own application.  Tenants are a group of users

Examples of multitenant application (Etsy, Facebook Groups, Github Organizations)

## Video Walkthrough

### 1. Clone Repo

    In Terminal:
        git clone https://github.com/turingschool-examples/storedom.git multitenancy
        
    In Terminal: 
        bundle && rake db:setup
        
&& will execute the second command if the first is successful
rake db:setup will run rake db:create, db:migrate and db:seed in one command

### 2. Start Rails Server

    In Terminal:
        rails s
        
### 3. Modify Routes
    
Current Routes are:

    In app_root/config/routes.rb
    
    Rails.application.routes.draw do 
        root 'items#index'
        
        resources :items, only: [:index, :show]
        resources :orders, only: [:index, :show]
        resources :users, only: [:index, :show]
    end
    
To create multitenant routes use namespace

    In app_root/config/routes.rb
    
    Rails.application.routes.draw do 
           root 'items#index'
           
           resources :items, only: [:index, :show]
           resources :orders, only: [:index, :show]
           resources :users, only: [:index, :show]
           
           namespace :stores, as: :store, path: "/:store" do
                resources :items, only: [:index, :show]
           end
       end
       
Breakdown of namespace :stores, as: :store, path: "/:store"

    namespace :stores
        Adds namespace of stores and inside the do - end block it calls additional resources necessary for the paths inside of the store (items, order, users)
        
    as: :store
        Renames helper paths from stores to store.  This only changes the helper path, not the url.
        
    path: "/:store" 
        Makes the store a parameter and enables the ability to access multiple stores
        
Finally change the root url

    In app_root/config/routes.rb
        root 'stores#index'
        
### 4. Generate Stores and Stores/Items Controllers

