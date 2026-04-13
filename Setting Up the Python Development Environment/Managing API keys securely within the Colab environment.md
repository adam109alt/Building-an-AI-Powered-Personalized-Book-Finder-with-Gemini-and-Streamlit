## IMPORTANT THING

First thing you should know is when you put your API key in the code directly it's soo dangerous you might forget and publish your code to github, public community's, etc,

Soo what we need is:

***Make those API keys is secret by:***

1. go to the left hand sidebar (**In google colab**)
2. click on *secret*
3. name the api key
4. get the API key from ***google AI studio*** then paste it in the *Value*
5. then make *Note Book* **access is on**

**And after you done all these steps run this code to check if everything is okay:**

```
from google.colab import userdata

api_key = userdata.get('GOOGLE_API_KEY')

if api_key:
    print("API Key successfully retrieved.")
else:
    print("Failed to retrieve API key. Check your Secrets settings.")
```
