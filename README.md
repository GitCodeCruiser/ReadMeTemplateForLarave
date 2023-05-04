# Chirrrp

A brief description of what this project does and who it's for

> ### Chirrrp Laravel codebase

This repo is functionality complete — PRs and issues welcome!

---

# Getting started

## Installation

Please check the official laravel installation guide for server requirements before you start. [Official Documentation](https://laravel.com/docs/5.4/installation#installation)

Alternative installation is possible without local dependencies relying on [Docker](#docker).

Clone the repository

    git clone 'Git repo http url'

Switch to the repo folder

    cd YOUR_PROJECT_FOLDER_NAME

Copy the example env file and make the required configuration changes in the .env file

    cp .env.example .env

Install all the dependencies using composer

    composer install

Run the database migrations (**Set the database connection in .env before migrating**)

    php artisan migrate

Generate a new application key

    php artisan key:generate

Generate a new pasports key

    php artisan passport:install

update the APP_URL in .env file to your URL

for localhost it is http://localhost:8000/ (with trailing slash)

Start the local development server

    php artisan serve

You can now access the server at http://localhost:8000

**TL;DR command list**

    git clone 'Git repo http url'
    cd YOUR_PROJECT_FOLDER_NAME
    composer install
    cp .env.example .env
    php artisan key:generate
    php artisan migrate
    php artisan passport:install

**Make sure you set the correct database connection information before running the migrations** [Environment variables](#environment-variables)

    php artisan migrate
    php artisan serve

## Database seeding

**Populate the database with seed data with relationships which includes users, articles, comments, tags, favorites and follows. This can help you to quickly start testing the api or couple a frontend and start using it with ready content.**

Open the DBSeeder and set the property values as per your requirement

    database/seeds/DBSeeder.php

Run the database seeder and you're done

    php artisan db:seed

**_Note_** : It's recommended to have a clean database before seeding. You can refresh your migrations at any point to clean the database by running the following command

    php artisan migrate:refresh

## vue dependencies

Install all the dependencies using npm (**Make sure you have node and npm installed**)

    npm install

Make a build for vue

    npm run build

## modify URL PATH IN VUE FILES

    - open the file (UrlConstants.js) on this path
        resources/js/ApiUrl/UrlConstants.js
    - modify the base URL path for API whatever path it is (it will be same api path)
    This will be to make api calls [http://localhost:8000/api]

**_Note_** This path is according to localhost server, you can update it accoridng to where you host it

## Docker (**optional**)

To install with [Docker](https://www.docker.com), run following commands:

```
git clone 'Git http url'
cd chrrrp
cp .env.example.docker .env
docker run -v $(pwd):/app composer install
cd ./docker
docker-compose up -d
docker-compose exec php php artisan key:generate
docker-compose exec php php artisan migrate
docker-compose exec php php artisan db:seed
docker-compose exec php php artisan serve --host=0.0.0.0
```

The api can be accessed at [http://localhost:8000/api](http://localhost:8000/api).

# Code overview

## Dependencies

- ABC
- XYZ

## Folders

- `app/Models` - Contains all the Eloquent models
- `app/Http/Controllers/Apis` - Contains all the controllers related to apis
- `app/Http/Controllers` - Contains few basic controllers
- `app/Http/Middleware` - Contains all the middleware
- `app/Http/Request` - Contains max of validations
- `app/Http/Repositories` - Contains max of database related logic
- `app/Http/Resources` - Contains max of the responses
- `app/Http/Services` - Contains max of the logic of controllers
- `config` - Contains all the application configuration files
- `database/migrations` - Contains all the database migrations
- `database/seeds` - Contains the database seeder
- `routes` - Contains all the api routes defined in api.php file
- `resources/js` - Contains all the vuejs

## Environment variables

- `.env` - Environment variables can be set in this file

**_Note_** : You can quickly set the database information and other variables in this file and have the application fully working.

---

# Testing API

Run the laravel development server

    php artisan serve

The api can now be accessed at

    http://localhost:8000/api

# Testing Web

Run the node development server
npm run dev

The api can now be accessed at

    APP_URL: http://localhost:8000

If you find any issue then
empty storage/framework/sessions folder except .gitignore file

Request headers

| **Required** | **Key**          | **Value**        |
| ------------ | ---------------- | ---------------- |
| Yes          | Content-Type     | application/json |
| Yes          | X-Requested-With | XMLHttpRequest   |
| Optional     | Authorization    | Bearer {token}   |

---

# Authentication

This applications uses Passport to handle authentication. The token is passed with each request using the `Authorization` header with `Token` scheme. The Passport authentication middleware handles the validation and authentication of the token. Please check the following sources to learn more about Passport.

- https://laravel.com/docs/9.x/passport

---

# Cross-Origin Resource Sharing (CORS)

- https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS
- https://en.wikipedia.org/wiki/Cross-origin_resource_sharing
- https://www.w3.org/TR/cors
