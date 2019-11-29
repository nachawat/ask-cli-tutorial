# Lab 1: ASK CLI Setup Guide

## [Amazon Developer Account](./01-amzn-developer-account.md) | [Tools](./02-tools.md) | **[ASK CLI](./03-ask-cli.md)** | [AWS Account](./04-aws-account.md)

## Alexa Skill Kit Command Line Interface (ASK CLI)

The Alexa Skills Kit Command Line Interface (ASK CLI) is a tool that lets developers manage their Alexa skills and related resources such as interaction models and account linking details from the command line. It performs skill management actions by calling the Alexa Skill Management API (SMAPI) under the hood. ASK CLI can be used to create, read, update, and test Alexa skills and connected AWS Lambda functions, as well as to submit skills for certification or withdraw them.

The ASK CLI requires an Amazon Developer Portal account. Make sure to [create an account](./01-amzn-developer-account.md) first.

**Do you have the ASK CLI Installed?**

To check whether you have the ASK CLI installed, open a terminal (command prompt on Windows) and type the following command:

```
ask --version
```

If the CLI is installed correctly then you should see an output like this:


```
ask --version
1.7.15
```

If the CLI is not installed, then you will get an error back stating that `ask` is not a recognized command. 

---

## Next Step: [Install the ASK CLI](./03-ask-cli-install.md) | Skip to [Initialize the ASK CLI](./03-ask-cli-init.md)
