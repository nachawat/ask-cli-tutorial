# Lab 3: AWS-Hosted with ASK CLI

## [CREATE](./01-create.md) | [DEPLOY](./02-deploy.md) | [TEST](./03-test-simulate.md) | **[BONUS](./04-bonus.md)**

# 1. Add an Intent to your Interaction Model

Edit Interaction Model en-US.json

Intent: MyNameIsIntent

Slot: name

Slot Type: AMAZON.FirstName

Utterances:

{name}

my name is {name}


Edit Skill Lambda

index.js 

Handler: MyNameIsIntentHandler

#### What happened ?
You added a new intent to capture users's firstname and prompts back their name.
For this change, you made the following operations:
* Add a new intent in your en-US Interaction Model (file: models/en-US.json).
* Add a new handler in your backend code (file: lambda/index.js).
* Update the LaunchRequestHandler to update the prompt spoken to the user (file: lambda/index.js).

# 2. Update your skill's code

# 3. Deploy your Skill

### Deploy

#### Command

```
git add .
git commit -m “add Name Intent”
ask deploy
```

#### Command

```
ask deploy
```

#### What happened ?

# 4. Test your Skill

#### Command

```
ask dialog --locale en-US
```

#### What happened ?

---

# 🏆 Congratulations - You have completed the Bonus part of the AWS-Hosted with ASK CLI Lab! 🏆

## Go to [Advanced Testing](../04-lab/README.md)