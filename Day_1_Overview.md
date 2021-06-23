# Day 1: 

## INTRO TO AWS  
- Intro to Cloud 
- Traditional Data Centers 
- Benifits of Cloud Computing 
- Types of Cloud Computing 
--- 
### AWS Global Infrasturature
- Regions 
- Availibility Zones
- Edge Locations 



## IAM SERVICE

### AWS Account
  - Sign up for AWS Account
  - Setting up Billing Alert 
  - Billing Dashboard , Cost Explorer 
    - Optionally Set up Multi Factor Authentication (MFA)
    - Optionally Delete root access key  
  - Root User
  - IAM User
  - IAM Group
  - IAM Policy
  - IAM Role
  
> IAM LAB 
- Create 2 group called `dev` , `sysops` 
- provide `dev` group 
  - EC2FullAccess
  - S3FullAccess
  - AmazonDynamoDBFullAccess

- provide `sysops` group 
  - AmazonRDSFullAccess
  - CloudWatchActionsEC2Access

Add few users to these 2 groups and login and try to access services they can access and can not access 

















## AWS learning resources 
**Free** : 
- [AWS provided video tutorials](https://www.aws.training/LearningLibrary)
- [AWS Documentation](https://docs.aws.amazon.com/)

**Paid** : 
- [Acloud guru](https://acloudguru.com)
  - Video tutorials and labs 
  - featuring cloud playground with provided aws user for practice

**AWS Exams** 
* [Exam page :](https://aws.amazon.com/certification/) 
- Exam Practice tests (paid)
  - [Tutorial Dojo](https://tutorialsdojo.com/)
  - [Whizlab]()
