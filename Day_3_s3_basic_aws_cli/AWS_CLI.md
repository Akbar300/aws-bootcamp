# AWS Command Line Interface (CLI)

The [AWS Command Line Interface (AWS CLI)](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html) is an open source tool that enables you to interact with AWS services using commands in your command-line shell.

## Installing AWS CLI
* MacOS [download link here](https://awscli.amazonaws.com/AWSCLIV2.pkg) 
* Windows [download link here](https://awscli.amazonaws.com/AWSCLIV2.msi)

Double click to start installing and follow all default options to complete installation. 

Verify installation by opening terminal or command line and run below command and you will get successful result to verify the version. 
```bash
aws --version
```

## Getting Access key and Secret key for AWS CLI
You will need to generate access key and secret key for programatic access to your aws account as we mentioned in IAM session. 

>The only time that you can view or download the secret access key is when you create the keys. You cannot recover them later. However, you can create new access keys at any time. You must also have permissions to perform the required IAM actions. For more information, see Permissions required to access IAM resources in the IAM User Guide.

To create access keys for an IAM user

* Sign in to the AWS Management Console and open the IAM console at https://console.aws.amazon.com/iam/.

* In the navigation pane, choose Users.

* Choose the name of the user whose access keys you want to create, and then choose the Security credentials tab.

* In the Access keys section, choose Create access key.

* To view the new access key pair, choose Show. You will not have access to the secret access key again after this dialog box closes. Your credentials will look something like this:
```
Access key ID: AKIAIOSFODNN7EXAMPLE
Secret access key: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
```
* To download the key pair, choose Download .csv file. Store the keys in a secure location. You will not have access to the secret access key again after this dialog box closes.

* After you download the .csv file, choose Close. When you create an access key, the key pair is active by default, and you can use the pair right away.

## Configuring AWS CLI 
get your credentials ready and type below command in the command line and hit enter

```bash
aws configure
```
You will be asked to enter for value as below , copy paste your access key and secret key as asked, for region name enter `us-east-1` , for format type `json` and you are all set

```bash
AWS Access Key ID [None]: AKIAIOSFODNN7_EXAMPLE
AWS Secret Access Key [None]: wJalrEXAMPLE_SECRET
Default region name [None]: us-east-1
Default output format [None]: json
```

## Using AWS CLI 
Command structure 
```
aws [options] <command> <subcommand> [parameters]
```
You can type the commands as remembered or you can get the help using auto prompt feature by running below command 
```
aws --cli-auto-prompt
```



## Sample bucket policy 

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::Bucket-Name/*"
            ]
        }
    ]
}
```
