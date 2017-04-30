FROM node:7.9.0

RUN apt-get update \
    && apt-get -y --no-install-recommends install unzip jq \
    && rm -rf /var/lib/apt/lists/*

ADD ./package.json /tmp/package.json

ADD https://github.com/gothinkster/angular2-realworld-example-app/archive/master.zip /tmp/example-app.zip

RUN unzip /tmp/example-app.zip \
    && mv /angular2-realworld-example-app-master /example-app \
    && cp /example-app/package.json /tmp/package-original.json \
    && jq -s '.[0] * .[1]' /tmp/package-original.json /tmp/package.json > /example-app/package.json \
    && sed -i -- 's/https:\/\/conduit.productionready.io\/api/http:\/\/127.0.0.1:8000\/api/g' /example-app/src/environments/environment.ts \
    && rm /tmp/example-app.zip

WORKDIR /example-app

RUN npm install

CMD ["npm", "start"]
