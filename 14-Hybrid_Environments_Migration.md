## 1. Border Gateway Protocol 101

#

### summary

- high level intro to BGP which is used by some AWS services such as Direct Connect and Dynamic Site to Site VPNs

### concepts

- Autonomous Systems are "black boxes". routers controlled by one entity a network in BGP
- Autonomous Systems Numbers are unique and allocated by IANA and are private. 16bit in length. some are private
- operates over TCP port 179 - it's reliable
- not automatic - peering is manually configured
- path-vector protocol. uses ASPATH
- know terms - iBGP and eBGP see slide
- ![high level BGP concepts](img/hybridBGPconcepts.png)

### architecture

- using Australia as a example. see slides and video for detailed explanation
- ![bgp arch example](img/hybridBGParch.png)

## 2. AWS Site-to-Site VPN

#

### summary

- AWS site to site VPN is a hardware solution which creates a highly scalable IPSEC VPN between an aWS VPN and external netowrk such as on-prem traditional networks
- VPNs are quick to setup vs direct connect, dont offer the same high performance, but do encrypt data in transit.
- this lesson details the concept and arch needed for exam

### concepts

### architecture

## Demos

#

### summary

## 3. Direct Connect

#

### summary

### concepts

### architecture

## 4. Direct Connect Resilience

#

### summary

### concepts

### architecture

## 5. Transit Gateway

#

### summary

### concepts

### architecture

## Demos

#

### summary

## 6. Storage Gateway

#

### summary

### concepts

### architecture

## 7. Snowball/Edge/Snowmobile

#

### summary

### concepts

### architecture

## 8. Directory Service

#

### summary

### concepts

### architecture

## 9. DataSync

#

### summary

### concepts

### architecture

## 10. FSx for Windows Servers

#

### summary

### concepts

### architecture

## 11. FSx For Lustre

#

### summary

### concepts

### architecture
