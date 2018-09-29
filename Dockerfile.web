FROM redash/redash:latest
WORKDIR /app
CMD /usr/local/bin/gunicorn -b 0.0.0.0:$PORT --name redash -w${REDASH_WEB_WORKERS:-1} redash.wsgi:app
