#LSQ Microservice Development Platform

LSQ is the first platform to allow you to quickly build robust applications using a **microservice architecture**. Like it's predecessor [Service-Oriented Architecture], Microservices have emerged as a solution to the challenges of developing, testing, and scaling complex applications. Recent technological advances such as cloud deployments and containerization have brought this methodology within reach of smaller teams that do not have dedicated (and expensive) Dev-Ops teams.

##What are Microservices?

> "The microservice architectural style is an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms... "

> Martin Fowler, *[Microservices]*

##Microservice Architecture

### <i class="icon-cog-alt"></i> Servers

In a microservice architecture, what is typically called the 'server' is broken apart into separate components, called "microservices". Each microservice is responsible for a single business function such as sending email or connecting to a database. By decoupling each business function you are able to ensure that issues in one area of your application do not impact other areas. In the future, as your application grows, each microservice can be managed and scaled separately. And as your organization grows, each microservice can be owned by a different team of developers and be managed and upgraded independently.

### <i class="icon-exchange"></i> Communication

Each microservice communicates with other services using standard http connections. Using http allows developers to easily develop microservices using their existing toolset. It also means that it is very easy to incorporate 3rd-party API's. 

### <i class="icon-hdd"></i> Data Persistence

A microservice architecture works best when each microservice is stateless - each request to a microservice completely independent of the requests that came before it. Is this allows for maximum flexibility when it comes time to scale. 

Furthermore, each microservice is responsible for maintaining it's own data. We currently recommend connecting to a cloud-hosted database provider, such [Compose.io]

##What are the advantages of a microservice architecture?

###Independence (both code and data)

Code: They can be written, deployed, upgraded and scaled independently. They can also be running on different platforms and written in different languages.

Data: Every service is responsible for each own data store. This removes database as a central point of contention. Each service owns and scales its own data store, and offers it to other services via APIs. It also means that consistency is eventual not immediate.

###Business-focused and team-owned

Each service is responsible for part of the business. Each service includes / owns full stack from infrastructure to business logic, to end user UX.

Each service is owned & built by a small team.

###Designed for failure

Each service recognizes that failure is real and will happen. 
Each service comes with logic for handling failure gracefully. Testing tools deliberately 
cause and simulate failure. 

###Automated

The system minimizes down-time by automating blue-green deployment, allowing gradual release / deployment of the services.
You also have state of the art monitoring tools to help flag and fix problems early. Provision / scale new machines rapidly. 

##So what's the problem?

> "...building, deploying and maintaining distributed applications is a highly technical feat. [ ]... it requires a new toolkit that is central to solving the coordination and orchestration challenges of running systems that span across multiple machines, datacenters and time zones. "

> Lenny Pruss, *[Warehouse Computing and the Evolution of the Datacenter]*

###Coordination

###Testing

###Deployment

And that's why we're building LSQ - a next-generation SaaS platform that will allow independent developers and small teams to take advantage of the 

##The LSQ Products

Follow the links below to learn more about the LSQ products:

- [LSQ Local] - Run and monitor multiple microservices using our free desktop application.
- [LSQ microservice templates] - Develop your own microservices using our free and open-source templates 
- [LSQ Connect] (coming soon) - Share and test microservice applications
- [LSQ Cloud] (coming soon) - intelligent microservice discovery


[Microservices]: http://martinfowler.com/articles/microservices.html
[Building Microservices]: http://shop.oreilly.com/product/0636920033158.do
[Warehouse Computing and the Evolution of the Datacenter]: http://lennypruss.co/post/110633066423/warehouse-computing-and-the-evolution-of-the


[Compose.io]: http://compose.io

[LSQ Local]: https://lsq.io/#local
[LSQ microservice templates]: https://github.com/LSQio
[LSQ Connect]: https://lsq.io/#products
[LSQ Cloud]: https://lsq.io/#products
