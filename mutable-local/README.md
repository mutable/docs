
# Mutable App
- [**About**](#mutable-local)
- [**Installing**](#installing)
- [**How to use**](#how-to-use)
-  [**Previous Releases**](#previous-releases)


## Mutable Local
Mutable Local App provides a simple way to develop microservices locally as well as deploy, manage and scale them on Mutable Cloud and Edge. The app is currently available on MacOS and Linux.

We have built Mutable Local App from the perspective of developers. We created it to allow customers and users to develop apps faster and better. With this in mind, please do not hesitate to contact us on Twitter [@mutable](https://twitter.com/mutable) and join us on [Slack](http://slack.mutable.io/).

The current version has a tight integration for Node.js. However, you can develop in any language of your choice.


## Installing
*Tested on macOS 10.14.3 & Ubuntu 18.04.1 LTS.* [Previous Releases](./README.md#previous-releases)

**Current Production Release**

**v0.9.22**

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.9.22.dmg)

[Linux 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.9.22.tar.gz)



## How to use

-  [**Local Development**](#local-development)
    - [**Creating Stack**](#creating-stack)
    - [**Creating Services**](#creating-services) / [**Cloning Services from GitHub**](#cloning-services-from-github)
    - [**Configuring Services**](#configuring-services)
    -  [**Running Services**](#running-services)
-  [**Proxy**](#proxy-service)
- [**Deploying**](#deploying)
    - [**Deploying Hosted Stack**](#creating-hosted-stack) 
    - [**Creating Hosted Service**](#creating-hosted-service)
    - [**Deploying Service**](#deploying-service)


# Local Development
In order for you to take full advantage of everything the Mutable App has to offer, please follow these instructions. 

When creating your Stacks and Services through the Mutable App, it will generate all the files and folders inside `${user}/home/mutable` directory (Ubuntu). If you have an existing project that you would like to run with Mutable, you must move them into that directory; otherwise, they won't be visible for the Mutable App.

## Creating Stack
Open Mutable App and click on `Create a new Stack` button.
![Screenshot from 2019-06-03 15-11-24](https://user-images.githubusercontent.com/20372024/58798030-980c7f80-8612-11e9-829a-37ee83519b36.png)

Input your project name into the field the app. 
`Services` column shows the number of services currently in your Stack.  
`Deployed` column shows how many of them are currently deployed to the Mutable Cloud.  
![Screenshot from 2019-06-03 15-12-33](https://user-images.githubusercontent.com/20372024/58798567-056ce000-8614-11e9-8191-a6381ad23faf.png)

`Terminal/Code` Buttons allow you to open Terminal or File Explorer in your project location.

![Screenshot from 2019-06-03 15-13-17](https://user-images.githubusercontent.com/20372024/58798537-f128e300-8613-11e9-92e1-ca55b4f5bdde.png)

We created our first Stack. Click on the Stack name to start creating its services.

## Creating Services
Click `Create Service` to create a new Blank service or select one of the boilerplate services that Mutable Team has provided for you. Boilerplate services are available on Mutable's GitHub page.

![Screenshot from 2019-06-03 15-52-22](https://user-images.githubusercontent.com/20372024/58799934-a6a96580-8617-11e9-90a9-d3a99c56f2e2.png)
Click `Create Service` and the App will create a directory with your service name and generate `.mutable`, `.env`, `Procfile` and `README.md` files inside it. 

Note: when creating your `node.js` server make sure to set the port to `process.env.PORT`.

`Example`: 
```js
    const server = Hapi.server({
        port: process.env.PORT || 3000
    });
```

## Cloning Services from GitHub
Mutable App also allows you to clone your own projects directly from the GitHub. ![Screenshot from 2019-06-04 14-32-05](https://user-images.githubusercontent.com/20372024/58872741-c8692200-86d5-11e9-8af8-70cc62038101.png)

We can see the created/cloned service in the Stack.
![Screenshot from 2019-06-03 16-09-39](https://user-images.githubusercontent.com/20372024/58800878-1caecc00-861a-11e9-9e68-520bf9029c77.png)

We have only 1 service in our Stack and later there may be more, so`Start all` button runs all the services in the current stack. 

Deploy tab allows you to create the current Stack in the Mutable Cloud for when the project needs to be deployed to the Cloud. After the Stack is deployed, the `Deploy` tab will list the already deployed services. 

We will come back to this after finishing the local setup.
`Collaborators`, `Domains`, `Certs` tabs require you to create a Stack in the Deploy tab and will be inactive. 

## Configuring services
Click on the Service name to go to Service interface.

![Screenshot from 2019-06-03 16-47-18](https://user-images.githubusercontent.com/20372024/58802876-49191700-861f-11e9-986a-699fb0fd6252.png)

`Service`, `Snapshot`, `Container` tabs also require you to create a Stack in the Stack's Deploy tab. 

Logs show that the service was attempted to run but was missing the start script. 
Start script can be added in the Service's `Settings` tab.
![Screenshot from 2019-06-03 18-25-57](https://user-images.githubusercontent.com/20372024/58809495-1544ee00-862d-11e9-81e6-b22bd58651b7.png)

`Start script`: input the script that starts your node.js application.
`Test Script`: 
`Build Script`: input the script that builds your front-end application (React, Angular).
These scrips should correspond to scripts in your Service's package.json. 

Also set `Health Check Type` to `http`, and set `Health Check Path` to `health`.
These settings are necessary for the Service's health check. 

## Running Services
After setting up your node.js application and making sure that the `Start script` from your Service `Settings` corresponds to the start script from your `package.json` Click the Run button.
![Screenshot from 2019-06-04 13-16-48](https://user-images.githubusercontent.com/20372024/58867306-4542ce80-86cb-11e9-9220-073f8a1671c4.png)
Service is running, and the `View Site` column displays the port number. `demo-service-swagger` service is using one of  Mutable's boilerplate services cloned from GitHub (See [Creating services](#creating-services) Section) with integrated `hapi-swagger` plugin for API visualization. Click on the port number of the service to go to the swagger page

![Screenshot from 2019-06-04 13-17-30](https://user-images.githubusercontent.com/20372024/58867308-4542ce80-86cb-11e9-9341-c0c3ffe2d780.png)
Click on the Service name to go the Service interface and view the logs. `View` also allows you to go visit the Swagger page.
![Screenshot from 2019-06-04 13-43-06](https://user-images.githubusercontent.com/20372024/58869142-b637b580-86ce-11e9-8ef1-780a4f1c32a9.png)



Note: If the service stops after clicking the Run button, make sure you have all your node modules installed and Start scripts correctly configured. All logs are available in the Service interface.
`Error Example:`
![Screenshot from 2019-06-04 13-14-34](https://user-images.githubusercontent.com/20372024/58869292-feef6e80-86ce-11e9-8773-004608d09808.png)
![Screenshot from 2019-06-04 13-15-11](https://user-images.githubusercontent.com/20372024/58869293-feef6e80-86ce-11e9-9edd-32e520c9f705.png)
 

---

# Proxy Service

Having multiple micro-services means we'll need something to connect them to each other.
Mutable Team provides `node-proxy` service to configure all the routing for the services.
`Proxy` service also manages the deployment configuration, but we'll get to that in the Deployment instructions.

GitHub: [Repo](https://github.com/mutable/node-proxy)

Clone the service into your stack (See [Cloning Services from GitHub](#cloning-services) Section) and input the name you want for your service.
![Screenshot from 2019-06-04 14-50-11](https://user-images.githubusercontent.com/20372024/58873761-1717bb80-86d8-11e9-9d70-fa6ddc73578b.png)

After clicking `Download from GitHub` you'll see the service added to the Stack.
![Screenshot from 2019-06-04 14-52-29](https://user-images.githubusercontent.com/20372024/58873895-65c55580-86d8-11e9-90a3-d46b1428a9a8.png)
Run `npm install` in the `proxy` project and Run the service. 
`proxy` services's `Readme.md` is available both on GitHub and in `README` tab of the `proxy` service's interface.
Set the proxy settings in the `Configuration` tab and click `Save`.

Note: This is an example configuration, you must adjust it according to your project APIs.
![Screenshot from 2019-06-04 19-47-38](https://user-images.githubusercontent.com/20372024/58893673-a4233a80-8701-11e9-8a2f-d50da8e9b1a0.png)

The `mutable.local` property inside the host corresponds with`mutable.local` hostname that has been added to the `/etc/hosts` file previously.
You may choose your own hostname, add it to the configuration.

Note: Even though we currently do not have services `"http://demo-web/[~]"` or `"http://demo-api/[~]"` in our Stack,  the `"target"` property must be present and have a value for the proxy configuration to work properly. Currently, the value is a placeholder and is not pointing to any existing service.

Proxy service's port is set to `8888` by default; however, you can change it from the `Envs` tab. 

`Proxy` service is the Stack's entry point. Everything goes through the `proxy` and then gets routed according to the configurations. You can learn more by reading the proxy's Readme.

Don't forget to add `Health Check Type: http` and `Health Check Path: health` properties in `Proxy`'s (or any other service's) `Settings` tab.

![Screenshot from 2019-06-04 19-21-43](https://user-images.githubusercontent.com/20372024/58891868-535e1280-86fe-11e9-9493-62c23885dbcf.png)

---
Now that `Proxy` is configured to be the entry point of our application, we can Run the service and open `mutable.local:8888` (or the hostname you configured your proxy and `hosts` file with) in the browser. 

![Screenshot from 2019-06-04 19-28-59](https://user-images.githubusercontent.com/20372024/58892385-29592000-86ff-11e9-98ea-a73dd2c32d7f.png)

This is Mutable's default `404 page` hardcoded in the `Proxy`'s configurations (editable). The app is throwing `404` because we do not have the front end service yet. Once we do, we'll put the service inside `"mutable.local"`'s  `"target"` property, in `Proxy`'s configuration, so that the `Proxy` would know where to redirect the request to `http://mutable.local:8888`.

I made the `/demo-endpoint` route in `demo-service-swagger` Service to test the `Proxy`'s configuration: 
```js 
    routes.push({
        method: 'GET',
        path: '/demo-endpoint',
        options: {
            description: 'Demo Endpoint',
            tags: ['api','mutable','config'],
            handler: (request, h) => {
                return `This endpoint is for PROXY testing`;
            }
        }
    });
``` 
And made a request to `http://mutable.local:8888/v1/demo-service/demo-endpoint`

![Screenshot from 2019-06-04 19-46-04](https://user-images.githubusercontent.com/20372024/58893539-6de5bb00-8701-11e9-9694-0ada6a2ed395.png)

In `Proxy`'s configuration,  we made`demo-service` the Alias of our `demo-service-swagger` Service and made a request to its `demo-endpoint` endpoint.  We made a request to the Alias (demo-service) and `Proxy` took care of the redirecting the request to the service (demo-service-swagger).


### Endnotes
If you are moving your existing project to the `${user}/home/mutable` directory please make sure to use only lowercase letters, numbers, underscores and dashes in directory and file names.


# Deploying

## Creating Hosted Stack
In order to deploy your application to the `Mutable Cloud` go to Stack's `Deploy`  tab and click `Create New Stack`  
![Screenshot from 2019-06-05 10-24-01](https://user-images.githubusercontent.com/20372024/58934774-8810af00-877c-11e9-89b1-7e0cf07cfc51.png)

Mutable App will suggest using the existing name of your local Stack.  Click `Create Stack`
![Screenshot from 2019-06-05 10-26-53](https://user-images.githubusercontent.com/20372024/58934760-7d561a00-877c-11e9-8397-41b70a81c877.png)
And a new `Hosted Stack` will be created in the `Mutable Dashboard`. 


Now your `Local Stack` needs to be Associated with the `Hosted Stack` that we just created. In order to do that, select the `Hosted Stack` from the list of your hosted stacks and click `Use Existing`.  
![Screenshot from 2019-06-05 10-57-00](https://user-images.githubusercontent.com/20372024/58936572-1a1ab680-8781-11e9-8d73-b7798cffa5f4.png)

Now we have our `Local Stack` and our `Hosted Stack`, after Associating them we can see the Deployment status of our Stack.
![Screenshot from 2019-06-05 11-21-06](https://user-images.githubusercontent.com/20372024/58937634-0c1a6500-8784-11e9-849c-d9fb7c6eb018.png)
This tab now shows the Deployed services, but since we haven't deployed any services yet, the list is empty.
`Disassociate Stack` disassociates your `Local Stack` from your `Hosted Stack`.

Note: After creating the `Hosted Stack`, the tabs `Collaborators` `Domains` `Certs` become available.

## Creating Hosted Service

Go back to the `Services` tab and Click on the service name you want to deploy.
In the Service's Interface go to the `Service` tab and click `Create New Service`.
![Screenshot from 2019-06-05 11-46-21](https://user-images.githubusercontent.com/20372024/58939180-acbe5400-8787-11e9-9800-19c3c3687eb5.png)

Just like with the Stack, Mutable will suggest you use your existing service name (`proxy` in this case) for the `Hosted Service` as well. Clicking `Create Service` will create the `Hosted Service` in our `Hosted Stack`'s services in `Mutable Dashboard`.
![Screenshot from 2019-06-05 11-50-30](https://user-images.githubusercontent.com/20372024/58939372-25bdab80-8788-11e9-822f-7ee293eda524.png)

Associate your `Local Service` with your `Hosted Service` by selecting the service you want to associate to and clicking `Use Existing`.
![Screenshot from 2019-06-05 11-52-18](https://user-images.githubusercontent.com/20372024/58939571-8d73f680-8788-11e9-89a5-33eaa6b5364e.png)
 
After Associating the `Service` tab will show the list of the `Hosted Service` versions over time. (needs improvement)
![Screenshot from 2019-06-05 11-54-49](https://user-images.githubusercontent.com/20372024/58939848-1f7bff00-8789-11e9-8e5a-61b4b6c4ffc7.png)
The list is empty because we haven't deployed the service yet. 

## Deploying Service
To deploy a `Service` on Mutable Cloud, you need `.mutable` and `Dockerfile` files in the root of the service directory. You also need to set the server port from the environment variable.

### .mutable
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
return tooBusy.lag().toString()
```

*Note: the response must be a string.*

### Dockerfile
Example for Node.js

```Dockerfile
FROM node:12.14.0

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

COPY . /usr/src/app
RUN npm install

ENV NODE_ENV production
ENTRYPOINT ["npm", "run"]
CMD ["start"]
```
### Server port
In Mutable Cloud, server port is being set up through environment variable, so make sure your server port is not hard coded and looks like this:
`port: process.env.PORT || 3000`


### Deploying
Go to `Snapshot` tab to create a Snapshot of your service at that moment. 
![Screenshot from 2019-06-05 12-27-12](https://user-images.githubusercontent.com/20372024/58941651-43414400-878d-11e9-9a06-00b5c4419247.png)


Fill in your Service snapshot details and click `Continue`.
![Screenshot from 2019-06-05 12-28-42](https://user-images.githubusercontent.com/20372024/58941779-8ac7d000-878d-11e9-8fbe-df03b59ec1a4.png)
Note: Make sure the `Health Check Type: http` and `Health Check Path:health`, are set in the `Service` settings tab.

Click `Build` to build the snapshot. `Deploy` button will activate once the Build is finished.
![Screenshot from 2019-06-05 12-28-59](https://user-images.githubusercontent.com/20372024/58941780-8b606680-878d-11e9-8544-eb80efe23a52.png)

And click `Deploy` to deploy it.
![Screenshot from 2019-06-05 12-24-55](https://user-images.githubusercontent.com/20372024/58941493-f78e9a80-878c-11e9-8134-3aaa88b860a3.png)

Go back to the `Service` tab and you'll see the deployed snapshot.
![Screenshot from 2019-06-05 12-31-37](https://user-images.githubusercontent.com/20372024/58942066-13467080-878e-11e9-9350-038f0e67b1cc.png)

Repeat the process if you want to deploy all the other services. 

Note: `Proxy` service's configuration must include the configuration of the deployed services.


## Previous Releases
**v0.8.2**

[macOS 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.8.2.dmg)

[Linux 64-bit](https://s3.amazonaws.com/local.mutable.io/app/MutableV0.8.2.tar.gz)


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



