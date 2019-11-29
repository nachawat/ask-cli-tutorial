# Lab 1: ASK CLI Setup Guide

## [Amazon Developer Account](./01-amzn-developer-account.md) | [Tools](./02-tools.md) | [ASK CLI](./03-ask-cli.md) | [AWS Account](./04-aws-account.md) | **[AWS Cloud 9](./05-cloud9.md)**

## AWS Cloud 9 Setup

Instead of using your own machine as a development environment to build Alexa Skills, you can use [AWS Cloud9](https://aws.amazon.com/cloud9/) which is a cloud-based integrated development environment (IDE) that lets you write, run, and debug your code with just a browser. It includes a code editor, debugger, and terminal. Cloud9 comes prepackaged with essential tools for popular programming languages, including JavaScript, Python, PHP, and more, so you don’t need to install files or configure your development machine to start new projects. Since your Cloud9 IDE is cloud-based, you can work on your projects from your office, home, or anywhere using an internet-connected machine. 

This guide will walk you through the process to quickly and easily setup an Alexa Skill Development environment with the ASK CLI using AWS Cloud9.

If you are here it means that you have:

✓ **An Amazon Developer Account** (if not, follow the guide to [Create a new Amazon Developer Account](./01-amzn-developer-account.md))

✓ **An AWS Account** (if not, follow the guide to [Create a new AWS Account](./04-aws-account.md))

---

#### Step 1 - Cloud9 environment creation

1. **Sign in** to your AWS Account. https://console.aws.amazon.com

1. Navigate to Cloud9 (browse for Cloud9 under Developer Tools, or type Cloud9 in the search box).

1. Click **Create an environment**.

1. Enter a name and optional description. Click **Next step**.

1. Accept the defaults and click **Next step**.

1. Review and click **Create Environment**.

1. Wait a few minutes while the environment is being created.

---

#### Step 2 - ASK CLI installation

1. Once the environment is ready, you will see the Cloud9 IDE. In the lower pane a default terminal session has been started for you. In this window, enter the following command to install the AKS CLI: 

```
npm install ask-cli -g
```

---

#### Step 3 - ASK CLI initialization

1. Configure the ASK CLI by entering the command `ask init --no-browser`. This will guide you through the setup process where you'll specify the AWS credentials to be used as well as the Developer Account to be used. The no-browser flag indicates that a URL should be displayed instead of automatically opening the URL in the default browser.

```
ask init --no-browser
This command will initialize the ASK CLI with a profile associated with your Amazon developer credentials.
------------------------- Step 1 of 2 : ASK CLI Initialization -------------------------
Paste the following url to your browser:
    https://www.amazon.com/ap/oa?redirect_uri=https%3A%2F%2Fs3.amazonaws.com%2Fask-cli%2Fresponse_parser.html&scope=alexa%3A%3Aask%3Askills%3Areadwrite%20alexa%3A%3Aask%3Amodels%3Areadwrite%20alexa%3A%3Aask%3Askills%3Atest%20alexa%3A%3Aask%3Acatalogs%3Aread%20alexa%3A%3Aask%3Acatalogs%3Areadwrite&state=Ask-SkillModel-ReadWrite&response_type=code&client_id=amzn1.application-oa2-client.aad322b5faab44b980c8f87f94fbac56
? Please enter the Authorization Code:  
```

2. Click the link which is generated. Click **Open** in the pop-up menu. This will open a new tab in your browser. **Sign in** to your Amazon Developer account.

3. Once you grant permissions, a code will appear in the browser. Copy this code.

4. Switch back to the Cloud9 terminal. Paste the code at the prompt.

5. If you have more than one Vendor ID associated with your login, select the one you want to use.
    > **Note**: If your VendorID cannot be retrieved (error message is 'call list-vendors error' / 401 / 'You are not authorized to access this operation'), it typically means you haven't fully created your Developer Account. Return to https://developer.amazon.com/alexa-skills-kit and finish providing the requested data.

```
ASK Profile "default" was successfully created. The details are recorded in ask-cli config ($HOME/.ask/cli_config).
? Your Amazon developer account has multiple Vendor IDs. Please choose the Vendor ID for the skills you want to manage. YourProfile: XXXXXXXXXXXXXX
Vendor ID set as XXXXXXXXXXXXXX.
```

6. Press **ENTER** to use the default profile. This will use the temporary AWS credentials managed by Cloud9. Click [here](https://docs.aws.amazon.com/cloud9/latest/user-guide/auth-and-access-control.html#auth-and-access-control-temporary-managed-credentials) to learn more about Temporary Credentials.

```
------------------------- Step 2 of 2 : Associate an AWS Profile with ASK CLI -------------------------
? If you want to host your skill's backend code in AWS Lambda (recommended), you must associate an AWS profile with the ASK CLI. Do you want to associ
ate an AWS profile? Yes
? Please choose from the following existing AWS profiles or create a new one. default
AWS profile "default" was successfully associated with your ASK profile "default".

------------------------- Initialization Complete -------------------------
Here is the summary for the profile setup: 
  ASK Profile: default
  AWS Profile: default
  Vendor ID: XXXXXXXXXXXXXX
```

7. Now that the ASK CLI is installed and configured, you need to update `.bashrc` file to allow the ASK CLI to create IAM roles compatible with Cloud9 Temporary Credential restrictions. 

 ```
 echo 'export ASK_DEPLOY_ROLE_PREFIX=Cloud9-' >> ~/.bashrc
 ```

 > **Note:** By appending it to the `.bashrc` file, it will be automatically set each time you use Cloud9.

8. To ensure the newly entered command-line parameter is correctly taken into account from `.bashrc` file, you will issue the following command:

```
source ~/.bashrc
```
---

### 🏆 Congratulations - You have completed the ASK CLI setup using AWS Cloud 9! 🏆

Now that you've created your Cloud9 development environment, you can use it for developing your skills. You can reconnect to it whenever you want to continue working on it, and it'll be in the same state as you left it. To make reconnecting easier, simply bookmark the URL.