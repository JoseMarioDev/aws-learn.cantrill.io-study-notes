## 1. Load Balancing Fundamentals

#

- Summary:

  - how load balancers work and what they actually do
  - how they differ from DNS HA features such as multivalue request routing

- fundamentals:
  - life w/o load balancers
    - all traffic goes to one server - bad
    - could have multiple servers and use DNS multi value routing to route traffic
      - helps but doesnt scale well
    - DNS routing is good globally but locally
    - locally use load balancing
    - ![life w/o lb](img/HAloadbalancing.png)
  - life w/load balancer
    - listens for a port
    - user connects to load balancer not server
    - client has no awareness of load balancer. thinks it's talking to server
    - lb runs health checks
    - ![load balancer arch](img/HAloadbalancerarch.png)
- exam notes:
  - clients connect to load balancer
    - specially to the listener
  - LB connects to targets(aka servers)
  - 2 connections. 1 to listener 1 to backend
  - client abstracted from individual servers
  - used for HA, FT, and scaling
    - ![exam power ups](img/HAlbexamnotes.png)

## 2. Application Load Balancing (ALB)

#

- Summary:

  - lesson steps through architecture of ALB
  - talks about Target Groups, connection architecture, and how ALB achieves HA and Scaling

- concepts:

  - ALB is a layer 7 LB - understands HTTP/S
  - scalable and highly available
  - internet facing or internal
    - depends if nodes have public IP or not
  - sits inbetween client and server
    - listens on the outside - sends to Targets(aka groups)
  - billing:
    - bills on hourly rate and LCU rate(capacity)
    - ![ALB concepts](img/HAalbconcepts.png)

- architecture:

  - each AZ in a VPC gets a lb node
  - client sends request to lb
  - uses cross zone load balancing to distribute load evenly among all AZs
    - ![HA lb arch](img/HAlbarch.png)
  - performs health checks
    - ![health checks](img/HAalbhealth.png)
  - target and groups:
    - where the load is going from the lb is a target
      - can be multiple things, ec2 instances, lambdas, etc
      - can be grouped together
    - ![HA alt target groups and paths](img/HAalbtargets.png)

- exam power ups:
  - targets are ec instances, lambda functions, containers
  - rules are path based or host based
  - supports ec2, ecs, eks, lambda, http/s/2,
  - alb can use SNI for multi SSL certs
  - albs are recommended vs clb(legacy classic lbs)
    - ![Ha Alb exam pu](img/HAalbexam.png)

## 3. Launch Configuration and Templates

#

- summary:

  - launch configurations and templates provide the **what** to auto scaling groups
  - define what gets provisioned
    - the AMI
    - instance type
    - networking & security
    - key pair to use
    - user data to interject
    - IAM role to attach

- concepts:
  - allow to define config of ec2 instance in advance
  - AMI, instance type, storage, key pair
  - networking, sec group
  - user data and IAM role
  - both are not editable. defined once LT has versions
  - LT has newer features - see slide
  - ![launch config and template concepts](img/HAlaunchconfig.png)
- architecture:
  - launch configs are not editable
  - templates are, are recommended by AWS are newer -![launch config and template arch](img/HAlauncharch.png)

## 4. Auto-Scaling Groups

#

## 5. Network Load Balancing (NLB)

#

## 6. SSL Offload & Session Stickiness

#
