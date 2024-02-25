# Amazon Virtual Private Cloud (VPC)

Amazon Virtual Private Cloud (VPC) is a service offered by AWS that allows you to create a virtual network in the cloud, providing you with complete control over your network environment, including IP address range, subnets, route tables, and network gateways. VPC enables you to securely connect your AWS resources, such as EC2 instances, RDS databases, and Lambda functions, and control inbound and outbound network traffic.

## Features of Amazon VPC

- **Isolated Virtual Network**: VPC provides an isolated virtual network environment that allows you to launch AWS resources in a logically isolated section of the AWS cloud.
- **Custom IP Address Range**: You can define your own IP address range (CIDR block) for your VPC, allowing you to choose the IP addresses for your resources according to your network requirements.
- **Subnet Configuration**: VPC allows you to divide your IP address range into one or more subnets, each located in a different Availability Zone (AZ), providing high availability and fault tolerance for your resources.
- **Internet and VPN Connectivity**: VPC allows you to connect your VPC to the internet using an internet gateway (IGW) and establish secure connections to your on-premises network using virtual private gateways (VPGs) and VPN connections.
- **Security**: VPC provides security features such as security groups and network access control lists (NACLs) to control inbound and outbound traffic to and from your resources.
- **Elastic Network Interfaces (ENIs)**: VPC allows you to attach elastic network interfaces (ENIs) to your EC2 instances, enabling them to communicate with other resources in your VPC and connect to the internet or on-premises networks.

## Use Cases for Amazon VPC

- **Enterprise Applications**: VPC is suitable for hosting enterprise applications and databases in a secure and isolated network environment.
- **Web Hosting**: VPC allows you to host web applications and websites securely, with fine-grained control over inbound and outbound traffic.
- **Hybrid Cloud**: VPC enables you to extend your on-premises network to the cloud and seamlessly integrate AWS resources with your existing infrastructure.
- **Big Data Processing**: VPC is ideal for running big data processing and analytics workloads, providing high-performance network connectivity between data sources and processing engines.

## Conclusion

Amazon Virtual Private Cloud (VPC) is a powerful networking service offered by AWS that allows you to create a virtual network in the cloud with complete control over your network environment. By leveraging VPC, you can securely connect your AWS resources, control inbound and outbound traffic, and build scalable and resilient cloud architectures.

