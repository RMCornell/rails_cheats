# ===== Rails Testing with Rspec =====

    -Before testing with Rspec make sure it has been installed and set up as noted above.
    
    -Rspec files end with _spec.rb, not _test.rb as with MiniTest or UnitTest
     
    -Spec File will contain the following:
        -controllers
        -features
        -helpers
        -models
        -rails_helper.rb
        -spec_helper.rb
    
    -Some of these directories will be present when you generate elements of rails application.  Others(features) you'll have to create on your own. 
    
## RSpec Setting Up Testing

    -let command will allow you to set up tests (attribute setting, etc).  Similar to Setup in MiniTest
    
    -Example:
           let(:idea) {Idea.create(name: "Nano Ninjas", description: "What it sounds like!")}
           -parameters for .create should be the table attributes and written to be a valid row (includes all) required elements.
           
## RSpec Writing Tests

    -tests are similar to the capybara tests but the assertions will be different
    
    Example: 
    
        it 'is valid' do
            expect(idea).to be_valid
          end
        
          it 'is invalid without a name' do
            idea.name = nil
            expect(idea).not_to be_valid
          end
        
          it 'is invalid without a description' do
            idea.description = nil
            expect(idea).not_to be_valid
          end
          
    -To run tests From Terminal
        rake spec