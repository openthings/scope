#FROM node:6.9.0
FROM openthings/ubuntu-nodejs:ARM64

WORKDIR /home/weave

COPY package.json /home/weave/

ENV NPM_CONFIG_LOGLEVEL=warn NPM_CONFIG_PROGRESS=false

RUN npm config set proxy=http://192.168.1.88:9999 && npm install

COPY webpack.local.config.js webpack.production.config.js server.js .babelrc .eslintrc .eslintignore /home/weave/
