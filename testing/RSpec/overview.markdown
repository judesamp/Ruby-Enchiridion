RSpec is a testing tool for the Ruby programming language. RSpec is designed to help programmers do Test-Driven Development (TDD). RSpec is used by many developers in the Rails community.


Basic RSpec Setup Instructions for Rails:
1. Add Gem to gemfile
2. Run 'bundle install'
3.
4.


Tips
• Be sure you close all of your 'do-end' blocks. Their lack can cause all sorts of fun confusion.


• When testing Rails controllers, the :assigns in 

expect(:assigns).to eq <whatever>

is basically equivalent to the variable @assigns in whatever action you're testing


• Test one thing at a time! Each test should have only one expect or should statement. So not this:


• Move repeated setup statements to the top of a block and make them generally available. Example: 





Balance such attempts to make the tests DRY with the need to make them readable and understandable. In other words, moving setup blocks too far away from where they're used can lead to confusion when developers are seeing the code for the first time.

5. 













Resources:
https://relishapp.com/rspec
rspec.info ()

RSpec docs: http://rspec.rubyforge.org/rspec/1.1.8/

Another intro to testing with RSpec: http://blog.teamtreehouse.com/an-introduction-to-rspec


Series on testing Rails using RSpect. A little old (2012), but good stuff: http://everydayrails.com/2012/03/12/testing-series-intro.html (a little outdate, but awesome)

Testing controllers specifically:
http://everydayrails.com/2012/04/07/testing-series-rspec-controllers.html


How Thoughtbot uses RSpec to test Rails:http://robots.thoughtbot.com/how-we-test-rails-applications 


Often associated Gems: Faker, factoryGirl, Capybara
