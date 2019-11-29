# Lab 2: Alexa-Hosted with ASK CLI

## [CREATE](./01-create.md) | [EDIT](./02-edit.md) | [DEPLOY](./03-deploy.md) | **[TEST](./04-test-dialog.md)**

We will perform 4 basic type of tests using ASK CLI commands:

1. [One Turn Simulation - Text Input](./04-test-simulate.md)

1. [One Turn Simulation - JSON Input](./04-test-invoke.md)

1. **[Multi-Turn Simulation](./04-test-dialog.md)** *<== CURRENT TEST*

1. [Pre-Certification Tests](./04-test-pre-certification.md) 

# Multi-Turn Simulation

To simulate a multi-turn conversation with your skill, you will open a [`dialog mode`](https://developer.amazon.com/docs/smapi/ask-cli-command-reference.html#dialog-command) from the ASK CLI.

This will allow you to test your skill behavior within a session. This is equivalent to speak to a device.

#### Command

```
ask dialog --locale en-US
```

#### Expected Output

```
  User  >  open hosted hello world
  Alexa >  Welcome, you can say Hello or Help. Which would you like to try?
  User  >  hello
  Alexa >  Hello World!
```

> **Note**: To quit the dialog mode, you simply need to enter the special command `!quit` or `Ctrl+C`.
>
> If the skill session has not ended, you will continue to see the "User >" prompt on the command line, and you can continue to input text as if conversing with Alexa.
> 
> If the skill session is ended, you will see the line '—Skill Session Ended.—' in the command-line window, but the interaction mode remains open. You will still see the "User >" prompt, and you can continue to input text

#### What happened?
Each dialog uses the [`simulate-skill`](https://developer.amazon.com/docs/smapi/ask-cli-command-reference.html#simulate-skill-subcommand) subcommand, which is an asynchronous operation that continues to poll the simulation result until it's available and then shows the Alexa text responses.

---

## Next Step: [Valide your Skill before Certification](./04-test-pre-certification.md)