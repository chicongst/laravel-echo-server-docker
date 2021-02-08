FROM node:10-buster-slim as base-echo

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

RUN npm install pm2 -g

RUN npm install

FROM base-echo
EXPOSE 6001
CMD ["pm2-runtime", "start", "app.json"]