FROM redash/redash:latest

ENV WORKERS_COUNT=${WORKERS_COUNT:-1}
ENV QUEUES=${QUEUES:-celery}

WORKDIR /app

CMD /usr/local/bin/celery worker --app=redash.worker --beat -c$WORKERS_COUNT -Q$QUEUES -linfo --maxtasksperchild=10 -Ofair
