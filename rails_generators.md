# ===== Rails Generators =====

Rails has several ways of generating the files and related files that are needed for an application.  Below are some of them.

Note that I will use generate in the command line but you can short cut this and just use 'rails g' when generating objects within rails.

## Model Generator
Models typically represent objects and the methods associated with those objects.  For example one model you may have is a user model, which will handle the attributes for that model and methods associated with each user. 

    From Terminal:
    rails generate model <Model_name>(singular)
    
    Example:
    rails generate User
    
Additionally, you can define the attributes of the model when generating the model using the generator.

    From Terminal: 
    rails generate model <Model_name>(singualar) <column_header>:<type> <second_column_header>:<type>
    
    Example: 
    rails generate User first_name:string last_name:string
    
The Model Generator will create the following:
    1. Database Migration with attributes at the end of the command
    2. Model file
    3. Testing file for the model generate with framework
    
Because the Model Generator creates a database migration you will need to run the migration to take the actions in the database defined in the migration.

    From Terminal:
    rake db:migrate
    
