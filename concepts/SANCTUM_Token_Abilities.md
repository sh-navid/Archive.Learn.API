# Laravel
## API
### AUTH - SANCTUM with Abilities
- Run `composer create-project laravel/laravel api.test`
- Run `composer require laravel/sanctum`
- Run `php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"`
- Put your database password in `.env`
- Run `php artisan migrate:fresh`
- Change `app/Http/Kernel.php` and uncomment `EnsureFrontendRequestsAreStateful` class
    - ~~~php
        'api' => [
            \Laravel\Sanctum\Http\Middleware\EnsureFrontendRequestsAreStateful::class,
        ],
      ~~~
- Change `use` section of `app/Models/User.php` to:
    - ~~~php
        use HasApiTokens, HasFactory, Notifiable;
      ~~~