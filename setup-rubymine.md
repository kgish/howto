# How to setup a project (my_project) using RubyMine

(rails only) = only needed for Rails projects.

Define a gemset for the project:

    $ rvm use 1.9.3-p448@my_project --create

or

    $ rvm use 2.0.0-p247@my_project --create

Install rails (rails only):

    $ gem install rails -v 3.2.8

or

    $ gem install rails -v 4.0.1

Create the project directory:

    $ rails new my_project (rails only)

or

    $ mkdir my_project

Add the .rvmrc file:

    $ cd my_project
    $ rvm --rvmrc ruby-1.9.3-p448@my_project
    $ rvm rvmrc trust `pwd`
    $ rvm rvmrc warning ignore  `pwd`/.rvmrc

Start Rubymine in project directory:

    $ mine .
    (ignore git warnings)

Ruby SDK and Gems:

    File > Settings ... > Ruby SDK and Gems
    Ruby SDK = 'RVM: ruby-1.9.3-p448[my_project]'

Modify Gemfile (rails only):
    
    $ cat Gemfile (ruby 1.9.3)
    source 'https://rubygems.org'

    gem 'rails', '3.2.8'

    group :development do
      gem 'sqlite3', '1.3.5'
    end

    # Gems used only for assets and not required
    # in production environments by default.
    group :assets do
      gem 'sass-rails',   '3.2.5'
      gem 'coffee-rails', '3.2.2'

      gem 'uglifier', '1.2.3'
    end

    gem 'jquery-rails', '2.0.2'
    <EOF>

or

    $ cat Gemfile (ruby 2.0.0)
    source 'https://rubygems.org'
    ruby '2.0.0'
    #ruby-gemset=railstutorial_rails_4_0

    gem 'rails', '4.0.1'

    group :development do
      gem 'sqlite3', '1.3.8'
    end

    gem 'sass-rails', '4.0.1'
    gem 'uglifier', '2.1.1'
    gem 'coffee-rails', '4.0.1'
    gem 'jquery-rails', '3.0.4'
    gem 'turbolinks', '1.1.1'
    gem 'jbuilder', '1.0.2'

    group :doc do
      gem 'sdoc', '0.3.20', require: false
    end

Run bundler (rails only)

    $ bundle install --without production
    $ bundle update
    $ bundle install

or

    Tools > Bundler > Install

Setup git repository:

    $ git init

or

    VCS > Import into Version Control > Create Git Repository
    Select my_project directory
    OK
    Answer Yes

Create the .gitignore file:

    $ cat .gitignore
    # Ignore bundler config.
    /.bundle

    # Ignore the default SQLite database.
    /db/*.sqlite3
    /db/*.sqlite3-journal

    # Ignore all logfiles and tempfiles.
    /log/*.log
    /tmp

    # Ignore other unneeded files.
    database.yml
    doc/
    *.swp
    *~
    .project
    .DS_Store
    .idea
    .secret 
    <EOF>

Commit initial version:

    $ touch README.md # see README.rdoc
    $ git add .
    $ git commit -m "Initial commit"

or

    Create README.md file
    Select files to add to repository in Project pane 
    VCS > Git > Add
    Select files from Changes pane to commit
    Right click > Commit Changes...
    Add comment then OK

Create GitHub repositoy

    Go to https://github.com/kgish
    Create a new repo (top right of kgish)
    Fill in: Repository name (my_project) and description
    Leave 'Initialize this repository with a README' unchecked
    
    $ git remote add origin https://github.com/kgish/my_project.git
    $ git push -u origin master

Start Rubymine:

    $ mine .
