# ===== Controllers =====

## Controller Basics
Controller files are held in the controllers directory under the app folder (app_root/app/controllers)
Each model will need an associated controller
Controller names are plural of the model they are controlling

If you use rails generate scaffold, rails will create and populate a basic controller set upu with details on what the controller does and attached routes.

The controller holds the actions that are associated with different routes that will be visited by users during interaction with the app.  

Basic Controller operations are related to the routes defined in app_root/config/routes.rb


    Controller Method   HTTP Verb             URL                                 prefix(always add _path to end)
        -#index             GET                /<model_name>(plural)               users_path
                                              -/users
                                              
        -#create            POST               /<model_name>(plural)               users_path method: :post
                                              -/users
                                              
        -#new               GET                /<model_name>(plural)/new           new_user_path
                                              -/users/new
                                              
        -#edit              GET                /<model_name>(plural)/:id/edit      edit_user_path
                                              -/users/1/edit (edits user id 1 where 1 is params([:id])
        
        -#show              GET                /<model_name>(plural)/:id           user_path(params[:id])?    
                                              -/users/1 (shows user 1 where 1 is (params[:id])
                                              
        -#update            PATCH              /model_name>(plural)/:id            user_path(params[:id]) method: :patch?
                                              -/users/1
        
        -#update            PUT                /<model_name>(plural)/:id           user_path(params[:id]) method: :put?
                                              -/users/1
        
        -#destroy           DELETE             /<model_name>(plural)/:id           user_path(params[:id]) method: :destroy?
                                              -/users/1
                                              
## Writing Controller Actions - Index
Index is the point that will display all of a given models objects.  Depending on what is wanted to be shown, this is typically a listing of all users, all pets, or all x of a given model

