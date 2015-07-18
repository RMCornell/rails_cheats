# ===== Starting a Project =====

There are several ways to start a rails project.  Below outlines the different ways to start a rails project, including the options that can be selected at start up. 

## Basic Start (No Options)
    From Terminal:
    rails new <project_name>
    
    Example:
    rails new running_with_scissors 

## Basic Start w/ Database option
Rails new will start automatically start with a sqlite database. But you can tell rails to start with a specific database (like postgres)

    From Terminal:
    rails new <project_name> -d <database_name>
    
    Example:
    rails new running_with_scissors -d postgresql
