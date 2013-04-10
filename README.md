rbenv-mongo
===========

Steps for setting up ruby environment using rbenv and using mongo.

# Setup a ruby environment using rbenv
### Steps to create a ruby environment using rbenv and then adding mongodb related gems

* * *

## Requirements

1. Apple ID and Github account (you can signup at the following - [Source](https://github.com/signup). )

2. Command Line Tools (through Xcode).
   - If you are on a Mac OS older than Mountain Lion, and Lion then download the sepcific xcode from [Source](https://developer.apple.com/xcode/)
   
3. Homebrew (The "Install Homebrew" section at the following URL - [Source](http://mxcl.github.io/homebrew/) is all you need)

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
  
1.8.6-p420
...
1.8.7-p358
...
1.9.2-p320
...
1.9.3-dev
...
2.0.0-dev
2.0.0-p0
...
jruby-1.5.6
...

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
