To reproduce error from https://github.com/laravel/passport/issues/1113 

```
git clone https://github.com/patrickomeara/passport_error.git
cd passport_error
touch database/database.sqlite
cp .env.example .env
composer install
php artisan migrate
php artisan passport:install
```
replace `<secret>` with secret from `passport:install` client id `2`
```
curl --request POST --header 'accept: application/json' --header 'content-type: application/json' --data '{"username":"person@example.com","password":"ZCP7kT","grant_type":"password","client_id":2,"client_secret":"<secret>","scope":"*","device_uuid":"B11D89CD-2208-4893-DAEB-1545C3351858"}' 'https://passport_error.test/oauth/token'
cat storage/logs/laravel.log
```
