# Laravel
## API
### AUTH - SANCTUM
- Run `composer require laravel/sanctum`
- Run `php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"`
- Put your database password in `.env`
- Run `php artisan migrate:fresh`
- Change `app/Http/Kernel.php` and uncomment `EnsureFrontendRequestsAreStateful` class
    - ~~~php
        'api' => [
            \Laravel\Sanctum\Http\Middleware\EnsureFrontendRequestsAreStateful::class,
            .
            .
            .
        ],
      ~~~