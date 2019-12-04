# ASK CLI Cheatsheet for Alexa-Hosted

Summary of the main operations to **Create-Deploy-Test** your skill using the [ASK CLI](https://developer.amazon.com/docs/smapi/quick-start-alexa-skills-kit-command-line-interface.html).

```
############
# CREATION
############

## Alexa-Hosted skill
### Backend programming language selected: Node.JS
### Clone the skill locally on your machine
ask create-hosted-skill --runtime nodejs8.10 --skill-name MyFirstHostedSkillWithCLI --auto-clone true

## AWS-Hosted skill
### Create a local copy of a skill (no deployment)
ask new

## Inspect Skill Structure
cd <_YOUR_SKILL_ROOT_FOLDER_>
ls -a

#############################
# CLONING AN EXISTING SKILL
#############################

## Make a locale copy of the skill from your Amazon Developer Account
ask clone --skill-id <_SKILL_ID_>

##############
# DEPLOYMENT
##############

## Alexa-Hosted skill specific
### Commit changes on local Git branch
### Alexa-Hosted has a Git repository structure
git add .
git commit -m "_my_commit_comments_"

## Deploy local changes on your Amazon Developer Account
ask deploy

###########
# TESTING
###########

## Test your Skill by providing an utterance
ask simulate --locale en-US --text "hello there"

## Test your Skill by simulating a multi-turn conversation
ask dialog --locale en-US

## Run a series of automated tests on your skill
ask validate —locales en-US

###############
# NLU TESTING
###############

## Get conflicting utterances & slots detected at model build
ask api get-conflicts --skill-id <SKILL_ID> --locale en-US

## Test model behavior
ask api nlu-profile --utterance "hello there" --skill-id <SKILL_ID> --locale en-US 

## NLU Evaluation Tool: regression tests
### Create an AnnotationSet
### Returns the AnnotationSet ID
ask api create-nlu-annotation-set --skill-id <SKILL_ID> --locale en-US --annotation-set-name AnnotationDemoBatch

### Add test cases to the AnnotationSet
ask api update-nlu-annotation-set-annotations --skill-id <SKILL_ID> --annotation-id <annotation-id> --annotations-file 
annotationSetTestCases.json
 --annotations-format application/json

### Trigger a new evaluation
### Returns the Evaluation ID
### An evaluation in an async operation
ask api evaluate-nlu --skill-id <SKILL_ID> --locale en-US --annotation-id <annotation-id>

### Get Evalutation Status
ask api get-nlu-evaluation --skill-id <SKILL_ID> --evaluation-id <evaluation-id>

### Get Evaluation Results
ask api get-nlu-evaluation-results --skill-id <SKILL_ID> --evaluation-id <evaluation-id>
```