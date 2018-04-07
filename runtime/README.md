# OlegGorJ/nodejs-on-docker-templates/runtime

[`OlegGorJ/nodejs-runtime`](https://index.docker.io/u/OlegGorJ/nodejs-runtime) is a [docker](https://docker.io) base image for easily running [nodejs](https://nodejs.org) application.

It can automatically bundle a nodejs application with its dependencies and set the default entrypoint with no additional Dockerfile instructions.

It is based on [`OlegGorJ/nodejs`](https://index.docker.io/u/OlegGorJ/nodejs) base image.

## Usage

- Create a Dockerfile in your nodejs application directory with the following content:

        FROM OlegGorJ/nodejs-runtime

- Run the following command in your application directory:

        docker build -t app .

## Sample

See the [sources](/hello) for [`OlegGorJ/nodejs-hello`](https://index.docker.io/u/OlegGorJ/nodejs-hello) based on this image.

## Notes

The image assumes that your application:

- has a file named [`package.json`](https://www.npmjs.org/doc/json.html) listing its dependencies.
- has a file named `server.js` as the entrypoint script or define in `package.json` the attribute: `"scripts": {"start": "node <entrypoint_script_js>"}`
- listens on port `8080`

### Example

`package.json`

    {
      "name": "hello-world",
      "description": "hello world test app",
      "version": "0.0.1",
      "private": true,
      "dependencies": {
        "express": "3.x"
      },
      "scripts": {"start": "node app.js"}
    }

When building your application docker image, `ONBUILD` triggers fetch the dependencies listed in `package.json` and cache them appropriately.



---
