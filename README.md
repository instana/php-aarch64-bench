# PHP aarch64 benchmarking

## Setup

[Install Symfony CLI](https://symfony.com/download)

```bash
wget https://get.symfony.com/cli/installer -O - | bash
```

Install Ondrejs PHP PPA

```bash
sudo add-apt-repository ppa:ondrej/php
mv /home/ubuntu/.symfony/bin/symfony /usr/local/bin/symfony
```

Install PHP

```bash
sudo apt install php7.4-fpm php7.4-xml php7.4-mbstring php7.4-sqlite3 php7.4-zip
# enable php-fpm so Instana can detect it and there is no delay in picking up the process
sudo systemctl enable php7.4-fpm && sudo systemctl start php7.4-fpm
```

Create the project in the `symfony_demo` subdirectory by either cloning this
project or directly via symfony cli:

```bash
symfony new --demo symfony_demo
```

Now, edit the `.env` file in your `symfony_demo` folder so it sets `ENV=prod` so
the container is compiled.

Grab the suitable executable of bombardier for your platform from
the projects' GitHub page: https://github.com/codesenberg/bombardier/releases/tag/v1.2.5

```
wget https://github.com/codesenberg/bombardier/releases/download/v1.2.5/bombardier-linux-amd64
chmod +x bombardier-linux-amd64
```

## Start the application

We use the http server the symfony cli provides. It will start a php-fpm instance on its
own.

```bash
symfony serve
```

## Access the application

The url we want to hit is `http://127.0.0.1/de/blog/`, it will issue a mixture of db-calls, templating
and http.


## License

The code belongs to the Symfony framework and is subject to the MIT license.
