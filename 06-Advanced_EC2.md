## Bootstrapping EC2 using User Data

#

- Bootstrapping is the process of configuring EC2 instance to perform automated install & configuration steps 'post launch' before instance is brought into service
- executed only once at **launch time**
- anything in User Data is executed by the instance OS
- if problem w/data instance can still be created, but you end up with bad config(see pic)
- User data is opaque to EC2 just a block of data

  - is not secure. don't use it for passwords or long term creds
  - user data is limited to 16kb
  - can be modified when instance stopped

  ![Alt text](img/ecbootstrap.png 'workflow')

- boot-time-to-service-time
  - time taken from launch time to service time
  - post launch time is time it takes to install apps on top of creating instance
  - can use AMI baking, front load the image
  - best way is to use AMI baking and bootstraping for optimal
    ![Alt text](img/ec2boottime.png 'best practices')

### Enhanced Bootstrapping with CFN-INIT

#

### EC2 Instance Roles & Profile

#

### SSM Parameter Store

#

### System and Application Logging on EC2

#

### EC2 Placement Groups - part 1

#

### EC2 Placement Groups - part 2

#

### Dedicated Hosts

#

### Enhanced Networking & EBS Optimized

#
