## The current GENAI SDK use the `client` and it's like the gateway when you are talking to the `google gemeni models`  

In the `Client` you will put your API 

```
from google import genai
from google.colab import userdata

api_key = userdata.get('GOOGLE_API_KEY')

client = genai.Client(api_key=api_key)
```
## The Authentication Lifecycle

Creating the `genai.Client` just saves your password locally. It doesn't connect to Google until the exact moment you ask it to generate content. This keeps your app fast and prevents unnecessary network traffic.

### Now let's test our API key by simple question

```
from google import genai
from google.colab import userdata

# Call the API key
api_key = userdata.get('GOOGLE_API_KEY')
client = genai.Client(api_key=api_key)

# Try it by simple example
response = client.models.generate_content(
    model = 'gemini-3-flash-preview',
    contents = 'Hello can you help me to find a book'
)

print(response.text)
```

the `model we are using is: gemini-3-flash-preview` and in the contents section is the `prompt` 
