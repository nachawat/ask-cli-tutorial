# Lab 2: Alexa-Hosted with ASK CLI

## [CREATE](./01-create.md) | [EDIT](./02-edit.md) | [DEPLOY](./03-deploy.md) | [TEST](./04-test-simulate.md) | **[BONUS](./05-bonus.md)**

In this section, we will focus on updating our skill on both the **interaction model** side as well as on the **backend code** side and look after the different steps to be performed. The objective will be to add to the skill the ability to collect the customer first name once we've prompted them and greet each customer with their first name afterwards.

# 1. Add an Intent to your Interaction Model

The Alexa Skills Kit is providing predefined slot types where a catalog of values have already been provided and trained by Alexa for you. To have the ability to collect customers first name, we will use the predefined `AMAZON.FirstName` slot type and create a new intent to collect such a value. We will provide to this intent a list of samples utterances to understand what the user will say. Within those utterances, to capture the customers' first name, we will define a new slot mapped to the `AMAZON.FirstName` type.

To perform this operation, you will edit the file `models/en-US.json` and add an intent named `MyNameIsIntent` the following way:

```json
{
    "interactionModel": {
        "languageModel": {
            "invocationName": "hello world",
            "intents": [
                {
                    "name": "MyNameIsIntent", 
                    "slots": [
                        {
                            "name": "first_name",
                            "type": "AMAZON.FirstName" 
                        }
                    ],
                    "samples": [
                        "{first_name}",
                        "my name is {first_name}", 
                        "you can call me {first_name}"
                    ]
                },
                ...
            ]
        }
    }
}
```

# 2. Update your skill's code


#### Create Intent Handler

To handle JSON Requests sent to our skill backend for newly createed intent `MyNameIsIntent`, we will add a new Handler in our Lambda code and reference it into the Request Handlers chain.

To perform this operation, you will edit the file `lambda/index.js` and add the following intent handler:

```javascript
const MyNameIsIntentHandler = { 
    canHandle(handlerInput) {
        return Alexa.getRequestType(handlerInput.requestEnvelope) === 'IntentRequest'
            && Alexa.getIntentName(handlerInput.requestEnvelope) === 'MyNameIsIntent';
    }, 
    handle(handlerInput) {
        const firstname = Alexa.getSlotValue(handlerInput.requestEnvelope, "first_name"); 
        const speechText = `Hello ${firstname}, it is my pleasure to meet you for ALX 314!`;
        return handlerInput.responseBuilder
            .speak(speechText)
            .getResponse();
    } 
};
```

#### Attach Intent Handler

Once the handler is created, we must attach it to the request handler chain from our `SkillBuilders` instance. To perform this operation, you will edit the file `lambda/index.js` and locate method: `.addRequestHandlers()` for the `Alexa.SkillBuilders.custom()` object in order to add the newly created handler

```
Alexa.SkillBuilders.custom()
    .addRequestHandlers(
        LaunchRequestHandler,
        MyNameIsIntentHandler,
        ...
    )
```

#### Update Welcome prompt

To let the users provide us their name, while invoking the skill, in the welcome prompt message, we will ask them for their first name.

To perform this operation, you will edit the file `lambda/index.js` and locate method `LaunchRequest.handle(handlerInput)` to update the output speech prompt:

```javascript
file: lambda/index.js
method: LaunchRequest.handle(handlerInput)

BEFORE:

const speakOutput = 'Welcome, you can say Hello or Help. Which would you like to try?';

AFTER:

const speakOutput = 'Welcome, what is your first name?';
```

# 3. Skill Modification: What happened ?

You added a new intent to capture users's firstname and prompts back their name.
For this change, you made the following operations:

* Add a new intent in your en-US Interaction Model (file: `models/en-US.json`).

* Add a new handler in your backend code (file: `lambda/index.js`).

* Attach the new handler into the request handler chain (file: `lambda/index.js`).

* Update the LaunchRequestHandler to change the prompt provided to the user (file: `lambda/index.js`).

# 4. Deploy your Skill

To deploy our local changes, we will first commit our changes to the local repository then make a deployment using the ASK CLI:

```
git add .
git commit -m “add Name Intent”
ask deploy
```

> **Note**: The `deploy` command *only* starts the AWS Lambda function deployment: it doesn't wait for the deployment to end before returning. Please ensure your AWS Lambda function (code) is correctly deployed before testing it.

# 4. Test your Skill

Once, your deployment is done, you can test the new version of your skill by using the dialog mode from the ASK CLI

```
ask dialog --locale en-US
  User  >  open hosted hello world
  Alexa >  Welcome, what is your first name?
  User  >  Benoit
  Alexa >  Hello Benoit, it is my pleasure to meet you for ALX 314!
```

---

# 🏆 Congratulations - You have completed the Bonus part of the Alexa-Hosted with ASK CLI Lab! 🏆

## Go to [Advanced Testing](../04-lab/README.md)