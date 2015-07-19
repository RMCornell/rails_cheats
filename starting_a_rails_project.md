# ===== Starting a Project =====

There are several ways to start a rails project.  Below outlines the different ways to start a rails project, including the options that can be selected at start up. 

## Project Start (No Options)
    From Terminal:
    rails new <project_name>
    
    Example:
    rails new running_with_scissors 

## Project Start w/ Database option
Rails new will start automatically start with a sqlite database. But you can tell rails to start with a specific database (like postgres)

    From Terminal:
    rails new <project_name> -d <database_name>
    
    Example:
    rails new running_with_scissors -d postgresql

## Project Start w/o Test Unit
Rails new will start automatically with a Unit Test framework.  But if you don't want that (generally because you want to use a different framework like Rspec or Jasmine) you can tell rails to not start with UnitTest

    From Terminal:
    rails new <project_new> --skip-unit-test
    
    Example:
    rails new running_with_scissors --skip-test-unit
    
## Project Start w/o UnitTest and Specifiying Database
To combine all the steps above in one line you can do the following
 
    From Terminal:
    rails new <project_name> . -T -d <database_name>
    
    Example:
    rails new running_with_scissors . -T -d postgresql

# ===== Adding Testing Frameworks =====
If you elect not to start with the built in UnitTest Framework you will want to add a testing framework after you have set up your project (Unless you hate TDD and like to live dangerously)

## Adding RSpec
    From Gemfile add: 
        gem 'rspec-rails'
        
    From Terminal:
        bundle install
        
    From Terminal:
        bundle exec rails generate rspec:install
        
## Adding Jasmine
    From Gemfile add:
        gem 'jasmine'
        
    From Terminal:
        bundle install
    
    From Terminal:
        rails generate jasmine:install
        
    From Terminal:
        rails generate jasmine:examples
        
## Other Set Up Considerations
If you plan to use heroku to host your app, you need to move the gem 'sqlite3' from production.  You can move it to Testing and Development and add the postgres gem becuase heroku runs off of postgres.

If you set up your application with postgres at the onset you don't need to do any of these steps:

    From Gemfile move:
        gem 'sqlite3' -> Testing/Development
        
    From Gemfile add:
        gem 'pg' -> Production
        
If you are using postgres in development and testing you will need to create the database separately before any migrations will run.

    From Terminal:
        rake db:create
        

## Conclusion
At this point most of the frameworks that are needed to start your rails app will be in place and you'll be able to start creating your app.



