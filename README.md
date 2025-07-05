# first 
rename .env.example .env

# build 
docker-compose up --build -d

# file permission
docker exec laravel_simple chown -R www-data:www-data storage bootstrap/cache
docker exec laravel_simple chmod -R 775 storage bootstrap/cache

# composer install
docker exec -it laravel_simple composer install

# migrate generate database
docker exec -it laravel_simple php artisan migrate

# generate key
docker exec -it laravel_simple php artisan key:generate






# maybe remove others containers ( will remove all )
docker rm $(docker ps -a -q)