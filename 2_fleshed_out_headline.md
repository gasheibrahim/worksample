## Course development

# Local Environment Development Course 

## For Window:
  To create a Local Environment Development Using Window You need To download Vagrant by using this link 'https://www.vagrantup.com' about vagrant, Vagrant is a tool to manage virtual machines. Using Vagrant makes it easy to create an environment.
  And you need to download virtualbox 'https://www.virtualbox.org/' About Virtualbox, VirtualBox is software that creates a virtual machine on a computer.
  By using VirtualBox, you will be able to create another computer in your own PC.
  And you need to download gitbash 'https://git-scm.com/download/win' About gitbash, Git Bash is an application for Microsoft Windows environments which provides an emulation layer for a Git command line experience.
  After, you need to initialize vagrant inorder to create folder where you keep your project:
## mkdir vagrant
## cd vagrant
## vagrant init ubuntu/xenial64
  After, you need to config vagrantfile using any text editor you have:
  / c / Users / User PC Name / vagrant / Vagrantfile
# -# - mode: ruby -# -
# vi: set ft=ruby :
  Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/xenial64"
    config.vm.network :"forwarded_port", guest: 3000, host: 3000
    config.vm.synced_folder "~/workspace", "/home/vagrant/workspace", :create => true, mount_options: ['dmode=777','fmode=755']
    config.vm.provision "shell", privileged: false, inline: <<-SHELL
      #To update ape-get
      sudo apt-get -y upgrade
      sudo apt-get -y update
      #To install peripheral library
      sudo apt-get install git curl g++ make vim nodejs libreadline-dev libssl-dev zlib1g-dev imagemagick libmagickcore-dev libmagickwand-dev -y
      # To remove the initial installation of ruby
      sudo apt-get remove ruby -y
      git clone git://github.com/rbenv/rbenv.git /home/vagrant/.rbenv
      #rbenv initialization
      echo 'export PATH="/home/vagrant/.rbenv/bin:$PATH"' >> /home/vagrant/.profile
      echo 'eval "$(rbenv init -)"' >> /home/vagrant/.profile
      . /home/vagrant/.profile
      #To install ruby-build
      mkdir -p /home/vagrant/.rbenv/plugins
      git clone git://github.com/rbenv/ruby-build.git /home/vagrant/.rbenv/plugins/ruby-build
      #To install ruby
      # To make a version which is the same as your own。
      rbenv install 2.6.3
      rbenv global 2.6.3
      rbenv rehash
      sudo apt-get install ruby-railties -y
      #To install the bundle
      gem install bundler --no-document
      #To install postgresql
      sudo apt-get install postgresql postgresql-contrib python-psycopg2 libpq-dev -y
    SHELL
  end

## For Linux:
  The easiest way to install Ruby on your Ubuntu system is through the apt package manager. At the time of writing, the version in the Ubuntu repositories is 2.5.1 which is the latest stable version of Ruby.

  >First, update the packages index:
  sudo apt update
  >Install Ruby by typing:
  sudo apt install ruby-full
  >To verify that the installation it was successful run the following command which will print the Ruby version:
  ruby --version
  >> Installing Ruby using Rbenv 
  Rbenv is a lightweight Ruby version management tool which allows you to easily switch Ruby versions. By default Rbenv doesn’t handle installing Ruby versions so we also need to install ruby-build which is a tool that helps you to install any version of Ruby you may need. It is available as a standalone program and as a plugin for rbenv.
  
  >First, update the packages index and install the packages required for the ruby-build tool to build Ruby from source:
  1. sudo apt update
  2. sudo apt install git curl libssl-dev libreadline-dev zlib1g-dev autoconf bison build-essential libyaml-dev libreadline-dev libncurses5-dev libffi-dev libgdbm-dev
  >Next, run the following curl command to install both rbenv and ruby-build:
  curl -sL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-installer | bash -
  >Add $HOME/.rbenv/bin to the user PATH .
  if you are using Bash, run:
  $ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
  $ echo 'eval "$(rbenv init -)"' >> ~/.bashrc
  $ source ~/.bashrc
  if you are using  Zsh run:
  $ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.zshrc
  $ echo 'eval "$(rbenv init -)"' >> ~/.zshrc
  $ source ~/.zshrc
  >Install the latest stable version of Ruby and set it as a default version with:
  rbenv install version you need to install
   eg:rbenv install 2.4.0
  rbenv global version you need to install
   eg: rbenv global 2.4.0
  >After check ruby version:
  $ ruby -v

