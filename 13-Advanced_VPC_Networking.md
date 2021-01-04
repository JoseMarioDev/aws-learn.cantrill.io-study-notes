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

### architecture

## 3. VPC Endpoints (Gateway)

#

### summary

### concepts

### architecture

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
