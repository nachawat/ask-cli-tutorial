# Lab 1: ASK CLI Setup Guide

## [Amazon Developer Account](./01-amzn-developer-account.md) | [Tools](./02-tools.md) | **[ASK CLI](./03-ask-cli.md)** | [AWS Account](./04-aws-account.md)

## ASK CLI Setup - Installation

If you are here it means that you have:

✓ **An Amazon Developer Account** (if not, follow the guide to [Create a new Amazon Developer Account](./01-amzn-developer-account.md))

✓ **The Development Tools installed** (if not, follow the guide to [Setup Development Tools](./02-tools.md))

Use `npm` to install ASK CLI. If you already have ASK CLI installed and want to update to the latest version, the same command can be used.

```
npm install -g ask-cli
```

If you are using Linux, the installation may require `sudo`:

```
sudo npm install -g ask-cli
```

> **Note:** Before you install ASK CLI on Windows, you must install the Node.js [windows-build-tools](https://www.npmjs.com/package/windows-build-tools) package. Before you install windows-build-tools, make sure you have [the version of Node.js that the package requires](https://www.npmjs.com/package/windows-build-tools#node-versions). To install windows-build-tools, first open PowerShell with the Run as Administrator option, then type npm install -g --production windows-build-tools.

Finally, verify that the installation was successful:

```
ask --version
1.7.15
```

---

## Next Step: [Initialize the ASK CLI](./03-ask-cli-init.md)