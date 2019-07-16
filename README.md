# Bitbucket Pipelines PHP 7.2 image

[![](https://images.microbadger.com/badges/version/karatbit/bitbucket-pipelines-default.svg)](https://microbadger.com/images/karatbit/bitbucket-pipelines-default "Get your own version badge on microbadger.com") [![](https://images.microbadger.com/badges/image/karatbit/bitbucket-pipelines-default.svg)](https://microbadger.com/images/karatbit/bitbucket-pipelines-default "Get your own image badge on microbadger.com")

## Based on Ubuntu 18.04

### Packages installed

- `php7.2-zip`, `php7.2-xml`, `php7.2-mbstring`, `php7.2-curl`, `php7.2-json`, `php7.2-imap`, `php7.2-mysql`, `php7.2-tokenizer`, `php7.2-xdebug`, `php7.2-intl`, `php7.2-soap`, `php7.2-pdo`, `php7.2-cli`, `php7.2-bcmath`, `php7.2-sqlite3` and `php7.2-gd`
- wget, curl, unzip
- Composer
- Mysql 5.7
- NPM

### Sample `bitbucket-pipelines.yml`

```YAML
image: karatbit/bitbucket-pipelines-default
pipelines:
  default:
    - step:
        script:
          - service mysql start
          - mysql -h localhost -u root -proot -e "CREATE DATABASE test;"
          - composer install --no-interaction --no-progress --prefer-dist
          - ./vendor/phpunit/phpunit/phpunit -v --coverage-text --colors=never --stderr
```
