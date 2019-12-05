# ask-cli-tutorial
This tutorial is designed to teach you the core fundamentals of the Alexa Skills Kit Command Line Interface (ASK CLI). The ASK CLI is a tool that lets developers manage their Alexa skills and related resources such as interaction models and account linking details from the command line. It performs skill management actions by calling the Alexa Skill Management API (SMAPI) under the hood. ASK CLI can be used to create, read, update, and test Alexa skills and connected AWS Lambda functions, as well as to submit skills for certification or withdraw them.
In this repository, you will find the necessary commands, JSON and code files for each module.

# Prerequisites

* [Amazon Developer Account](https://developer.amazon.com/)
* [AWS Account](https://portal.aws.amazon.com/billing/signup#/start)
* [AWS Profile](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html#id_users_create_console)
* [Node.js / NPM](https://nodejs.org/en/download/)
* [git](https://git-scm.com/downloads)

# Skill Architecture
Each skill consists of two basic parts, a front end and a back end. The front end is the voice interface, or VUI. 
The voice interface is configured through the voice interaction model. 
The back end is where the logic of your skill resides.

Here are a few definitions to get familiar with when building Skills:

* `Alexa Skills Kit`: A collection of APIs, tools, and documentation for giving Alexa new capabilities.
* `Invocation Name`: A name that represents the custom skill the customer wants to use.
* `Intents`: A mechanism to handle a specific request or input from an Alexa user.
* `Utterances`: Sentences or fragments that an Alexa user says to use a skill that get handled by an intent.
* `Slots`: An optional part of an utterance that can have variable values, e.g. color or date. 
* `Prompt`: A string of text that should be spoken to the customer to ask for more information. You include the prompt text in your response to a customer's request. 

# What You'll Learn

* [Alexa Skills Kit](https://developer.amazon.com/alexa-skills-kit)
* [Alexa Hosted Skills](https://developer.amazon.com/docs/hosted-skills/build-a-skill-end-to-end-using-an-alexa-hosted-skill.html)
* [Intents, Utterances, Slots](https://developer.amazon.com/docs/custom-skills/create-intents-utterances-and-slots.html)
* [Ask NodeJS SDK](https://ask-sdk-for-nodejs.readthedocs.io/en/latest/)
* [ASK CLI Documentation](https://developer.amazon.com/docs/smapi/quick-start-alexa-skills-kit-command-line-interface.html)
* [ASK CLI Beta (v2)](https://github.com/alexa-labs/ask-cli)

# Workshop

1. [Lab 1: Setup](./01-lab/README.md)
1. [Lab 2: Alexa-Hosted Skill with ASK CLI](./02-lab/README.md)
1. [Lab 3: AWS-Hosted Skill with ASK CLI](./03-lab/README.md)
1. [Lab 4: Advanced Testing with ASK CLI](./04-lab/README.md)
1. [Lab 5: ASK CLI Beta (v2)](./05-lab/README.md)

Or go directly to the [CheatSheet](./cheatsheet.md)

# Additional Resources

* Get a better understanding about Skill Building Vocabulary: [Glossary](https://developer.amazon.com/docs/alexa-design/glossary.html)
* Get your questions answered: [Amazon Developer Forums](https://forums.developer.amazon.com/spaces/165/index.html)
* Have a Feature Request in mind? Submit it here: [Alexa Skills - User Voice](https://alexa.uservoice.com/forums/906892-alexa-skills-developer-voice-and-vote)

# License

This library is licensed under the Amazon Software License