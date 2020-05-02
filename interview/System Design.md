# System Design

__Ref__

https://capitalone.github.io/architecture-viewer/?url=https://raw.githubusercontent.com/capitalone/architecture-viewer/master/sample_plantuml_data/example.adoc

https://docs.microsoft.com/en-us/azure/architecture/best-practices/api-design

__Old Design__ 

- Monolithic, centralized
- Predicted scalability
- RDMS
- Strong consistency
- Design to avoid failures
- Big update
- Manual management
- Snowflake serers

__New Design__

- Decomposed, de-centralized
- Elastic scale
- mix of storage
- parallel and asyn processing
- design for failure
- small update
- auto self management
- immutable infrastructure

## System Design Basic

__Some of the elements are followed__

- Design and redesign of business processes.
- Defining Data Models.
- Defining the events and their procedure.
- Designing of Applications.
- Designing how the different services, process, events, and data will work together.
- Defining how the system will be secured
- Defining the technologies that will be used such as applications, components, toolsets, APIs and libraries.

__The various subsets of System Design__

*Logical Design*

It is the abstract representation of the data flow, inputs, and outputs of the system. It explains the sources, destinations, data stores and data flows all in a process that satisfies the user needs. The logical design of a system is prepared while keeping the level of detail that virtually tells the information flow and out of the system in mind. The `data flow` and `E-R diagrams` are used respectively.

*Physical Design*

The process of actual input and output of the system is related to physical design. The main criteria of physical design are to manage how the data is verified, processed and displayed as the result. It basically revolves around the interface design, process design and data design of the user.

*Architectural Design*

It is also called the high level of design that emphasizes the design of system architecture. It explains the nature and root of the system.

*Detailed Design*

It follows the Architectural Design and emphasizes on the development of every subject.

__Working with System Design__

*Program Documentation*; 
It explains the inputs, outputs and processing logic for all the program courses.

*System Documentation*;
It describes the system functions and the way they are implemented.

*Operations Documentation*;
It explains the program, system analyst, programmer, and system identification.

*User Documentation*;
It includes steps and information to the users who will communicate with the system.

__Advantages of System Design__

- It reduces the cost of designing.
- It eliminates inconsistencies.
- It speeds up the process.
- It makes the life of the customer easier and simpler.
- It provides a lot of resources.


__Why should we use System Design?__

- *Reliability*; means the ability of a system to tolerate faults 
	- Hibread cloud system
	- Kubarnati
- *Scalability*; is the system’s ability to deliver reasonable performance in face of increased load.
	- Docker or contanarization
	- Kubarnati; auto scale
	- Cloud
- *Maintainability*; means writing code that can easily be understood, refactored and upgraded by someone who is not the original author of the code.
	- Code review
	- SonarQube 
	- Continiouse learing

## Architecture styles

__N-tier__

N-tier is a traditional architecture for enterprise applications. Dependencies are managed by dividing the application into layers that perform logical functions, such as presentation, business logic, and data access. A layer can only call into layers that sit below it. However, this horizontal layering can be a liability. 

*Prob* <br/>
It can be hard to introduce changes in one part of the application without touching the rest of the application. That makes frequent updates a challenge, limiting how quickly new features can be added.

*Used* <br/>
N-tier is a natural fit for migrating existing applications that already use a layered architecture. 

__Web-Queue-Worker__

In this style, the application has a web front end that handles HTTP requests and a back-end worker that performs CPU-intensive tasks or long-running operations. The front end communicates to the worker through an asynchronous message queue.

*Prob* <br/>
The use of managed services simplifies deployment and operations. But with complex domains, it can be hard to manage dependencies. The front end and the worker can easily become large, monolithic components that are hard to maintain and update. 

__Microservices__

A microservices application is composed of many small, independent services. Each service implements a single business capability. Services are loosely coupled, communicating through API contracts.

*Used*

- build small
- small dev team
- lot of coordination between teams
- frequent updates
- faster innovation
- more resilient architecture

__Event-driven architecture__

a publish-subscribe (pub-sub) model, where producers publish events, and consumers subscribe to them. The producers are independent from the consumers, and consumers are independent from each other.

*Used*

- process a large volume
- very low latency
- when diff sub system perform diff type of proesses

__Big Data, Big Compute__

*Big data* divides a very large dataset into chunks, performing parallel processing across the entire set, for analysis and reporting. 

*Big compute*, also called high-performance computing (HPC), makes parallel computations across a large number (thousands) of cores. 

## API Design

### RESTFull

- designed around resources, which are any kind of object, data, or service that can be accessed by the client.
- A resource has an identifier, which is a URI that uniquely identifies that resource. Ex; `https://adventure-works.com/orders/1`
- Clients interact with a service by exchanging representations of resources.
- REST APIs use a uniform interface, which helps to decouple the client and service implementations.
- REST APIs use a stateless request model. 
- REST APIs are driven by hypermedia links that are contained in the representation. Ex;
```
{
    "orderID":3,
    "productID":2,
    "quantity":4,
    "orderValue":16.60,
    "links": [
        {"rel":"product","href":"https://adventure-works.com/customers/3", "action":"GET" },
        {"rel":"product","href":"https://adventure-works.com/customers/3", "action":"PUT" }
    ]
}
```

__Operation__

- _GET_ retrieves a representation of the resource at the specified URI. The body of the response message contains the details of the requested resource.
- _POST_ creates a new resource at the specified URI. The body of the request message provides the details of the new resource. Note that POST can also be used to trigger operations that don't actually create resources.
- _PUT_ either creates or replaces the resource at the specified URI. The body of the request message specifies the resource to be created or updated.
- _PATCH_ performs a partial update of a resource. The request body specifies the set of changes to apply to the resource.
- _DELETE_ removes the resource at the specified URI.

__Filter and paginate data__

GET requests over collection resources can potentially return a large number of items. You should design a web API to limit the amount of data returned by any single request.
```
/orders?limit=25&offset=50
```
Also consider imposing an upper limit on the number of items returned, to help prevent Denial of Service attacks. 

__How to send large resources with GET__

- send by chunks of resources
- API should support the _Accept-Ranges_ header. This indicates GET operation supports partial requests.
- consider implementing _HTTP HEAD_ requests for these resources

## Database Design

__Why your should choose `relational database`?__

- Relational schemas are always a good first default choice.
- You need to enforce strict schema on write constraints.
- maintain zero data redundancy
- data model has many to one and many to many relationships.

__Why your should choose `NoSql database`?__

- if your data model exhibits a tree like, one to many relationships, using a NoSQL database might make more sense.

- self contained JSON document.
- Lastly in case your data model does not have a fixed schema, going the NoSQL route might make more sense.

__Why your should choose `Graph database`?__

- data model needs to support many ‘many-many’ relationships. 
- easily extending relationships between heterogeneous objects.
