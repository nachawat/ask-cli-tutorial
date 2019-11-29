# Lab 3: AWS-Hosted with ASK CLI

You can build a custom skill for Alexa by implementing a *web service* that accepts requests from and sends responses to the Alexa service in the cloud. You can build your web service using any programming language, as long as the service meets the following requirements. The easiest way to build the cloud-based service for a custom Alexa skill is to use [AWS Lambda](https://aws.amazon.com/lambda/), an Amazon Web Services offering that runs your code only when it's needed and scales automatically, so there is no need to provision or continuously run servers. You upload the code for your Alexa skill to a Lambda function and Lambda does the rest, executing it in response to Alexa voice interactions and automatically managing the compute resources for you. In this lab, you will use your own AWS account to host your skill programming logic (code) using AWS Lambda.

## Prerequisistes

To perform this lab, you need the following resources setup to develop your skill.

| Resources                   | Installation Guide  | 
| ----------------------------|---------------------|
| Amazon Developer Account    | [Account Creation](../01-lab/01-amzn-developer-account.md)|
| NPM, Node.js, Git           | [Install Tools](../01-lab/02-tools.md)                    | 
| ASK CLI                     | [Install the CLI](../01-lab/03-ask-cli.md)                | 
| AWS Account                 | [Account Creation](../01-lab/04-aws-account.md)           | 

## Objective

The objective of this lab is to teach you the basic operations to build your skill using the ASK CLI and resources from your AWS account. We will cover the following topics:

1. [Create the skill](./01-create.md)
1. [Deploy the skill](./02-deploy.md)
1. [Test the Skill](./03-test-simulate.md)

#### [START THE LAB](./01-create.md)