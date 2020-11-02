// Start docker
cd docker
docker-compose build
docker-compose up -d

// Stop docker
docker-compose down

// Start laravel in docker
docker exec -it zlatkit-php-fpm cp .env.example .env
docker exec -it zlatkit-php-fpm composer install
docker exec -it zlatkit-php-fpm npm install

// Refresh migrate and seed
docker exec -it zlatkit-php-fpm php artisan migrate:refresh --seed

// phpunit test
docker exec -it zlatkit-php-fpm ./vendor/phpunit/phpunit/phpunit --configuration ./phpunit.xml

// add hosts /etc/hosts
// 127.0.0.1       zlatkit.loc
sudo nano /etc/hosts

// .env
DEBUGBAR_ENABLED=true

DB_CONNECTION=mysql
DB_HOST=zlatkit-mysql
DB_PORT=3306
DB_DATABASE=zlatkit
DB_USERNAME=zlatkit
DB_PASSWORD=zlatkit

REDIS_HOST=zlatkit-redis
REDIS_PASSWORD=redis
REDIS_PORT=6379 

// site
http://zlatkit.loc/
// phpmyadmin
http://zlatkit.loc:8183/