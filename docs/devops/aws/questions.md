# AWS Questions

-----General--------
<details>
<summary>What is AWS?</summary>


AWS (Amazon Web Services) is a cloud computing platform provided by Amazon. It offers a wide range of on-demand computing services and resources, such as servers, storage, databases, networking, and more, over the internet. AWS allows businesses and individuals to access and utilize these services without the need to own and manage physical hardware. It's commonly used for hosting websites, running applications, and storing data, offering scalability and flexibility to meet various computing needs.

</details>
<details>
<summary>What are two services of AWS where you could store secrets?</summary>


Two AWS services for storing secrets securely are:

- **AWS Secrets Manager**: A service specifically designed for managing and rotating sensitive information like database passwords, API keys, and other credentials. It provides encryption, automated rotation, and access control for secrets.

- **AWS Parameter Store**: A service that allows you to store and manage configuration data, including secrets, in a hierarchical structure. It's often used for storing application configuration parameters and secrets in a secure manner.

</details>
<details>
<summary>What is the relation between the Availability Zone and Region in AWS?</summary>


- A **Region** is a geographical area that consists of multiple, isolated Availability Zones. AWS Regions are entirely separate from one another and are spread across the world to provide geographic diversity and redundancy.

- An **Availability Zone (AZ**) is a data center or facility within an AWS Region. Each Availability Zone is physically separate from the others and is designed to be isolated from failures in other Availability Zones within the same Region. This isolation ensures high availability and fault tolerance.

In summary, AWS Regions are composed of multiple Availability Zones. When you choose a Region for your resources, you're selecting a specific geographical location with multiple isolated data centers (Availability Zones) to host your services and data. This setup enables redundancy, scalability, and resilience for your applications and infrastructure.

</details>
<details>
<summary>What is auto-scaling?</summary>

- Auto-scaling is a cloud computing feature that automatically adjusts the number of resources (such as servers) allocated to your application based on real-time demand. It helps ensure that your application can handle varying levels of traffic efficiently by adding or removing resources as needed, thereby improving performance and cost-efficiency.

</details>
<details>
<summary>What services can help minimise a DDoS attack?</summary>


To minimize a Distributed Denial of Service (DDoS) attack on your infrastructure, you can use services like:

- **AWS Shield**: AWS Shield is a managed DDoS protection service that safeguards your applications against large-scale, sophisticated attacks.

</details>
<details>
<summary>What is an AMI?</summary>

- An **AMI (Amazon Machine Image)** is a pre-configured and templated virtual machine image used to create virtual servers (EC2 instances) in Amazon Web Services (AWS). It contains an operating system, software applications, and any custom configurations needed for your cloud-based servers. AMIs enable you to quickly launch and replicate server instances, making it easier to scale your infrastructure and deploy consistent computing environments.

</details>
<details>
<summary>What are different types of load balancers?</summary>


There are three main types of load balancers:

- **Application Load Balancer (ALB)**: ALBs operate at the application layer (Layer 7) and are ideal for routing HTTP and HTTPS traffic. They are capable of content-based routing, SSL termination, and support for container-based applications.

- **Network Load Balancer (NLB)**: NLBs function at the transport layer (Layer 4) and are designed for handling TCP, UDP, and TLS traffic. They are highly performant and suitable for low-latency and high-throughput workloads.

- **Classic Load Balancer (CLB)**: CLBs are the legacy load balancers in AWS, offering basic Layer 4 and Layer 7 load balancing capabilities. They are typically used for simple traffic distribution requirements.

Each type of load balancer has specific use cases and features, allowing you to choose the one that best suits your application's needs.

</details>


-----Networking-----
<details>
<summary>What is a VPC?</summary>

A VPC (Virtual Private Cloud) is a virtual network environment provided by Amazon Web Services (AWS). It allows you to create and configure a logically isolated section of the AWS cloud where you can launch AWS resources like virtual servers (EC2 instances), databases, and more.

Key features of a VPC include:

- **Isolation**: VPCs provide network isolation, allowing you to create private and public subnets to control access to resources.

- **Custom IP Address Ranges**: You can define your IP address range for the VPC, enabling you to design your network architecture.

- **Security Groups and Network ACLs**: These allow you to control inbound and outbound traffic to and from resources within the VPC.

- **Connectivity Options**: VPCs can be connected to other VPCs, on-premises networks, and the internet using various networking options.

- **Subnets**: VPCs are divided into subnets, each associated with a specific Availability Zone. Subnets are used to distribute resources and provide high availability.

In summary, a VPC is a fundamental networking component in AWS that lets you create a virtual network environment to host and manage your cloud-based resources with control over network architecture and security.

</details>

<details>
<summary>How do Subnets work?</summary>

- Subnets are like separate neighborhoods within your cloud network. Each subnet has its own area of IP addresses and is isolated from the others. They're often placed in different parts of the cloud for extra safety, and you can control how traffic flows in and out of each subnet. This helps keep your cloud resources organized and secure.

</details>

<details>
<summary>What network object do you need to allow a server ingress from the internet?</summary>

- To allow a server to receive incoming traffic from the internet, you typically need to configure a **security group (in AWS)** or **a firewall rule** aka NACL (in general networking terms) to permit incoming traffic on the specific ports or protocols you want to allow. This enables your server to accept requests from the internet while still maintaining security by specifying which traffic is allowed.

</details>

<details>
<summary>How can your resources in the VPC get access to the internet?</summary>

To allow resources in your VPC to access the internet, you need to set up the following:

