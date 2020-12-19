## 1. Architecture Evolution - Part 1 - Monolithic and Tiered

#

### summary

- 2 part lesson, first part covers how applications can be evolved from monolithic to tiered architecture

### concepts

- monolithic architecture
  - one box handles everything. see cattube example
  - cons: one failure to part affects everything. fail together. also scale together since on same server, and bill together
  - ![monolithic arch](img/serverlessmonoarch.png)
- tiered architecture
  - things are still connected together, but can scale independently
  - can use internal load balancers to manage each tier's load
  - allows for horizontal scaling and HA
  - cons: each tier is still dependent on each other so can't scale to zero and could still fail
  - ![tiered arch](img/serverlesstieredarch.png)

## 2. Architecture Evolution - Part 2 - Queue Based, Microservice & Event Driven

#

### summary

- part 2 looks at the evolution of architecture - queue based design, microservices, event driven architecture

### concepts

- queue

  - similar to CS. FIFO
  - uses async communications, doesn't depend on another tier. decoupled. think cattube s3 bucket from slide
  - ![queue arch](img/serverlessqueuearch.png)

- microservice and event driven architecture
  - do individual things well
  - a microservice is just a tiny self sufficient application
  - producers are triggered by events, consumers take from producers
  - events are generated when something happens
  - event routers handle events between producers/consumers via event bus
  - event driven architures only consume resources when required
  - ![event driven concepts](img/serverlesseventconcepts.png)

### architecture

- slides
  - ![microservices arch](img/serverlessmicroarch.png)
  - ![event driven arch](img/serverlesseventarch.png)

## 3. AWS Lambda

#

### summary

-

### concepts

-

### architecture

-

## 4. CloudWatchEvents and EventBridge

#

### summary

-

### concepts

-

### architecture

-

## 5. API Gateway

#

### summary

-

### concepts

-

### architecture

-

## 6. Serverless Architecture

#

### summary

-

### concepts

-

### architecture

-

## 7. Simple Notification Service

#

### summary

-

### concepts

-

### architecture

-

## 8. Step Functions

#

### summary

-

### concepts

-

### architecture

-

## 9. Simple Queue Service

#

### summary

-

### concepts

-

### architecture

-

## 10. Kinesis & Kinesis Firehouse

#

### summary

-

### concepts

-

### architecture

-
