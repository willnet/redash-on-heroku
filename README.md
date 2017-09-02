# Redash on Heroku

Dockerfiles for hosting redash on heroku

## How to deploy

```sh
git clone git@github.com:willnet/redash-on-heroku.git
cd redash-on-heroku
heroku create your_app_name
heroku container:push --recursive
```

## How to setup

### Add Addons

Add following addons on heroku dashboard.

- heroku postgres
- Redis Cloud(or something)
- sendgrid (or something)

Choose redis addon allow more than or equal 30 connections. Otherwise you will get connection errors frequently.

### Add environment variables

Add environment variables like following.

```
heroku config:set PYTHONUNBUFFERED=0
heroku config:set QUEUES=queries,scheduled_queries,celery
heroku config:set REDASH_COOKIE_SECRET=YOUR_SECRET_TOKEN
heroku config:set REDASH_DATABASE_URL=YOUR_POSTGRES_URL
heroku config:set REDASH_LOG_LEVEL=INFO
heroku config:set REDASH_REDIS_URL=YOUR_REDIS_URL
heroku config:set REDASH_MAIL_PASSWORD=YOUR_ADDON_PASSWORD
heroku config:set REDASH_MAIL_PORT=587
heroku config:set REDASH_MAIL_SERVER=YOUR_ADDON_DOMAIN
heroku config:set REDASH_MAIL_USERNAME=YOUR_ADDON_USERNAME
heroku config:set REDASH_MAIL_USE_TLS=true
heroku config:set REDASH_MAIL_DEFAULT_SENDER=YOUR_MAIL_ADDRESS
```

### Create database

After deploy and add postgres addon, create database like following.

```sh
heroku run /app/manage.py database create_tables
```