## For MAC Os:
  First you need to install Homebrew by using:
  For sierra:
  /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
  For others:
  ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
  And after installing homebrew you need to update it by using:
  $ brew upgrade
  >After you need to Install rbenv and ruby-build:
  brew install rbenv ruby-build
  >Install a Ruby version:
  rbenv install Version of ruby you need to install
    eg: rbenv install 2.4.0
  >Set the global Ruby version
  rbenv global Version of ruby you need to install
    eg: rbenv global 2.4.0
  >check your Ruby Version:
    ruby -v

## Git / Github Course

# Introduction
  Git is an Open Source Distributed Version Control System. ... So Git can be used to store content — it is mostly used to store code due to the other features it provides. Version Control System: The code which is stored in Git keeps changing as more code is added. Also, many developers can add code in parallel.
  GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere. This tutorial teaches you GitHub essentials like repositories, branches, commits, and Pull Requests.
# repository
  When creating a new project on your local machine using git, you'll first create a new repository (or often, 'repo', for short). To use git we'll be using the terminal.
# Branch
  Now that you've made a new commit, let's try something a little more advanced.
# Some Git Commands
# git init for Initialize a local Git repository
# git clone ssh://git@github.com/[username]/[repository-name].git for Create a local copy of a remote repository
# git status for Check status
# git add [file-name.txt] for Add a file to the staging area
# git add -A for Add all new and changed files to the staging area
# git commit -m "[commit message]" for Commit changes
# git rm -r [file-name.txt] for Remove a file (or folder)
# git branch for List branches (the asterisk denotes the current branch)
# git branch -a for List all branches (local and remote)
# git branch [branch name] for Create a new branch
# git branch -d [branch name] for Delete a branch
# git push origin --delete [branch name] for Delete a remote branch
# git checkout -b [branch name] for Create a new branch and switch to it
# git stash for Stash changes in a dirty working directory
# git stash clear for Remove all stashed entries
# git push origin [branch name] for Push a branch to your remote repository
# git push -u origin [branch name] for Push changes to remote repository (and remember the branch)
# git push for Push changes to remote repository (remembered branch)
# git push origin --delete [branch name] for Delete a remote branch
# git pull for Update local repository to the newest commit
# git remote add origin ssh://git@github.com/[username]/[repository-name].git for Add a remote repository
# git remote set-url origin ssh://git@github.com/[username]/[repository-name].git for Set a repository's origin branch to SSH

## HTML Course
# HTML Introduction
    HTML is the standard markup language for creating Web pages.
# What is HTML??
    HTML stands for Hyper Text Markup Language
    HTML is the standard markup language for creating Web pages
    HTML describes the structure of a Web page
    HTML consists of a series of elements
# What is tag??
    The <html> tag represents the root of an HTML document.
    The <html> tag is the container for all other HTML elements (except for the <!DOCTYPE> tag).
# What is types of tag?
# there are two types of tag which are:
      1.Paired Tag: A paired tag consist of two tags, first one is called an opening tag and the second one is called a closing tag. These tags contains the text in between at which the effect of that tag will be applied.
        Example: <div> </div>
      2.An Unpaired tag is a single tag which does not need a companion tag.
      These tags can be written like < > or < /> both works as same, it’s your choice which style you choose.
        Example: <br> or <br />
# What is browser??
    A web browser is a software application for accessing information on the World Wide Web. When a user requests a web page from a particular website, the web browser retrieves the necessary content from a web server and then displays the page on the user's device.
# Difference Between Website and Webpage
    A webpage is an independent part of a website that contains the links to other web pages on the website. On the other hand, a website is a collection of relevant web pages that is addressed to a Uniform Resource Locator.
