#FROM node:6.9.0
<<<<<<< HEAD
#FROM openthings/ubuntu-nodejs:ARM64
FROM openthings/ubuntu-rock:ARM64

# Install common build dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    wget \
    bzr \
    git \
    mercurial \
    openssh-client \
    subversion \
    procps \
    autoconf \
    automake \
    bzip2 \
    file \
    g++ \
    gcc \
    imagemagick \
    libbz2-dev \
    libc6-dev \
    libcurl4-openssl-dev \
    libevent-dev \
    libffi-dev \
    libgeoip-dev \
    libglib2.0-dev \
    libjpeg-dev \
    liblzma-dev \
    libmagickcore-dev \
    libmagickwand-dev \
    libmysqlclient-dev \
    libncurses-dev \
    libpng-dev \
    libpq-dev \
    libreadline-dev \
    libsqlite3-dev \
    libssl-dev \
    libtool \
    libwebp-dev \
    libxml2-dev \
    libxslt-dev \
    libyaml-dev \
    make \
    patch \
    xz-utils \
    zlib1g-dev

WORKDIR /home/weave

#export NVM_NODEJS_ORG_MIRROR=http://nodejs.org/dist
ENV HTTPS_PROXY=192.168.1.88:9999 GIT_SSL_NO_VERIFY=true 
ENV NVM_DIR="/root/.nvm" NVM_NODEJS_ORG_MIRROR=http://nodejs.org/dist
ENV NPM_CONFIG_LOGLEVEL=http NPM_CONFIG_PROGRESS=true 

RUN	git clone --progress https://github.com/creationix/nvm.git && \
	cd nvm && ./install.sh

#	export NVM_DIR="/root/.nvm" && \
#	[ -s "$NVM_DIR/nvm.sh" ] && \
#	. "$NVM_DIR/nvm.sh" 

RUN	. "/root/.nvm/nvm.sh" && \
	nvm install 6.9.2 && \
	nvm ls 

#	npm config set registry=https://registry.npm.taobao.org && \

RUN 	. "/root/.nvm/nvm.sh" && \
	npm -v && \
	wget https://www.npmjs.com/install.sh -O npminstall.sh && \
	chmod +x npminstall.sh && \
	./npminstall.sh && \
	npm -v && \
	npm config set proxy=http://192.168.1.88:9999 && \
	npm config set registry=http://registry.npmjs.org && \
	npm install minimatch openssl semver

COPY package.json /home/weave/
=======
FROM aarch64/ubuntu-nodejs:ARM64

WORKDIR /home/weave

COPY package.json /home/weave/

ENV NPM_CONFIG_LOGLEVEL=warn NPM_CONFIG_PROGRESS=false

RUN npm config set proxy=http://192.168.1.88:9999 && npm install

>>>>>>> master
COPY webpack.local.config.js webpack.production.config.js server.js .babelrc .eslintrc .eslintignore /home/weave/

RUN	. "/root/.nvm/nvm.sh" && \
	npm install
#	npm prune && npm ls

ENV PATH=/root/.nvm/versions/node/v6.9.2/bin:$PATH
