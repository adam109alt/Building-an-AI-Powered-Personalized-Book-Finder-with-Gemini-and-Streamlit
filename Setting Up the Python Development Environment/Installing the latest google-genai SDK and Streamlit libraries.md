### First thing we need is to install the library's we will use:

`!pip install -q google-genai streamlit`

`!` is to tell *google colab* to run this code as shell command not a python code

`-q` This will hide all the installations things to make the output is clean 

### Second thing we need to check if we installed the library corecttly by:

```
import streamlit as st
from google import genai

print(f"GenAI SDK version: {genai.__version__}")
```

**If you don't see ImportError, and the output was a version number then the *installation have done sucsessfully***

### The core of our project is

the user input -> streamlit -> python logic -> google genai SDK -> google model -> the respone -> API or the SDK -> python logic -> streamlit

**Summary**

**You have now established the foundation for your development workspace. By installing the `google-genai SDK` and `streamlit`,
you have equipped your Python environment with the necessary tools for both generative intelligence and front-end delivery.
In the upcoming sections, we will move into configuring the API keys securely, which is the final step before you begin writing the logic to talk to the AI.**
