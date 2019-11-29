# Lab 2: Alexa-Hosted with ASK CLI

With [Alexa-Hosted](https://developer.amazon.com/docs/hosted-skills/build-a-skill-end-to-end-using-an-alexa-hosted-skill.html), Alexa automatically provisions and manages a set of AWS cloud services for your skill’s back-end without the need of an AWS Account.
You will gain access to an [AWS Lambda](https://aws.amazon.com/lambda/) function and associated [Amazon Cloudwatch Logs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html), an [Amazon S3](https://aws.amazon.com/s3/) bucket for media storage, and an Amazon S3-backed key-value table for managing session persistence.
When you create the skill, the service also sets up an [AWS CodeCommit](https://aws.amazon.com/codecommit/) repository for managing your code, which you can access using the [Alexa Skills Kit Command Line Interface](https://github.com/alexa/alexa-skills-kit-sdk-for-nodejs) (ASK CLI) to edit your skill.

## Prerequisistes

To perform this lab, you need the following resources setup to develop your skill. Installation Guides are available in [Lab 1](../01-lab/README.md).

| Resources                   | Installation Guide  | 
| ----------------------------|---------------------|
| Amazon Developer Account    | [Account Creation](../01-lab/01-amzn-developer-account.md)|
| NPM, Node.js, Git           | [Install Tools](../01-lab/02-ask-cli.md)                  | 
| ASK CLI                     | [Install the CLI](../01-lab/02-ask-cli.md)                | 

## Objective

The objective of this lab is to teach you the basic operations to build your skill using the ASK CLI in the context of a Hosted-Skill. We will cover the following topics:

1. [Create the skill](./01-create.md)
1. [Edit the skill](./02-edit.md)
1. [Deploy the skill](./03-deploy.md)
1. [Test the Skill](./04-test-simulate.md)

#### [START THE LAB](./01-create.md)