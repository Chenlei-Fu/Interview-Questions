# API
### REST
REST is not a specific web service but a design concept (architecture) for managing state information. It's an Architectural Styles and the Design of Network-based Software Architectures. 
The most basic way of thinking about REST is as a way of formatting the URLs of your web applications.

Fundamental REST Principles:
1. Client-Server Communication
2. Stateless
We next add a constraint to the client-server interaction: communication must be stateless in nature, as in the client-stateless-server (CSS) style, such that each request from client to server must contain all of the information necessary to understand the request, and cannot take advantage of any stored context on the server. Session state is therefore kept entirely on the client.

3. Cache
In order to improve network efficiency, we add cache constraints to form the client-cache-stateless-server style. Cache constraints require that the data within a response to a request be implicitly or explicitly labeled as cacheable or non-cacheable. If a response is cacheable, then a client cache is given the right to reuse that response data for later, equivalent requests.

4. Uniform Interface
All components must interact through a single uniform interface. Because all component interaction occurs via this interface, interaction with different services is very simple.

**REST service is a web service, but a web service is not necessarily a REST service.**


### Maven
Maven is a "build management tool", it's for defining how your .java files get compiled to .class, packaged into .jar (or .war or .ear) file, (pre/post) processed with tools, managing your CLASSPATH, and all others sorts of tasks that are required to build your project. 
It attempts to be completely self-contained in it that you shouldn't need any additional tools or scripts by incorporating other common tasks.
It's also designed around the "build portability" theme, so that you don't get issues as having the same code with the same buildscript working on other computers. 

**Why you should use it?**
1. Maven will download all the libraries that you use and the libraries that they use for you automatically. This let you avoid dependency hell
2. It uses "Convention over Configuration" so that by default you don't need to define the tasks you want to do. You don't need to write a "compile", "test", "package", or "clean" step like you would have to do in Ant or a Makefile.
3. Maven also has lots of nice plug-ins that you can install that will handle many routine tasks. Just add them to your pom.xml and they will integrate with everything else you want to do.


