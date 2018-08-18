## Mutable Local App
Mutable Local App is a desktop tool for MacOs and Linux. Its primary purpose is to provide a simple way to develop and manage microservices and deploy and scale them on Mutable Cloud.

We have built Mutable Local App from the perspective of developers. We created it to allow us and customers and users to make apps faster and better. With this in mind, please do not hesitate to contact us on Twitter [@mutable](https://twitter.com/mutable) and join us on [Slack](http://slack.mutable.io/).

The current version has a tight integration for Node.js. However, you can develop in any language of your choice. There are a two requirements; a [policy](./README.md#.mutable) file and a [Dockerfile](./README.md#Dockerfile); to deploy the service on Mutable Cloud.


## Installing
*Tested on macOS 10.13.6 & Ubuntu 18.04.1 LTS.* [Previous Releases](./README.md#previous-rleases)

**Current Production Release**

**v0.7.1** - [Release Notes](./release-notes/v0.7.1)

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.7.1.dmg)

[Linux 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.7.1.tar.gz)



## Deploying
To deploy on Mutable Cloud, you need a `.mutable` and a `Dockerfile` in the root of the service directory. 

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

## Previous Releases

**v0.6.1** - [Release Notes](./release-notes/v0.6.1)

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.6.1.dmg)

[Linux 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.6.1.zip)


**v0.6.0** - [Release Notes](./release-notes/v0.6.0)

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.6.0.dmg)


**v0.5.2** - [Release Notes](./release-notes/v0.5.2)

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.5.2.dmg)


**v0.5.1** - [Release Notes](./release-notes/v0.5.1)

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.5.1.dmg)


**v0.5.0** - [Release Notes](./release-notes/v0.5.0)

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.5.0.dmg)
