# Laravel
## API
### AUTH - SANCTUM
- https://github.com/laravel/sanctum
- https://laravel.com/docs/10.x/sanctum
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
- Change `use` section of `app/Models/User.php` to:
    - ~~~php
        use HasApiTokens, HasFactory, Notifiable;
        .
        .
        .
      ~~~
- Create a controller `php artisan make:controller AuthController`
- Routes
    - ~~~php
        Route::middleware('auth:sanctum')->get('/user', function (Request $request) {
            return $request->user();
        });

        Route::post('/register', [AuthController::class, 'register']);

        Route::post('/login', [AuthController::class, 'login']);

        Route::group(['middleware' => ['auth:sanctum']], function () {
            // protected routes

            Route::post('/logout', [AuthController::class, 'logout']);
        });
      ~~~