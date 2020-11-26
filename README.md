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

## License

The code belongs to the Symfony framework and is subject to the MIT license.
