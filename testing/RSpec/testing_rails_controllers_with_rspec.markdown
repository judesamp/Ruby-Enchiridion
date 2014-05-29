## Rspec
RSpec is a testing tool for the Ruby programming language. RSpec is designed to help programmers do Test-Driven Development (TDD). RSpec is a commonly used testing tool in the Rails community.

### Testing Rails Controllers with RSpec

#### Basic RSpec Setup Instructions for Rails
1. Add Gem to gemfile (in both developement and test groups)
```
group :development, :test do
  gem 'rspec-rails', '~> 3.0.0.beta'
end
```
2. Run 'bundle install'
3. Initialize spec directory by running 'rails generate rspec:install' --- this will create a spec directory and put a spec_helper.rb file inside of it. This spec helper file contains setup and configuration for rspec.
4. In the file where you'll be writing tests (users_controller_spec.rb, for instance), type "require 'spec_helper'" at the top of the file.
5. Now you're ready to start writing tests. (See tips or resources for more detailed setup info.)
6. Runs the tests with 'rake spec.' This will run all the tests in the spec directory. To run more specific tests, drill down with something like 'rake spec/controllers/users_controller_spec.rb' You can also use 'rspec' in place of the rake command.


#### Tips
• Be sure you close all of your 'do-end' blocks. Their lack can cause all sorts of fun confusion.


• When testing Rails controllers, the :assigns in 

```
expect(assigns(:events)).to eq <value>
```

is basically equivalent to the variable @events in whatever action you're testing

• Test one thing at a time! Each test should have only one expect or should statement.

• Move repeated setup statements to the top of a block and make them generally available. Here is an example (notice the let statement at the top, making a user available during each of the tests nested within this block): 

```
describe EventsController do
  
  let(:user) { FactoryGirl.create(:user) }

  describe "GET #index" do

    it "assigns collection of events" do
      login(user)
      event = FactoryGirl.create(:event)
      current_user.events << event
      get :index
      expect(assigns(:events)).to eq [event]
    end

    it "renders the index page" do
      login(user)
      get :index
      response.should render_template :index
    end

  end

end
```

Balance such attempts to make the tests DRY with the need to make them readable and understandable. In other words, moving setup blocks too far away from where they're used can lead to confusion when developers are seeing the code for the first time.

• Inside the spec directory, create a controllers folder where you can place your controller tests and a models folder where you can test your models. A spec directory might have the following structure:

```
-spec
  - controllers
    users_controller_spec.rb
  - factories
    user.rb
  - fixtures
  - models
    user_spec.rb
  - support
    devise_support.rb
  spec_helper.rb
```


#### Resources:
• [A great link](https://relishapp.com/rspec) for rspec examples. The official spot for RSpec documentation.

• [A link](http://rspec.info) with a quick intro to RSpec. Includes info on the RSpec book.

• Another intro to [testing with RSpec](http://blog.teamtreehouse.com/an-introduction-to-rspec).

• [Series on testing Rails](http://everydayrails.com/2012/03/12/testing-series-intro.html) using RSpec. A little outdated (2012), but good stuff. 

• [Testing controllers](http://everydayrails.com/2012/04/07/testing-series-rspec-controllers.html).

• [How Thoughtbot uses RSpec](http://robots.thoughtbot.com/how-we-test-rails-applications) to test Rails.


#### Often Associated Gems
+ Faker
+ factoryGirl
+ Capybara
+ Guard