# Where did HTML come from? 
    1989: Tim Berners-Lee invents the Web with HTML as its publishing language. The World Wide Web began life in the place where you would least expect it: at CERN, the European Laboratory for Particle Physics in Geneva, Switzerland.
# What is HTML Syntax
    Syntax is the arrangement of elements and attributes to create well-formed documents. ... In HTML, this is the purpose of elements and attributes, and the logical (sense and reference) relationship between elements and the attributes of those elements.

## CSS Course
# CSS Introduction
    CSS stands for Cascading Style Sheets
    CSS describes how HTML elements are to be displayed on screen, paper, or in other media
    CSS saves a lot of work. It can control the layout of multiple web pages all at once
    External stylesheets are stored in CSS files
# Syntax Of Css
    A CSS rule-set consists of a selector and a declaration block:
      Selector { property: Value }
      Example: 
      p {
        color: red;
        text-align: center;
      }
# CSS Properties
    Examples:
      background
      background-image
      font-family
      font-size
      padding
      margin
      text-align
# CSS Box Models
    The CSS box model is essentially a box that wraps around every HTML element. It consists of: margins, borders, padding, and the actual content. 
      Example: div {
        width: 300px;
        border: 15px solid green;
        padding: 50px;
        margin: 20px;
      }
# CSS Positioning
    The position property specifies the type of positioning method used for an element (static, relative, fixed, absolute or sticky).
      Example:div.static {
        position: static;
        border: 3px solid #73AD21;
      }
# CSS Responsive Design
    Responsive web design makes your web page look good on all devices.
    Responsive web design uses only HTML and CSS.
    Responsive web design is not a program or a JavaScript.
# CSS Layout
    A website is often divided into headers, menus, content and a footer.
# CSS Display Property
    The display CSS property groups whether an element is treated as a block or inline element and the layout used for its children, such as flow layout, grid or flex. Formally, the display property groups an element's inner and outer display types.
      Examples:
      .div {
      display:  [ <display-outside> | <display-inside> ] | <display-listitem> | <display-internal> | <display-box> | <display-legacy> ;
      }

## JS Course
# JS Introductions
    JavaScript was invented by Brendan Eich in 1995, and became an ECMA standard in 1997.
    ECMA-262 is the official name of the standard. ECMAScript is the official name of the language.
    JavaScript is a lightweight, cross-platform and interpreted scripting language. It is well-known for the development of web pages, many non-browser environments also use it. JavaScript can be used for Client-side developments as well as Server-side developments.
# Difference Between Variable And Constant
    var declarations are globally scoped or function scoped while let and const are block scoped. var variables can be updated and re-declared within its scope; let variables can be updated but not re-declared; const variables can neither be updated nor re-declared. They are all hoisted to the top of their scope.
# JS Operations
    JavaScript includes operators that perform some operation on single or multiple operands (data value) and produce a result. JavaScript includes various categories of operators: Arithmetic operators, Comparison operators, Logical operators, Assignment operators, Conditional operators.
# JS Conditions 
    In JavaScript we have the following conditional statements: Use if to specify a block of code to be executed, if a specified condition is true. Use else to specify a block of code to be executed, if the same condition is false. Use else if to specify a new condition to test, if the first condition is false.
      # Syntax# 
      if (condition) {
        //  block of code to be executed if the condition is true
      }
      # Example# 
      if (hour < 18) {
        greeting = "Good day";
      }
# JS Loop
    JavaScript loops are used to repeatedly run a block of code - until a certain condition is met. When developers talk about iteration or iterating over, say, an array, it is the same as looping. JavaScript offers several options to repeatedly run a block of code, including while, do while, for and for-in.
    Loops are handy, if you want to run the same code over and over again, each time with a different value.
# JS Array
    JavaScript arrays are used to store multiple values in a single variable.
    Arrays are list-like objects whose prototype has methods to perform traversal and mutation operations. Neither the length of a JavaScript array nor the types of its elements are fixed.
    # Example# 
    let fruits = ['Apple', 'Banana']
    console.log(fruits.length)
