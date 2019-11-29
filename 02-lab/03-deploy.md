# Lab 2: Alexa-Hosted with ASK CLI

## [CREATE](./01-create.md) | [EDIT](./02-edit.md) | **[DEPLOY](./03-deploy.md)** | [TEST](./04-test-simulate.md)

# 1. Deploy your skill

To deploy your skill to your Amazon Developer Account, you will use the [`deploy`](https://developer.amazon.com/docs/smapi/ask-cli-command-reference.html#deploy-command) command. This command will be responsible for the following tasks:

* Deploying all skill artefacts: manifest, models, source code.

* Uploading your local `Git` repository content to the remote version:  
   1. Merge the local `dev` branch into local `master` branch 
   2. Push your local `dev` branch to the remote `dev` branch, 
   3. Push your local `master` branch to the remote `master` branch.

> **Note:** This command must be run **inside** the skill project directory.

#### Command

```
ask deploy
```
#### Expected Output

```
Profile for the deployment: [default]
This skill project was cloned from a pre-existing skill. Deploying this project will
  - Update skill metadata (skill.json)
  - Update interaction model (models/*.json)
  - Merge dev branch into master branch
  - Push dev branch & master branch
  - Trigger deployment of your skill code
? Do you want to proceed with the above deployments? Yes

-------------------- Update Skill Project --------------------
Skill Id: amzn1.ask.skill.XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
Skill metadata deploy finished.
Model deployment finished.
[Info]: No in-skill product to be deployed.

Your skill code deployment has started. You can watch the progress from the console:
https://developer.amazon.com/alexa/console/ask/editor/amzn1.ask.skill.XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/development/en_US
```

> **Note**: The `deploy` command *only* starts the AWS Lambda function deployment: it doesn't wait for the deployment to end before returning. Please ensure your AWS Lambda function (code) is correctly deployed before testing it.

---

## Next Step: [Test your Skill](./04-test-simulate.md)