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
- ![w/gateway](img/advVPCendptsgw.png)

## 4. VPC Endpoints (Interface)

#

### summary

- interface endpoints are used to allow private IP addressing to access public AWS services
- S3 and DynamoDB are handled by gateway endpoints
- other supported services are handled by interface endpoints
- unlike gateway endpoints, interface endpoints are not HA by default - they are normal VPC network interfaces and should be placed 1 per AZ to ensure full HA

### concepts

- similar to gateway endpts but diff execution
- provide private access to AWS public services
- ...anything not S3 or DDB
- difference: interface endpts are not HA by default
  - added to specific subnets
  - for HA add one endpt to one subnet per AZ used in the VPC
- network access controlled via Security Group
- Endpoint policies - restrict what can be done w/endpoint
- TCP and IPv4 support only
- uses PrivateLink behind the scenes
- ![vpc endpoints interface concepts](img/advVPCendpts-interface.png)

### more concepts

- Gateway endpts use a prefix list
- interface endpts use DNS
- new DNS endpoint name
- given number of DNS names
  - endpoint regional DNS
  - endpoint Zonal DNS
- applications can optionally use these or ...
- PrivateDNS overrides the default DNS for services
- ![interface endpts concepts](img/advVPCinterfaceconcepts.png)

### architecture

- arch example w/o interface endpts
- ![ex w/o interface endpts](img/advVPCinterfacearch.png)
- arch ex w/interface endpts
- ![ex w/ interface endpts](img/advVPCwEndpts.png)
- arch ex w/interface endpts and private DNS
- ![ex w/ interface endpts and DNS](img/advVPCwEndptsDNS.png)

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
