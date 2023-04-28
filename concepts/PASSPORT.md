# Laravel
## API
### PASSPORT
- To use it; Run `composer create-project laravel/laravel api.test`
- CD `api.test`
- Run `composer require laravel/passport`
- Enter database password in `.env`
- Run `php artisan migrate:fresh`
- Run `php artisan passport:install`
- Modify `config/auth.php`
    - ~~~php
        'guards' => [
            'web' => [
                'driver' => 'session',
                'provider' => 'users',
            ],

            'api' => [
                'driver' => 'passport',
                'provider' => 'users',
            ],
        ],
      ~~~
- Run `php artisan passport:keys`
    - Checkout in `/storage`
        - `oauth-private.key`
        - `oauth-public.key`
- Modify `app/Providers/AuthServiceProvider.php`
    - ~~~php
        class AuthServiceProvider extends ServiceProvider
        {
            protected $policies = [
                'App\Models\Model' => 'App\Policies\ModelPolicy',
            ];

            public function boot()
            {
                $this->registerPolicies();
            }
        }
      ~~~