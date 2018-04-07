# OlegGorJ/nodejs-on-docker-templates/base

[`OlegGorJ/nodejs`](https://index.docker.io/u/OlegGorJ/nodejs) is a [docker](https://docker.io) base image that bundles the latest version of [nodejs](https://nodejs.org) and [npm](https://npmjs.org) installed from [nodejs.org](http://nodejs.org/download/).

It serves as a base for the [`OlegGorJ/nodejs-runtime`](https://index.docker.io/u/OlegGorJ/nodejs-runtime) image.

## Usage

- Create a Dockerfile in your nodejs application directory with the following content:

        FROM OlegGorJ/nodejs

        WORKDIR /app
        ADD package.json /app/
        RUN npm install
        ADD . /app

        CMD []
        ENTRYPOINT ["/nodejs/bin/npm", "start"]

- Run the following command in your application directory:

        docker build -t my/app .
