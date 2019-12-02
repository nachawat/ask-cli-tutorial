# Lab 5: AWS-Hosted with ASK-X CLI (Beta)

A new open source version of the ASK CLI include support for [AWS CloudFormation](http://aws.amazon.com/cloudformation), so you can now manage your entire skill infrastructure from a single file. This will provide you with a starter CloudFormation template that includes the most common components for building a great skill experience, including an AWS Lambda function and a S3 bucket. If you are more experienced with CloudFormation you can also provision any other AWS resource supported by CloudFormation with ease.
In this lab, you will use your own AWS account and deploy your Skill artefacts using AWS Cloudformation and [Alexa Skill Package API](https://developer.amazon.com/docs/smapi/skill-package-api-reference.html)


## Prerequisistes

To perform this lab, you need the following resources setup to develop your skill.

| Resources                   | Installation Guide  | 
| ----------------------------|---------------------|
| Amazon Developer Account    | [Account Creation](../01-lab/01-amzn-developer-account.md)|
| NPM, Node.js, Git           | [Install Tools](../01-lab/02-tools.md)                    | 
| AWS Account                 | [Account Creation](../01-lab/04-aws-account.md)           | 

## Objective

The objective of this lab is to teach you the basic operations to build your skill using the new ASK CLI to deploy your Skill artefacts using AWS Cloudformation and [Alexa Skill Package API](https://developer.amazon.com/docs/smapi/skill-package-api-reference.html)

> **Note:** do not mistake between `ask` (the current ASK CLI) and `askx` (the new ASK CLI)

#### [START THE LAB](https://github.com/alexa-labs/ask-cli)