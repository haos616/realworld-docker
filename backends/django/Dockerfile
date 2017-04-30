FROM python:3.6.1

RUN apt-get update \
    && apt-get -y --no-install-recommends install unzip \
    && rm -rf /var/lib/apt/lists/*

ADD ./docker-entrypoint.sh /scripts/docker-entrypoint.sh

ADD https://github.com/gothinkster/django-realworld-example-app/archive/master.zip /tmp/example-app.zip

RUN unzip /tmp/example-app.zip \
    && mv /django-realworld-example-app-master /example-app \
    && rm /tmp/example-app.zip \
    && chmod +x /scripts/docker-entrypoint.sh

WORKDIR /example-app

RUN pip install -r requirements.txt

ENTRYPOINT ["/scripts/docker-entrypoint.sh"]

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
