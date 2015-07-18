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
    
## Controller Generator
Controllers are used to do the work that needs to be done in the app and then provide the results to the views for display.

    From Terminal:
    rails generate controller <controller_name>(plural)
    
    Example:
    rails generate controller Users
    
The Controller Generator will create the following:
    1. model controller
    2. Directory for Views
    3. Testing and Helper File
    4. Assets for Javascript and stylesheets

Controller generation does not create any active record associations or migrations so there is no need to migrate the database after generating one. 

## Migration Generator
Migrations are used to make changes to a database, either adding or removing columns, or adding and removing tables as well as creating foreign keys between tables if they were not set up when the models were generated. 

These are used for changing tables in database.  Initial set up should be done through the Model Generator. 

    From Terminal:
    rails generate migration <Action><To><Table_name> <column_header>:<type>
    
    Example:
    rails generate migration AddPetIdToUsers pet:references
    
References create a foreign key in the table they are being added to. If you don't utilize this in the terminal, you will need to open the migration file that is created and manually add the changes you want to make. 

Confirm the migration file is correct and then migrate:

    From Terminal:
    rake db:migrate

## Scaffold Generator
Scaffold is a rapid way to generate models and controllers for a rails app in one command from the terminal. 

    From Terminal:
    rails generate scaffold <model_name> <column_headers>:<type>
    
    Example: 
    rails generate scaffold User first_name:string last_name:string

The Scaffold generator will create the following:
    1. Database Migration for Model Generated
    2. Controller for model generated
    3. Model
    4. All Views for the model
    5. All Testing Specs and Test helpers
    6. All Assets

Use of scaffold should be limited as it tends to create a lot of technical overhead, adding files that you may not need in your particular application.
 
 After you have confirmed that the migration is correct, migrate the database.
 
    From Terminal:
    rake db:migrate
    


