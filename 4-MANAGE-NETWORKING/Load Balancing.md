# Load Balancing

![Load Balancing](https://private-us-east-1.manuscdn.com/sessionFile/PELdhIFr8k4l8jvbPIIMbc/sandbox/aYxk5uAwRLLxbEoe3HlKhb-images_1778005339181_na1fn_L2hvbWUvdWJ1bnR1L2F6dXJlX25ldHdvcmtpbmdfZGlhZ3JhbXMvaW1hZ2VzL2xvYWQtYmFsYW5jaW5n.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvUEVMZGhJRnI4azRsOGp2YlBJSU1iYy9zYW5kYm94L2FZeGs1dUF3UkxMeGJFb2UzSGxLaGItaW1hZ2VzXzE3NzgwMDUzMzkxODFfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwyRjZkWEpsWDI1bGRIZHZjbXRwYm1kZlpHbGhaM0poYlhNdmFXMWhaMlZ6TDJ4dllXUXRZbUZzWVc1amFXNW4ucG5nIiwiQ29uZGl0aW9uIjp7IkRhdGVMZXNzVGhhbiI6eyJBV1M6RXBvY2hUaW1lIjoxNzk4NzYxNjAwfX19XX0_&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=ub3R6~YXlZGS-UnJzlJ6sFAn19vSzh8-b4FN3TC95u-9Of3~N43Po6HQNuDhOoAyz0HtBkTD1Y-El05nrw6V54EaZzhlLOsmWWe7rjsNvtv4zPGY1OdrW7vEU7KAct-sQlPUw8l3yhTSdfOWM2CmeZxTaetlR8Lc2-mDrkX44TdLiR9CT0n-oO5~MAJn0dyxWcYoPAWmXlZ~bWXWa83AACUSIIT-ymN4ueJ9CmlQ2llR3ztvotCDYTWLOhxrkbC7IYgulvNjM0u~xr0xuYv6TwHIiqJRRWI6R25jbcRdfElfZ40K9Y6KdYkPwh606ZA~w6-GxOyjaLeVAhaVBvRaRA__)

## Overview

Load Balancing is a critical architectural pattern used to distribute incoming client requests across multiple servers. As illustrated in this diagram, the primary goals of load balancing are to ensure high availability, enable scalability, and maintain optimal performance for applications. By acting as a single entry point, the load balancer abstracts the complexity of the backend infrastructure from the end-users.

Understanding how load balancers operate is fundamental for designing resilient cloud applications that can handle varying levels of traffic without downtime.

> **Learn how to design highly available architectures on [Cloud360](https://cloud360.co) and watch our load balancing tutorials on the [Cloud360 YouTube Channel](https://www.youtube.com/channel/UCs005hN86JSDg4PghrhZVjg).**

---

## 1. The Client Request Flow

The process begins with the **Clients**—users accessing the application via web browsers (Web User 1, Web User 2) or mobile devices (Mobile User 1, Mobile User 2). 

These users send requests over the **Internet**. Instead of connecting directly to an individual application server, all incoming requests are routed to the **Load Balancer**. The load balancer acts as a reverse proxy, presenting a single IP address (or DNS name) to the public, effectively hiding the backend servers.

---

## 2. Core Load Balancer Functions

The Load Balancer performs several critical functions to manage traffic effectively:

### Traffic Distribution
The primary job is to distribute traffic to the backend servers (App Server 1, App Server 2, App Server 3). The diagram highlights **Round-Robin Distribution**, a common algorithm where requests are distributed evenly across healthy servers in a sequential, circular order. Other algorithms include Least Connections (sending traffic to the server with the fewest active connections) or IP Hash (routing based on the client's IP address).

### Health Checks
A load balancer is only effective if it routes traffic to servers that are actually working. It continuously monitors server health using **Health Checks** (e.g., pinging a specific URL or checking a port). In the diagram, App Servers 1, 2, and 3 are marked as "Healthy" (green checkmark), while one server is marked as a "Failed Server" (red X) because it is unhealthy or overloaded.

### Failover
When a health check fails, the load balancer initiates a **Failover**. It immediately stops sending traffic to the failed server and automatically redirects those requests to the remaining healthy servers. This ensures that users do not experience errors or downtime, even if underlying hardware or software fails.

---

## 3. Backend Infrastructure

The backend infrastructure behind the load balancer typically consists of multiple tiers to handle processing and data storage efficiently.

- **App Servers**: These servers process the business logic. Because the load balancer distributes the work, these servers can be scaled horizontally (adding more servers) to handle increased load.
- **Cache Layer**: To improve performance, App Servers often query a Cache Layer (like Redis or Memcached) before hitting the database. This stores frequently accessed data in memory for rapid retrieval.
- **Database Tier**: The persistent storage layer, often consisting of a Primary DB for write operations and Read Replicas to offload read queries, further distributing the load at the data tier.

---

## 4. Key Benefits of Load Balancing

The bottom section of the diagram outlines the six primary benefits of implementing a load balancing solution:

1. **High Availability**: Ensures no single server is a single point of failure. If one server goes down, others continue handling requests seamlessly.
2. **Scalability**: Allows organizations to easily scale out by adding more servers behind the load balancer to handle increased traffic, without changing the client-facing endpoint.
3. **Session Handling**: Also known as "sticky sessions" or session persistence. The load balancer can be configured to route a specific user to the same backend server for the duration of their session, which is necessary for certain types of applications.
4. **Security & SSL Offload**: The load balancer can handle SSL/TLS termination. This means it decrypts incoming HTTPS traffic, inspects it, and then forwards it (often unencrypted) to the backend servers. This offloads the CPU-intensive decryption process from the app servers and provides a centralized point to filter malicious traffic.
5. **Centralized Management**: Simplifies the administration of the environment. Administrators can monitor, configure, and update backend servers from a single control point without disrupting service.

---

## Exam Relevance (AZ-104, AZ-305)

For Microsoft Azure certification exams, it is crucial to understand the different load balancing options available:

- **Azure Load Balancer**: Operates at Layer 4 (TCP/UDP). Best for high-performance, low-latency network traffic distribution. It does not understand HTTP/HTTPS.
- **Azure Application Gateway**: Operates at Layer 7 (HTTP/HTTPS). Best for web traffic. It supports URL path-based routing, SSL termination, and includes a Web Application Firewall (WAF).
- **Azure Front Door**: A global, Layer 7 load balancer and Content Delivery Network (CDN) for web applications.
- **Azure Traffic Manager**: A DNS-based traffic load balancer that enables you to distribute traffic optimally to services across global Azure regions.

> **Ready to implement robust load balancing in Azure? Visit [Cloud360](https://cloud360.co) for expert architectural guidance and subscribe to the [Cloud360 YouTube Channel](https://www.youtube.com/channel/UCs005hN86JSDg4PghrhZVjg) for practical implementation tutorials.**
