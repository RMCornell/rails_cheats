# ===== Rails Testing with Capybara =====

## Capybara Initial Set Up
    -Open Gemfile and add:
        gem 'capybara'
        gem 'launchy'
    
    -From Terminal
        bundle
    
    -create and integration directory to hold integration tests
   
    -Below the "describe '<view description>", type: :feature do" line place:
        
            include Capybara::DSL
            
        -This can be moved at a later time to a <model_name>_helper_spec.rb file to limit redunancy and repetition in feature tests.
        
## Writing Capybara Tests
    -To write a capybara test, define step by step what actions the user will take on the website and what behaviors they should expect.
      
    -Can also use capybara to create tests based on what data you expect to display on a page after a particular action has been taken.
        -Focus on generated content from methods (i.e. lists, etc) not just identifying the presence of headings. 
        
    -Steps for Writing a Capybara test:
        1. visit the page you are testing
        2. Is there specific content that should be on the page? If so, verify page has_content
        3. Is there actions to be tested on the page (Forms to fill out, links to click, buttons, etc)
        4. Perform actions and assert results from actions
        5. If action will cause a page change, assert new page has_content expected when action is taken
    
    Example:
  
       it 'Displays a listing of ideas' do
          visit ideas_path
          expect(page).to have_content('Welcome')
        end
      
      Capybara Cheat-Sheet: https://gist.github.com/zhengjia/428105