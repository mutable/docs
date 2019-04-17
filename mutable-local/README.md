## Mutable Local App
Mutable Local App provides a simple way to develop microservices locally as well as deploy, manage and scale them on Mutable Cloud and Edge. The app is currently available on MacOS and Linux.

We have built Mutable Local App from the perspective of developers. We created it to allow customers and users to develop apps faster and better. With this in mind, please do not hesitate to contact us on Twitter [@mutable](https://twitter.com/mutable) and join us on [Slack](http://slack.mutable.io/).

The current version has a tight integration for Node.js. However, you can develop in any language of your choice.


## Installing
*Tested on macOS 10.14.3 & Ubuntu 18.04.1 LTS.* [Previous Releases](./README.md#previous-releases)

**Current Production Release**

**v0.8.2** - [Release Notes](./release-notes/v0.8.2.md)

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.8.2.dmg)

[Linux 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.8.2.tar.gz)



## Deploying
To deploy on Mutable Cloud, you need `.mutable` and `Dockerfile` files in the root of the service directory. You also need to set the server port from the environment variable.

## .mutable
```json
{
    "watch": "routes/*.js,app.js,api/*.js",
    "healthCheck": "health",
    "watchRestartTest": false,
    "watchRestartService": true,
    "healthCheckType": "http",
    "minContainers": 1,
    "maxContainers": 1,
    "memory": 256
}
```
The `.mutable` object, and Mutable Cloud, requires a `healthCheck` endpoint which responds with a lag ping.

Example in Node.js using [toobusy-js](https://www.npmjs.com/package/toobusy-js).

```js
return tooBusy.lag()+''
```

*Note: the response must be a string.*

## Dockerfile
Example for Node.js

```Dockerfile
FROM node:6.10.3

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

COPY . /usr/src/app
RUN npm install

ENV NODE_ENV production
ENTRYPOINT ["npm", "run"]
CMD ["start"]
```
## Server port
In Mutable Cloud, server port is being set up through environment variable, so make sure your server port is not hard coded and looks like this:
`port: process.env.PORT || 3000`

## Previous Releases
**v0.7.4**

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.7.4.dmg)

[Linux 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.7.4.zip)


**v0.6.1**

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.6.1.dmg)

[Linux 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.6.1.zip)


**v0.6.0**

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.6.0.dmg)


**v0.5.2**

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.5.2.dmg)


**v0.5.1**

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.5.1.dmg)


**v0.5.0**

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.5.0.dmg)
