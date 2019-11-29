# Lab 2: Alexa-Hosted with ASK CLI

## [CREATE](./01-create.md) | [EDIT](./02-edit.md) | [DEPLOY](./03-deploy.md) | **[TEST](./04-test-simulate.md)**

We will perform 4 basic type of tests using ASK CLI commands:

1. **[One Turn Simulation - Text Input](./04-test-simulate.md)** *<== CURRENT TEST*

1. [One Turn Simulation - JSON Input](./04-test-invoke.md)

1. [Multi-Turn Simulation](./04-test-dialog.md)

1. [Pre-Certification Tests](./04-test-pre-certification.md) 

# One Turn Simulation - Text Input

To start testing your skill, we will [`simulate`](https://developer.amazon.com/docs/smapi/ask-cli-command-reference.html#simulate-command) an invocation of your skill with a text input.

It will test the input against your skill model and code. This is equivalent to speak to a device.

#### Command

```
ask simulate --locale en-US --text "open hosted hello world"
```

#### Expected Output

```json
✓ Simulation created for simulation id: fff3d782-de6c-46b1-84bc-d15a118f0024
{
  "id": "fff3d782-de6c-46b1-84bc-d15a118f0024",
  "status": "SUCCESSFUL",
  "result": {
    "alexaExecutionInfo": {
      "alexaResponses": [
        {
          "type": "Speech",
          "content": {
            "caption": "Welcome, you can say Hello or Help. Which would you like to try?"
          }
        }
      ],
      "consideredIntents": [
        {
          "name": "<LaunchRequest>"
        }
      ]
    },
    "skillExecutionInfo": {
      "invocations": [
        {
          "invocationRequest": {
            "endpoint": "arn:aws:lambda:us-east-1:YYYYYYYYYYYY:function:XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX:Release_0",
            "body": {
              "version": "1.0",
              "session": {
                "new": true,
                "sessionId": "amzn1.echo-api.session.123...",
                "application": {
                  "applicationId": "amzn1.ask.skill.XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"
                },
                "user": {
                  "userId": "amzn1.ask.account.AF6P4M..."
                }
              },
              "context": {
                "System": {
                  "application": {
                    "applicationId": "amzn1.ask.skill.XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"
                  },
                  "user": {
                    "userId": "amzn1.ask.account.AF6P4M..."
                  },
                  "device": {
                    "deviceId": "amzn1.ask.device.AFRGW4...",
                    "supportedInterfaces": {}
                  },
                  "apiEndpoint": "https://api.eu.amazonalexa.com",
                  "apiAccessToken": "eyJ0eX..."
                }
              },
              "request": {
                "type": "LaunchRequest",
                "requestId": "amzn1.echo-api.request.71bd92...",
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
                "shouldEndSession": false,
                "type": "_DEFAULT_RESPONSE"
              },
              "sessionAttributes": {},
              "userAgent": "ask-node/2.7.0 Node/v8.10.0"
            }
          },
          "metrics": {
            "skillExecutionTimeInMilliseconds": 489
          }
        }
      ]
    }
  }
}
```

#### What happened?

The ASK CLI used the [`Skill Simulation API`](https://developer.amazon.com/docs/smapi/skill-simulation-api.html) to forge a request to simulate a skill execution. 

The output provides us with the following information (among others):

* `status`: Current status of the simulation. One of: `IN_PROGRESS`, `SUCCESSFUL`, or `FAILED`.
* `result.alexaExecutionInfo.alexaResponses.content`: Object that contains the content of the Alexa response.
* `result.alexaExecutionInfo.consideredIntents`: An array contains at most 5 considered intents returned by natural language understanding (NLU).
* `result.skillExecutionInfo.invocations.invocationRequest.body`: JSON payload that was sent to the skill's AWS Lambda.
* `result.skillExecutionInfo.invocations.invocationResponse.body`: JSON Payload that was returned by the skill's AWS Lambda.

In case of error, the response will include an error message and the associated HTTP response status code

---

## Next Step: [Test your skill backend](./04-test-invoke.md)