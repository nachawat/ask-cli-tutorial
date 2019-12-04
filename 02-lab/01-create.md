# Lab 2: Alexa-Hosted with ASK CLI

## **[CREATE](./01-create.md)** | [EDIT](./02-edit.md) | [DEPLOY](./03-deploy.md) | [TEST](./04-test-simulate.md)

# 1. Create a Hosted Skill 

To create an Alexa-Hosted skill, you will use the [`create-hosted-skill`](https://developer.amazon.com/docs/smapi/ask-cli-command-reference.html#create-hosted-skill-command) command. 

By default, this command doesn't clone the skill to your computer.

To ensure, we get a locale copy, we will use the `--auto-clone true` option:

#### Command

```
ask create-hosted-skill --runtime nodejs8.10 --skill-name MyFirstHostedSkillWithCLI --auto-clone true
```

#### Expected Output

```
-------------------- Create Alexa Hosted Skill Project --------------------
Hosted skill provisioning finished.
-------------------- Clone Alexa Hosted Skill Project --------------------
Project directory for MyFirstHostedSkillWithCLI created at
    ./MyFirstHostedSkillWithCLI

Skill schema for MyFirstHostedSkillWithCLI created at
    ./MyFirstHostedSkillWithCLI/skill.json

Skill model for en-US created at
    ./MyFirstHostedSkillWithCLI/models/en-US.json

No in-skill product associated with current skill.

[Info]: Could not find hooks folder, creating a new hooks folder and downloading scripts.
[Warn]: Skill manifest (skill.json) has been updated. Please check and commit the changes.
[Warn]: Interaction model has been updated. Please check and commit the changes.
[Info]: MyFirstHostedSkillWithCLI successfuly cloned.
```

#### What happened?
* A new skill has been created on your Amazon Developer account with the following artefacts:
    - an Interaction Model (locale: `en-US`).
    - an backend code template (language: `Node.js`)
* The interaction Model has been saved and deployed.
* The backend code has been saved in the AWS Lambda endpoint but not deployed.
* A copy has been cloned on your computer.

> **Note**: If this is your first Alexa-hosted skill, ASK CLI opens a web browser so that you can sign in to your Amazon developer account and perform a CAPTCHA test. If you can't open a web browser on the local computer, you can use the `--no-browser` option to complete this step.

# 2. Inspect the skill structure

All the skill artefacts has been cloned on your computer into a Skill project folder named after the Skill Name (folder: `MyFirstHostedSkillWithCLI`). We will know review the folder content to understand the skill Structure for a Hosted-Skill:

#### Command

```
cd MyFirstHostedSkillWithCLI
ls -a
```

#### Expected Output

```
MyFirstHostedSkillWithCLI
|-- .ask
|   |-- config
|-- .git
|   |-- ...
|-- .gitignore
|-- hooks
|   |-- pre_deploy_hook.sh
|-- lambda
|   |-- index.js
|   |-- package.json
|   |-- util.js
|-- models
|   |-- en-US.json
|-- skill.json
```

#### What happened?
You reviewed the different parts of the skill project:

* `.ask` – A hidden folder that contains the ASK CLI's config file.

* `.git` – A hidden folder that contains all the information that is necessary for your project in version control and all the information about commits, remote repository address, ...

* `.gitignore` – A hidden file that specifies intentionally untracked files to ignore.

* `hooks` – A folder that contains the hook scripts. Amazon provides two possible hooks: post_new_hook (run automatically at the end of the `ask new` command) and pre_deploy_hook (run automatically at the end of the `ask deploy` command).

* `lambda` – A folder that contains the source code for the skill's AWS Lambda function. The files contained here depend on the runtime for the skill.

* `models` – A folder that contains one or more interaction models for the skill. Each interaction model is defined in a JSON file named according to the locale (e.g en-US.json).

* `skill.json` – A file that contains the skill manifest.

> **Note**: The skill ID is available from the hidden file `.ask/config` :

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

## Next Step: [Edit your Skill](./02-edit.md)