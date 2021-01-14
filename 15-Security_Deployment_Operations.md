## 1. AWS Secrets Manager

#

### summary

- product that manages secrets within AWS. There is some overlap between it and the SSM parameter store - but secrets manager is specialized for secrets
- Secrets Manager is capable of automatic credential rotation using Lambda
- for supported services, it can even adjust the credentials of the service itself
- [lesson link](https://learn.cantrill.io/courses/730712/lectures/15793908)

### concepts

- often gets confused w/SSM parameter store
- when to use one vs the other. does share some functionality with Parameter Store
- Secrets Manager is designed for secrets....passwords, API Keys
- usable via console, CLI, API, or SDKs(integration)
- supports automatic rotation of secrets using Lambda
- directly integrates with some AWS products(RDS)
- ![Secrets Manager concepts](img/securitySMconcepts.png)

### architecture

- ex of a web app using SDK retrieve database creds
- Secrets Manager can periodically use Lambda function to rotate secrets
- secured using KMS
- ![Secrets Mgr arch example](img/securitySMarch.png)

## 2. AWS WAF & Shield

#

### summary

- AWS Shield and Web Application Firewall are both products which provide perimeter defense for AWS networks
- Shield provides DDOS protection and WAF is a Layer 7 Application firewall
- [what is a DDOS attack](https://www.cloudflare.com/en-au/learning/ddos/what-is-a-ddos-attack/)
- [lesson link](https://learn.cantrill.io/courses/730712/lectures/15792890)

### concepts

### architecture

## 3. CloudHSM

#

### summary

### concepts

### architecture
