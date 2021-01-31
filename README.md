# AWS-CCP
Notes about AWS in preparation for the Certified Cloud Practitioner exam

## Topics
-[What is AWS?](#what-is-aws)
-[Benefits of AWS](#benefits-of-aws)
-[Global Infrastructure](#global-infrastructure)
-[Account Setup](#account-setup)
-[Products & Services](#products-&-services)

### What is AWS?
AWS is **I**nfrastructure **a**s **a** **S**ervice (IaaS). It forms the base for delivering other products. Heroku is a **P**latform **a**s **a** **S**ervice (PaaS), through which applications can be hosted, and Gmail and Salesforce are **S**oftware **a**s **a** **S**ervice (SaaS).

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
  
##### Pricing (cheapest to most expensive)
1. **On-Demand** (least commitment)
  - Low-cost & flexible
  - Pay-per-hour
  - **use case:** Short-term, spiky, unpredictable workloads, first-time apps
  - For **workloads that cannot be interrupted**
2. **Reserved Instances (RI)**
  - **Use case:** Steady state or predictable usage
  - Can resell unused RI in the **R**eserved **I**nstance **M**arketplace
  - Reduced pricing based on **Term**, **Class Offering**, and **Payment Option**
  **Terms:** 1yr or 3yr
  **Payment Options:** All Upfront / Partial Upfront / No Upfront
  **Class Offerings:**
    - **Standard:** Up to 75% off compared to On-Demand. Cannot change RI Attributes
    - **Convertible:** Up to 53% off. **Can** change RI Attributes **if greater or equal in value**
    -**Scheduled:** Reserve instances for specific time periods
3. **Spot Pricing** (up to **90% off**)
  - Uses spare computing capacity
  - Flexible start and end times
  **Use case:** When interruptions are acceptable. Non-critical background jobs
  - Instances can be terminated by AWS **at any time**, with not partial hour charges
  - If instance is terminated by you, will be charged for the extra hour
4. **Dedicated Hosting** (most expensive)
  - Dedicated servers
  - On-demand or reserved (up to 70% off)
  - **Use case:** When you need a guarantee of isolate hardware (enterprise requirements)

#### AWS Lambda
  Lambda is a service that allows code for "serverless" applications, i.e. apps run on auto-scaling cloud-based servers that are 'pay-as-you-go', to be written for the front-end. It responds to events initiated by the user by firing functions based on the event.
  
#### Free Services
  -Completely free: IAM, Amazon VPC, Organizations & Consolidated Billing, AWS Cost Explorer
  - Free, but resources they provision cost money:
    - **Auto Scaling**
    - **CloudFormation**
    - **Elastic Beanstalk**
    - OpsWorks
    - Amplify
    - AppSync
    - CodeStar

#### Support Plans (cheapest to most expensive)
**7** Trusted Advisor Checks
  1. **Basic:** $0/month
    - Email support for **Billing and Account** only
  2. **Developer:** $20/month
    Above, plus:
    - Tech email support ~24 hours until reply
    - **No** third-party support
    - General Guidance <24 hours 'til reply
    - System Impaired <12 hours 'til reply
  3. **Business:** $100/month
    Above, plus:
    - Chat, Phone tech support 24/7 w/ screen sharing
    - Production System Impaired <4 hours
    - Production system **DOWN** <1 hour
    - Third party support (Node.js, Python, etc.)
    
  4. **Enterprise** $15,000/month
    Above, plus:
    - Business Critical System **DOWN** <15 minutes
    - Personal Concierge
    - **T**echnical **A**ccount **M**anager
 
 #### AWS Marketplace
 A curated digital catalogue of **I**ndependent **S**oftware **V**endors
  - Free to use, but products may cost money
  - Sales channel for ISVs - Sell your own solutions
  - Products can be offered as:
    - AMIs
    - AWS CloudFormation templates
    - SaaS
    - Web ACL
    - AWS WAF rules
    
 #### AWS Trusted Advisor
 An automated checklist of best practices
  - **Security**
    - MFA on root account
    - IAM Access key rotation
  - **Cost Optimization**
    - Idle load balancers
    - Unassociated elastic IP addresses
    - etc.
  - **Performance**
    - High utilization Amazon EC2 instances
  - **Fault Tolerance**
    - Amazon RDS backups
  - **Service Limits**
    - VPC
    
#### Consolidated Billing
One master account pays the entire bill for all associated member accounts

#### Volume Discounts
Member accounts are summed toward the total usage, so be sure to register your account to the organization
  - First 10TB @ $0.12 per GB
  - Next 40TB @ $0.13 per GB