- **Internet Gateway (IGW)**: Attach an Internet Gateway to your VPC. It acts as a bridge between your VPC and the internet.

- **Route Table**: Modify the route table associated with your subnets to include a route (0.0.0.0/0) pointing to the Internet Gateway.

- **Elastic IP (EIP)**: For resources like EC2 instances that need a static public IP, allocate and associate an Elastic IP address.

With these configurations, resources in your VPC can send and receive traffic to and from the internet through the Internet Gateway while maintaining network security through security groups and network ACLs.

</details>


-----Scenario-based-----
<details>
<summary>I want to create a 3 Tier Architecture. Can you explain step by step of how I can go about this?</summary>

1. **Presentation Layer (Web):**

Step 1: Launch an Amazon EC2 instance for your web server. This instance will host your website or web application.
Step 2: Configure security groups to allow incoming web traffic (HTTP/HTTPS) to the web server.
Step 3: Optionally, attach an Elastic IP (EIP) for a static public IP address.

2. **Application Layer (App):**

Step 4: Launch another EC2 instance for your application server(s). This instance runs the business logic of your application.
Step 5: Configure security groups to allow incoming traffic from the web server to the application server on the necessary ports.
Step 6: Install and configure any middleware or application software required for your application.

3. **Data Layer (Database):**

Step 7: Create an Amazon RDS (Relational Database Service) instance or set up a database server (e.g., on EC2) for your database layer.
Step 8: Configure security groups to allow incoming database connections only from the application server(s).
Step 9: Create your database schema and tables, and configure database access and permissions.

</details>
<details>

<summary>In VPC with private and public subnets, database servers should ideally be launched into which subnet?</summary>

- In a VPC with both private and public subnets, database servers should ideally be launched into the **private subnets**. Placing database servers in private subnets ensures that they are not directly accessible from the internet, which enhances security. Public subnets are typically used for resources that need to be accessible from the internet, like web servers.

</details>

<details>
<summary>What are some security best pracites for EC2s?</summary>

- **Use Security Groups**: Configure security groups to control incoming and outgoing traffic to your EC2 instances. Only allow necessary ports and sources.

- **Use Key Pairs**: Authenticate access to your EC2 instances using key pairs (SSH keys for Linux or RDP keys for Windows) instead of passwords.

- **Regular Updates**: Keep your EC2 instances and their software up to date with security patches and updates.

- **Use IAM Roles**: Assign IAM roles to EC2 instances to grant them specific permissions, reducing the need for storing access keys on the instance.

- **Enable Monitoring**: Use Amazon CloudWatch to monitor performance and set up alarms for unusual activity or resource exhaustion.

- **Data Encryption**: Encrypt data at rest using services like Amazon EBS encryption and in-transit using SSL/TLS.

- **Snapshot Backups**: Create EBS snapshots and AMIs regularly to back up your instances, ensuring data recovery in case of failures.

- **Instance Isolation**: Separate instances into public and private subnets within a Virtual Private Cloud (VPC) for network isolation.

- **Disable Root Access**: Disable remote root login on Linux instances and use a sudo user for administrative tasks.

**IAM Policies**: Use fine-grained IAM policies to restrict access based on the principle of least privilege.

- **Use Bastion Hosts**: If necessary, employ a bastion host (jump server) to access private instances securely.

- **Monitor Access**: Monitor and audit access to your EC2 instances, including login attempts and user actions.

- **Automate Security**: Implement automation tools like AWS Systems Manager and AWS Config to enforce security policies.

</details>

<details>
<summary>I created a web application with autoscaling. I observed that the traffic on my application is the highest on Wednesdays and Fridays between 9 AM and 7 PM. What would be the best solution for me to handle the scaling?</summary>

To handle scaling for your web application with high traffic on Wednesdays and Fridays between 9 AM and 7 PM, you can:

- **Schedule-Based Auto Scaling**: Use AWS Auto Scaling's scheduled scaling feature. Set up a schedule to increase the desired number of instances during the peak hours on Wednesdays and Fridays and decrease it during off-peak hours.

- **Target Tracking Scaling Policy**: Create a target tracking scaling policy based on a metric like CPU utilization or request count per instance. Set the target to automatically adjust the number of instances to maintain a specific metric value. This can help handle traffic fluctuations efficiently.

By combining these approaches, your application can automatically adjust its capacity to meet demand, ensuring it scales up during peak times and scales down during quieter periods, optimizing cost and performance.

</details>

<details>
<summary>You have an application running on your Amazon EC2 instance. You want to reduce the load on your instance as soon as the CPU utilization reaches 100 percent. How will you do that?</summary>

To automatically reduce the load on your Amazon EC2 instance when CPU utilization reaches 100 percent, follow these steps:

- **Create an Auto Scaling Group**: Set up an Auto Scaling Group for your EC2 instance if you haven't already.

- **Create a Target Tracking Scaling Policy**: Within the Auto Scaling Group configuration, create a Target Tracking Scaling Policy.

- **Select CPU Utilization as the Metric**: Choose CPU utilization as the metric to track.

- **Set the Target Value**: Specify the target CPU utilization level at which you want to take action, such as 80 or 90 percent, not 100 percent, to avoid any performance issues. AWS Auto Scaling will automatically adjust the number of instances to maintain this target value.

- **Define Scaling Actions**: Configure scaling actions for when the CPU utilization exceeds the target value. You can specify actions to increase or decrease the number of instances based on your requirements.

- **Apply the Policy**: Apply the Target Tracking Scaling Policy to your Auto Scaling Group.


</details>


-----Others-----
- Name some managed runtimes for Lambda
