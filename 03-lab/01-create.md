# Lab 3: AWS-Hosted with ASK CLI

## **[CREATE](./01-create.md)** | [DEPLOY](./02-deploy.md) | [TEST](./03-test-simulate.md)

# 1. Create a Skill 

To create a skill, you will use the [`new`](https://developer.amazon.com/docs/smapi/ask-cli-command-reference.html#new-command) command. 

It will create a new skill project locally your machine from a pre-existing template you will select.

#### Command

```
ask new
```

1. You will select the runtime used for your code logic deployed on AWS Lambda. **Select** `Node.js V8` and type **Enter**:

```
? Please select the runtime (Use arrow keys)
❯ Node.js V8 
  Python3 
```

2. After selecting the runtime (`Node.js V8`), you will be prompt to select a pre-defined templates. **Select** `Hello World` and type **Enter**:

```
? List of templates you can choose (Use arrow keys)
❯ Hello World 
  Buttons ColorChanger 
  City Guide 
  Decision Tree 
  Fact 
  Feed 
  Foodie 
(Move up and down to reveal more choices)
```

3. After selecting the project template (`Hello World`), you will be prompt to enter a skill name. That will correspond to the folder's name created on your computer. Leave the entry **empty** and type **Enter**:

```
? Please type in your skill name:  (skill-sample-nodejs-hello-world) 
```

At that point, a new folder has been created on your computer using a `Hello World` template.

#### Expected Final Output

```
? Please select the runtime Node.js V8
? List of templates you can choose Hello World
? Please type in your skill name:  skill-sample-nodejs-hello-world
Skill "skill-sample-nodejs-hello-world" has been created based on the chosen template
```

#### What happened?
* A new Skill has been created **locally** on your machine with the following artefacts:
    - an Interaction Model (locale: `en-US`).
    - an backend code template (language: `Node.js`)

# 2. Inspect the skill structure

All the Skill artefacts has been created on your computer into a skill project folder named after the Skill Name (folder: `skill-sample-nodejs-hello-world`). We will know review the folder content to understand the skill structure:

#### Command

```
cd skill-sample-nodejs-hello-world
ls -a
```

#### Expected Output

```
skill-sample-nodejs-hello-world
|-- .ask
|   |-- config
|-- hooks
|   |-- post_new_hook.ps1
|   |-- post_new_hook.sh
|   |-- pre_deploy_hook.ps1
|   |-- pre_deploy_hook.sh
|-- lambda
|   |-- custom
|   |--   |-- index.js
|   |--   |-- languageStrings.js
|   |--   |-- package.json
|   |--   |-- util.js
|-- models
|   |-- de-DE.json
|   |-- en-AU.json
|   |-- en-CA.json
|   |-- en-GB.json
|   |-- en-IN.json
|   |-- en-US.json
|   |-- ...
|-- skill.json
```

#### What happened?
You reviewed the different parts of the Skill project:

* `.ask` – A hidden folder that contains the ASK CLI's config file.

* `hooks` – A folder that contains the hook scripts. Amazon provides two possible hooks: post_new_hook (run automatically at the end of the `ask new` command) and pre_deploy_hook (run automatically at the end of the `ask deploy` command).

* `lambda` – A folder that contains the source code for the skill's AWS Lambda function. The files contained here depend on the runtime for the skill.

* `models` – A folder that contains one or more interaction models for the skill. Each interaction model is defined in a JSON file named according to the locale (e.g en-US.json).

* `skill.json` – A file that contains the skill manifest.

---

## Next Step: [Deploy your Skill](./02-deploy.md)