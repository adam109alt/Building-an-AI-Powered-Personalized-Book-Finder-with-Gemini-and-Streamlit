## Sending a basic text to gemeni 3 

**First thing we will make our client API KEY**

```
from google import genai
from google.colab import userdata

api_key = userdata.get('GOOGLE_API_KEY')
clinet = genai.Client(api_key=api_key)
```

**Second thing we will make our response**

```
# Send simple example to the model
response = clinet.models.generate_content(
    model = 'gemini-3-flash-preview',
    contents = 'Recommend three classic science fiction novels for a beginner.'
)

# Print the response
print(response.text)
```

here we are using `gemini-3-flash-preview` model, and the prompt of it is the `contents`, And then we print the response by: `print(response.text)`

the gemini SDK follow this workflow: 

`send the request -> wait the model to process -> recive the response`

## Handling Response Metadata

The response variable is not just some variable no we use in it the context window of the `model` we put in it the `system instuctions` and the `temperature` 

and we can know the meta data of the response (tokens, model version) of the AI by:

```
print(f'The tokens that have been used in this response is: {response.usage_metadata}')
print(f'the model that have generated this reponse is: {response.model_version}')
```

You can also add `config` in the response section

```
from google.genai import types

response = client.models.generate_content(
    model="gemini-2.0-flash",
    contents="Explain why 'Dune' is a significant book in 2 sentences.",
    config=types.GenerateContentConfig(
        temperature=0.7,
        max_output_tokens=150
    )
)
```

## Summary

You have now mastered the entry point of the GenAI SDK: initializing a client and executing a basic text generation request. We also looked at how to inspect the returned metadata and tune the generation parameters. In the next stage, we will shift from simple text requests to managing structured outputs, which is critical for turning raw model responses into the usable data required for our book finder application.
