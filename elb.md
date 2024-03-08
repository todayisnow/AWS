# AWS Elastic Load Balancing (ELB)

AWS Elastic Load Balancing (ELB) automatically distributes incoming application traffic across multiple targets, such as EC2 instances, containers, IP addresses, and Lambda functions, to ensure that no single resource becomes overwhelmed. ELB helps improve the availability and fault tolerance of your applications by evenly distributing traffic and automatically scaling to meet demand.

![image](https://github.com/todayisnow/AWS/assets/22843851/3b0a4093-e1d5-425d-b63c-3e33e365826b)


## Features of Elastic Load Balancers

- **High Availability**: ELBs are designed to be highly available and fault-tolerant, with built-in redundancy and automatic failover.
- **Auto Scaling**: ELBs can automatically scale up or down to handle changes in traffic volume and ensure consistent application performance.
- **Security**: ELBs support SSL termination, client certificate authentication, and integration with AWS WAF (Web Application Firewall) to protect your applications from common web exploits and attacks.
- **Health Checks**: ELBs perform health checks on the targets and automatically route traffic only to healthy targets, ensuring optimal application availability.
- **Monitoring and Logging**: ELBs provide detailed monitoring metrics and access logs that can be used for performance monitoring, troubleshooting, and analysis.

## Types of Elastic Load Balancers

AWS offers several types of load balancers to suit different use cases:

![image](https://github.com/todayisnow/AWS/assets/22843851/e8355123-dc53-41a2-892d-1aaf095538b5)


### Application Load Balancer (ALB):
  The Application Load Balancer (ALB) is a type of load balancer offered by AWS that operates at the application layer (Layer 7) of the OSI model. It is designed to handle HTTP, HTTPS, and WebSocket traffic and provides advanced routing capabilities, content-based routing, and support for multiple protocols.

#### Features of Application Load Balancer

- **Advanced Routing**: ALB supports advanced routing features such as path-based routing, host-based routing, and content-based routing, allowing you to route traffic to different target groups based on the request path, host header, or content.
- **TLS Termination**: ALB supports SSL termination, allowing it to terminate SSL/TLS connections from clients and forward decrypted traffic to the targets, reducing the computational overhead on the targets.
- **WebSockets**: ALB supports WebSocket traffic, allowing it to handle real-time communication between clients and servers over a single, long-lived connection.
- **Integration with AWS Services**: ALB can be integrated with other AWS services such as AWS WAF (Web Application Firewall), AWS Auto Scaling, and AWS Lambda, allowing you to build scalable and secure applications.
- **Containerized Applications**: ALB supports routing traffic to targets running in ECS (Elastic Container Service) and EKS (Elastic Kubernetes Service), making it suitable for containerized applications deployed in Docker containers or Kubernetes clusters.

#### Use Cases for Application Load Balancer

- **Web Applications**: ALB is well-suited for web applications that require advanced routing capabilities, SSL termination, and support for multiple protocols such as HTTP, HTTPS, and WebSocket.
- **Microservices Architecture**: ALB can be used to route traffic to microservices deployed in containers or virtual machines, providing scalable and flexible communication between services.
- **API Gateway**: ALB can serve as an API gateway for RESTful APIs and web services, allowing you to route requests to different backend services based on the request path or method.

### Network Load Balancer (NLB):
The Network Load Balancer (NLB) is a type of load balancer offered by AWS that operates at the transport layer (Layer 4) of the OSI model. It is designed to handle large volumes of traffic with ultra-low latency and high throughput, making it suitable for use cases that require extreme performance and scalability.

#### Features of Network Load Balancer

- **Ultra-Low Latency**: NLB provides ultra-low latency for TCP, UDP, and TLS traffic, making it ideal for applications that require real-time communication and low-latency responses.
- **High Throughput**: NLB can handle millions of requests per second and support tens of millions of concurrent connections, making it suitable for high-throughput workloads such as gaming, streaming, and real-time analytics.
- **Connection Persistence**: NLB supports connection persistence, also known as session affinity or sticky sessions, which allows the load balancer to route subsequent requests from the same client to the same target, ensuring a consistent user experience.
- **Cross-Zone Load Balancing**: NLB automatically distributes traffic evenly across targets in multiple Availability Zones, improving fault tolerance and high availability.
- **Health Checks**: NLB performs health checks on the targets and automatically routes traffic only to healthy targets, ensuring optimal application availability.
- **Static IP Addresses**: NLB provides static IP addresses that remain constant even if the load balancer is deleted and recreated, making it easier to manage DNS configurations and network traffic routing.

#### Use Cases for Network Load Balancer

- **High-Performance Applications**: NLB is well-suited for applications that require extreme performance and low-latency communication, such as gaming, streaming, and real-time communication applications.
- **Microservices Architecture**: NLB can be used to load balance traffic across microservices deployed in containers or virtual machines, providing scalable and high-performance communication between services.
- **Internet-Facing Applications**: NLB can handle internet-facing workloads with high volumes of traffic, such as web servers, APIs, and content delivery networks (CDNs).

### Gateway Load Balancer (GWLB):
   The Gateway Load Balancer (GWLB) is a type of load balancer offered by AWS that is designed to load balance traffic across multiple virtual appliances, such as firewalls, intrusion detection systems (IDS), and deep packet inspection (DPI) systems. GWLB operates at the network layer (Layer 3) of the OSI model and is ideal for architectures that require scalable and high-performance traffic inspection.

#### Features of Gateway Load Balancer

- **Traffic Inspection**: GWLB allows you to route traffic to multiple virtual appliances for inspection and filtering, enabling you to enforce security policies, monitor network traffic, and perform deep packet inspection (DPI) for threat detection and prevention.
- **Scalability**: GWLB is designed to handle large volumes of traffic and can scale to support thousands of virtual appliances, making it suitable for high-throughput workloads that require extensive traffic inspection.
- **High Availability**: GWLB provides built-in redundancy and automatic failover to ensure high availability and fault tolerance for your network architecture.
- **Integration with AWS Services**: GWLB can be integrated with other AWS services such as AWS Transit Gateway, VPC (Virtual Private Cloud) peering, and VPC endpoints, allowing you to build scalable and secure network architectures in the cloud.

#### Use Cases for Gateway Load Balancer

- **Security and Compliance**: GWLB can be used to route traffic through virtual appliances such as firewalls and IDS to enforce security policies, monitor network traffic for threats, and maintain compliance with regulatory requirements.
- **Network Monitoring and Analysis**: GWLB can route traffic to virtual appliances that perform deep packet inspection (DPI) and network analysis, allowing you to monitor network traffic, detect anomalies, and troubleshoot network issues.
- **Load Balancing for Virtual Appliances**: GWLB can distribute traffic evenly across multiple virtual appliances to optimize resource utilization and ensure consistent performance for traffic inspection and filtering.



## Listeners and Target Groups in AWS Elastic Load Balancing (ELB)

Listeners and target groups are essential components of AWS Elastic Load Balancing (ELB) that enable you to route incoming traffic to specific destinations based on rules and criteria.

  - **Listeners**:  Configured on the load balancer and define how the load balancer should handle incoming traffic. Each listener is associated with a protocol (such as HTTP, HTTPS, TCP, or UDP) and a port number. When a request is received on a specific port, the listener forwards the request to one or more target groups based on the rules defined for that listener.

![image](https://github.com/todayisnow/AWS/assets/22843851/da2120a8-3191-4c44-8544-1361528de754)


  - **Example of Listener Configuration**: For example, you can configure an HTTP listener on port 80 to forward traffic to a target group that contains web servers running on EC2 instances. Similarly, you can configure an HTTPS listener on port 443 to forward encrypted traffic to a different target group that contains secure web servers.

   - **Target Groups**: Used to route incoming traffic to one or more registered targets, such as EC2 instances, containers, IP addresses, or Lambda functions. When you create a target group, you specify the protocol and port number that the targets will receive traffic on. The load balancer routes incoming requests to the targets in the target group based on the rules defined for the associated listener. ALB/NLB can route traffice to multiple target group. A target can be registered with a target group multiple times but using different ports.

      - **Example of Target Group Configuration**:  For example, you can create a target group for your web servers running on EC2 instances and specify that incoming HTTP traffic on port 80 should be routed to this target group. The load balancer will then distribute incoming requests among the registered EC2 instances in the target group.


## Conclusion

AWS Elastic Load Balancing (ELB) is a fully managed load balancing service that helps distribute incoming application traffic across multiple targets, improving the availability, fault tolerance, and scalability of your applications. By leveraging ELB, you can ensure that your applications can handle varying levels of traffic while maintaining high performance and availability.
Listeners and target groups are fundamental components of AWS Elastic Load Balancing (ELB) that enable you to route incoming traffic to specific destinations based on rules and criteria. By leveraging listeners and target groups, you can achieve flexible, scalable, and fault-tolerant load balancing for your applications.

For more information, refer to the [AWS documentation on Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/).



# Example Usage of Elastic Load Balancer (ELB) with Two Instances

## Scenario:
You have a web application deployed on two Amazon EC2 instances and you want to distribute incoming traffic between these instances using an Elastic Load Balancer (ELB).

## Steps:

1. **Create EC2 Instances**:
   - Launch two EC2 instances in your preferred AWS region.
   - Configure the instances with the necessary software and settings for your web application.

2. **Create a Target Group**:
   - Navigate to the Amazon EC2 console and create a target group.
   - Specify the protocol and port that the instances will listen on (e.g., HTTP on port 80).
   - Register the EC2 instances with the target group.

3. **Create a Load Balancer**:
   - Navigate to the Amazon EC2 console and create a new load balancer.
   - Choose the appropriate load balancer type (e.g., Application Load Balancer or Network Load Balancer).
   - Configure the listeners (e.g., HTTP on port 80).
   - Specify the target group created in the previous step.

4. **Configure Health Checks**:
   - Configure health checks for the target group to monitor the health of the EC2 instances.
   - Define the health check settings (e.g., protocol, port, path, timeout, interval, etc.).

5. **Update DNS Records**:
   - Update your DNS records to point to the DNS name of the load balancer.
   - This allows incoming traffic to be directed to the load balancer, which in turn distributes it to the registered instances.

6. **Testing**:
   - Access your web application using the DNS name of the load balancer.
   - Verify that the traffic is evenly distributed between the two EC2 instances.

## Conclusion:
By using Elastic Load Balancer (ELB) with two instances, you can achieve improved availability, fault tolerance, and scalability for your web application. The load balancer distributes incoming traffic across multiple instances, ensuring that your application can handle varying levels of traffic and remain responsive to user requests.

# Creating a load balancer using the AWS Command Line Interface (CLI) 
```bash
#!/bin/bash

# Get List of vpcs
aws ec2 describe-vpcs --query 'Vpcs[*].[VpcId, CidrBlock]'

# Get List of Subnets:

aws ec2 describe-subnets --query 'Subnets[*].[SubnetId, VpcId, CidrBlock]'

# Get List of Security Groups:

aws ec2 describe-security-groups --query 'SecurityGroups[*].[GroupId, GroupName, VpcId]'

# Get List of Instances:

aws ec2 describe-instances --query 'Reservations[*].Instances[*].[InstanceId, InstanceType, State.Name, PrivateIpAddress, PublicIpAddress]'


# Create NLB
LB_ARN=$(aws elbv2 create-load-balancer --name devops-alb --type application --subnets subnet-0557a7c0a25ed45bb subnet-08b524372d20503c8 --security-groups sg-0f42cec4178d21881 | grep -oP '(?<="LoadBalancerArn": ")[^"]*' )


echo "$LB_ARN"
 
# Create Target Group
TG_ARN=$(aws elbv2 create-target-group --name devops-tg --protocol HTTP --port 8002 --vpc-id vpc-0163c5e3c877c7ea2 | grep -oP '(?<="TargetGroupArn": ")[^"]*')


echo "$TG_ARN"

# Register targets (EC2 instances) with the target group
aws elbv2 register-targets --target-group-arn $TG_ARN --targets Id=i-0e50f0d8dc174f767 Id=i-0f6506dc106e1b428

# Create a listener for the load balancer
LS_ARN=$(aws elbv2 create-listener --load-balancer-arn $LB_ARN --protocol HTTP --port 8002  --default-actions Type=forward,TargetGroupArn=$TG_ARN | grep -oP '(?<="ListenerArn": ")[^"]*')


echo "$LS_ARN"


# Describe the load balancer to get its DNS name
aws elbv2 describe-load-balancers     --load-balancer-arns $LB_ARN    --query 'LoadBalancers[*].DNSName'

# Update DNS records to point to the load balancer's DNS name
# Update the DNS records in your DNS management console to point to the DNS name obtained in the previous step.


#aws elbv2 delete-listener --listener-arn $LS_ARN
#aws elbv2 delete-load-balancer --load-balancer-arn $LB_ARN
#aws elbv2 delete-target-group --target-group-arn $TG_ARN

```


For more information, refer to the [AWS documentation on Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/).



[Back to Main](readme.md)
