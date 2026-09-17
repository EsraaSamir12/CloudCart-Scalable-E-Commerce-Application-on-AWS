# CloudCart - Scalable E-Commerce Application on AWS

## Project Overview

CloudCart is a cloud-based e-commerce application deployed on Amazon Web Services (AWS). The project focuses on transforming a traditional single-server application into a scalable, highly available, and reliable cloud-based architecture.

The main challenge was to design an infrastructure that could handle increasing application traffic without depending on a single server. To address this challenge, the application was deployed across multiple Amazon EC2 instances distributed across multiple Availability Zones.

The architecture separates the main application components into different layers, including compute, load balancing, database, session management, storage, networking, monitoring, and notifications.

## Architecture

The architecture is built inside an Amazon VPC with dedicated networking and security configurations controlling communication between the different components.

<p align="center">
  <img src="https://raw.githubusercontent.com/EsraaSamir12/CloudCart-Scalable-E-Commerce-Application-on-AWS/main/CloudCart-Image.jpeg"
       alt="CloudCart AWS Architecture"
       width="900">
</p>

## Application Layer

The frontend and backend application are deployed on Amazon EC2 instances. Multiple instances are used instead of relying on a single server, allowing the application to continue operating even if one instance becomes unavailable.

The EC2 instances are distributed across multiple Availability Zones to improve availability and reduce dependency on a single infrastructure location.

An Application Load Balancer is placed in front of the EC2 instances. It receives incoming HTTP requests and distributes traffic across the available application instances.

EC2 Auto Scaling is used to automatically adjust the number of application instances according to traffic and resource demand.

## Database Layer

Amazon RDS for MySQL is used as the application's managed relational database.

Instead of running and maintaining a MySQL database directly on an EC2 instance, Amazon RDS provides a managed database environment for storing and accessing application data.

The application connects to the RDS database through the private network configuration inside the VPC.

## Session Management

One of the challenges of running the application across multiple EC2 instances is managing user sessions.

When a user sends multiple requests, the Application Load Balancer may route those requests to different EC2 instances. If session information is stored locally on a single instance, the user's session may not be available when the request reaches another instance.

To solve this problem, Amazon ElastiCache with Redis is used as centralized session storage.

The application stores session information in Redis instead of relying only on local EC2 storage. This allows multiple application instances to access the same session data.

## Storage

Different AWS storage services are used based on the application's requirements.

Amazon EBS provides block-level storage associated with EC2 instances and can be used for instance-level application storage.

Amazon EFS provides shared file storage that can be accessed by multiple EC2 instances.

Amazon S3 provides object storage for application files and other data that require durable and scalable storage.

## Networking and Security

The complete infrastructure is deployed inside an Amazon VPC.

The VPC provides the network environment for the application and allows the different AWS components to communicate securely.

Subnets are used to organize resources within the VPC, while Route Tables control network traffic between different destinations.

Security Groups are used as virtual firewalls to control inbound and outbound traffic between the application, load balancer, database, and other AWS services.

Internet Gateway and NAT Gateway are used where required to provide controlled connectivity between private and public resources.

## Monitoring and Notifications

Amazon CloudWatch is used to monitor the application's infrastructure and collect metrics from AWS resources.

CloudWatch can be used to monitor resource utilization and application-related metrics and to create alarms when specific conditions are met.

Amazon SNS is used as a notification service to send alerts when important monitoring events occur.

This allows infrastructure events to be monitored and notifications to be delivered when configured thresholds or conditions are triggered.

## AWS Services Used

### Compute

* Amazon EC2
* EC2 Auto Scaling

### Networking

* Amazon VPC
* Application Load Balancer
* Subnets
* Route Tables
* Internet Gateway
* NAT Gateway
* Security Groups

### Database

* Amazon RDS
* MySQL

### Session Management

* Amazon ElastiCache
* Redis

### Storage

* Amazon S3
* Amazon EBS
* Amazon EFS

### Monitoring and Notifications

* Amazon CloudWatch
* Amazon SNS

## Key Features

* Scalable application infrastructure using Amazon EC2
* Traffic distribution using Application Load Balancer
* Automatic scaling based on application demand
* Deployment across multiple Availability Zones
* Managed MySQL database using Amazon RDS
* Centralized session management using Redis
* Object storage using Amazon S3
* Block storage using Amazon EBS
* Shared file storage using Amazon EFS
* Network isolation using Amazon VPC
* Traffic control using Route Tables and Security Groups
* Infrastructure monitoring using Amazon CloudWatch
* Automated notifications using Amazon SNS

## High Availability

CloudCart is designed to improve application availability by distributing the application across multiple EC2 instances and Availability Zones.

The Application Load Balancer distributes incoming traffic across available instances, while Auto Scaling allows additional instances to be launched when required.

Using multiple application instances reduces the application's dependency on a single EC2 instance.

## Scalability

The application layer is designed to scale according to changes in traffic.

Auto Scaling can increase the number of EC2 instances when application demand increases and reduce the number of instances when demand decreases.

The Application Load Balancer automatically distributes incoming requests across the available instances.

Centralized Redis session storage allows the application to maintain shared session information while requests are distributed across multiple servers.

## Project Objectives

The main objectives of the CloudCart project were to:

* Transform a traditional e-commerce application into a cloud-based architecture.
* Implement a scalable application infrastructure.
* Improve application availability by using multiple EC2 instances and Availability Zones.
* Distribute incoming traffic using an Application Load Balancer.
* Implement automatic scaling using EC2 Auto Scaling.
* Use Amazon RDS as a managed MySQL database.
* Implement centralized session management using Redis.
* Use different AWS storage services according to application requirements.
* Configure VPC networking and security controls.
* Implement monitoring and notification mechanisms using CloudWatch and SNS.

## Project Outcome

CloudCart provided practical experience in designing and deploying a complete cloud-based application architecture using AWS.

The project demonstrates how different AWS services can work together to transform a traditional application into a more scalable and highly available architecture while separating application, database, storage, networking, session management, monitoring, and notification responsibilities.
