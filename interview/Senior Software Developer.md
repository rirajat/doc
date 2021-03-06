# Senior Software Developer

__Table of Contains__
<!-- MarkdownTOC -->

- [Mehodology](#mehodology)
	- [Agile](#agile)
- [Testing](#testing)
- [Security](#security)
		- [Web Security](#web-security)
- [CI/CD](#cicd)
	- [Docker](#docker)
	- [Jankins](#jankins)
	- [Kubarnait](#kubarnait)
	- [Revision Control](#revision-control)
- [Microservice](#microservice)
	- [Kafka](#kafka)
	- [SOA](#soa)
		- [RestFull](#restfull)
		- [Soap](#soap)
- [Design pattrn](#design-pattrn)
	- [SOLID](#solid)
	- [MVC](#mvc)
	- [MVVM](#mvvm)
	- [TDD](#tdd)
	- [Architecture](#architecture)
- [Programming](#programming)
		- [Object Oriented Programming \(OOP\)](#object-oriented-programming-oop)
		- [C\](#c)
		- [ASP MVC](#asp-mvc)
		- [Java](#java)
			- [Spring boot](#spring-boot)
			- [Memory Management](#memory-management)
		- [JavaScript](#javascript)
- [Database](#database)
- [Appication Performance](#appication-performance)
	- [Code Profiling](#code-profiling)
- [The Right Way To Say “I Don't Know” In An Interview](#the-right-way-to-say-%E2%80%9Ci-dont-know%E2%80%9D-in-an-interview)
- [Question to ask at the end](#question-to-ask-at-the-end)
- [Some other question](#some-other-question)

<!-- /MarkdownTOC -->

---

<a id="mehodology"></a>
## Mehodology

<a id="agile"></a>
### Agile

__Velocity__ is the rate of which team progeresses by sprint.

__Scrum Ban__ is a Scrum and Kanban based model for the software develpement.

__Agile quality strategies.__
- Iteration
- Re-factoring
- Dynamic code analysis
- Short feedback cycles
- Reviews and inspection
- Standards and guidelines
- Milestone reviews

__Drawback of the Agile model__
- Hard to generate task effort
- Hard to focus on design and doc
- Unclear requirment cause delay
- Only leader can make any desition.

<a id="testing"></a>
## Testing 

__Traceability matrix__ relationship between test case nad requirments

__White box testing__ test code coverage, path coverage, condition coverage

__black box testing__ test code without knowing internal structure of code. Boundary value analysis

__Different testing levels__

- unit 
- integration
- system 
- acceptance

__Test Plans consists of__

- scope
- test case identifier
- features
- test stategy
- test approach
- responsibiities
- risk and contingencies

__UAT__ testing involves running a product through a series of specific tests which determines whether the product will meet the needs of its users

__System Testing__ is finding defects when the system undergoes testing as a whole; it is also known as end-to-end testing.

<a id="security"></a>
## Security

__How to store Password inside the code?__

- use *char* array
- stored it as *hashed* code

__Why it is more secure to store sensitive data in character array?__

In java string is immutable and are stored in string pool. this may not be remove after you finished using it because of GC. Charter array is mutable and you can set it to blank once you are done.

__Hash vs Encription__

*Hashing* - A hash is a string or number generated from a string of text. The resulting string or number is a fixed length, and will vary widely with small variations in input. The best hashing algorithms are designed so that it's impossible to turn a hash back into its original string.
Ex; 

- MD5
- SHA/SHA-1/SHA-2
	
*Encryption* - Encryption turns data into a series of unreadable characters, that aren't of a fixed length. The key difference between encryption and hashing is that encrypted strings can be reversed back into their original decrypted form if you have the right key. 
Ex; 

- AES 
- PGP

__Apache Shiro__ is an open source software security framework that performs authentication, authorization, cryptography and session management. Shiro has been designed to be an intuitive and easy-to-use framework while still providing robust security features.

<a id="web-security"></a>
#### Web Security

__How to mitigate the SQL Injection risks?__

- Prepared Statements 
- Stored Procedures
- Input Validation
- ORM

__What is Cross Site Scripting (XSS)?__

By using Cross Site Scripting (XSS) technique, users executed malicious scripts (also called payloads) unintentionally by clicking on untrusted links and hence, these scripts pass cookies information to attackers.

__What is ClickJacking?__

ClickJacking is an attack that fools users into thinking they are clicking on one thing when they are actually clicking on another. The attack is possible thanks to HTML frames (iframes). 

__role base security__

varify the role and identity

<a id="cicd"></a>
## CI/CD

__What's the difference between a blue/green deployment and a rolling deployment?__

In `Blue Green Deployment`, you have TWO complete environments. One is Blue environment which is running and the Green environment to which you want to upgrade. Once you swap the environment from blue to green, the traffic is directed to your new green environment. You can delete or save your old blue environment for backup until the green environment is stable.
    
In `Rolling Deployment`, you have only ONE complete environment. The code is deployed in the subset of instances of the same environment and moves to another subset after completion.

__What are the differences between continuous integration, continuous delivery, and continuous deployment?__

Developers practicing `continuous integration` merge their changes back to the main branch as often as possible. By doing so, you avoid the integration hell that usually happens when people wait for release day to merge their changes into the release branch.

`Continuous delivery` is an extension of continuous integration to make sure that you can release new changes to your customers quickly in a sustainable way. This means that on top of having automated your testing, you also have automated your release process and you can deploy your application at any point of time by clicking on a button.

`Continuous deployment` goes one step further than continuous delivery. With this practice, every change that passes all stages of your production pipeline is released to your customers. There's no human intervention, and only a failed test will prevent a new change to be deployed to production.

__What Is Sticky Session Load Balancing? What Do You Mean By *Session Affinity*?__

`Sticky session or a session affinity` technique is another popular load balancing technique that requires a user session to be always served by an allocated machine. 

In a load balanced server application where user information is stored in session it will be required to keep the session data available to all machines. This can be avoided by always serving a particular user session request from one machine. The machine is associated with a session as soon as the session is created. All the requests in a particular session are always redirected to the associated machine. This ensures the user data is only at one machine and load is also shared.
    
This is typically done by using SessionId cookie. The cookie is sent to the client for the first request and every subsequent request by client must be containing that same cookie to identify the session. 

<a id="docker"></a>
### Docker

__What is it?__

containerizing the applications to isolate it from each other in order to ensure high availability and more efficiency irrespective of the environments such as Development, Testing or Production

__The important three components are;__

-  *Server*: The server is the docker daemon called dockerd which can manage and create Docker containers, images, networks, etc
-  *Rest API*: Rest API controls docker daemon on its processes
-  *CLI*: Command Line Interface is a user interface that is used to input commands in the docker
-  *Docker Client*: Users of Docker can communicate with Docker via the host. 
-  *Docker Host*: This component contains Docker Daemon, Containers and its images.
-  *Docker Registries*: Docker hub is the storage place for Docker images of a public registry. 
-  *Docker Image* is a set of files and a combination of parameters which will allow creating the instances to run in separate containers as an isolated process.
-  *Docker hub* is a kind of repository to the images where these images can be stored and this access is public. 
-  *Docker Objects* are Docker Images,
-  *Docker Swarm* native gathering for docker which helps you to a group of Docker hosts into a single and virtual docker host
-  *memory-swap* is a modifier flag that only has meaning if --memory is also set. Using swap allows the container to write excess memory requirements to disk when the container has exhausted all the RAM that is available to it.
-  *Docker cient*; Docker provides Command Line Interface tools to the client to interact with Docker daemon. 
-  *monitor the docker*; Docker states and Docker Events 

__States of Docker container__

- Running
- Paused
- Restarting
- Exited
	
__Lifecycle of Docker Container;__

- Create a container.
- Run the Docker container.
- Pause the Container.
- Unpause the Container.
- Start the Container.
- Stop the Container.
- Restart the Container.
- Kill the Container.
- Destroy the Container.

__Commends__

- `docker run` – Runs a command in a new container.
- `docker start` – Starts one or more stopped containers
- `docker stop` – Stops one or more running containers
- `docker build` – Builds an image form a Docker file
- `docker pull` – Pulls an image or a repository from a registry
- `docker push` – Pushes an image or a repository to a registry
- `docker export` – Exports a container’s filesystem as a tar archive
- `docker exec` – Runs a command in a run-time container
- `docker search` – Searches the Docker Hub for images
- `docker attach` – Attaches to a running container
- `docker commit` – Creates a new image from a container’s changes

<a id="jankins"></a>
### Jankins

__Pre-requisites__ management repository like GIT or SVN repository and Build script.

__Agent__ It is directive to tell Jenkins to execute the pipeline in particular manner and order.

__Post-section__ If we have to add some notification and to perform other tasks at the end of a pipeline, 

__Jenkins file__: It is a text file having the information about Jenkins pipeline and is checked into source control.

__Command__
- `Jenkins.exe start` command helps in starting the Jenkins.
- `Jenkins.exe restart` to restart Jenkins and ‘Jenkins.exe stop’ to stop Jenkins.

__Pipeline__ 

A Pipeline’s code defines your entire build process, which typically includes stages for building an application, testing it and then delivering it.
- Node - A node is a machine which is part of the Jenkins environment and is capable of executing a Pipeline
- Stages - A stage block defines a conceptually distinct subset of tasks performed through the entire Pipeline
	- soner qube check
	- run unit test
	- build
	- deployed/promote
- Step - what to do at a particular point in time


<a id="kubarnait"></a>
### Kubarnait

__What is `Container Orchestration`?__

So, as orchestration means the amalgamation of all instruments playing together in harmony in music, similarly container orchestration means all the services in individual containers working together to fulfill the needs of a single server.

<a id="revision-control"></a>
### Revision Control

- Git
- SVN

<a id="microservice"></a>
## Microservice

__Service Discovery__ 

Identify the network location of the service

*Client‑Side Discovery* - the client is responsible for determining the network locations of available service instances and load balancing requests across them

*Server‑Side Discovery* - The load balancer queries the service registry and routes each request to an available service instance

*Service Registry* - It is a database containing the network locations of service instances.

__Semantic Monitoring__

Semantic monitoring along with service layer monitoring approaches monitoring of microservices from a business point of view. Once an issue is detected, they allow faster isolation and bug triaging, thereby reducing the main time required to repair. 

__PACT__ 

PACT is an open source tool. It helps in testing the interactions between consumers and service providers. 

<a id="kafka"></a>
### Kafka

__What are the elements of Kafka?__

- _Topic_: It is a bunch of similar kinds of messages.
- _Producer_: Using this, one can issue communications to the topic.
- _Consumer_: It endures to a variety of topics and takes data from brokers.
- _Broker_: This is the place where the issued messages are stored.

__Describe partitioning key__

Its role is to specify the target divider of the memo within the producer. Usually, a hash-oriented divider concludes the divider ID according to the given factors. Consumers also use tailored partitions.

__Elaborate the architecture of Kafka.__

In Kafka, a cluster contains multiple brokers since it is a distributed system. Topic in the system will get divided into multiple partitions, and each broker stores one or more of those partitions so that multiple producers and consumers can publish and retrieve messages at the same time.

<a id="soa"></a>
### SOA

<a id="restfull"></a>
#### RestFull

__Core Concept__

- Get (Retrieve)
- Post (Create)
- Put (Replace)
- Patch (Update)
- Delete (delete)

__Versioning__

- URI Path
- query parameters
- custom headers
- content negotiation

<a id="soap"></a>
#### Soap

<a id="design-pattrn"></a>
## Design pattrn

* Fault-tolerant distributed systems often handle failures in two steps: 
	- first, detect the failure and, 
	- second, take some recovery action. A common approach to detecting failures is end-to-end timeouts, but using timeouts brings problems.
* Anti-Corruption Layer
	- Implement a façade or adapter layer between different subsystems that don't share the same semantics. This layer translates requests that one subsystem makes to the other subsystem. Use this pattern to ensure that an application's design is not limited by dependencies on outside subsystems. This pattern was first described by Eric Evans in Domain-Driven Design.
* difference between cohesion and coupling?
	- Cohesion is the indication of the relationship within module. 
	- Coupling is the indication of the relationships between modules.
* A higher order function is a function that takes a function as an argument, or returns a function . 
	* A namespace is a declarative region that provides a scope to the identifiers (the names of types, functions, variables, etc) inside it. Namespaces are used to organize code into logical groups and to prevent name collisions that can occur especially when your code base includes multiple libraries.
* The Inversion of Control (IoC) and Dependency Injection (DI) patterns are all about removing dependencies from your code.
	```
	public class TextEditor {
	    private IocSpellChecker checker;
	    public TextEditor(IocSpellChecker checker) {
	        this.checker = checker;
	    }
	}
	```
* Dependency Injection - A class accepts the objects it requires from an injector instead of creating the objects directly. 
	- Constructor
	- Property
	- Method
* Singleton - Ensure a class has only one instance, and provide a global point of access to it. 
* Abstract factory - Provide an interface for creating families of related or dependent objects without specifying their concrete classes. 
* Builder - Separate the construction of a complex object from its representation, allowing the same construction process to create various representations. 
* Object pool- Avoid expensive acquisition and release of resources by recycling objects that are no longer in use. 
	- connection pool 
	- thread pool
* Prototype - create new objects from the 'skeleton' of an existing object, thus boosting performance and  - keeping memory footprints to a minimum. 
* Observer or Publish/subscribe - Define a one-to-many dependency between objects where a state change in one object results in all its dependents being notified and updated automatically. 
* Visitor - Represent an operation to be performed on the elements of an object structure.
* Event-based asynchronous - Addresses problems with the asynchronous pattern that occur in multithreaded programs

<a id="solid"></a>
### SOLID

* `Single Responsibility Principle`: 
	Class should have only one reason to change. 
* `Open and Closed Principle`: 
	Open for extension but closed for modification.
* `Liskov Substitution Principle`:
	This principle is foundation for building code that is maintainable and reusable.
* `Interface Segregation Principle`:
	The Interface Segregation Principle states that clients should not be forced to implement interfaces they don’t use.
* `Dependency Inversion Principle`:
	- High-level modules should not depend on low-level modules. Both should depend on abstractions.
	- Abstractions should not depend on details. Details should depend on abstractions.

<a id="mvc"></a>
### MVC
<a id="mvvm"></a>
### MVVM
<a id="tdd"></a>
### TDD
- You are not allowed to write any production code unless it is to make a failing unit test pass.
- You are not allowed to write any more of a unit test than is sufficient to fail; and compilation failures are failures.
- You are not allowed to write any more production code than is sufficient to pass the one failing unit test.

<a id="architecture"></a>
### Architecture

- Layered
- Event driven
- Microservice
- Monolithic

<a id="programming"></a>
## Programming

<a id="object-oriented-programming-oop"></a>
#### Object Oriented Programming (OOP)

__Object__ is an instance of a class.

__Class__ is simply a representation of a type of object.

__Constructor__ is a method used to initialize the state of an object, and it gets invoked at the time of object creation. 

__Destructor__ is a method which is automatically called when the object is made of scope or destroyed.

__Symbol table__ is an important data structure created and maintained by compilers in order to store information about the occurrence of various entities such as variable names, function names, objects, classes, interfaces, etc. The symbol table contains information to locate and relocate symbolic definitions and references. The assembler creates the symbol table section for the object file. It makes an entry in the symbol table for each symbol that is defined or referenced in the input file and is needed during linking.

__Core concept__

- Abstraction
- Encapsulation - public, private
- Inheritance - subclass
- Polymorphism - overwriting

__Abstract class vs interface__

*Abastract class*
- An abstract class permits you to make functionality that subclasses can implement or override whereas an interface only permits you to state functionality but not to implement it.
- An abstract class can have constructors
- An abstract class is a good choice if you have plans for future expansion  – i.e. if a future expansion is likely in the class hierarchy.

*Interface*
- You should use an interface if you want a contract on some behavior or functionality. You should not use an interface if you need to write the same code for the interface methods.
- An interface is basically a contract

In Java, an abstract class can implement an interface, and not provide implementations of all of the interface’s methods.  It is the responsibility of the first concrete class that has that abstract class as an ancestor to implement all of the methods in the interface.
- Abstract class can implement interface but do not need to implement the methord
- Interface can not implement interface

C# on the other hand seems to require that the abstract class provide implementations for all of the methods on the interface. Even if that implementation is just a method signature.

- Abstract class need to implement interface methord
- Interface can inharit from other interface
- An abstract class is a special type of class that cannot be instantiated

__Static__

- can not declare inside the methord
- The value is initialized when the class is loaded. Therefore each time you execute the code, it is initialized to the value "Java" as is defined in the class. The new value is not saved, it is only changed in memory and is "reset" when the code is executed again. 
- scope is defined only within the running program. everytime class is executed.
- It means the static variable are NOT global variable but only global to single execution!!!

C#

- class scope
- object can not access Static methord/var
- `Test t = null; t.StaticI - not accessable`

Java

- Static variables are "per class"
- object can access Static methord
- `Test t = null; t.StaticI - is accessable`

__Overloading and Overriding__

*Overloading* occurs when two or more methods in one class have the same method name but different parameters.

*Overriding* means having two methods with the same method name and parameters (i.e., method signature)

__Structure and Class__

The default access type of a Structure is public, but class access type is private. 
A structure is used for grouping data, whereas a class can be used for grouping data and methods. 

__Type of scope (C#/Java)__

- Class-Level Scope
- Method-Level Scope
- Nested Scope/Block scope
- dynamic scoping/lexical scoping/static scoping

__HashSet vs ArrayList__

- HashSet ensures there are no duplicates, gives you an O(1) contains() method but doesn't preserve order.
    - is a set
- ArrayList doesn't ensure there are no duplicates, contains() is O(n) but you can control the order of the entries.
	- is a list
- ArrayList is backed by an Array while HashSet is backed by an HashMap. 
- ArrayList maintains the order of the object in which they are inserted while HashSet is an unordered collection and doesn’t maintain any order. 
- ArrayList is index based we can retrieve object by calling get(index) method or remove objects by calling remove(index) method while HashSet is completely object based. 
- ArrayList not apply any restriction, we can add any number of null value while HashSet allow one null value. 

__context-switching in multi-threading__

*Context Switching* is the process of storing and restoring of CPU state so that Thread execution can be resumed from the same point at a later point of time. Context Switching is the essential feature for multitasking operating system and support for multi-threaded environment. 


<a id="c"></a>
#### C\#

__Can multiple catch blocks be executed?__

No, Multiple catch blocks can't be executed. Once the proper catch code executed, the control is transferred to the finally block, and then the code that follows the finally block gets executed. 

__What is Jagged Arrays?__

The Array which has elements of type array is called jagged Array. The elements can be of different dimensions and sizes. We can also call jagged Array as an Array of arrays. 

__What is the difference between ref & out parameters?__

An argument passed as ref must be initialized before passing to the method whereas out parameter needs not to be initialized before passing to a method. 

__What is serialization?__

When we want to transport an object through a network, then we have to convert the object into a stream of bytes. The process of converting an object into a stream of bytes is called Serialization. For an object to be serializable, it should implement ISerialize Interface. De-serialization is the reverse process of creating an object from a stream of bytes. 

__What is the difference between constants and read-only?__

Constant variables are declared and initialized at compile time. The value can't be changed afterward. Read-only is used only when we want to assign the value at run time. 

__sealed classes in C#__

Sealed classes are used to restrict the inheritance feature of object oriented programming. Once a class is defined as a sealed class, this class cannot be inherited. 

__Describe the accessibility modifier "protected internal".__

Protected Internal variables/methods are accessible within the same assembly and also from the classes that are derived from this parent class. 

__What are the differences between System.String and System.Text.StringBuilder classes?__

System.String is immutable. When we modify the value of a string variable, then a new memory is allocated to the new value and the previous memory allocation released. System.StringBuilder was designed to have a concept of a mutable string where a variety of operations can be performed without allocation separate memory location for the modified string. 

__What is the difference between Finalize() and Dispose() methods?__

Dispose() is called when we want for an object to release any unmanaged resources with them. On the other hand, Finalize() is used for the same purpose, but it doesn't assure the garbage collection of an object.

*Java does not have dispose. It has finalize only*

__What is an object pool in .NET?__

An object pool is a container having objects ready to be used. It tracks the object that is currently in use, total number of objects in the pool. This reduces the overhead of creating and re-creating objects. 

__What are delegates?__

A delegate is a type that represents references to methods with a particular parameter list and return type.

Delegates are same are function pointers in C++, but the only difference is that they are type safe, unlike function pointers. Delegates are required because they can be used to write much more generic type-safe functions.

__What are indexers in C# .NET?__

Indexers are known as smart arrays in C#. It allows the instances of a class to be indexed in the same way as an array. 

`public string this[int index] { get; set; }`

__Is C# code is managed or unmanaged code?__

C# is managed code because Common language runtime can compile

__difference between Virtual method and Abstract method?__

A Virtual method must always have a default implementation. However, it can be overridden in the derived class, though not mandatory. It can be overridden using override keyword.
		
An Abstract method does not have an implementation. It resides in the abstract class. It is mandatory that the derived class implements the abstract method. An override keyword is not necessary here though it can be used.

__What are Boxing and Unboxing?__

Converting a value type to reference type is called *Boxing*.

Explicit conversion of same reference type (created by boxing) back to value type is called *Unboxing*.

__multi-dimensional array?__

`int[,] numbers = new int[3,2] { {1,2} ,{2,3},{3,4} };`

__What is a Deadlock?__

A Deadlock is a situation where a process is not able to complete its execution because two or more processes are waiting for each other to finish. This usually occurs in multi-threading.

__What is Serialization?__

Serialization is a process of converting a code to its binary format. Once it is converted to bytes, it can be easily stored and written to a disk or any such storage devices. Serializations are mainly useful when we do not want to lose the original form of the code and it can be retrieved anytime in the future. 

*XML serialization* – It serializes all the public properties to the XML document. Since the data is in XML format, it can be easily read and manipulated in various formats. The classes reside in System.sml.Serialization.

*SOAP* – Classes reside in System.Runtime.Serialization. Similar to XML but produces a complete SOAP compliant envelope which can be used by any system that understands SOAP.  

*Binary Serialization* – Allows any code to be converted to its binary form. Can serialize and restore public and non-public properties. It is faster and occupies less space.

__What is Heap and what is Stack?__

- Both are memory locations, wherein Heap is global and Stack is local.
- The Stack has a defined first-in-first-out stack structure, while the Heap does not have a defined data structure.
- The Stack is faster than the Heap. A stack is in “cache” and doesn’t have to synchronize with other threads like the Heap.
- The Stack stores values while the Heap stores objects.

__What is LINQ?__

It is standardization to consult data and convert it into objects, regardless of the source. It is a query manager for databases, XML and enumerable collections using a single language.

__deferred execution and the immediate execution in LINQ__

A deferred execution encapsulates a query’s definition without executing it till the data is used at runtime.

By default, the executions are deferred but we can do them immediately by calling “To List ()”. 

__constants and read only variables?__

For constants, the compilation contains declaration and initialization. Its value cannot change. 

For read-only variables, the runtime execution contains the assignment of values. 

- Read-only variables can support reference-type variables. Constants can hold only value-type variables. 
- Developers evaluate read-only variables at the runtime. They evaluate constants at the compile time.
- Read only can be only assign through constractor

__Explain Mutex__

Threads share a mutually exclusive resource manager, Mutex. It ensures that only one thread at a time makes use of one resource (one object) at a time.

__What is Semaphore?__

Semaphores are used when we have to restrict how many threads can enter a critical region.

__What is Lock?__

Locks needs an object to continue its operation. It apply a lock on a target object and only one thread can lock that target object at a time. 

__What is ReaderWriterLockSlim?__

ReaderWriterLock is useful in multithreaded programs where mainly threads needs only read access and occasionally some thread want to update the shared data. 

__How can you make a Singleton class thread safe?__

To make singleton class thread-safe, we can apply double-check locking algorithm. In this algorithm, we can put two if conditions to check object is null or not. 

__Monitor Class__

Provides a mechanism that synchronizes access to objects. same as lock

	Monitor.Enter(s_lock);
	Monitor.Exit(s_lock); 

__Thread notification__

    foo.notify() => Monitor.Pulse(foo) // let thread run
	foo.notifyAll() => Monitor.PulseAll(foo)/Monitor.Push(this) // notify any waiting threads
	foo.wait() =>  Monitor.Wait(foo) //wait to finish the thread

__volatile__ 

The volatile keyword indicates that a field might be modified by multiple threads that are executing at the same time.

__What is immutability, what is it for and how is it codified?__

The ability of objects not to change their state, once created, helps improve the maintainability of the code. When a mutable object encapsulates its changes without being explicit in the code, following the flow becomes difficult. The level of difficulty increases in case of multi-threaded applications. To create immutable objects, pass the arguments for their creation in the constructor; make their properties read-only later.

__What is the difference between encrypting a password and applying a hashing?__

It is quite difficult (almost impossible) to decrypt a hashing (MD5 or SHA1, for example). The process of password validation compares the password in plain text with a hash to the stored one. Conversely, one can decrypt an encrypted password with access to the keys and the encryption algorithms (such as Triple-DES).

__What is a variable of implicit type and what is its scope?__

It is a variable that doesn’t require type declaration since the compiler automatically determines its type. Its scope is local, within a method. It only allows inferring the kind the first time it assigns a value

__Constractor, destractor, finalize, Dispose__

Constractor do not have return type not even void.

`~ClassName()` - destractor call finalize in object.

Dispose use IDispose interface.

__difference between Task and Thread in .NET__

The Task class from the Task Parallel Library offers the best of both worlds. Like the ThreadPool, a task does not create its own OS thread. Instead, tasks are executed by a TaskScheduler; the default scheduler simply runs on the ThreadPool. Unlike the ThreadPool, Task also allows you to find out when it finishes, and (via the generic Task) to return a result. 

Thread represents an actual OS-level thread, with its own stack and kernel resources. Thread allows the highest degree of control; you can Abort() or Suspend() or Resume() a thread, you can observe its state, and you can set thread-level properties like the stack size, apartment state, or culture. ThreadPool is a wrapper around a pool of threads maintained by the CLR.

__What is the "yield" keyword used for in C#?__

In the iterator block, the yield keyword is used together with the return keyword to provide a value to the enumerator object.

__abstract class__

abstract class can not be 'sealed' or 'static'

<a id="asp-mvc"></a>
#### ASP MVC

__trafer data__

- Model
- ViewBag
- ViewData
- TempData

__Filter__

ASP.NET MVC Filter is a custom class where you can write custom logic to execute before or after an action method executes.

__ActionFilter__

Action filter executes before and after an action method executes.

__Routing__

Routing to eliminate needs of mapping each URL with a physical file.

__Action Selectors__

Action selector is the attribute that can be applied to the action methods.

*ActionName* attribute allows us to specify a different action name than the method name.

*NonAction* selector attribute indicates that a public method of a Controller is not an action method.

The *ActionVerbs* selector is used when you want to control the selection of an action method based on a Http request method.

__Model Binding__

Model binding is a well-designed bridge between the HTTP request and the C# action methods.

<a id="java"></a>
#### Java

__Do all the properties of an Immutable Object need to be final in Java?__

Not necessary. You can achieve the same functionality by making a member non-final but private and not modifying them except in the constructor.

__Private static__

only visible inside the class and which has only 1 copy, shared by all instances of the class.

__What’s wrong with using HashMap in the multi-threaded environment? When does the put() method go to the infinite loop?__

Well, nothing is wrong; it just depends upon how you use it. For example, if you initialize a HashMap by just one thread and all threads are only reading from it, then it’s perfectly fine.

Since the put() operation can cause re-sizing and lead to an infinite loop, that’s why either you should use Hashtable or ConcurrentHashMap, later is even better.

__Can you write a critical section code for the singleton?__

	public class Singleton {
	    private static volatile Singleton _instance;
	    public static Singleton getInstance() {
	        if (_instance == null) {
	            synchronized (Singleton.class) {
	                if (_instance == null) {
	                    _instance = new Singleton();
	                }
	            }
	        }
	        return _instance;
	    }
	}

__Fail-fast vs Fail-safe__

*fail-fast* - fail as soon as they relalize; ie. ArrayList

*fail-safe* - handel the failure; ie. ConcurrentHashMap

__ThreadLocal__

A single ThreadLocal instance can store different values for each thread independently. 

In Java, each thread has its own stack, including its own copy of variables it can access. When the thread is created, it copies the value of all accessible variables into its own stack. The volatile keyword basically says to the JVM “Warning, this variable may be modified in another Thread”.

__Catch an exception thrown by another thread__

	Thread.UncaughtExceptionHandler

__Why interface needed?__

Multiple inheritance cannot be achieved in java. To overcome this problem Interface concept is introduced.

__Method references__

Method references were introduced in Java 8 and allow constructors and methods (static or otherwise) to be used as lambdas.

__Enums__
Enums are essentially final classes with a fixed number of instances. They can implement interfaces but cannot extend another class.

__static initializers__

A static initializer gives you the opportunity to run code during the initial loading of a class and it guarantees that this code will only run once and will finish running before your class can be accessed in any way.

	public static final Map<String, Boolean> FEATURE_FLAGS;
    static {
        Map<String, Boolean> flags = new HashMap<>();
        flags.put("frustrate-users", false);
        flags.put("reticulate-splines", true);
        flags.put(...);
        FEATURE_FLAGS = Collections.unmodifiableMap(flags);
    }

__Difference between Array and Array List.__

Array size is declared

ArrayList size not requeired

__Difference between String, String Builder, and String Buffer.__
		
*String* imutable
		
*String Buffer* store in stack and mutable and replace old value with new. Its sencronized and thread safe.

*String builder* is not thread save same as string buffer.

__HashMap and HashTable.__

*HashMap* not syncronize and thread safe.
		
*HashTable* synchronized and thread safe.

__yield method__

A yield method moves the currently running thread to a  runnable state and allows the other threads for execution

__Difference between notify() method and notifyAll() method in Java.__
		
`notify`; send a signal to wake up a single thread
		
`notifyall`; sends signal to wake up all the threads

<a id="spring-boot"></a>
##### Spring boot

__What is Spring Boot?__

Spring Boot is another Java framework from Sring umbrella

__feature__

- starter dependency
- auto-config
- spring initializer
- spring actuator
- spring cli

__Starter dependency__

allow you to see inside the running spring boot application
		
__Inversion of Control, or IoC__

process in which an object defines its dependencies without creating them.
		
__Bean__ 

Code managed by spring framework

- singleton scope
- propttype scope - create new bean everytime
- request scope - create bean in every http request
- session scope - http session lifetime
- global scope - create bean in global session and can be shared in other session.

__Autowired__

allows spring to resolve and inject collaboration beans.

- Properties
- Setters
- Constrator
- Optional autowired
- Qualifer - use to hint at and narrow down the required bean.
- Custom Qualifier 

<a id="memory-management"></a>
##### Memory Management

__jps__ - show all memory info

`jstack -l 11568 > thread_dump.txt` - send all thread dump in the file

`kill -3 11568` - kill the process

__Applicaiton use to identify memory__

- JProfiler
- visualvm

__Java Memory managemnt looks like__

Hip space and metaspace

__Java memory level__

- eden
- S0
- S1
- Old memory
- Perm

<a id="javascript"></a>
#### JavaScript

- Promis
- EmberJs
- VouJs
- Angular

<a id="database"></a>
## Database

__Type of databases__

- RDMS: SQLServer, MySql, Postgrad, Oracal
- NoSql: MongoDb, Casandra, Readis
- Graph Database: Neo4j

__Database Performance__

- Make Sure Snapshot Mode Is On
- indexing
- avoid fragment indexing
- run missing index report
- monitor database session
- profiling sql query
- Dynamic Management Views (DMV’s) Used
	- identify slow query
- Join

__Hibernate__

*session* - session is used to get a new connection

*transient* - new instant of a persistent class

*persistent* - instance has a representaion in the database

*detached* - close the session persistent instance will be detached

__JPA__

__ACID__

set of properties of database transactions intended to guarantee validity even in the event of errors, power failures, etc.

*Atomicity* -  Atomicity guarantees that each transaction is treated as a single "unit", which either succeeds completely, or fails completely: if any of the statements constituting a transaction fails to complete, the entire transaction fails and the database is left unchanged.

*Consistency* - Consistency ensures that a transaction can only bring the database from one valid state to another,

*Isolation* -  Isolation is the main goal of concurrency control; depending on the method used, the effects of an incomplete transaction might not even be visible to other transactions.

*Durability* - Durability guarantees that once a transaction has been committed, it will remain committed even in the case of a system failure

__SQL vs. no SQL__

SQL databases are primarily called as Relational Databases (RDBMS); whereas NoSQL database are primarily called as non-relational or distributed database.

__Improve Performance__

- Optimize Queries
- Create optimal indexes
- Update CPU
- Allocate more memory
- Data defragmentation
- Disk Types
- Database version
- Stream data

__Reading Large number of data__

- Chunking your data
- Dropping data
- Set specific data types for each column

__Faster query__

- Use only the correct number of columns you need
- Reduce nested views to reduce lags
- Use automatic partitioning SQL server features
- Convert scalar functions into table-valued functions
- Avoid sub query
- Create a Highly Selective Index
- Data pre-staging
	-Data pre-staging means you can have your reports faster. Join data tables ahead of reporting, presentation or writing time to avoid joining them together at once.
- Use temp tables
	- Temporary tables come in handy in several situations, especially when you are joining a small table to a larger one.
- Avoid negative searches
	- Nothing slows data as much as carrying out negative searches. To avoid this, rewrite your queries with better indexes, especially for large amounts of data.
- Avoid cursors
- Do not use Globally Unique Identifiers 
- Avoid triggers
- Separate large and small transactions
- use stored procedures

Architecture

- Horizontal scaling means that you scale by adding more machines into your pool of resources
- Vertical scaling means that you scale by adding more power (CPU, RAM) to an existing machine.

<a id="appication-performance"></a>
## Appication Performance

__Tranfer Large data__

- Batch processing
- Parallel processing

__Large Data Files__

- Allowed more memory
- worked with small smaple
- change data formate
- strem data
- prograssive loading
- big data platfrom

__Reading large number of data__

- Stream

__High performance__

- Up time
	- kubarnati
- parallal processing
	- Invoice file thransfer form ftp. 7 diff files
- fail safe
	- kubarnati can restart after shoutdonw
- high throughput
	- bratch processing
	- edge computing
	- kafka messing
	- in memory database
	- cacheing
- continuous monitoring
	- dynatrace
- rollout deployment
	- jankins & OpenShift
- scalabelity
	- kubarnati auto scalling
- Loggin

__Session__

In computer science and networking in particular, a session is a temporary and interactive information interchange between two or more communicating devices, or between a computer and user.

The session can be stored on the server, or on the client. If it's on the client, it will be stored by the browser, most likely in cookies and if it is stored on the server, the session ids are created and managed by the server

<a id="code-profiling"></a>
### Code Profiling

__C\#__

- VS code profiling
- RedGate ANTS
- dotTrace

__Java__

- VisualVM
- JProfiler
- Dynatrace: JVM profiling in production

__JavaScript__

- Chrome dev-tools

__Database__

- SQL sever profiler

<a id="the-right-way-to-say-%E2%80%9Ci-dont-know%E2%80%9D-in-an-interview"></a>
## The Right Way To Say “I Don't Know” In An Interview

- Take some time to think. It's perfectly acceptable to take a moment to breathe and think before launching into an answer. ...
- Ask clarifying questions. ...
- Know when to say “I don't know.” ...
- Take the opportunity to follow up.

<a id="question-to-ask-at-the-end"></a>
## Question to ask at the end

- What opportunities will I have to learn and grow?
- Which part of the position has the steepest learning curve? What can I do in order to get up to speed quickly?
- day-to-day responsibilities of this job?
- What do you think are the most important qualities for someone to excel in this role?
- What are the biggest opportunities facing the company/department right now?
- What are the biggest challenges facing the company/department right now?
- What do you like best about working for this company?

<a id="some-other-question"></a>
## Some other question

__A time you held a leadership position__

Cargo mangement application, Invoice transfer, 

__A time you had to present__

Reotinto, 

__A time you went above and beyond for an asignment__

Invoide management, CDR transfer, Airlines interline
