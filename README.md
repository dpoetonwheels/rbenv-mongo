rbenv
===========

Steps for setting up ruby environment using rbenv.

# Setup a ruby environment using rbenv

* * *

## Requirements

a. Apple ID and Github account (you can signup at the following - [Source](https://github.com/signup). )

b. Command Line Tools (through Xcode).
   
- If you are on a Mac OS older than Mountain Lion, and Lion then download 
  the sepcific xcode from [Source](https://developer.apple.com/xcode/)

c. Homebrew (The "Install Homebrew" section at the following URL - [Source](http://mxcl.github.io/homebrew/) is all you need)

For a detailed reference of all the steps till Step 5 please look at the following:
[Source](http://www.moncefbelyamani.com/how-to-install-xcode-homebrew-git-rvm-ruby-on-mac/)
* * *

## Installation Steps

Step 1. Install rbenv using the following commands
  
  ~~~ sh
  $ brew update
  $ brew install rbenv
  ~~~

Step 2. Configure rbenv using the following:

  a) Add ~/.rbenv/bin to your $PATH for access to the rbenv command-line utility.
  
  ~~~ sh
  $ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
  ~~~

  b) Add rbenv init to your shell to enable shims and autocompletion.
  ~~~ sh
  $ echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
  ~~~
  
Step 3. Install ruby-build using the following command

  ~~~ sh
  $ brew install ruby-build
  ~~~
  
Step 4. Select the ruby version from ruby-build using the following commands:
  
  a) The following command would list out all the ruby definitions to be selected by rbenv
  
  ~~~ sh
  $ ruby-build --definitions
  ~~~
  
  For example,
  ~~~ sh
      1.8.7-p352
      1.9.2-p290
      1.9.3-p327
      2.0.0-p0
      jruby-1.7.1
      rbx-1.2.4
      ree-1.8.7-2011.03
   ~~~
   
  b) Select the ruby version you need through rbenv as follows:
  
  ~~~ sh
  $ rbenv install 2.0.0-p0
  ~~~
  
Step 5. Rebuild the shim executables. You should do this any time you
   install a new Ruby executable (for example, when installing a new
   Ruby version, or when installing a gem that provides a command).

   ~~~ sh
   $ rbenv rehash
   ~~~

Step 6. If you want to take a look at which ruby versions you currently have, do the following: 

   ~~~ sh
   $ rbenv versions
   ~~~

You might see something as follows:

$ rbenv versions
  system
  1.9.3-p194
* 2.0.0-p0 (set by /Users/devang.desai/.ruby-version)
   
The * indicates your current ruby version. You can also update it as follows:

   ~~~ sh
   $ rbenv local 1.9.3-p194
   ~~~

* * *

# Setup mongodb using existing rbenv ruby environment.
### Steps to add mongodb and related gems to your application

* * *

## Requirements

1. rbenv and ruby environment as shown above.

2. rubygems and rails. If not available using rbenv then do the following to get rubygems and rails:
   
   ~~~ sh
   $ gem update --system
   $ gem install rails
   ~~~

## Installation Steps

If you are using brew or macports the following URL would be helpful:

[Source](http://docs.mongodb.org/manual/tutorial/install-mongodb-on-os-x/)

Step 1. Type the following commands in a terminal to install mongodb

   ~~~ sh
   $ brew update
   $ brew install mongodb
   ~~~

* * *
### Additional Note:

 If you need a specific mongodb version or you want to switch between mongodb versions do the following:
 
 a) You can verify which mongodb versions are available for you to swtich to using the following command:
 
   ~~~ sh
   $ brew versions mongodb
   ~~~
   
   You should see something as follows:
   ~~~ sh
2.4.1-x86_64 git checkout 74062f3 /usr/local/Library/Formula/mongodb.rb
2.4.0-x86_64 git checkout 4e36c7c /usr/local/Library/Formula/mongodb.rb
2.2.3-x86_64 git checkout 527611d /usr/local/Library/Formula/mongodb.rb
2.2.2-x86_64 git checkout fe5bc4d /usr/local/Library/Formula/mongodb.rb
2.2.1-x86_64 git checkout 5825f62 /usr/local/Library/Formula/mongodb.rb
2.2.0-x86_64 git checkout 9348b10 /usr/local/Library/Formula/mongodb.rb
2.0.7-x86_64 git checkout 6434ebb /usr/local/Library/Formula/mongodb.rb
2.0.6-x86_64 git checkout 2553479 /usr/local/Library/Formula/mongodb.rb
2.0.5-x86_64 git checkout c6d3538 /usr/local/Library/Formula/mongodb.rb
2.0.4-x86_64 git checkout 3231798 /usr/local/Library/Formula/mongodb.rb
2.0.3-x86_64 git checkout aaa3b21 /usr/local/Library/Formula/mongodb.rb
2.0.2-x86_64 git checkout dfcc838 /usr/local/Library/Formula/mongodb.rb
2.0.1-x86_64 git checkout e50a75a /usr/local/Library/Formula/mongodb.rb
2.0.0-x86_64 git checkout 72cb073 /usr/local/Library/Formula/mongodb.rb
...
   ~~~
   
 b) Pick one you want and get the following script
 [Source](https://gist.github.com/dpoetonwheels/5359742) 
 
 c) You might have to chown to run the script and give it permissions. Once, done run the following command:
   ~~~ sh
   $ ./brewv mongodb 2.4.0                      # selected mongodb version 2.4.0
   ~~~
   
   You should see something as follows and the switch would happen from 2.4.1 to 2.4.0
   
   ~~~ sh
   ==> Downloading http://fastdl.mongodb.org/osx/mongodb-osx-x86_64-2.4.0.tgz
######################################################################## 100.0%
==> Caveats
To have launchd start mongodb at login:
    ln -sfv /usr/local/opt/mongodb/*.plist ~/Library/LaunchAgents
Then to load mongodb now:
    launchctl load ~/Library/LaunchAgents/homebrew.mxcl.mongodb.plist
Or, if you don't want/need launchctl, you can just run:
    mongod
==> Summary
🍺  /usr/local/Cellar/mongodb/2.4.0-x86_64: 21 files, 314M, built in 51 seconds
Unstaged changes after reset:
M   Library/Formula/mongodb.rb
mongodb 2.4.0 installed.
You can now switch versions with 'brew switch mongodb <version>'
~~~

* * *

Step 2. Verify that you have mongodb instance using the following command:

   ~~~ sh
   $ mongod
   ~~~   

Step 3. Create a rails app without active record and start using mongodb instead in your Gemfile

   ~~~ sh
   $ rails new YOUR_APP_NAME --skip-active-record
   ~~~

Step 4. Use a mongodb rails gem in your Gemfile 

Once the new application is created you can choose from one of the several mongodb rails gems out there 
as mongo_mapper, mongoid, mongodoc, etc.

We would use mongoid as follows:

Add the following to your Gemfile:
(Mongoid requires bson_ext)

   ~~~ sh
   # ODM
   gem "mongoid", ">= 3.0.3"
   gem 'bson_ext', '~> 1.8.3'
   
   # For Test Frameworks (BDD, TDD)
   gem "mongoid-rspec", ">= 1.4.6", :group => :test
   ~~~   

Step 5. Do a bundle update as follows:

   ~~~ sh
   $ bundle update
   ~~~   

Step 6. Create a default mongoid.yml for mongodb configuration.

Once you have the required gems, you can create a sample mongoid.yml under YOUR_APP_NAME/config folder or 
let Rails create one for you using the following command:

   ~~~ sh
   $ rails g mongoid:config
   ~~~   

The above would generate something as follows:

   ~~~ sh
   development:
      database: YOUR_APP_NAME_development
      hosts:
        - localhost:27017
   
   test:
      database: YOUR_APP_NAME_test
      hosts:
        - localhost:27017
   
# set these environment variables on your prod server
production:
  host: <%= ENV['MONGOID_HOST'] %>
  port: <%= ENV['MONGOID_PORT'] %>
  username: <%= ENV['MONGOID_USERNAME'] %>
  password: <%= ENV['MONGOID_PASSWORD'] %>
  database: <%= ENV['MONGOID_DATABASE'] %>
  # slaves:
  #   - host: slave1.local
  #     port: 27018
  #   - host: slave2.local
  #     port: 27019

   ~~~   

Please make sure you have a default sessions which was not generated using "rails g mongoid:config". Your new mongoid.yml
file should look like the following:

~~~ sh
development:
  sessions:
    default:
      database: YOUR_APP_NAME_development
      hosts:
        - localhost:27017
   
test:
 sessions:
    default:
      database: YOUR_APP_NAME_test
      hosts:
        - localhost:27017

# set these environment variables on your prod server
production:
  host: <%= ENV['MONGOID_HOST'] %>
  port: <%= ENV['MONGOID_PORT'] %>
  username: <%= ENV['MONGOID_USERNAME'] %>
  password: <%= ENV['MONGOID_PASSWORD'] %>
  database: <%= ENV['MONGOID_DATABASE'] %>
  # slaves:
  #   - host: slave1.local
  #     port: 27018
  #   - host: slave2.local
  #     port: 27019

   ~~~   

Now, you are all set to use the mongoid gem. Have a mongod instance running and you can verify connecting to it
using the following command

   ~~~ sh
   $ mongo
   ~~~   
   
For a detailed mongoid configuration you can refer to the following 2 URL's:

[Source](http://mongoid.org/en/mongoid/docs/installation.html)
[Source](http://docs.mongodb.org/manual/tutorial/install-mongodb-on-os-x/)
