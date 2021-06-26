# CloudFormation

AWS CloudFormation gives you an easy way to model a collection of related AWS and third-party resources, provision them quickly and consistently, and manage them throughout their lifecycles, by treating infrastructure as code.

### Infrastructure as code
The process of managing and provisioning infrastructure through machine readable definition files

Benefits : 
- Easier to mainatn Infrastructure definitons in source control
- Reliable and repeatable 
- Eliminate environment drift 
- Early access to test environment 

## CloudFormation Template

A CloudFormation template(JSON or YAML) describes your desired resources and their dependencies so you can launch and configure them together as a stack. 

You can use a template to create, update, and delete an entire `stack` as a single unit, as often as you need to, instead of managing resources individually.

You can use same template to create as many stack as you need.

Below is an example of simplest template to create s3 bucket with public read access

`YAML` format

```yaml 
Resources: 
    MyBucket:
        Type: AWS::S3::Bucket
        Properties: 
          AccessControl: PublicRead
```
`JSON` format
```json
{
   "Resources": {
      "MyBucket": {
         "Type": "AWS::S3::Bucket",
         "Properties": {
            "AccessControl": "PublicRead"
         }
      }
   }
}
```

### Template anatomy

* `AWSTemplateFormatVersion`
 
  The AWSTemplateFormatVersion section (optional) identifies the capabilities of the template. The latest template format version is 2010-09-09 and is currently the only valid value.

* `Description`

* `Parameters` 
  Get dynamic value while creating stack and use it for the rest of the section. for example seclecting ec2 instance type or count or bucket name  

* `Mappings`
  
  The optional Mappings section matches a key to a corresponding set of named values

* `Conditions`
  
    The optional Conditions section contains statements that define the circumstances under which entities are created or configured

* **`Resources`** (ONLY REQUIRED PART) 
 
  The required Resources section declares the AWS resources that you want to include in the stack, such as an Amazon EC2 instance or an Amazon S3 bucket.
  ```yaml
  Resources:
  Logical ID:
    Type: Resource type
    Properties:
      Set of properties
  ```

* `Outputs` 
The optional Outputs section declares output values that you can display after creation complete for example EC2 IP Address or Website URL from S3 static site

### Intristic Functions 
AWS CloudFormation provides several built-in functions that help you manage your stacks. Use intrinsic functions in your templates to assign values to properties that are not available until runtime.
