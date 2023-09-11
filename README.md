

The underlying principles and principles of RPC and the application of various Java coding practices.



1. **Registration Center**: The first thing to have is a registration center. It is recommended to use Zookeeper. The registration center is responsible for the registration and search of service addresses, which is equivalent to directory services. When the server starts, the service name and its corresponding address (ip+port) are registered in the registration center, and the service consumer finds the corresponding service address based on the service name. After having the service address, the service consumer can request the server through the network.
2. **Network transmission**: Since you want to call a remote method, you must send a request. The request must at least contain the class name, method name and related parameters you call! The Netty framework based on NIO is recommended.
3. **Serialization**: Since network transmission is involved, serialization must be involved. You cannot directly use the serialization that comes with JDK! The serialization that comes with the JDK is inefficient and has security vulnerabilities. Therefore, you also need to consider which serialization protocol to use. The more commonly used ones are hession2, kyro, and protostuff.
4. **Dynamic Agent**: In addition, dynamic agent is also needed. Because the main purpose of RPC is to make calling remote methods as simple as calling local methods, using a dynamic proxy can shield the details of remote method calls such as network transmission. That is to say, when you call a remote method, the network request will actually be transmitted through the proxy object. Otherwise, how could the remote method be called directly?
5. **Load Balancing**: Load balancing is also needed. Why? For example, a service in our system has a particularly large number of visits. We have deployed this service on multiple servers. When a client initiates a request, multiple servers can handle the request. Then, how to correctly choose the server to handle the request is critical. If you need one server to handle requests for the service, then the meaning of deploying the service on multiple servers no longer exists. Load balancing is to prevent a single server from responding to the same request, which can easily cause server downtime, crashes and other problems. We can clearly feel its meaning from the four words of load balancing.
6.......

###Basic situation of the project and optimization points

Based on the traditional **BIO** method **Socket** for network transmission, and then using the **JDK's own serialization mechanism** to implement this RPC framework

**Java**:

1. Dynamic proxy mechanism;
2. Comparison of serialization mechanisms and various serialization frameworks, such as hession2, kyro, and protostuff.
3. Use of thread pool;
4. Use of `CompletableFuture`
5.......

**Netty**:

1. Use Netty for network transmission;
2. Introduction to `ByteBuf`
3. Netty sticky package unpacking
4. Netty long connection and heartbeat mechanism

**Zookeeper** :

1. Basic concepts;
2. Data structure;
3. How to use Netflix’s open source zookeeper client framework Curator to perform additions, deletions, modifications, and queries;


