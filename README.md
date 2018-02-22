# jumpstart
The jumpstart project is a template for quickly getting a ruby on rails and 
reactjs project started that uses webpacker and bootstrap.

# Installing software
## Software Versions
rbenv
node      - 9.3.0
npm       - 5.6.0
ruby      - 2.4.3
rails     - 5.1.5
sqlite3   - 
## Dependencies
homebrew  - Macos package manager
rbenv     - Managing ruby versions 
node      - NodeJS
npm       - Node package manager for managing JavaScipt packages
overmind  - Process manager that I can run multiple processes

### homebrew

### rbenv
Rbenv is a ruby version manager that can be used to set the version of ruby
running for an application. The following is cheetsheet of useful commands

** List of rbenv commands **
```bash
mac: rbenv commands
```

** List of installed ruby versions **
```bash
mac: rbenv versions
```

** Current version of ruby in working directory **
```bash
mac: rbenv version
```

** Set the local version of ruby **
```bash
mac: rbenv local <version>
```

** Set the global version of ruby **
```bash
mac: rbenv global <version>
```

** List of all ruby versions that can be installed **
```bash
mac: rbenv install --list
```

** Install a specific version of ruby **
```bash
mac: rbenv install <version>
```

** Set version of ruby for a project **
```bash
mac: cd ${project_dir_}
mac: vi ./.ruby-version       # Set the file to the ruby version
mac: rbenv rehash             # Resets the ruby version
```

### NodeJS
### npm
### Overmind
#### Installation
```bash
mac: brew install tmux        # on macOS (with homebrew)
mac: brew install overmind
```

#### Usage
Add a Procfile to the project directory and use overmind to start the project.
```bash
mac: cd ${project_dir}
```

Create the ```Procfile``` in the project file with the following content:
```bash
server: bin/rails server
assets: bin/webpack-dev-server
```

Start the rails and webpack servers
```bash
mac: overmind start
```

## Github
Create the project on github and clone into the jumpstart directory

## Ruby on Rails
The following sections will go through the setup of Ruby on Rails with Reactjs
using the webpacker gem. For the first version of the template we will use
webpacker for JavaScript files and sprockets for CSS and Images.

```bash
mac: cd ${wdir}/jumpstart
mac: gem install bundler
mac: gem install rails
mac: cd ..
mac: rails new jumpstart --skip-coffee --skip-turbolinks --webpack=react -T
mac: bundle install
mac: bundle binstubs bundler --force    # regenerate the binstubs
```

Now verify that rails and webpacker is up and running
```bash
mac: overmind start   # Starts bin/rails and bin/webpack-dev-server
```

Go to **http://localhost:5000** and you should get the "Yay! You're on rails" 
page

### Other Gems
haml
better_errors
annotate

### Smoke Test
Create a simple controller and view and verify that will be used for verifying
my setup.

```
mac: bin/rails g controller pages home
```

```
# config/routes.rb
Rails.application.routes.draw do
  root to: "pages#home"
end
```

## Setup Bootstrap SASS/CSS
First, I'm going to setup the sass/css styling of the jumpstart app using 
bootstrap 4.0.0 to verify that it is installed and configured correctly. 

**NOTE:** Later I will setup the JavaScript components

1. Install the gem in the Gemfile and run bundle install
2. Rename the application.css to application.scss
3. Remove all the content from the application.scss as the '* require' is used for
   loading css and not scss files.
4. Create global.scss and bootstrap_and_overrides.sccs files and import them in the
   application.scss
5. Restart the rails server
5. Add a custom css class in the pages#home and verify everything is working.

## Setup Testing
**CREATE SEPARATE SECTION FOR TESTING**
### Rspec

**NOTE:** 
I used the -T option so testing is not installed with the project, I will install
rspec and capybara next for testing.

Add ```rspec-rails``` to both the ```:development``` and ```:test``` groups in the Gemfile:

```
group :development, :test do
  gem 'rspec-rails', '~> 3.7'
end
```

Download, install, and initialize Rspec

```
mac: bundle install
mac: bin/rails generate rspec:install
```

### Capybara
**NOTE:**
I WILL ADD CAPYBARA LATER IN THE PROCESS


