# Manual

## Step1

__shell__
Create Rails App
~~~shell
docker-compose run web rails new . --force --database=mysql --skip-bundle
~~~

## Step2
__Gemfile__
Add webpacker
~~~ruby
gem 'webpacker'
~~~

## Step3
__shell__
Install Vue
~~~shell
docker-compose run web bundle update
docker-compose build
docker-compose run web rails webpacker:install
docker-compose run web rails webpakcer:install:vue
~~~

## Step4
__database.yml__
Setting Database
~~~yml
default: &default
    adapter: mysql2
    encoding: utf8
    username: root
    password: password
    host: db
    pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
~~~

## Step5
__shell__
Create Database
~~~shell
docker-compose run web rails db:create
~~~

## Step6
__shell__
Start server
~~~shell
docker-compose up -d
~~~