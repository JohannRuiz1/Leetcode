
### REST
- Representational State Transfer
- Uses standard HTTP methods for resource manipulation
- Stateless and efficient
- Promotes a client-server relationship with separation of concerns
- Best for: simple, resource-oriented applications
- Why? REST is stateless and follows standard HTTP methods, making it easy to implement and scale CRUD operations in web apps

### GraphQL
- Query Language for APIs
- Allows clients to request specific data structure from servers
- Provides a single endpoint for flexible and efficient data retrieval 
- Best for: Flexible, efficient data fetching
- Why? Allows request only the needed data, minimizes over-fetching and under-fetching

### SOAP
- Simple Object Access Protocol
- Exchanging XML data between web services 
- Both stateful and stateless activities are supported
- Highly secure
- Best for: High-security, enterprise applications
- Why? XML-based and built with strict security standards, used in banking and healthcare that require ACID compliance and security protocols

### gRPC
- Google Remote Procedure Call
- High-performance RPC framework for Google
- Uses Protocol Buffers for data serialization and provides a structured 
- Strongly-typed contract for services
- Best for: High-performance, low-latency distributed systems
- Why? gRPC leverages HTTP/2 and protocol buggers for faster data transmission. It supports bidirectional streaming, making it perfect for microservice and mobile applications

### WebSockets
- Communication protocol providing full-duplex, bidirectional, real-time communication over a single, long-lived connection
- Best for: real-time applications (gaming, chat, live notifications)
- Why? Persistent, two-way communication between client and server, ensuring ultra-low latency for high-interactivity scenarios

### MQTT
- Msg Queuing Telemetry Transport
- Lightweight and efficient messaging protocol designed for low-bandwidth
- Publish-subscribe model for async communication, popular with IoT
- Best for: IoT applications
- Why? Lightweight protocol designed for low-bandwidth, power constrained decices. Pub-sub model makes it perfect for sensor-based systems 