For more information, refer to the [AWS documentation on Amazon VPC](https://docs.aws.amazon.com/vpc/).


# Components of Amazon Virtual Private Cloud (VPC)

Amazon Virtual Private Cloud (VPC) consists of several key components that allow you to create a virtual network in the cloud and control the networking environment for your AWS resources. Here are the main components of VPC and how they work:

![vpc](./images/vpc.png)

## 1. CIDR Block
- The CIDR (Classless Inter-Domain Routing) block is the IP address range that you specify for your VPC.
- It determines the range of IP addresses that can be assigned to resources within your VPC.

## 2. Subnets
- Subnets are subdivisions of the CIDR block that you define within your VPC.
- Each subnet is associated with a specific Availability Zone (AZ) and can contain a range of IP addresses from the parent CIDR block.
- Subnets provide a way to organize and isolate resources within your VPC and enable high availability and fault tolerance by distributing resources across multiple AZs.

## 3. Route Tables
- Route tables are used to define the routing rules for traffic within your VPC.
- Each subnet is associated with a route table, which determines how traffic is routed to and from resources within the subnet.
- Route tables contain entries that specify the destination CIDR blocks and the target (e.g., an internet gateway or virtual private gateway) for traffic destined for those CIDR blocks.

## 4. Internet Gateway (IGW)
- An internet gateway is a horizontally scaled, redundant, and highly available VPC component that allows communication between instances in your VPC and the internet.
- It provides a target for internet-bound traffic from resources within your VPC.
- To enable internet access for resources within your VPC, you attach an internet gateway to your VPC and update the route table to route traffic destined for the internet to the internet gateway.

## 5. Virtual Private Gateway (VGW)
- A virtual private gateway is a VPC component that represents the VPN (Virtual Private Network) endpoint on the AWS side of a VPN connection.
- It enables secure communication between your VPC and your on-premises network or other remote networks via VPN connections.

## 6. NAT Gateway
- A NAT (Network Address Translation) gateway is a managed service that allows instances within a private subnet to initiate outbound internet traffic while preventing inbound traffic from reaching those instances.
- It enables instances within private subnets to access the internet for software updates, package downloads, and other external services.

## 7. Security Groups
- Security groups act as virtual firewalls for your instances, controlling inbound and outbound traffic at the instance level.
- You can specify rules in a security group to allow or deny traffic based on IP protocol, port number, and source or destination IP address.
- Each instance in your VPC is associated with one or more security groups, and you can modify the security group rules at any time.

## 8. Network Access Control Lists (NACLs)
- Network Access Control Lists (NACLs) act as stateless firewalls for controlling traffic at the subnet level.
- Unlike security groups, NACLs operate at the subnet level and evaluate traffic based on subnet-level rules.
- You can specify rules in a NACL to allow or deny traffic based on IP protocol, port number, and source or destination IP address.

## How It Works
- When you create a VPC, you define the CIDR block for the VPC and create subnets within that CIDR block.
- You configure route tables to determine how traffic is routed within the VPC, including routing traffic to the internet via internet gateways or to remote networks via virtual private gateways.
- You can use security groups to control inbound and outbound traffic at the instance level and NACLs to control traffic at the subnet level.
- By configuring these components, you can create a customized and secure networking environment for your AWS resources within your VPC.


# Amazon Virtual Private Cloud (VPC) Pricing

Amazon VPC offers a flexible and pay-as-you-go pricing model based on the resources and features you use. The pricing for VPC includes charges for various components and features such as the number of VPCs, the number of subnets, data transfer, NAT gateway usage, and VPN connections. Here are the key factors that determine the pricing for Amazon VPC:

## 1. VPC Creation
- There is no additional charge for creating a VPC in AWS. You can create multiple VPCs in your AWS account at no extra cost.

## 2. Subnets
- There is no additional charge for creating subnets within your VPC. You can create multiple subnets within each VPC to organize your resources.

## 3. Data Transfer
- Data transfer charges apply for traffic that flows in and out of your VPC, including traffic between your VPC and the internet, between VPCs in different AWS regions, and between your VPC and other AWS services.
- Data transfer pricing varies by region and depends on the amount of data transferred.

## 4. NAT Gateway
- NAT Gateway usage is charged per hour for each NAT gateway that you create in your VPC.
- Data processing charges also apply for data processed by NAT gateways.

## 5. VPN Connections
- VPN connections between your VPC and your on-premises network or other remote networks incur hourly charges based on the type of VPN connection (e.g., IPsec VPN or AWS Site-to-Site VPN).

## 6. Other Features
- Additional charges may apply for features such as AWS Direct Connect, VPC peering, VPC endpoint services, and other advanced networking features.

## Pricing Calculator
- You can use the AWS Pricing Calculator to estimate the cost of Amazon VPC based on your specific requirements and usage patterns.
- The pricing calculator allows you to customize various parameters such as the number of VPCs, subnets, data transfer volume, and other features to get an accurate cost estimate.

## Conclusion
Amazon VPC offers a flexible pricing model that allows you to pay only for the resources and features you use. By understanding the pricing factors and using the AWS Pricing Calculator, you can effectively manage and optimize the cost of your VPC deployment in AWS.

For detailed pricing information, refer to the [AWS Pricing page](https://aws.amazon.com/pricing/).

# Designing an Amazon Virtual Private Cloud (VPC)

Designing an Amazon Virtual Private Cloud (VPC) involves several key steps to create a secure, scalable, and efficient network infrastructure for your AWS resources. Here's a guide on how to design a VPC:

## 1. Define Requirements
- Identify the requirements for your VPC, including the number of resources, traffic patterns, security requirements, and connectivity options.
- Consider factors such as scalability, fault tolerance, compliance, and performance when defining your requirements.

## 2. Plan IP Addressing
- Determine the IP address range (CIDR block) for your VPC based on the number of resources and subnets you need.
- Allocate IP address ranges for each subnet within your VPC, considering factors such as scalability, segregation, and future growth.

## 3. Design Subnets
- Divide your VPC's IP address range into subnets based on your requirements for isolation, availability, and scalability.
- Create public subnets for resources that require direct internet access and private subnets for internal resources that should not be directly accessible from the internet.

## 4. Configure Routing
- Design and configure route tables to control the routing of traffic within your VPC and between your VPC and external networks.
- Configure internet gateways (IGWs) for internet access, virtual private gateways (VGWs) for VPN connectivity, and route propagation for seamless routing.

## 5. Implement Security
- Design security groups and network access control lists (NACLs) to control inbound and outbound traffic to and from your resources within the VPC.
- Define security policies and enforce least privilege principles to ensure a secure network environment.

## 6. Enable Connectivity
- Configure connectivity options such as VPN connections, AWS Direct Connect, VPC peering, and AWS Transit Gateway to connect your VPC to on-premises networks and other AWS resources.
- Ensure secure and reliable connectivity between your VPC and external networks.

## 7. Monitor and Manage
- Implement monitoring and logging solutions to track the performance, availability, and security of your VPC and its resources.
- Use AWS CloudWatch, VPC Flow Logs, and other monitoring tools to gain visibility into network traffic and resource usage.

## Conclusion
Designing an Amazon Virtual Private Cloud (VPC) involves careful planning and consideration of various factors such as IP addressing, subnetting, routing, security, and connectivity. By following the steps outlined above, you can create a well-designed VPC that meets your specific requirements for security, scalability, and performance.

For more information, refer to the [AWS documentation on Amazon VPC](https://docs.aws.amazon.com/vpc/).

# VPC Subnet Design

When designing subnets within an Amazon Virtual Private Cloud (VPC), it's essential to consider factors such as scalability, availability, security, and routing requirements. A well-designed subnet layout ensures efficient resource utilization and seamless communication between resources while adhering to best practices for network architecture.

## 1. Define Subnet Requirements

Before designing subnets, define the requirements for your VPC, including the number of resources, traffic patterns, and security requirements. Consider factors such as public-facing applications, backend services, databases, and internal services that require isolation.

## 2. Determine IP Addressing Scheme

Define the IP addressing scheme for your VPC subnet layout. Choose a CIDR block for your VPC that provides sufficient IP addresses for your resources while allowing for future growth. Divide the CIDR block into smaller subnets based on your requirements and traffic patterns.

## 3. Create Subnets

Create subnets within your VPC based on the defined IP addressing scheme. Divide the CIDR block into subnets of appropriate sizes to accommodate different types of resources. Consider creating separate subnets for public-facing resources, backend services, databases, and internal resources.

## 4. Assign Subnet Types

Assign appropriate types to each subnet based on its purpose and requirements. Common subnet types include:
- **Public Subnets**: Subnets with direct internet access for public-facing resources such as web servers or load balancers.
- **Private Subnets**: Subnets without direct internet access for backend services, databases, or internal resources.
- **DMZ Subnets**: Demilitarized zones (DMZ) for hosting publicly accessible resources while maintaining security.

## 5. Configure Routing and Security

Configure routing tables and security groups to control inbound and outbound traffic to and from the subnets. Use route tables to define routes between subnets and to the internet gateway (IGW) for public subnets. Configure security groups to enforce security policies and control access between resources within and outside the subnets.

## Example Subnet Layout

Here's an example subnet layout for a VPC with a CIDR block of 10.0.0.0/16:

- **Public Subnets**:
  - Subnet 1: 10.0.1.0/24
  - Subnet 2: 10.0.2.0/24

- **Private Subnets**:
  - Subnet 3: 10.0.3.0/24
  - Subnet 4: 10.0.4.0/24

- **DMZ Subnets**:
  - Subnet 5: 10.0.5.0/24

![subnet](./images/vpc3.png)

## Conclusion

Designing a VPC subnet layout involves careful planning and consideration of various factors such as IP addressing, subnet types, routing, and security requirements. By following best practices and adhering to your specific requirements, you can create an efficient and secure subnet layout for your Amazon VPC.

For more information, refer to the [AWS documentation on Amazon VPC](https://docs.aws.amazon.com/vpc/).



# CIDR (Classless Inter-Domain Routing)

CIDR, which stands for Classless Inter-Domain Routing, is a method used to allocate and specify IP addresses and IP address ranges. CIDR notation is used to represent IP address ranges using a combination of an IP address and a suffix indicating the number of bits in the network portion of the address. CIDR notation is commonly used in networking and routing configurations to define subnets and IP address ranges.

## Format

CIDR notation consists of an IP address followed by a forward slash (/) and a number indicating the size of the network prefix or subnet mask. For example, the CIDR notation "192.0.2.0/24" represents the IP address range from 192.0.2.0 to 192.0.2.255, where the first 24 bits (3 bytes) represent the network portion of the address, and the remaining 8 bits represent the host portion.

## Prefix Length

The number following the forward slash (/) in CIDR notation represents the number of bits in the network prefix or subnet mask. This number is also known as the prefix length. The prefix length determines the size of the network and the number of available IP addresses. For example, a prefix length of 24 (as in "192.0.2.0/24") corresponds to a subnet mask of 255.255.255.0 and allows for 256 IP addresses (2^8) in the subnet.

## CIDR Blocks

CIDR blocks are contiguous ranges of IP addresses represented in CIDR notation. CIDR blocks are commonly used to define IP address ranges for networks, subnets, and routing configurations. For example, the CIDR block "192.0.2.0/24" represents the range of IP addresses from 192.0.2.0 to 192.0.2.255.

## Subnetting

CIDR notation is used in subnetting to divide a larger IP address range into smaller, more manageable subnets. Subnetting allows for efficient use of IP addresses and better organization of network resources. CIDR notation is used to represent both the larger network and the individual subnets within it.

## Conclusion

CIDR (Classless Inter-Domain Routing) notation is a standard method used to represent IP address ranges and subnets in networking and routing configurations. By using CIDR notation, network administrators can efficiently allocate and manage IP addresses and define network boundaries and subnets.

For more information, refer to the [CIDR Wikipedia page](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing).


# VPC CIDR Blocks

A CIDR (Classless Inter-Domain Routing) block is a range of IP addresses that define the address space for your Amazon Virtual Private Cloud (VPC). When creating a VPC, you must specify a CIDR block, which determines the range of IP addresses available for resources within the VPC. Here's a guide on VPC CIDR blocks:

## CIDR Notation

CIDR notation is used to represent IP address ranges in a compact format. It consists of an IP address followed by a forward slash (/) and a number indicating the number of bits in the network prefix. For example, "10.0.0.0/16" represents the CIDR block with the IP address range from 10.0.0.0 to 10.0.255.255, where the first 16 bits represent the network portion of the address.

## Choosing CIDR Blocks

When choosing a CIDR block for your VPC, consider the following factors:
- **Size**: Choose a CIDR block that provides enough IP addresses for your resources while allowing for future growth.
- **Isolation**: Divide the CIDR block into smaller subnets to isolate different types of resources and control traffic flow.
- **Overlap**: Avoid overlapping CIDR blocks with existing networks to prevent conflicts and ensure seamless connectivity.

## Reserved CIDR Blocks

Some CIDR blocks are reserved by AWS and cannot be used for VPCs. These reserved CIDR blocks include:
- **10.0.0.0/8**: The entire 10.0.0.0/8 CIDR block is reserved for private use and cannot be used for VPCs.
- **100.64.0.0/10**: The 100.64.0.0/10 CIDR block is reserved for carrier-grade NAT (CGN) and cannot be used for VPCs.

## Example CIDR Blocks

Here are some example CIDR blocks commonly used for VPCs:
- **10.0.0.0/16**: Provides 65,536 IP addresses for resources within the VPC.
- **172.16.0.0/16**: Provides 65,536 IP addresses for resources within the VPC.
- **192.168.0.0/16**: Provides 65,536 IP addresses for resources within the VPC.

![cidr](./images/vpc2.png)

## Conclusion

Choosing the right CIDR block is essential when creating a VPC, as it determines the range of IP addresses available for your resources. By considering factors such as size, isolation, and reserved blocks, you can select a CIDR block that meets your specific requirements for your Amazon VPC.

For more information, refer to the [AWS documentation on Amazon VPC CIDR Blocks](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html).

---

# Create VPC, Subnets, Internet Gateway, and Route Table from AWS Console

Follow these steps to create a VPC, subnets, internet gateway, and route table from the AWS Management Console:

![design](./images/vpc4.png)

## 1. Create VPC:
- Go to the AWS Management Console and navigate to the VPC dashboard.
- Click on "Create VPC" and provide the necessary details such as VPC name, CIDR block `10.0.0.0/16`, and other optional settings.
- Click on "Create" to create the VPC.

## 2. Create Subnets:
- After creating the VPC, navigate to the "Subnets" section in the VPC dashboard.
- Click on "Create subnet" and select the VPC created in the previous step.
- Provide the subnet details including name, CIDR block `10.0.1.0/24`, availability zone "subnets in same vpc can be in different availability zone", and other settings.
- Repeat this process to create multiple subnets for different purposes (e.g., public, private).

## 3. Create Internet Gateway (IGW):
- In the VPC dashboard, navigate to the "Internet Gateways" section.
- Click on "Create internet gateway" and provide a name for the IGW.
- Select the newly created IGW and attach it to the VPC by clicking on "Attach to VPC" and selecting the VPC.

## 4. Create Route Table:
- In the VPC dashboard, navigate to the "Route Tables" section.
- Click on "Create route table" and provide a name for the route table."one created by default"
- Select the newly created route table and associate it with the VPC by clicking on "Edit routes" and adding a route to the internet gateway.
  - 10.0.0.0/16 -> local
  - 0.0.0.0/0   -> IGW-xxxx

## 5. Associate Subnets:
- After creating the route table, select it and navigate to the "Subnet associations" tab.
- Click on "Edit subnet associations" and select the subnets created earlier to associate them with the route table.

## Conclusion:
By following these steps, you can create a VPC, subnets, internet gateway, and route table from the AWS Management Console. This setup provides the foundation for hosting your AWS resources in a secure and isolated network environment.

For detailed instructions and additional options, refer to the [AWS documentation on Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/).


# Create VPC, Subnets, Internet Gateway, and Route Table Using AWS CLI

Follow these steps to create a VPC, subnets, internet gateway, and route table using the AWS Command Line Interface (CLI):

## 1. Create VPC:
```bash
aws ec2 create-vpc --cidr-block 10.0.0.0/16
```

## 2. Create Subnets:
```bash
aws ec2 create-subnet --vpc-id <VPC_ID> --cidr-block 10.0.1.0/24 --availability-zone <AZ>
aws ec2 create-subnet --vpc-id <VPC_ID> --cidr-block 10.0.2.0/24 --availability-zone <AZ>
```

## 3. Create Internet Gateway (IGW):
```bash
aws ec2 create-internet-gateway
```

## 4. Attach Internet Gateway to VPC:
```bash
aws ec2 attach-internet-gateway --vpc-id <VPC_ID> --internet-gateway-id <IGW_ID>
```

## 5. Create Route Table:
```bash
aws ec2 create-route-table --vpc-id <VPC_ID>
```

## 6. Add Route to Internet Gateway:
```bash
aws ec2 create-route --route-table-id <ROUTE_TABLE_ID> --destination-cidr-block 0.0.0.0/0 --gateway-id <IGW_ID>
```

## 7. Associate Subnets with Route Table:
```bash
aws ec2 associate-route-table --subnet-id <SUBNET_ID> --route-table-id <ROUT
```


# Create VPC, Subnets, Internet Gateway, and Route Table Using AWS CLI with well structured `bash script`
```bash
#!/bin/bash

# create vpc 10.0.0.0/16

check_vpc=$(aws ec2 describe-vpcs --region us-east-1 --filters Name=tag:Name,Values=devops90-vpc | grep -oP '(?<="VpcId": ")[^"]*')
if [ -z "$check_vpc" ]; then

    vpc_result=$(aws ec2 create-vpc \
        --cidr-block 10.0.0.0/16 --region us-east-1 \
        --tag-specification ResourceType=vpc,Tags="[{Key=Name,Value=devops90-vpc}]" \
        --output json)
    echo $vpc_result

    vpc_id=$(echo $vpc_result | grep -oP '(?<="VpcId": ")[^"]*')
    echo $vpc_id

    if [ -z "$vpc_id" ]; then
        echo "Error in creating the vpc"
        exit 1
    fi

    echo "VPC created."

else
    echo "VPC already exist"
    vpc_id=$check_vpc
    echo $vpc_id
fi

echo "-------------------------------"
# ----------------------------------------------------------------------------

# create public subnet 10.0.1.0/24 in first az
# create public subnet 10.0.2.0/24 in second az
# create private subnet 10.0.3.0/24 in first az
# create private subnet 10.0.4.0/24 in second az

create_subnet()
{
    # $1 subnet number, $2 az, $3 public or private
    check_subnet=$(aws ec2 describe-subnets --region us-east-1 --filters Name=tag:Name,Values=sub-$3-$1-devops90 | grep -oP '(?<="SubnetId": ")[^"]*')
    if [ -z "$check_subnet" ]; then
        echo "subnet $1 will be created"

        subnet_result=$(aws ec2 create-subnet \
            --vpc-id $vpc_id --availability-zone us-east-1$2 \
            --cidr-block 10.0.$1.0/24 \
            --tag-specifications ResourceType=subnet,Tags="[{Key=Name,Value=sub-$3-$1-devops90}]" --output json)
            
        echo $subnet_result

        subnet_id=$(echo $subnet_result | grep -oP '(?<="SubnetId": ")[^"]*')
        echo $subnet_id

        if [ -z "$subnet_id" ]; then
            echo "Error in create subnet $1"
            exit 1
        fi
        echo "subnet $1 created."
    else
        echo "subnet $1 already exist"
        subnet_id=$check_subnet
        echo $subnet_id
    fi

}

create_subnet 1 a public
sub1_id=$subnet_id

create_subnet 2 b public
sub2_id=$subnet_id

create_subnet 3 a private
sub3_id=$subnet_id

create_subnet 4 b private
sub4_id=$subnet_id

echo "-------------------------------"

# ----------------------------------------------------------------------------

# create internet gateway
check_igw=$(aws ec2 describe-internet-gateways  --filters Name=tag:Name,Values=devops90-igw | grep -oP '(?<="InternetGatewayId": ")[^"]*')
if [ -z "$check_igw" ]; then
    echo "internet gateway will be created"

    igw_id=$(aws ec2 create-internet-gateway --region us-east-1 \
        --tag-specifications ResourceType=internet-gateway,Tags="[{Key=Name,Value=devops90-igw}]" --output json | grep -oP '(?<="InternetGatewayId": ")[^"]*')

    if [ -z "$igw_id" ]; then
        echo "Error in create internet gateway"
        exit 1
    fi
    echo "internet gateway created."
    
else
    echo "internet gateway already exist"
    igw_id=$check_igw
fi

echo $igw_id

# Attach the internet gateway to vpc (no output)

igw_attach=$(aws ec2 describe-internet-gateways --internet-gateway-ids $igw_id | grep -oP '(?<="VpcId": ")[^"]*')
if [  "$igw_attach" != "$vpc_id" ]; then
    attach_result=$(aws ec2 attach-internet-gateway --internet-gateway-id $igw_id --vpc-id $vpc_id)
    if [ -z "$attach_result" ]; then
        echo "internet gateway attached to the vpc"
    else 
        echo "Internet gateway AlreadyAssociated"
    fi
else
    echo "Internet gateway already attached to this vpc"
fi

echo "-------------------------------"
# ----------------------------------------------------------------------------

# create public rout table
check_rtb=$(aws ec2 describe-route-tables --filters Name=tag:Name,Values=public-devops90-rtb | grep -oP '(?<="RouteTableId": ")[^"]*' | uniq)

if [ -z "$check_rtb" ]; then
    echo "public route table will be created"
    public_rtb_id=$(aws ec2 create-route-table --vpc-id $vpc_id --tag-specifications ResourceType=route-table,Tags="[{Key=Name,Value=public-devops90-rtb}]"  --output json | grep -oP '(?<="RouteTableId": ")[^"]*'  | uniq)
    if [ -z "$public_rtb_id" ]; then
        echo "Error in create public route table"
        exit 1
    fi
    echo "public route table created."

    # create public route 
    route_result=$(aws ec2 create-route --route-table-id $public_rtb_id \
        --destination-cidr-block 0.0.0.0/0 --gateway-id $igw_id | grep -oP '(?<="Return": )[^,]*')
    echo $route_result
    if [ "$route_result" != "true" ]; then
        echo "public route creation faild"
        exit 1
    fi
    echo "public route created"

else 
    echo "public route table already exist"
    public_rtb_id=$check_rtb
fi

echo $public_rtb_id


# associate public route table to the public subnets
aws ec2 associate-route-table --route-table-id $public_rtb_id --subnet-id $sub1_id
aws ec2 associate-route-table --route-table-id $public_rtb_id --subnet-id $sub2_id


echo "-------------------------------"
# ----------------------------------------------------------------------------

# create private route table
check_rtb=$(aws ec2 describe-route-tables --filters Name=tag:Name,Values=private-devops90-rtb | grep -oP '(?<="RouteTableId": ")[^"]*'  | uniq)
if [ -z "$check_rtb" ]; then
    echo "private route table will be created"
    private_rtb_id=$(aws ec2 create-route-table --vpc-id $vpc_id --tag-specifications ResourceType=route-table,Tags="[{Key=Name,Value=private-devops90-rtb}]"  --output json | grep -oP '(?<="RouteTableId": ")[^"]*'  | uniq)
    
    if [ -z "$private_rtb_id" ]; then
        echo "Error in create private route table"
        exit 1
    fi
    echo "private route table created."

else 
    echo "private route table already exist"
    private_rtb_id=$check_rtb
fi

echo $private_rtb_id

# associate public route table to the public subnets
aws ec2 associate-route-table --route-table-id $private_rtb_id --subnet-id $sub3_id
aws ec2 associate-route-table --route-table-id $private_rtb_id --subnet-id $sub4_id
# ----------------------------------------------------------------------------

```



[Back to Main](readme.md)
