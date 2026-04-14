## Sending a basic text to gemeni 3 

**First thing we will make our client**

```
from google import genai
from google.colab import userdata

api_key = userdata.get('GOOGLE_API_KEY')
clinet = genai.Client(api_key=api_key)
```

```
# Send simple example to the model
response = clinet.models.generate_content(
    model = 'gemini-3-flash-preview',
    contents = 'Recommend three classic science fiction novels for a beginner.'
)

# Print the response
print(response.text)
```

It's following this workflow when chatting with google gemini 

`send the request -> wait the model to process -> recive the response`
