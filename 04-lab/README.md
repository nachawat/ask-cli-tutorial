# Advanced Testing with the ASK CLI

We will cover here some NLU testing that you can perform without even having a programming logic.

### 1- Conflict Detection

Upon Interaction Model build automatic conflict detection will be trigger to identify [duplicate utterances and slots](https://developer.amazon.com/docs/smapi/utterance-conflict-detection-api.html). As this is an asynchronous job, to retrieve the result you can run the following command:

```
ask api get-conflicts --skill-id <SKILL_ID> --locale en-US
```

### 2- Utterances Profiler

After building your Interaction Model, you can test your Interaction Model without any programming logic being implement by using the [Utterances Profiler](https://developer.amazon.com/docs/custom-skills/test-utterances-and-improve-your-interaction-model.html). It is accessible from the Alexa Developer Console as well as from the ASK CLI using the following command:

```
ask api nlu-profile --utterance "hello there" --skill-id <SKILL_ID> --locale en-US 
```

This command will test the given utterance against Alexa NLU once your Interaction Model has been built and will provide you with the selected intent and the considered intents (but discard).

### 3- NLU Annotations


To evaluate your model, you define a set of utterances mapped to the intents and slots you expect to be sent to your skill. This is called an annotation set. Then you start an NLU evaluation with the annotation set to determine how well you skill's model performs against your expectations. The tool can help you measure the accuracy of your NLU model, and run regression testing to ensure that changes to your model don't degrade the customer experience.

You can use the [NLU Evaluation Tool](https://developer.amazon.com/docs/custom-skills/batch-test-your-nlu-model.html) with skill models for all locales. You can also access these tools with the Skill Management API (SMAPI) or the ASK Command Line Interface (ASK CLI). 

#### Step 1: Create the AnnotationSet

You first need to create the Annotation Set with the following command and get an Annotation Set ID in exchange:

```
ask api create-nlu-annotation-set --skill-id <SKILL_ID> --locale en-US --annotation-set-name AnnotationDemoBatch
```

##### Step 2: Add Test Cases to the Set

After creating the Annotation Set, you will append some test cases with expected output values. Each Test case contains at least the utterance and the intent to be mapped to.

```
ask api update-nlu-annotation-set-annotations --skill-id <SKILL_ID> --annotation-id <annotation-id> --annotations-file annotationSet.json --annotations-format application/json
```

> **Note:** you can find here a sample file showing the JSON structure to add test cases to an Annotation Set: [annotationSet](./annotationSet.json)

#### Step 3: Trigger a new evaluation of your Annotation Set

Once, your Annotation Set is created and populated with test cases, you can launch an evalutation with the following command:

```
ask api evaluate-nlu --skill-id <SKILL_ID> --locale en-US --annotation-id <annotation-id>
```

This will trigger an asynchronous evaluation and return you an Evaluation ID (<evaluation-id>).

#### Step 4: Get the status for the ongoing evaluation of your Annotation Set

As the evaluation of your Annotation Set is asynchronous, you can get the latest of this execution running the following command:

```
ask api get-nlu-evaluation --skill-id <SKILL_ID> --evaluation-id <evaluation-id>
```

#### Step 5: Get the results from the evaluation of your Annotation Set

Once, the evalutation exection is over, you can get the latest results running the following command: 

```
ask api get-nlu-evaluation-results --skill-id <SKILL_ID> --evaluation-id <evaluation-id>
```