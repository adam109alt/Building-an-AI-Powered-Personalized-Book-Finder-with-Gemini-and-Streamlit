## Why do we need the AI to have memory?

Because it's stateless if we just asked the thing from 1 second then we asking another thing that is related on the same topic and then the AI dose know about it

### Ok how can we make memory using google genAI SDK

***The code:***

```
from google import genai
from google.colab import userdata

api_key = userdata.get('GOOGLE_API_KEY')
client = genai.Client(api_key=api_key)

chat = client.chats.create(model="gemini-3.1-flash-lite-preview")

response1 = chat.send_message("My name is Adam.")
print(f"AI: {response1.text}")

response2 = chat.send_message("what is my name??")
print(f"AI: {response2.text}")
```

- We imported the genai and the google colab library that will make us accsess the *API key*
- We put our API key in the client
- we setup the chat model we will use
- then we start asking by `chat.send_message` then we put in it the question, then print the response

### But it's also look like it's stateless

**Well yeah it's look like stateless, if the user want to see the AI response then asks the next question, But it's good if you have multiple questions that you just want to know it's response**

*But we can make it like not stateless if we make it loop*

The code:

```
from google import genai
from google.colab import userdata

api_key = userdata.get('GOOGLE_API_KEY')
client = genai.Client(api_key=api_key)

chat = client.chats.create(model="gemini-3.1-flash-lite-preview")

while True:

  user = input('User: ')

  response5 = chat.send_message(user)
  print("AI:", response5.text)

  if user == 'exit':
    break
```

- of course imported the librarys and setup the API
- but we made an very small uprade that we make an loop that will not break until i type exit

and this is mutch more `basic` and `easier` and more `affective

And this is how we can chat with the model very normally
