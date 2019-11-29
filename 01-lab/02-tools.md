# Lab 1: ASK CLI Setup Guide

## [Amazon Developer Account](./01-amzn-developer-account.md) | **[Tools](./02-tools.md)** | [ASK CLI](./03-ask-cli.md) | [AWS Account](./04-aws-account.md)

## Install Development Tools

The ASK CLI requires an Amazon Developer Portal account. Make sure to [create an account](./01-amzn-developer-account.md) first.

In addition, the ASK CLI requires some tools to be installed on your machine beforehand:

* Node.js and `npm`
    * ASK CLI requires Node.js version 6 or higher. 
    * `npm` is used to install the ASK CLI as a package and any packages that it depends on.

* `Git`, for cloning skills from templates in Git repositories and use [Alexa-Hosted](https://developer.amazon.com/docs/hosted-skills/build-a-skill-end-to-end-using-an-alexa-hosted-skill.html) Skills.

> **Note:** Instead of using your computer as your skill development environment, you can use [AWS Cloud9](https://aws.amazon.com/cloud9/) which is a cloud-based integrated development environment (IDE). To setup an AWS Cloud9 environment refer to the [following guide](./05-cloud9.md)


#### To install or update Node.js and `npm`

To check the version of Node.js, open a command prompt and type the following:

```
node --version
1.7.15
```

To install or update your version of Node.js, refer to the [Node.js downloads page](https://nodejs.org/en/download/). We recommend that you use the [current release or active LTS version of Node.js](https://github.com/nodejs/Release#release-schedule)


#### To install or update `Git`

To check the version of `Git`, open a command prompt and type the following:

```
git --version
git version 2.18.0
```

To install or update your version of `Git`, refer to the installation guide from [Git Documentation](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

> **Note:** If you install Git for Windows from https://git-scm.com/download/win, make sure to select the Enable symbolic links option during installation.

---

## Next Step: [Install the ASK CLI](./03-ask-cli.md)