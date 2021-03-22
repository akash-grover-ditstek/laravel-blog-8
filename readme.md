# Laravel 8.0 blog

The purpose of this repository is to show good development practices on [Laravel](http://laravel.com/) as well as to present cases of use of the framework's features like:

- [Authentication](https://laravel.com/docs/8.x/authentication)
- API
  - Token authentication
  - [API Resources](https://laravel.com/docs/8.x/eloquent-resources)
  - Versioning
- [Blade](https://laravel.com/docs/8.x/blade)
- [Broadcasting](https://laravel.com/docs/8.x/broadcasting)
- [Cache](https://laravel.com/docs/8.x/cache)
- [Email Verification](https://laravel.com/docs/8.x/verification)
- [Filesystem](https://laravel.com/docs/8.x/filesystem)
- [Helpers](https://laravel.com/docs/8.x/helpers)
- [Horizon](https://laravel.com/docs/8.x/horizon)
- [Localization](https://laravel.com/docs/8.x/localization)
- [Mail](https://laravel.com/docs/8.x/mail)
- [Migrations](https://laravel.com/docs/8.x/migrations)
- [Policies](https://laravel.com/docs/8.x/authorization)
- [Providers](https://laravel.com/docs/8.x/providers)
- [Requests](https://laravel.com/docs/8.x/validation#form-request-validation)
- [Seeding & Factories](https://laravel.com/docs/8.x/seeding)
- [Testing](https://laravel.com/docs/8.x/testing)
- [Homestead](https://laravel.com/docs/8.x/homestead)

Beside Laravel, this project uses other tools like:

- [Bootstrap 4](https://getbootstrap.com/)
- [PHP-CS-Fixer](https://github.com/FriendsOfPhp/PHP-CS-Fixer)
- [Travis CI](https://travis-ci.org/)
- [Font Awesome](http://fontawesome.io/)
- [Vue.js](https://vuejs.org/)
- [axios](https://github.com/mzabriskie/axios)
- [Redis](https://redis.io/)
- [spatie/laravel-medialibrary](https://github.com/spatie/laravel-medialibrary)
- Many more to discover.

## Installation

Setting up your development environment on your local machine :
```bash
 git clone https://github.com/akash-grover-ditstek/laravel-blog-8.git blog
 cd blog
 cp .env.example .env
 composer install composer require laravel/horizon --ignore-platform-reqs
 php artisan key:generate
 php artisan horizon:install
 php artisan telescope:install
 php artisan storage:link
 php artisan migrate --seed
 php artisan serve
 
```
Now you can access the application via [http://localhost:8000](http://localhost:8000).

you can use to sign in :
email: akash@grover.com
password: admin

```
npm install
```

Starting job for newsletter :
```
php artisan tinker
> PrepareNewsletterSubscriptionEmail::dispatch();
```

## Useful commands
Seeding the database :
```
php artisan db:seed
```

Generating backup :
```
php artisan vendor:publish --provider="Spatie\Backup\BackupServiceProvider"
php artisan backup:run
```

Generating fake data :
```
php artisan db:seed --class=DevDatabaseSeeder
```

Discover package
```
php artisan package:discover
```

In development environnement, rebuild the database :
```
php artisan migrate:fresh --seed
```

## Accessing the API

Clients can access to the REST API. API requests require authentication via token. You can create a new token in your user profile.

Then, you can use this token either as url parameter or in Authorization header :

```
# Url parameter
GET http://localhost:8000/api/v1/posts?api_token=your_private_token_here

# Authorization Header
curl --header "Authorization: Bearer your_private_token_here" http://localhost:8000/api/v1/posts
```

API are prefixed by `api` and the API version number like so `v1`.

Do not forget to set the `X-Requested-With` header to `XMLHttpRequest`. Otherwise, Laravel won't recognize the call as an AJAX request.

To list all the available routes for API :

```
php artisan route:list --path=api
```
## License

This project is released under the [MIT](http://opensource.org/licenses/MIT) license.