# AWS-CCP
Notes about AWS in preparation for the Certified Cloud Practitioner exam

## Topics
-[What is AWS?](#what-is-aws)
-[Benefits of AWS](#benefits-of-aws)
-[Global Infrastructure](#global-infrastructure)
-[Account Setup](#account-setup)
-[Products & Services](#products-&-services)

### What is AWS?
AWS is Infrastructure As A Service (IAAS). It forms the base for delivering other products. Heroku is a Platform As A Service (PAAS), through which applications can be hosted, and Gmail and Salesforce are Software As A Service (SAAS).

### Benefits of AWS
#### Reduce capital expenditure
AWS requires almost no upfront capital expenditure, instead requiring variable expenditure based on usage.

#### Receive lower cost service
AWS benefits from economies of scale, spreading its capital expenditure among all of its users, meaning it can provide services for far cheaper.

#### Eliminate capacity concerns
AWS can scale automatically to meet peak demand.

#### Increase speed and agility
Because there is no need to purchase, install, configure, and maintain servers, as well as the fact that many services such as load-balancers are pre-built, customers can grow with demand, and pivot rapidly.

#### Eliminate data center maintenance
All hardware is maintained by AWS, and accessed remotely by users.

#### Attain low-latency global reach
Since AWS has availability zones in regions all over the world, users are never far from a data center.

### Global Infrastructure
#### Geographic Regions (GR): 22
##### Availability Zones (AZ): 69
Inter-AZ latency: <10ms
###### Edge Locations (EL): Nearing at >= 3 per AZ
Each EL has a is owned by a trusted partner of AWS, and serves requests for **Cloudfront** and **Route53**, as well as **S3 Transfer Acceleration** and **API Gateway traffic**

### Account Setup
After creating an account,
1. Enable Multi-Factor Authentication (MFA) for **ALL USERS**
2. Create an **IAM** user to use instead of root
  - Create an 'Admins' group
  - **assign a role of 'Admin' with all permissions except user creation/deletion/editing
3. Set the password policy
  - Force rotation of credentials (90-day expiration)
4. (Optional) Set a public key for SSH

#### AWS Access Options
- SSH
- AWS Sessions Manager (Recommended)
  1. 'Systems Manager'
  2. 'Node Management'
  3. 'Sessions Manager'
  4. `sudo su - [ec2] - user`

### Products & Services
#### **E**lastic **C**loud **C**omputing (**EC2**)
  1. Create an **A**mazon **M**achine **I**mage (AMI), a copy of the server
  2. Use the AMI to create an '**Auto Scaling Group**'
  - AMI can be used when upgrading a server

#### AWS Lambda
  Lambda is a service that allows code for "serverless" applications, i.e. apps run on auto-scaling cloud-based servers that are 'pay-as-you-go', to be written for the front-end. It responds to events initiated by the user by firing functions based on the event. 
