# Lab 3: AWS-Hosted with ASK CLI

## [CREATE](./01-create.md) | [DEPLOY](./02-deploy.md) | [TEST](./03-test-simulate.md) | **[BONUS](./04-bonus.md)**

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

To perform this operation, you will edit the file `lambda/custom/index.js` and add the following intent handler:

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

Once the handler is created, we must attach it to the request handler chain from our `SkillBuilders` instance. To perform this operation, you will edit the file `lambda/custom/index.js` and locate method: `.addRequestHandlers()` for the `Alexa.SkillBuilders.custom()` object in order to add the newly created handler

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

To perform this operation, you will edit the file `lambda/custom/languageStrings.js` and a new object dedicated to the en-US locale containing the updated welcom prompt:

```javascript
module.exports = {
    "en-US": {
        translation: {
            WELCOME_MSG: 'Welcome, what is your name?'
        }
    },
...
```

# 3. Skill Modification: What happened ?

You added a new intent to capture users's firstname and prompts back their name. For this change, you made the following operations:

* Add a new intent in your en-US Interaction Model (file: `models/en-US.json`).

* Add a new handler in your backend code (file: `lambda/custom/index.js`).

* Attach the new handler into the request handler chain (file: `lambda/custom/index.js`).

* Update the welcome prompt only for locale `en-US` by adding dedicated `en-US` key/value into localization file (file: `lambda/custom/languageStrings.js`).

# 4. Deploy your Skill

To deploy our local changes, we make an ASK CLI deployment:

```
ask deploy
```

> **Note**: The `deploy` command *only* starts the AWS Lambda function deployment: it doesn't wait for the deployment to end before returning. Please ensure your AWS Lambda function (code) is correctly deployed before testing it.

# 4. Test your Skill

Once, your deployment is done, you can test the new version of your skill by using the dialog mode from the ASK CLI

```
ask dialog --locale en-US
  User  >  open hello world
  Alexa >  Welcome, what is your first name?
  User  >  Benoit
  Alexa >  Hello Benoit, it is my pleasure to meet you for ALX 314!
```

---

# 🏆 Congratulations - You have completed the Bonus part of the AWS-Hosted with ASK CLI Lab! 🏆

## Go to [Advanced Testing](../04-lab/README.md)