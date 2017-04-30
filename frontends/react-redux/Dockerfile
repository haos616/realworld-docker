FROM node:7.9.0

RUN apt-get update \
    && apt-get -y --no-install-recommends install unzip \
    && rm -rf /var/lib/apt/lists/*

ADD https://github.com/gothinkster/react-redux-realworld-example-app/archive/master.zip /tmp/example-app.zip

RUN unzip /tmp/example-app.zip \
    && mv /react-redux-realworld-example-app-master /example-app \
    && rm /tmp/example-app.zip \
    && sed -i -- 's/https:\/\/conduit.productionready.io\/api/http:\/\/127.0.0.1:8000\/api/g' /example-app/src/agent.js

ADD ./.env /example-app/.env

WORKDIR /example-app

RUN npm install

CMD ["npm", "start"]
