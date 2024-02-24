# AWS Elastic Load Balancing (ELB)

AWS Elastic Load Balancing (ELB) automatically distributes incoming application traffic across multiple targets, such as EC2 instances, containers, IP addresses, and Lambda functions, to ensure that no single resource becomes overwhelmed. ELB helps improve the availability and fault tolerance of your applications by evenly distributing traffic and automatically scaling to meet demand.

## Types of Elastic Load Balancers

AWS offers several types of load balancers to suit different use cases:

1. **Application Load Balancer (ALB)**:
   - ALB operates at the application layer (Layer 7) of the OSI model and provides advanced routing capabilities, content-based routing, and support for multiple protocols, including HTTP, HTTPS, and WebSocket.
   - It is ideal for balancing HTTP and HTTPS traffic and is well-suited for applications that require advanced routing features.

2. **Network Load Balancer (NLB)**:
   - NLB operates at the transport layer (Layer 4) of the OSI model and provides ultra-low latency and high throughput for TCP, UDP, and TLS traffic.
   - It is suitable for applications that require extreme performance and high throughput, such as gaming, streaming, and real-time communication applications.

3. **Gateway Load Balancer (GWLB)**:
   - GWLB is a new type of load balancer introduced by AWS that is designed to load balance traffic across multiple virtual appliances, such as firewalls, intrusion detection systems (IDS), and deep packet inspection (DPI) systems.
   - It is ideal for architectures that require scalable and high-performance traffic inspection.

## Features of Elastic Load Balancers

- **High Availability**: ELBs are designed to be highly available and fault-tolerant, with built-in redundancy and automatic failover.
- **Auto Scaling**: ELBs can automatically scale up or down to handle changes in traffic volume and ensure consistent application performance.
- **Security**: ELBs support SSL termination, client certificate authentication, and integration with AWS WAF (Web Application Firewall) to protect your applications from common web exploits and attacks.
- **Health Checks**: ELBs perform health checks on the targets and automatically route traffic only to healthy targets, ensuring optimal application availability.
- **Monitoring and Logging**: ELBs provide detailed monitoring metrics and access logs that can be used for performance monitoring, troubleshooting, and analysis.

## Conclusion

AWS Elastic Load Balancing (ELB) is a fully managed load balancing service that helps distribute incoming application traffic across multiple targets, improving the availability, fault tolerance, and scalability of your applications. By leveraging ELB, you can ensure that your applications can handle varying levels of traffic while maintaining high performance and availability.

For more information, refer to the [AWS documentation on Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/).




[Back to Main](readme.md)
