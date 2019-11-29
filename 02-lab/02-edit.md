# Lab 2: Alexa-Hosted with ASK CLI

## [CREATE](./01-create.md) | **[EDIT](./02-edit.md)** | [DEPLOY](./03-deploy.md) | [TEST](./04-test-simulate.md)

# 1. Edit your invocation name

When creating an Alexa-Hosted Skill, the [Invocation Name](https://developer.amazon.com/docs/custom-skills/choose-the-invocation-name-for-a-custom-skill.html) shall be updated to reflect your final invocation name.

To perform this operation, you will edit the file `models/en-US.json` and look for `invocatioName` property to provide your own:

```json
*************************
file: models/en-US.json
*************************
CHANGE (line 4)
"invocationName": "change me",

TO (line 4)
"invocationName": "hosted hello world",
```

#### What happened?

You updated the invocation name of your `en-US` Interaction Model locally on your computer.

# 2. Commit your changes

### Git Repository Structure

When cloning an Alexa-hosted skill, the `ASK CLI` creates a skill project folder based on a `Git` repository configured with the following branches:
* The `dev` branch, which corresponds to the current saved state shown in the developer console.
* The `master` branch, which corresponds to what is deployed to the development-stage AWS Lambda endpoint.
* The `prod` branch, which corresponds to what is deployed to the live AWS Lambda endpoint, if your skill is already live.

You can review the branches of your repository with the following command:

#### Command

```
git branch
```

#### Expected Output

```
* dev
  master
  prod
```

### Record changes to the repository

To deploy any changes made locally, you must first commit your changes into the `dev` branch:

#### Command
```
git add .
git commit -m “update invocation name”
```

#### Expected Output
```
[dev fe67dbf] update invocation name
 4 files changed, 61 insertions(+)
 create mode 100644 .DS_Store
 create mode 100644 .gitignore
 create mode 100644 models/en-US.json
 create mode 100644 skill.json
```

#### What happened?
You committed your local changes into your `Git` repository.

> **Note**: If you want to directly access your `Git` repository (AWS CodeCommit repository), the credentials are available in the hidden file `.ask/config` :
```json
  "alexaHosted": {
    "isAlexaHostedSkill": true,
    "profile": "default",
    "gitCredentialsCache": {
      "protocol": "https",
      "host": "git-codecommit.us-east-1.amazonaws.com",
      "path": "v1/repos/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
      "username": "ABCD1234...",
      "password": "9876ZYX...",
      "expiresAt": 0
    }
  }
```

---

## Next Step: [Deploy your Skill](./03-deploy.md)