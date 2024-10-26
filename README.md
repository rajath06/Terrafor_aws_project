# AWS Infrastructure Setup with Terraform: VPC, Subnets, EC2 Instances, and Load Balancer for Web Application Deployment
This project uses Terraform to automate the deployment of an AWS VPC with subnets, an internet gateway, security groups, EC2 instances, a load balancer, and a target group. The setup is designed to host an HTML page, ensuring scalability, accessibility, and health checks across instances.

# Prerequisites
1 AWS Account with IAM credentials

2 Terraform installed on your local machine

# Project Setup

# 1. Create VPC with Subnets
- Create a VPC with two subnets based on the provided network diagram.
- Each subnet will host an EC2 instance for load balancing across availability zones.

# 2. Create an Internet Gateway
- Attach an internet gateway to the VPC to enable internet access.

# 3. Configure Route Table
- Update the VPC route table to direct internet-bound traffic (destination 0.0.0.0/0) to the internet gateway.
- Associate the route table with both subnets for internet connectivity.

# 4. Set Up Security Group
- Create a security group to manage access to EC2 instances.
Add inbound and outbound rules:
- Inbound rules for specific ports (e.g., SSH on port 22 and HTTP on port 80).
- Outbound rules for general internet access.
  
# 5. Launch EC2 Instances
- Create EC2 instances in each subnet.
- Use user data to install necessary software on instance launch.
  
# 6. Load Balancer Setup
- Deploy an Application Load Balancer (ALB) to distribute traffic across instances in both subnets.
- Set the load balancer to span both availability zones.
  
# 7. Configure Target Group
- Create a target group for the EC2 instances, defining health checks to monitor instance health.
- The target group will forward requests to the instances.
  
# 8. Add Listeners

- Define listeners to route traffic between the load balancer and target group.
- Listeners act as intermediaries, managing traffic flow to target instances.
  
# 9. Output Load Balancer DNS
- Print the load balancer DNS name for easy access to the deployed environment.
  
# Commands Used
- terraform apply -auto-approve: Automatically applies changes without confirmation prompts.
- terraform fmt: Formats Terraform files to follow best practices.
# Final Note
This setup hosts a static HTML page, deployed via EC2 instances in a load-balanced configuration

