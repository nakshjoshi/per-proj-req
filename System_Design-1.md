# System Design for Beginners

- **Client** is basically the user making a request to the **server**.
- A **server** is a machine that's expected to be up 24/7. It should have a public IP address and can be located anywhere in the world.
- Think of a **Virtual Machine (VM)** as an emulated computer inside a real one.
- **DNS (Domain Name System)** helps map human-readable domain names to IP addresses.

---

## Server Overload and Fault Tolerance

- If too many users request something at once, and the server doesn't have enough physical resources, it can **crash**.
- Even if a system is **fault-tolerant**, there's still a limit to how much it can handle.
- We should utilize resources efficiently—**over-optimization is also bad**, it can lead to wastage.

---

## Scaling Techniques

### Vertical Scaling
- This means adding more resources (like CPU, RAM, GPU) to a **single machine**.
- But it's not possible to add resources to a running machine. We need to **restart** it, causing **downtime**.
- Since there’s only one machine, we don’t need a load balancer.

### Horizontal Scaling
- Here, we add **multiple machines in parallel** to avoid downtime.
- But these machines will all have **different IP addresses**, and DNS can only point to **one**.
- So, we use a **Load Balancer (LB)** as an intermediate server. The DNS sends the user to the LB, and the LB distributes traffic to available servers.

---

## Load Balancer and Health Checks

- Load Balancers use algorithms like **Round Robin** to distribute traffic.
- When a new server is added, the LB is informed.
- It checks whether the server is **healthy** before forwarding requests to it.
- Amazon calls this **Elastic Load Balancing**, and the load balancer itself has strong resources.

---

## Microservice Architecture

- Every functionality (auth, order, payments, etc.) is handled by a **separate microservice** running on its own server(s).
- Each microservice can have its own **horizontal scaling** and **load balancer**.
- The **API Gateway** handles routing to the correct microservice and acts as a **centralized entry point**.
- You can also **attach an Auth Service** to the API Gateway for security.
- On AWS: `User -> API Gateway -> Microservices`

---

## Queueing Systems and Async Handling

- Use **Amazon SQS (Simple Queue Service)**, a **pull-based mechanism**, for **batch processing**.
- This helps when handling lots of time-consuming requests asynchronously.
- The service continues accepting requests while some tasks are processed in the background using a queue.

### CSV Queue
- Conceptually used to queue multiple data inputs for later processing.

---

## Rate Limiting

- Helps to **prevent DDoS attacks** by blocking requests after a certain number per second or minute.
- Strategies include:
  - **Leaky Bucket**
  - **Token Bucket**

---

## PUB-SUB Model

- With **SNS (Simple Notification Service)**, a single gateway can notify multiple channels.
- This is an **event-driven architecture** and usually doesn’t wait for acknowledgments.
- If a notification channel fails (like external service down), there’s:
  - **No callback**
  - Either requeue the message or use a **Dead Letter Queue (DLQ)** to handle failures.

### Fanout Pattern
- One message gets **sent to multiple services** like email, inventory, shipping.
- Helps different parts of the system operate independently.

---

### Q: What is the difference between Fanout and SNS Pub-Sub?

**A:**  
Both are types of pub-sub models, but:
- **Fanout** is when a **single event triggers multiple independent services** (like parallel branches).
- **SNS Pub-Sub** refers more generally to a **pub-sub system**, not necessarily all services have to act or acknowledge. SNS can implement fanout.

---

## Database Scaling

- You can **scale the database** by creating **read replicas**.
- The **primary node** handles all **writes/inserts**.
- **Read replicas** only handle reads to reduce the load on the primary.

### Q: When do you use the primary node vs read replicas?

**A:**  
- Use the **primary node** for all write operations.
- Use **read replicas** when you want to handle large volumes of read operations, like displaying data.

---

## Caching

- Tools like **Redis** help store frequent data in memory.
- This provides **faster responses** and takes the load off the database.
- The system first **checks the cache**. If it’s a **cache miss**, it fetches from the DB and stores it in the cache.
- Useful for **repetitive and complex computations**.

---

## CDN (Content Delivery Network)

- Services like **CloudFront** act as a CDN **before the load balancer**.
- The user's request goes to the **nearest CloudFront node**, which then routes to the **load balancer IP**.
- CDNs use **Anycast**, meaning:
  - Same IP is used by multiple global servers.
  - Requests are automatically routed to the **nearest/fastest** server.

---

### Q: If I want to query something, how does the region’s CDN cache help?

**A:**  
If the data already exists in your region’s **CloudFront cache**, the request is served **very fast**.  
If not, the CDN **fetches it from the origin server or load balancer** and may cache it for future use.
