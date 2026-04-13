# The Configuration layer

```
import streamlit as st
from google import genai

client = genai.Client(api_key='GOOGLE_API_KEY')
```

**This handles your API key**

# The User Interface Layer (Streamlit)

This layer defines the layout. You use Streamlit's "functional" approach here: you call a function, and the component immediately appears on the screen.

Layout components: `st.sidebar` for navigation or settings, `st.columns` for side-by-side content, and `st.container` for grouping elements.
Input widgets: `st.text_input` or `st.selectbox` for capturing user preferences.
Output elements: `st.write`, `st.markdown`, or `st.image` to display book recommendations.


# The Logic and Data Layer
```
def get_book_recommendation(user_prompt):
  # Call Gemeni API and get the format
  respone = client.models.generate_content(
      model = 'gemini-3.1-pro-preview',
      contents = user_prompt
  )
  return respone.text
```

**The core of your architecture is "Separation of Concerns." By keeping your API interaction logic separate from your UI rendering functions, you create a robust structure. Remember that your code will execute repeatedly; by using st.session_state and modular functions, you ensure that the application feels like a cohesive, single-page experience rather than a series of disconnected script runs.**
