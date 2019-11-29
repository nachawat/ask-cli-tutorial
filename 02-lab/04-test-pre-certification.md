# Lab 2: Alexa-Hosted with ASK CLI

## [CREATE](./01-create.md) | [EDIT](./02-edit.md) | [DEPLOY](./03-deploy.md) | **[TEST](./04-test-pre-certification.md)**

We will perform 4 basic type of tests using ASK CLI commands:

1. [One Turn Simulation - Text Input](./04-test-simulate.md)

1. [One Turn Simulation - JSON Input](./04-test-invoke.md)

1. [Multi-Turn Simulation](./04-test-dialog.md)

1. **[Pre-Certification Tests](./04-test-pre-certification.md)** *<== CURRENT TEST*

# Pre-Certification Tests

Before submitted your skill for certification, you shall execute a series of tests to validate your skill behavior. Those tests provide immediate feedback for common certification failures. To be able to submit to certification, all tests ran by the [`validate`](https://developer.amazon.com/docs/smapi/ask-cli-command-reference.html#validate-command) command **must** pass. It is also a good pratice to run those tests at any time during development as regression testing.

#### Command

```
ask validate —locales en-US
```

#### Expected Output

```json
✓ Validation created for validation id: b32086ce-aedb-4ad7-85ae-1ac6a0476a90
  Waiting for validation response {
  "id": "b32086ce-aedb-4ad7-85ae-1ac6a0476a90",
  "status": "FAILED",
  "result": {
    "validations": [
      {
        "locale": "en-US",
        "title": "An Example Phrase is missing for the en-US locale. In the Distribution tab, go to Skill Preview for en-US to add example phrases.",
        "status": "FAILED",
        "importance": "REQUIRED"
      },
      {
        "locale": "en-US",
        "title": "A Detailed Description of the skill is missing for the en-US locale. In the Distribution tab, go to Skill Preview for en-US to add a detailed description.",
        "status": "FAILED",
        "importance": "REQUIRED"
      },
      {
        "title": "A selection is missing for the question ‘Does this skill allow users to make purchases or spend real money?’. In the Distribution tab, go to the Privacy & Compliance section to provide an answer.",
        "status": "FAILED",
        "importance": "REQUIRED"
      },
      {
        "title": "There are no countries or regions selected for your skill’s availability. In the Distribution tab, go to the Availability section and select where your skill should be distributed.",
        "status": "FAILED",
        "importance": "REQUIRED"
      },
      {
        "title": "Confirmation for ‘Export compliance’ is missing. In the Distribution tab, please go to the Privacy & Compliance section to resolve the issue.",
        "status": "FAILED",
        "importance": "REQUIRED"
      },
      {
        "title": "A selection is missing for the question ‘Does this skill contain advertising?’. In the Distribution tab, go to the Privacy & Compliance section to provide an answer.",
        "status": "FAILED",
        "importance": "REQUIRED"
      },
      {
        "locale": "en-US",
        "title": "A Large Skill Icon is missing for the en-US locale. In the Distribution tab, go to Skill Preview for en-US to add a large skill icon.",
        "status": "FAILED",
        "importance": "REQUIRED"
      },
      {
        "title": "Testing Instructions are missing. In the Distribution tab, go to the Privacy & Compliance section to enter testing instructions.",
        "status": "FAILED",
        "importance": "REQUIRED"
      },
      {
        "title": "The Category is missing for this skill. In the Distribution tab, go to Skill Preview to add a skill category.",
        "status": "FAILED",
        "importance": "REQUIRED"
      },
      {
        "locale": "en-US",
        "title": "A Small Skill Icon is missing for the en-US locale. In the Distribution tab, go to Skill Preview for en-US to add a small skill icon.",
        "status": "FAILED",
        "importance": "REQUIRED"
      },
      {
        "title": "A selection is missing for the question ‘Is this skill directed to or does it target children under the age of 13?’. In the Distribution tab, go to the Privacy & Compliance section to provide an answer.",
        "status": "FAILED",
        "importance": "REQUIRED"
      },
      {
        "locale": "en-US",
        "title": "A One Sentence Description of the skill is missing for the en-US locale. In the Distribution tab, go to Skill Preview for en-US to add the skill description.",
        "status": "FAILED",
        "importance": "REQUIRED"
      },
      {
        "title": "A selection is missing for the question ‘Does this Alexa skill collect users’ personal information?’. In the Distribution tab, go to the Privacy & Compliance section to provide an answer.",
        "status": "FAILED",
        "importance": "REQUIRED"
      },
      {
        "locale": "en-US",
        "title": "Not enough example phrases provided",
        "description": "[en-US] Required: Provide at least 1 example phrase",
        "status": "FAILED",
        "importance": "REQUIRED"
      }
    ]
  }
}
```

#### What happened?

The ASK CLI used the [`Skill Validation API`](https://developer.amazon.com/docs/smapi/skill-validation-api.html) to perform a set of pre-certification tests on your skill. This is an asynchronous operation which polls the validation result until it is available. 
If you prefer to run the validation and obtain the validation results in two separate steps, you can use the following subcommands [`validate-skill`](https://developer.amazon.com/docs/smapi/ask-cli-command-reference.html#validate-skill-subcommand) and [`get-validation`](https://developer.amazon.com/docs/smapi/ask-cli-command-reference.html#get-validation-subcommand).

All tests performed are available in the `validations` object with the following properties:

* `locale`: The locale tested
* `title`: The title of the test made
* `description`: The description of the test made
* `status`: The validation status. Either `SUCCESSFUL`, or `FAILED`.
* `importance`: One of: `REQUIRED`, `RECOMMENDED`, or `RECOMMENDED/REQUIRED`.

If at least one test with importance `REQUIRED` is failing, the overall validation status is `FAILED` (you cannot submit to certification).

---

# 🏆 Congratulations - You have completed the Alexa-Hosted with ASK CLI Lab! 🏆

## Bonus Step: [Update your Skill](./05-bonus.md) | Skip to [Advanced Testing](../04-lab/README.md)