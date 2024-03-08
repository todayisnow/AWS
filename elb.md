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

![image](https://github.com/todayisnow/AWS/assets/22843851/da2120a8-3191-4c44-8544-1361528de754)

  - **Listeners**:  Configured on the load balancer and define how the load balancer should handle incoming traffic. Each listener is associated with a protocol (such as HTTP, HTTPS, TCP, or UDP) and a port number. When a request is received on a specific port, the listener forwards the request to one or more target groups based on the rules defined for that listener.
  
    - **Example of Listener Configuration**: For example, you can configure an HTTP listener on port 80 to forward traffic to a target group that contains web servers running on EC2 instances. Similarly, you can configure an HTTPS listener on port 443 to forward encrypted traffic to a different target group that contains secure web servers.



  - **Target Groups**: Used to route incoming traffic to one or more registered targets, such as EC2 instances, containers, IP addresses, or Lambda functions. When you create a target group, you specify the protocol and port number that the targets will receive traffic on. The load balancer routes incoming requests to the targets in the target group based on the rules defined for the associated listener. ALB/NLB can route traffice to multiple target group. A target can be registered with a target group multiple times but using different ports.

      - **Example of Target Group Configuration**:  For example, you can create a target group for your web servers running on EC2 instances and specify that incoming HTTP traffic on port 80 should be routed to this target group. The load balancer will then distribute incoming requests among the registered EC2 instances in the target group.


## Conclusion

AWS Elastic Load Balancing (ELB) is a fully managed load balancing service that helps distribute incoming application traffic across multiple targets, improving the availability, fault tolerance, and scalability of your applications. By leveraging ELB, you can ensure that your applications can handle varying levels of traffic while maintaining high performance and availability.
Listeners and target groups are fundamental components of AWS Elastic Load Balancing (ELB) that enable you to route incoming traffic to specific destinations based on rules and criteria. By leveraging listeners and target groups, you can achieve flexible, scalable, and fault-tolerant load balancing for your applications.

For more information, refer to the [AWS documentation on Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/).


# ELB Health Checks

Elastic Load Balancing (ELB) health checks are used to monitor the health of the registered instances behind the load balancer. Health checks help ensure that traffic is routed only to healthy instances, improving the availability and reliability of your application. Here's how ELB health checks work:

## Key Concepts

- **Target Group**: In the context of Application Load Balancers (ALB) and Network Load Balancers (NLB), health checks are associated with target groups. Each target group is associated with a set of instances that are registered with the load balancer.

- **Health Check Configuration**: When configuring a target group, you specify the health check settings, including the protocol, port, path, timeout, interval, and threshold. These settings determine how the load balancer performs health checks on the registered instances.

- **Health Check Protocol**: You can configure the health check protocol to be either HTTP, HTTPS, TCP, or SSL. For HTTP and HTTPS protocols, the load balancer sends an HTTP or HTTPS request to the specified path on the instance and expects a successful response within a specified timeout period.

- **Health Check Path**: The health check path is the endpoint on the instance that the load balancer sends health check requests to. This endpoint should return a 2xx HTTP status code to indicate that the instance is healthy.

- **Health Check Interval**: The health check interval is the time interval between consecutive health checks. During this interval, the load balancer does not send health check requests to the instance.

- **Health Check Timeout**: The health check timeout is the maximum time that the load balancer waits for a response from the instance before considering the health check to have failed.

- **Health Check Threshold**: The health check threshold is the number of consecutive failed health checks required to mark an instance as unhealthy.

## Benefits

- **Improved Availability**: ELB health checks continuously monitor the health of the registered instances and automatically route traffic only to healthy instances. This helps improve the availability of your application by avoiding sending traffic to unhealthy instances.

- **Automated Failover**: If an instance fails health checks and is marked as unhealthy, the load balancer automatically stops routing traffic to that instance. This automated failover ensures that only healthy instances handle incoming requests.

- **Dynamic Scaling**: ELB health checks play a crucial role in dynamic scaling scenarios. As instances are added or removed from the load balancer, health checks ensure that only healthy instances are included in the load balancer's rotation.

## Best Practices

- **Configure Proper Health Check Settings**: Ensure that health check settings are configured appropriately for your application's requirements, including the protocol, port, path, timeout, interval, and threshold.

- **Monitor Health Check Results**: Regularly monitor the health check results to identify any issues with the registered instances. AWS provides CloudWatch metrics for monitoring ELB health checks, allowing you to set up alarms and notifications for unhealthy instances.

- **Implement Redundancy**: To ensure high availability, distribute your application across multiple Availability Zones and configure health checks to monitor instances in each zone. This redundancy helps mitigate the impact of failures in individual zones.

## Conclusion

ELB health checks are a critical component of maintaining the availability and reliability of your application running behind an Elastic Load Balancer. By configuring appropriate health check settings and monitoring health check results, you can ensure that traffic is consistently routed to healthy instances, improving the overall performance of your application.

For more information about configuring health checks for your ELB, refer to the [AWS documentation](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/target-group-health-checks.html).

# ELB Cross-Zone load balancing
Enabling cross-zone load balancing helps improve the distribution of traffic across multiple Availability Zones, leading to better resource utilization and potentially improved application performance. However, it's important to consider the specific requirements and characteristics of your application before enabling cross-zone load balancing, as it may incur additional costs and affect how your application behaves in certain scenarios.

## ELB without Cross-Zone Load Balancing:
- When you create an ELB without enabling cross-zone load balancing, each load balancer node distributes traffic only to the instances that are registered with it, in its own Availability Zone. This means that if you have multiple Availability Zones and traffic is primarily coming from one zone, the instances in other zones may be underutilized. This can lead to uneven distribution of traffic and potential inefficiencies.

![image](https://github.com/todayisnow/AWS/assets/22843851/e759f02f-d0a3-45c4-bbb2-78810ebd4263)


## ELB with Cross-Zone Load Balancing:
- Enabling cross-zone load balancing allows each load balancer node to distribute traffic equally across all registered instances in all enabled Availability Zones. This means that each load balancer node can route requests to instances in any Availability Zone, improving the distribution of traffic and potentially leading to better overall performance and utilization of resources.


# ELB and Connection Draining

**ELB and Connection Draining**:
When you enable connection draining on your ELB, it allows the load balancer to complete any requests that are in progress before removing the instance from service. This ensures that clients are not abruptly disconnected and helps maintain a seamless experience during instance maintenance or termination.

Here's how it works:
- When you initiate a deregistration of an instance from the load balancer (e.g., during scaling down or instance termination), the load balancer stops sending new requests to that instance.
- The load balancer continues to route existing requests to the instance until either they are completed or until the configured timeout period is reached.
- Once all in-flight requests are completed or the timeout period expires, the instance is deregistered from the load balancer.

**Benefits of Connection Draining**:
- **Seamless User Experience**: Users won't experience disruptions or errors due to ongoing requests being terminated abruptly.
- **Graceful Handling of Instances**: Instances can be gracefully removed from the load balancer without causing disruptions to clients.
- **Better Application Stability**: Helps maintain application stability during deployments, scaling events, or instance terminations.

**Configuration**:
- You can configure connection draining settings (e.g., timeout period) when setting up your ELB or through the AWS Management Console, CLI, or API.
- It's important to configure the timeout period appropriately based on your application's behavior and expected request duration.


# ELB Security Groups

Elastic Load Balancing (ELB) is a service provided by Amazon Web Services (AWS) that automatically distributes incoming application traffic across multiple targets, such as EC2 instances, in multiple Availability Zones to ensure high availability and fault tolerance for your applications. ELB security groups allow you to control the traffic that is allowed to reach your load balancer.

![image](https://github.com/todayisnow/AWS/assets/22843851/fc69b85e-4e68-4c9d-a1ad-f5a46566d17c)


## Overview

ELB security groups act as virtual firewalls that control the traffic allowed to reach your load balancer. They operate at the transport layer (Layer 4) of the OSI model, which means they can filter traffic based on IP addresses, port numbers, and protocols.

## Key Features

- **Inbound Rules**: You can define inbound rules to control the incoming traffic to your load balancer. These rules specify the allowed sources (IP addresses or CIDR blocks), ports, and protocols.

- **Outbound Rules**: ELB security groups also support outbound rules to control the outgoing traffic from your load balancer. You can specify the allowed destinations, ports, and protocols for outbound traffic.

- **Stateful Filtering**: ELB security groups are stateful, which means they automatically allow return traffic for inbound connections that are initiated from allowed sources.

- **Default Rules**: By default, ELB security groups allow all traffic within the same security group and deny all other traffic. You must explicitly add inbound and outbound rules to allow specific traffic.

## Use Cases

- **Web Applications**: ELB security groups are commonly used to protect web applications deployed behind an ELB. You can restrict access to the load balancer based on the intended users or applications.

- **Microservices**: In microservices architectures, ELB security groups help control the communication between different components or services by allowing only the necessary traffic.

- **Compliance Requirements**: ELB security groups can be configured to meet specific compliance requirements, such as restricting access to sensitive data or complying with regulatory standards.

## Best Practices

- **Least Privilege**: Follow the principle of least privilege when defining inbound and outbound rules for your ELB security groups. Only allow the minimum required traffic to ensure security.

- **Regular Review**: Regularly review and update your ELB security group rules to align with your application's changing requirements and security policies.

- **Logging and Monitoring**: Enable logging and monitoring for your ELB security groups to track and analyze traffic patterns, detect anomalies, and identify potential security threats.

## Conclusion

ELB security groups provide a flexible and effective way to control the traffic allowed to reach your load balancer, helping you enhance the security of your applications deployed in the AWS cloud.

For detailed documentation and configuration options, refer to the [AWS Elastic Load Balancing documentation](https://docs.aws.amazon.com/elasticloadbalancing/).



# ELB and SSL Certificate

Elastic Load Balancing (ELB) is a service provided by Amazon Web Services (AWS) that automatically distributes incoming application traffic across multiple targets, such as EC2 instances, in multiple Availability Zones to ensure high availability and fault tolerance for your applications. SSL (Secure Sockets Layer) certificates play a crucial role in securing communication between clients and servers by encrypting data transmitted over the network.

![image](https://github.com/todayisnow/AWS/assets/22843851/45055911-8280-4fca-bdba-60bff74309cd)


## Overview

ELB supports SSL termination, which allows it to terminate SSL connections from clients and then decrypt and forward the traffic to the backend instances in plain HTTP. This offloads the SSL decryption process from the backend instances, improving their performance and reducing their load.

## Key Features

- **SSL Termination**: ELB can terminate SSL connections from clients, decrypt the traffic, and forward it to the backend instances in plain HTTP.

- **Server Name Indication (SNI)**: ELB supports SNI, which allows it to serve multiple SSL certificates on a single IP address. This is useful when hosting multiple websites or applications on the same ELB.

- **Certificate Management**: You can manage SSL certificates for your ELB using AWS Certificate Manager (ACM). ACM makes it easy to provision, manage, and deploy SSL/TLS certificates for use with ELB and other AWS services.

- **HTTPS Listeners**: ELB supports HTTPS listeners, allowing you to configure it to accept HTTPS traffic from clients.

## Use Cases

- **Secure Web Applications**: ELB with SSL termination is commonly used to secure web applications by encrypting traffic between clients and the load balancer.

- **Compliance Requirements**: SSL termination with ELB helps meet compliance requirements for data encryption in transit, such as those mandated by regulatory standards like PCI DSS and HIPAA.

- **Single Sign-On (SSO)**: ELB can be used as a front-end load balancer for SSO solutions, encrypting traffic between clients and the authentication servers.

## Best Practices

- **Use ACM**: Use AWS Certificate Manager (ACM) to provision and manage SSL certificates for your ELB. ACM integrates seamlessly with ELB and simplifies the process of managing SSL certificates.

- **Enable HTTPS Listeners**: If your application requires HTTPS traffic, configure HTTPS listeners on your ELB to ensure that SSL-encrypted traffic is accepted.

- **Regular Certificate Updates**: Keep your SSL certificates up to date by regularly renewing them before they expire. ACM can automatically renew certificates that are managed by ACM.



## Conclusion

ELB with SSL termination provides a secure and scalable solution for distributing incoming traffic to your backend instances while offloading the SSL decryption process. By using SSL certificates managed by ACM, you can simplify certificate management and ensure the security of your applications.

For detailed documentation and configuration options, refer to the [AWS Elastic Load Balancing documentation](https://docs.aws.amazon.com/elasticloadbalancing/).


# ELB Monitoring and Logging

Elastic Load Balancing (ELB) offers monitoring and logging capabilities that provide insights into the health, performance, and traffic patterns of your load balancers. Monitoring and logging help you troubleshoot issues, optimize performance, and ensure the reliability of your applications.

## Monitoring

ELB provides built-in monitoring features that allow you to track various metrics related to the health and performance of your load balancers. These metrics include:

- **Request Count**: Number of requests processed by the load balancer.
- **Latency**: Time taken by the load balancer to respond to each request.
- **HTTP Code Count**: Count of HTTP response codes returned by the load balancer.
- **Backend Connection Errors**: Errors encountered when establishing connections with backend instances.
- **Healthy Host Count**: Number of healthy backend instances registered with the load balancer.
- **UnHealthy Host Count**: Number of unhealthy backend instances registered with the load balancer.

You can view these metrics using Amazon CloudWatch, which provides detailed monitoring dashboards, customizable alarms, and metric graphs to help you monitor the health and performance of your load balancers in real-time.

## Logging

ELB also supports access logging, which allows you to capture detailed information about each request processed by your load balancers. Access logs include details such as the client's IP address, request timestamp, response status code, and more. You can use access logs to analyze traffic patterns, diagnose issues, and comply with regulatory requirements.

ELB access logs can be stored in Amazon S3 buckets, where they can be analyzed using various tools, such as Amazon Athena, Amazon Redshift, or third-party log analysis tools. You can enable access logging for your load balancers and specify the S3 bucket where the logs should be stored.

## Best Practices

- **Enable Monitoring**: Enable CloudWatch monitoring for your ELB to track key metrics and set up alarms to receive notifications when thresholds are exceeded.
- **Enable Access Logging**: Enable access logging for your ELB to capture detailed information about incoming requests and store the logs in an S3 bucket for analysis.
- **Analyze Logs**: Regularly analyze ELB access logs to gain insights into traffic patterns, diagnose issues, and optimize performance.
- **Monitor and Tune**: Use monitoring data to identify performance bottlenecks and tune your load balancers for optimal performance.

## Conclusion

Monitoring and logging are essential components of managing and maintaining the health, performance, and reliability of your load balancers in AWS. By leveraging the monitoring and logging features provided by ELB, you can gain valuable insights into your application's traffic patterns, diagnose issues, and ensure the smooth operation of your infrastructure.

For detailed documentation and configuration options, refer to the [AWS Elastic Load Balancing documentation](https://docs.aws.amazon.com/elasticloadbalancing/).
 

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