# Js Event
    JavaScript's interaction with HTML is handled through events that occur when the user or the browser manipulates a page. When the page loads, it is called an event. When the user clicks a button, that click too is an event. Other examples include events like pressing any key, closing a window, resizing a window, etc.
    # Example# 
    <button onclick="document.getElementById('demo').innerHTML = Date()">The time is?</button>
# JS DOM Manipulation
    The Document Object Model (DOM) is a programming interface for HTML and XML documents. ... The Document Object Model (DOM) represents that same document so it can be manipulated. The DOM is an object-oriented representation of the web page, which can be modified with a scripting language such as JavaScript.

## Ruby Course
# Introduction to Ruby
    Ruby is an object-oriented programming language developed by Yukihiro Matsumoto. Ruby is a dynamic programming language with a complex but at the same time expressive grammar. Ruby also has a core class library with a rich and powerful API.

    Ruby is inspired by other low level and object oriented programming languages like Lisp, Smalltalk, and Perl and uses syntax that is easy for C and Java programmers to learn.

    Ruby, a dynamic and open source programming language with a focus on simplicity and productivity, has an elegant syntax that is natural to read and easy to write.

    Although it's easy to program in Ruby, it is not a simple language.
# Ruby Functions
    Variable Number of Parameters: Ruby allows the programmer to define a method that can take the variable number of arguments. It is useful when the user doesn't know the number of parameters to be passed while defining the method. Return statement in Methods: Return statement used to returns one or more values.
      # Syntax# 
        def functionname(variable)
          return <value>
        end
      # Example# 
        def say_hello(name)
          var = “Hello, ” + name
          return var
        end
# Ruby Algorithm and data structure
    Using the right data structure or algorithm for the situation is an important aspect of programming. In computer science literature, many data structures and algorithms have been researched and extensively documented. However, there is still no standard library in Ruby implementing useful structures and algorithms like Red/Black Trees, tries, different sorting algorithms, etc. This project will create such a library with documentation on when to use a particular structure/algorithm. It will also come with a benchmark suite to compare performance in different situations.
# OOP In Ruby
    Object-oriented design is the process of planning a system of interacting objects for the purpose of solving a software problem. It is one approach to software design.
    Object-oriented design has been created to solve problems that have arisen as the scale of development increases.
# Ruby Conditions
# Syntax
    if conditional [then]
      code...
    [elsif conditional [then]
      code...]...
    [else
      code...]
    end
# Ruby Loop
    Looping in programming languages is a feature which clears the way for the execution of a set of instructions or functions repeatedly when some of the condition evaluates to true or false. Ruby provides the different types of loop to handle the condition based situation in the program to make the programmers task simpler. The loops in Ruby are :
# while loop
        Syntax:
        while conditional [do]
          # code to be executed
        end
# for loop
        Syntax:
        for variable_name[, variable...] in expression [do]
          # code to be executed
        end
# do..while loop
        Syntax:
        loop do
          # code to be executed
        break if Boolean_Expression
        end
# until loop
        until conditional [do]
          # code to be executed
        end
# Ruby Array
    Ruby arrays are ordered, integer-indexed collections of any object. ... Ruby arrays can hold objects such as String, Integer, Fixnum, Hash, Symbol, even other Array objects. Ruby arrays are not as rigid as arrays in other languages. Ruby arrays grow automatically while adding elements to them.
      # Example:#  sharks = ["Hammerhead", "Great White", "Tiger"]
  
## Ruby On Rails Course
# Introduction To Rails
    Rails is a web application development framework written in the Ruby programming language. It is designed to make programming web applications easier by making assumptions about what every developer needs to get started. It allows you to write less code while accomplishing more than many other languages and frameworks. Experienced Rails developers also report that it makes web application development more fun.
# MVC In Rails 
    MVC is a pattern for the architecture of a software application. It separates an application into the following components:
      # Models#  for handling data and business logic
      # Controllers#  for handling the user interface and application
      # Views#  for handling graphical user interface objects and presentation
# Scaffolding
    Scaffolding in Ruby on Rails refers to the auto-generation of a set of a model, views, and a controller usually used for a single database table. It's way easier to do this, instead of coding everything yourself, it saves you a lot of time!
      # Example# 
        rails generate scaffold User name:string email:string
