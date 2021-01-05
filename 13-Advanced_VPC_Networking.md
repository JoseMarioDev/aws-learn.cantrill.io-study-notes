## 1. VPC Flow Logs

#

### summary

- VPC flow logs is a feature allowing the monitoring of traffic flow to and from interfaces within a VPC
- VPC flow logs can be added at a VPC, subnet, or interface level
- flow logs don't monitor packet contents -> that requires a packet sniffer
- flow logs can be stored on S3 or cloudwatch logs

### concepts

- essential diagnostic tool
- need to know functionality for exam
- only capture packet metadata. not packet contents
- source/dest ip address, etc anything you can observe from the outside
- can apply to 3 diff levels
- VPC, subnet, interface
- flow logs are not realtime
- can be config to use S3 or cloudwatch logs
- ![adv vpc flowlog concepts](img/advVPCflowlogconcepts.png)
- inheritance down see arch slide

### flow logs

- collection of fields
- ex: bob is pinging ec2 instance inside his subnet
- flow log in slide
- source dest ip port number protocol number accepted/rejected
- dont log all traffic. some things are excluded
- ![ex of log entry](img/advVPCflowlogentry.png)

### architecture

- make sure you put the monitor in the correct spot. see slide
  ![flow log arch](img/advVPCflowlogarch.png)

## 2. Egress-Only Internet Gateway

#

### summary

- allow outbound(and response) only access to the public AWS services and public internet for IPv6 enabled instances or other VPC based services

### concepts

- IG that only allows connections from inside to outside
- w/IPv4 addresses are private/public
- NAT allows private IPs to access public networks
- without allowing externally initiated connections(in)
- with IPv6 all IPs are public
- IG(IPv6) allows all IPs in and out
- NAT doesn't work with IPv6, that why we have egress-only IG
- ![egress only IG concepts](img/advVPCegressconcepts.png)

### architecture

- ![egress arch](img/advVPCegressarch.png)

## 3. VPC Endpoints (Gateway)

#

### summary

- Gateway endpoints are a type of VPC endpoint which allows access to S3 and DynamoDB without using public addressing
- Gateway endpoints add 'prefix lists' to a route table, allowing the VPC router to direct traffic flow to the public services via the gateway endpoint

### concepts

- used in more complex arch
- provide private access to services - S3 and DynamoDB
- normally public ip addresses are required
- prefix list added to route table -> gateway endpoint
- GE are highly available (HA) across all AZs in a region by default
- endpoint policy is used to control what it can access
- regional...can't access cross-region service
- 2 main use cases
  - private vpc allow to access public resources - S3 or DynamoDB
  - private only S3 buckets. help prevent leaky buckets
- limitations: only accessible from inside that specific VPC
- ![vpc endpoints(gateway) concepts](img/advVPCgwendpts.png)

### architecture

- current architecture w/o vpc endpts
- ![arch w/o gateway](img/advVPCendptsgwarch-old.png)
- arch w/gateway endpt
- ![w/gateway](img/advVPCendptsgwarch-new.png)

## 4. VPC Endpoints (Interface)

#

### summary

### concepts

### architecture

## Demos

#

### summary

## 5. VPC Peering

#

### summary

### concepts

### architecture

## Demo

#
