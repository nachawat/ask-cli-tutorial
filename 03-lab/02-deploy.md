# Lab 3: AWS-Hosted with ASK CLI

## [CREATE](./01-create.md) | **[DEPLOY](./02-deploy.md)** | [TEST](./03-test-simulate.md)

# 1. Deploy your skill

To deploy your skill to your Amazon Developer Account, you will use the [`deploy`](https://developer.amazon.com/docs/smapi/ask-cli-command-reference.html#deploy-command) command. This command will be responsible for deploying the following skill artefacts:

* Deployment on Amazon Developer Portal: 
  * manifest (file: `skill.json`)
  * models (folder: `models/`)

* Deployment on your AWS Account:
  * source code (folder: `lambda/custom/`) as a new AWS Lambda function. 

> **Note:** This command must be run **inside** the skill project directory.

#### Command

```
ask deploy
```

#### Expected Output

```
Profile for the deployment: [default]
-------------------- Create Skill Project --------------------
Skill Id: amzn1.ask.skill.XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
Skill metadata deploy finished.
Model deployment finished.
[Warn]: No runtime and handler settings found for alexaUsage "custom/default" when creating Lambda function. CLI will use "nodejs8.10" and "index.handler" as the Runtime and Handler to create Lambda. You can update the runtime and handler for the target Lambda in the project config and deploy again if you want to set differently.
Lambda deployment finished.
Lambda function(s) created:
  [Lambda ARN] arn:aws:lambda:us-east-1:XXXXXXXXXXXX:function:ask-custom-helloworld-default
[Info]: No in-skill product to be deployed.
Your skill is now deployed and enabled in the development stage. Try simulate your Alexa skill skill using "ask dialog" command.
```

> **Note**: Once deployed, the skill ID is available from the hidden file `.ask/config` :

```json
{
  "deploy_settings": {
    "default": {
      "skill_id": "amzn1.ask.skill.XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
      ...
    }
  },
  ...
} 
```

---

## Next Step: [Test your Skill](./03-test-simulate.md)