# Devise 
    Devise is the cornerstone gem for Ruby on Rails authentication. With Devise, creating a User that can log in and out of your application is so simple because Devise takes care of all the controllers necessary for user creation ( users_controller ) and for user sessions ( users_sessions_controller ).
      # Also you can refer to 'https://github.com/heartcombo/devise' to generate devise and used# 
# Postgresql
    prepare PostgreSQL for rails development. Ruby on Rails supports many databases such as MySQL, SQLite (Default) and PostgreSQL. We will use PostgreSQL as the database for this guide.
    Install PostgreSQL and some other required packages with the apt command:
# $ apt-get -y install postgresql postgresql-contrib libpq-dev
    When the installation is done, login to the postgres user and access the postgresql shell.
# su - postgres
# psql
    Give the postgres user a new password with command below:
# \password postgres
      Enter New Password:
    Next, create a new role named 'rails-dev' for the rails development with the command below:
# create role rails_dev with createdb login password 'aqwe123';
    Set a new password for the user and check that the user has been created.

    Now check the new role and you will see new role has been created:
      $ \du
# Rails Migrations
    Migrations are a feature of Active Record that allows you to evolve your database schema over time. Rather than write schema modifications in pure SQL, migrations allow you to use a Ruby DSL to describe changes to your tables. After reading this guide, you will know: The generators you can use to create them.
# Example
    rails generate migration AddPartNumberToProducts
# Active Record 
    Rails Active Records provide an interface and binding between the tables in a relational database and the Ruby program code that manipulates database records. ... Each Active Record object has CRUD (Create, Read, Update, and Delete) methods for database access.
    Active Record is the M in MVC - the model - which is the layer of the system responsible for representing business data and logic. Active Record facilitates the creation and use of business objects whose data requires persistent storage to a database. It is an implementation of the Active Record pattern which itself is a description of an Object Relational Mapping system.
# Deploying on Heroku
    First of all you need to install heroku in your environment, To install heroku in your environment please refer to '# https://devcenter.heroku.com/articles/heroku-cli# '
    And also here are some commands of Deploying project on heroku:
# Heroku login
# git add -A
# git commit -m "init"
# Heroku create
# git push heroku master
# heroku run rake db:migrate
# heroku config
# Security In rails
    Open-source software development frameworks, such as Ruby on Rails, are considered highly secure, and this is often quite true. Rails (particularly its latest versions, starting from 4.0) offers a number of built-in tools for fending off the vast majority of threats.
# Association
    an association is a connection between two Active Record models. Why do we need associations between models? Because they make common operations simpler and easier in your code. For example, consider a simple Rails application that includes a model for authors and a model for books. Each author can have many books. Without associations, the model declarations would look like this:
# Example
      class Author < ApplicationRecord
      end
      class Book < ApplicationRecord
      end
# Error Page
    Normally, 404 and 500 error pages are static HTML files that live in the public directory of a Rails application. These are boring, minimally-styled pages that don't get the same treatment as the rest of the app.
    Also you can refer to 'https://mattbrictson.com/dynamic-rails-error-pages'
# Rails Action mailer
    Action Mailer allows you to send emails from your application using mailer classes and views.
    Also you can refer to 'https://guides.rubyonrails.org/action_mailer_basics.html'
# Image Uploader
    If you are building a web application, you definitely will want to enable image uploading. Image uploading is an important feature in modern-day applications, and images have been known to be useful in search engine optimization.

    In this tutorial (which is the first part of the Rails Image Uploading series), I will show you how to enable image uploading in your Rails application using CarrierWave. It will be a simple application as the focus is on the image uploading.

    CarrierWave is a Ruby gem that provides a simple and extremely flexible way to upload files from Ruby applications.

    Also You can Refer to 'https://code.tutsplus.com/tutorials/rails-image-upload-using-carrierwave-in-a-rails-app--cms-25183' to make it

## conclusion

Thank you for taking the time to study this course. In this lesson, I’ll review some useful resources for your continued learning about Rails.

# Thank you for your time# !!!