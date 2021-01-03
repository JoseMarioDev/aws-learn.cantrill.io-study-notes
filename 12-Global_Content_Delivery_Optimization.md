## 1. CloudFront Architecture Basics

#

### summary

- cloudfront is AWS's content delivery network(CDN) product
- lesson introduces key product concepts and terms, visually steps through the architecture and talks in detail about managing caching performance

### concepts

- cloudfront is a global object cache(CDN)
- content is cached in locations close to customers
- lower latency and higher throughput
- can handle static and dynamic content
- ![cfn basics](img/cfnconcepts.png)

### terms

- origin - source location of your content
- distribution - the configuration unit of cloudfront
- edge location - local infrastructure whic hosts a cache of your data
- regional edge cache - larger version of edge location. provides another layer of caching
- ![cfn terms](img/cfnterms.png)

### architecture

- bob uploads data to bucket, sets config in a distribution that points to bucket as origin.
- edge locations cache content, are globally distributed.
- each distribution as a domain name
- you config each distribution and deploy it to the edge locations
- in middle, are the regional edge locations. support multiple edges in same location area
- if data isnt in edge location, it checks the regional edge. see slide
- integrates w/ACM to add HTTPS availability
- caching is only for GETS. PUTS go directly to origin, no right caching. know for exam
- ![cfn arch basics w/regional edges](img/cfnarch.png)

### caching optimization

- when caching object, you also cache any query string parameters
- to get cached copy, you need to also cache the query string
- be careful when using query string parameters. i.e. order_id
- option Forward to Origin - YES or NO
- ![cfn optimization and query strings](img/cfnoptimization.png)

## 2. ACM

#

### summary

- AWS certificate manager is a service which allows the creation, management, and renewal of certs
- allows deployment of certs onto supported AWS services such as Cloudfront and ALB

### concepts

### architecture

## Demos

#

#

## 3. Securing CF and S3 using OAI

#

### summary

### concepts

### architecture

## Demo

#

## 4. Lambda@Edge

#

### summary

### concepts

### architecture

## 5. Global Accelerator

#

### summary

### concepts

### architecture
