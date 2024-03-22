## Questions for AWS interviews / Certifications

#### Explain about the SNS, SQS and SES services?
Amazon Simple Notification Service (**SNS**) is fully managed, secured, available messaging services by AWS that help decouple server less applications, micro-services, and distributed systems. SNS can be started within minutes from either AWS management console, command-line interface, or software development kit.
• Amazon Simple Queue Service (**SQS**) is a fully managed message queues for server less applications, micro-services, and distributed systems. The advantage of SQS FIFO guarantees single time processing and exact order sent by this kind of messaging service.
• Amazon Simple Email Service (**SES**) offers sending and receiving email services for informal, notify, and marketing correspond
ence via email for their cloud customers through SMTP interface.

#### 1. What’s the difference between on-demand and spot instance?

   - Spot instances provide a lower cost option for developers to manage non-essential tasks on AWS platform. These instances are those you would bid on and they launch once the bid is higher than the going price based on supply and demand. There is a major drawback on spot instances, if the spot exceeds the bid price it can be terminated at any time.
   - On-demand instances are created based on user need and cost by the hour. When they are no longer required, they can be released.

#### 3. Explain the difference between vertical and horizontal scaling?.
Vertical scaling is a growth mechanism by which an existing machine is given more compute power. Horizontal scale occurs when companies grow by adding more machines to their infrastructure.

#### 4. Explain VPC and its security?
A virtual private cloud (VPC) is an isolated private cloud environment typically hosted and secured within another cloud, which is usually a public cloud. VPC allows the user to select IP address range, create subnets, and configure route tables, network gateways, and security settings.

Security within a VPC is provided through

- **Security groups** — Act as a firewall for associated EC2 instances, controlling both inbound and outbound traffic at the instance level
Network access control lists (ACLs) — Act as a firewall for associated subnets, controlling both inbound and outbound traffic at the subnet level
- **Flow logs** — VPC Flow Logs is a feature that enables you to capture information about the IP traffic going to and from network interfaces in the VPC and can help in monitoring the traffic or troubleshooting any connectivity issues

#### 5. What is the IGW and NAT?
Its highly available VPC component that allows communication between instances in the VPC and the Internet.
- An Internet gateway serves two purposes:
   - To provide a target in the VPC route tables for Internet-routable traffic,
   - To perform network address translation (NAT) for instances that have been assigned public IP addresses.
- **NAT** - device enables instances in a private subnet to connect to the Internet or other AWS services, but prevents the Internet from initiating connections with the instances.

#### 6. What is the relation between AMI and Instance?
Instances can be launched by AMIs. One AMI can launch as many instances as required. An instance type defines the hardware of the host computer including information about computers and its memory abilities. After launching an instance, it works as a traditional host and could be interacted with as with any other computer.

#### 7. Explain the AWS services and how they communicate?
<img width="1155" alt="image" src="https://github.com/sandipsahoo2k2/my/assets/5547869/03665c8d-fb08-4bcb-81ef-75a027ddf699">

#### 8. What are edge locations in AWS?
Edge locations in AWS are data centers that deliver as low a latency as possible, i.e., these data centers are physically close to the client. When a user tries to access content, the searches automatically search in the edge location for the fastest responses.

#### 9. Explain the difference between elasticity from scalability?
**Elasticity** : The ability of a system to handle an increase in the workload by simply adding hardware resources when demand rises, and rolling back scaled resources when there’s no demand.
**Scalability** : ability of a system to increase the hardware resources for handling an increase in demand. It can be achieved by either increasing the hardware specs or increasing the number of processing nodes.

#### 10. Difference between NACL and SG?
<img width="652" alt="image" src="https://github.com/sandipsahoo2k2/my/assets/5547869/772d9afb-5160-4451-8b29-b56b2998b699">

#### 11. Difference between S3 & Glacier?
S3 stands for Simple Storage Service and it is Object-based storage, S3 provides secure, durable, highly scalable object storage. This is easy to use with a simple web services interface to store and retrieve any amount of data from anywhere on the web.

S3 Glacier storage class is the cheapest storage class, but it can be used for archive only. You can store any amount of data at a lower cost than other storage classes. You can upload the objects directly to the Glacier. S3 Glacier provides three types of models:

**Expedited**: In this, data is stored for a few minutes, with very high fee.
**Standard**: The retrieval time of the standard model is 3 to 5 hours.
**Bulk**: The retrieval time of the bulk model is 5 to 12 hours.

