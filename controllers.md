# ===== Controllers =====



    Controller Method   HTTP Verb          URL                                 prefix(always add _path to end)
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