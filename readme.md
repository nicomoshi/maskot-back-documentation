# MASKOT - Backend

## Table of contents
  * [Requirements](#requirements)
- [Install Repo & Packages](#install-repo---packages)
  * [1. Clone Repository:](#1-clone-repository-)
  * [2. Install NPM Packages:](#2-install-npm-packages-)
  * [3. Install Composer Packages:](#3-install-composer-packages-)
  * [4. Link storage:](#4-link-storage-)
- [Prepare VM](#prepare-vm)
  * [1. Create environment file:](#1-create-environment-file-)
  * [2. Edit environment file:](#2-edit-environment-file-)
  * [3. Make Homestead file:](#3-make-homestead-file-)
  * [4. Edit Homestead.yaml:](#4-edit-homesteadyaml-)

## Before you install

### Requirements


[Full Requirements Page](https://www.notion.so/Maskot-da6fb6a910b840fe8e8ebbe2bf0c39b3)

- [Homebrew](https://www.notion.so/HomeBrew-b1cc1dbaa3db4a148a07953c0b772ad7) Latest
- [PHP](https://www.notion.so/PHP-60b5ef2e2bde4d559c8dc27714a0a326) 7.3
- [NPM](https://www.notion.so/NPM-20b8a81d6243444f8ef844ec0655ab0a) Latest
- [Vagrant](https://www.notion.so/Vagrant-653a00de2f9b4991a9832f3058545f39) Latest
- [VirtualBox](https://www.notion.so/VirtualBox-a8a846d5b1374be39cb09df29130fed8) Latest
- [Homestead](https://www.notion.so/Homestead-e4bf957a632f433b925d432b9e9f453e) Latest
- [Composer](https://www.notion.so/Composer-63392bc980454f05ad0a9d37fdbe897c) 1.10.1
- [Sequel Pro](https://www.notion.so/Sequel-Pro-ebb9691c34134109ba5c50d3a6c2c309)
- .env file (Ask Developer)

## Install Repo & Packages

### 1. Clone Repository:
```sh
git clone --recursive git@github.com:mirkco/maskot-backend.git .
```

### 2. Install NPM Packages:
```sh
npm install
```

### 3. Install Composer Packages:
```sh
composer install
```

### 4. Link storage:
```sh
php artisan storage:link
```

## Prepare VM

### 1. Create environment file:
```sh
cp .env.homestead .env
```

### 2. Edit environment file:
In project's root folder, replace .env with file provided by developer.

### 3. Make Homestead file:
```sh
php vendor/bin/homestead make
```

### 4. Edit Homestead.yaml:
**1.** Locate Homestead.yaml file in project't root folder, replace with:
```sh
ip: 192.168.10.10
memory: 2048
cpus: 1
hostname: maskot-frontend
name: maskot-frontend
provider: virtualbox
authorize: ~/.ssh/id_rsa.pub
keys:
  - ~/.ssh/id_rsa
folders:
  - map: [localPath]/maskot-frontend
    to: /home/vagrant/maskot-frontend
  - map: [localPath]/maskot-backend
    to: /home/vagrant/maskot-backend
sites:
  - map: frontend.default.mirkdev.co
    to: /home/vagrant/maskot-frontend/public
  - map: default.default.mirkdev.co
    to: /home/vagrant/maskot-backend/public
databases:
  - homestead
  - maskot_frontend_dev
  - team_maskot

```
**2.** Replace **[localPath]** with local project's path (E.g. /Users/Developer/Projects/maskot-backend)