#### 11.b Different S3 Modes
* With S3 Object Lock, you can store objects using a write-once-read-many (WORM) model. Object Lock can help prevent objects from being deleted or overwritten for a fixed amount of time or indefinitely
* Compliance mode - compliance mode, a protected object version can’t be overwritten or deleted by any user, including the root user in your AWS account
* Governance mode - User with specific IAM permissions can delete protected resources.
* Legal hold option doesn't have any retention period and remain effective until it is removed.

#### 12. What is Load Balancer ?
Load Balancer is a virtual machine or appliance that balances your web application load that could be Http or Https traffic. It balances a load of multiple web servers so that no web server gets overwhelmed.

**Application Load Balancer**(Layer 7 (HTTP/HTTPS traffic), Flexible)
- ALB can in turn route traffic to different services based on either the host or the content of the path contained within that URL. It has other advantage as well like SSL Termination, Sticky Sessions

**Network Load Balancer** (Layer 4 (TLS/TCP/UDP traffic), Static IPs.)
- It is context-less, caring only about the network-layer information contained within the packets it is directing this way and that.
ELB only allows routing based on port number. TCP traffic when high performance is required.
It makes routing decisions at the transport layer (TCP/SSL), and it can handle millions of requests per second.

#### 13. What is cloud watch?
Amazon CloudWatch is a monitoring and management service that provides data and actionable insights for AWS, hybrid, and on-premises applications and infrastructure resources. With CloudWatch, you can collect and access all your performance and operational data in form of logs and metrics from a single platform.

#### Different types of cloud computing?
There are three main types of cloud computing offered as services by the service providers..

**Infrastructure as a Service** (IaaS) provides basic building blocks such as virtual or dedicated hardware in the form of computers, data storage space as well as networking access in the form of IT infrastructure.
**Platform as a Service** (PaaS) offers managing hardware and operating systems for the customers and focusing on deploying their products.
**Software as a Service** (SaaS) offers complete management of end-user applications along with management of infrastructure supporting these applications.

#### What is EC2 or elastic compute cloud and their pricing model?
EC2 is a virtual machine that provides resizable compute capacity in the cloud. EC2 allows you to pay for the capacity that you actually use. There are 4 types of pricing options in AWS as descried below.

- **On Demand**
   It allows you to pay a fixed rate by the hour or even by the second with no commitment. It is suitable for the applications with short term, spiky or unpredictable workloads that cannot be interrupted.
   On Demand is perfect for the users who want low cost and flexibility of Amazon EC2 without any up-front investment or long-term commitment.

- **Reserved**
  It is useful for applications with steady state and for the applications that require reserved capacity.
  You can contract by paying some upfront for 1 or 3 years in length., so it gives you a significant discount on the hourly charge for an
  instance.
- **Spot Instances**
   It allows you to bid for a price whatever price that you want for instance capacity and providing better savings if your applications have flexible start and end times.
   It is useful for urgent need for large amounts of additional computing capacity.
- **Dedicated Hosts**
   Dedicated hosts are used to address compliance requirements and reduces host by allowing to use your existing server-bound server licenses.
   It can be purchased as a Reservation for up to 70% off On-Demand price.

#### AWS DataSync
 DataSync allows you to copy large datasets with millions of files without having to build custom solutions with open-source tools or licenses and manage expensive commercial network acceleration software. You can use DataSync to migrate active data to AWS, transfer data to the cloud for analysis and processing, archive data to free up on-premises storage capacity or replicate data to AWS for business continuity.

AWS DataSync enables you to migrate your on-premises data to Amazon S3, Amazon EFS, and Amazon FSx for Windows File Server. You can configure DataSync to make an initial copy of your entire dataset and schedule subsequent incremental transfers of changing data toward Amazon S3. Enabling S3 Object Lock prevents your existing and future records from being deleted or overwritten.

_AWS DataSync is primarily used to migrate existing data to Amazon S3. On the other hand, AWS Storage Gateway is more suitable if you still want to retain access to the migrated data and for ongoing updates from your on-premises file-based applications._

#### What are the benefits for moving into cloud computing?
- **Scalability**: Cloud allows scale up or down based on usage, you only need to pay per use for the computing and storage perspective.
- **Reliability**: Cloud providers offer the reliability of their infrastructure up to nearly 100%, with provision for multiple levels of redundancy and backups in case it is needed.
- **Security**: Most cloud providers are compliant with industry-level security protocols like HIPAA, PCI, offer access restrictions to applications and systems at multiple levels and monitoring services at a very granular level to trigger alarms.
- **Cost Efficiency**: Moving to the cloud for startup companies offers benefits of cost savings by differing from investing in expensive servers, managing, and maintaining them. Every month, companies have to pay only for the computing power and storage that are utilized by them during the month.
