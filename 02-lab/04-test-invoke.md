# Lab 2: Alexa-Hosted with ASK CLI

## [CREATE](./01-create.md) | [EDIT](./02-edit.md) | [DEPLOY](./03-deploy.md) | **[TEST](./04-test-invoke.md)**

We will perform 4 basic type of tests using ASK CLI commands:

1. [One Turn Simulation - Text Input](./04-test-simulate.md)

1. **[One Turn Simulation - JSON Input](./04-test-invoke.md)** *<== CURRENT TEST*

1. [Multi-Turn Simulation](./04-test-dialog.md)

1. [Pre-Certification Tests](./04-test-pre-certification.md) 

# One Turn Simulation - JSON Input

To test the deployed skill code **only**, we will use the [`invoke-skill`](https://developer.amazon.com/docs/smapi/ask-cli-command-reference.html#invoke-skill-subcommand) subcommand by providing a sample JSON request compliant with the [Alexa Request JSON Reference](https://developer.amazon.com/docs/custom-skills/request-and-response-json-reference.html#request-format).

It will sent the JSON Request to the AWS Lambda function and wait for the Reponse JSON output.

#### Command

```
ask api invoke-skill --skill-id amzn1.ask.skill.[unique-value-here] --file launchRequest.json --endpoint-region default 
```

> **Note**: the JSON payload to be sent to your skill is available in the following file: [`launchRequest.json`](./launchRequest.json).
>
> Ensure you update the `[your-skill-id]` placeholder in file `launchRequest.json` by your skill ID value before using it.

#### Expected Output

```json
{
  "status": "SUCCESSFUL",
  "result": {
    "skillExecutionInfo": {
      "invocationRequest": {
        "endpoint": "arn:aws:lambda:us-east-1:YYYYYYYYYYYY:function:XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX:Release_0",
        "body": {
          "version": "1.0",
          "session": {
            "new": true,
            "sessionId": "amzn1.echo-api.session.123",
            "application": {
              "applicationId": "amzn1.ask.skill.XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"
            },
            "user": {
              "userId": "amzn1.ask.account.AF6P4M"
            }
          },
          "context": {
            "System": {
              "application": {
                "applicationId": "amzn1.ask.skill.XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"
              },
              "user": {
                "userId": "amzn1.ask.account.AF6P4M"
              },
              "device": {
                "deviceId": "amzn1.ask.device.AFRGW4",
                "supportedInterfaces": {}
              },
              "apiEndpoint": "https://api.eu.amazonalexa.com",
              "apiAccessToken": "eyJ0eX"
            }
          },
          "request": {
            "type": "LaunchRequest",
            "requestId": "amzn1.echo-api.request.71bd92",
            "timestamp": "2019-10-15T19:02:17Z",
            "locale": "en-US",
            "shouldLinkResultBeReturned": false
          }
        }
      },
      "invocationResponse": {
        "body": {
          "version": "1.0",
          "response": {
            "outputSpeech": {
              "type": "SSML",
              "ssml": "<speak>Welcome, you can say Hello or Help. Which would you like to try?</speak>"
            },
            "reprompt": {
              "outputSpeech": {
                "type": "SSML",
                "ssml": "<speak>Welcome, you can say Hello or Help. Which would you like to try?</speak>"
              }
            },
            "shouldEndSession": false
          },
          "userAgent": "ask-node/2.7.0 Node/v8.10.0",
          "sessionAttributes": {}
        }
      },
      "metrics": {
        "skillExecutionTimeInMilliseconds": 20
      }
    }
  }
}
```

#### What happened?

The ASK CLI used the [`Skill Invocation API`](https://developer.amazon.com/docs/smapi/skill-invocation-api.html) to forge a request to invoke the AWS Lambda endpoint used by the skill. 

The output provides us with the following information (among others):

* `status`: Current status of the skill invocation. Either `SUCCESSFUL`, or `FAILED`.
* `invocationRequest.body`: JSON payload that was sent to the skill's AWS Lambda.
* `invocationResponse.body`: JSON Payload that was returned by the skill's AWS Lambda.

In case of error, the response will include an error message and the associated HTTP response status code.

---

## Next Step: [Test a dialog with your Skill](./04-test-dialog.md)