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

## 3. Launch Configuration and Templates

#

## 4. Auto-Scaling Groups

#

## 5. Network Load Balancing (NLB)

#

## 6. SSL Offload & Session Stickiness

#
