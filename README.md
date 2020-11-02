<!DOCTYPE html>
<html>
<head>
</head>
<body>
<p>
// Start docker<br />
cd docker<br />
docker-compose build<br />
docker-compose up -d<br />
<br />
// Stop docker<br />
docker-compose down<br />
<br />
// Start laravel in docker<br />
docker exec -it zlatkit-php-fpm cp .env.example .env<br />
docker exec -it zlatkit-php-fpm composer install<br />
docker exec -it zlatkit-php-fpm npm install<br />
<br />
// Refresh migrate and seed<br />
docker exec -it zlatkit-php-fpm php artisan migrate:refresh --seed<br />
<br />
// phpunit test<br />
docker exec -it zlatkit-php-fpm ./vendor/phpunit/phpunit/phpunit --configuration ./phpunit.xml<br />
<br />
// add hosts /etc/hosts<br />
// 127.0.0.1       zlatkit.loc<br />
sudo nano /etc/hosts<br />
<br />
// .env<br />
DEBUGBAR_ENABLED=true<br />
<br />
DB_CONNECTION=mysql<br />
DB_HOST=zlatkit-mysql<br />
DB_PORT=3306<br />
DB_DATABASE=zlatkit<br />
DB_USERNAME=zlatkit<br />
DB_PASSWORD=zlatkit<br />
<br />
REDIS_HOST=zlatkit-redis<br />
REDIS_PASSWORD=redis<br />
REDIS_PORT=6379 <br />
<br />
// site<br />
<a href="http://zlatkit.loc/" aria-invalid="true">http://zlatkit.loc/</a><br />
// phpmyadmin<br />
<a href="http://zlatkit.loc:8183/" aria-invalid="true">http://zlatkit.loc:8183/</a></p>
<p style="text-align: center;"><br />
<br />
</p>
</body>
</html>
