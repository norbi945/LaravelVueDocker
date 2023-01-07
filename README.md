# ItsyBisty

## Setting up the server

After running `docker-compose up`, you need to start the nginx service in webserver's docker container:
```bash
service nginx start
```

If you not not linked your virtualhosts yet, you can do it with the following commands at webserver's container:
```bash
ln -s /etc/nginx/sites-available/api.itsy-bitsy.test /etc/nginx/sites-enabled/api.itsy-bitsy.test # for api
ln -s /etc/nginx/sites-available/itsy-bitsy.test /etc/nginx/sites-enabled/itsy-bitsy.test # for client
ln -s /etc/nginx/sites-available/adminer.test /etc/nginx/sites-enabled/adminer.test # for adminer
```
After that you can reach the api at `http://api.itsy-bitsy.test` and the webpage at `http://itsy-bitsy.test`.
If you using adminer, link the adminer's config too, and you can reach at `http://adminer.test`.

## Setting up the API:

(Working on php container's api directory - the root of the api)

First, you need to install the composer depenedcies with `composer install`.

After you need to generate your application key with the following command:
```bash
php artisan key:generate
```

After that, do the following steps:
- Set up your database connection at the `.env`.
- Set the `APP_URL` variable to the API's root ( http://api.itsy-bitsy.test ).
- Set up your mailer connection.

## Starting the webpage application

From the webserver's container you can run the following at the client project's directory:
```bash
npm run dev
```
