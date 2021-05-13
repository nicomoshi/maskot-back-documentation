# MASKOT - Backend

## Overview

The Maskot Backend provides CMS access to allow standard CRUD functionality to the App data

The Maskot Backend also provides an API for the mobile app.

This is an update to the readme..

# Development
## Installation
```sh
    // Project Setup
    $ git clone --recursive git@github.com:mirkco/maskot-backend.git .
    $ composer install
    $ npm install
    $ php artisan storage:link
```

Now all necessary files are downloaded, spin up the VM.
This package is equipped to run via [Homestead](https://laravel.com/docs/5.3/homestead)

```sh
    $ cp .env.homestead .env
    
    # NOTE: THE APP_KEY (generated below) MUST BE THE EXACT SAME ON FRONTEND AND BACKEND
    $ php artisan key:generate
    
    $ php vendor/bin/homestead make
    $ vagrant up
```

Finally add `127.0.0.1 backend.maskot.dev` to your `/etc/hosts` file.

### Database Configuration
This project then requires at least 2 databases to operate, and development requires and additional 2 (making 4 in total):

Database 1: `maskot_frontend_dev` - The database for the Frontend (only required if you don't have an instance of the frontend already running)

Database 2: `team_maskot` - The initial/default Club all users are subscribed to

Database 3: `sample_1` - An additional testing Club

Database 4: `sample_2` - An additional testing Club

SSH into your environment.
Run the following custom artisan command to deploy everything:
```sh
    $ php artisan maskot:deploy
```

Note you can completely reset all databases with the following command
```sh
    $ php artisan maskot:reset
```


### Additional required setup
Both the frontend and backend make use of many third party services, all with individual API keys etc.

All this information is set in the `.env` file, however they are left out of source control for obvious reasons. You will need to obtain the required values for service from that service's control panel.

Required `.env` vars are (taken from `.env.homestead`):

```

// AWS S3 File Storage
AWS_S3_KEY=
AWS_S3_SECRET=
AWS_S3_REGION=
AWS_S3_BUCKET=

// Mail - Staging/Production use Sendgrid
MAIL_DRIVER=smtp
MAIL_HOST=mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null

// Pusher.io for Notification Broadcasting
PUSHER_APP_ID=
PUSHER_APP_KEY=
PUSHER_APP_SECRET=

// Google Places API for address searching
GOOGLE_PLACES_API_KEY=

// Facebook API for social auth
FACEBOOK_APP_ID=
FACEBOOK_APP_SECRET=

// Maskot Stripe Account - Test Keys
STRIPE_KEY=
STRIPE_SECRET=
STRIPE_DEV_CLIENT_ID=
```



## Usage
Access via `backend.maskot.dev`


# Tests
```sh
    $ cp .env.circleci .env
    $ php artisan key:generate
    $ php artisan migrate --path database/migrations/frontend --database=frontend
    $ php artisan migrate --path database/migrations/backend --database=backend
    $ php artisan db:seed --class=BackendSeeder --database=backend
```
