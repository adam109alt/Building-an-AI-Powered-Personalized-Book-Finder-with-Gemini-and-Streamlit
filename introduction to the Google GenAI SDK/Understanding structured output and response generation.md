## Why Structured Output Matters

LLMs naturally respond with unstructured text — great for complex, creative, or multi-step tasks, but overkill when you just need specific fields. What if instead of a paragraph, you got back exactly `('title', 'author', 'year', 'description')`? That's what we're building here.

---

### Cell 1 — Define the Schema

```python
from pydantic import BaseModel

class Book(BaseModel):
    title: str
    author: str
    year: int
    description: str

class RecommendationList(BaseModel):
    books: list[Book]
```

We import `BaseModel` from the `pydantic` library to define our data schema.

The `Book` class defines the structure of a single book with four fields: `title`, `author`, `year`, and `description`. By inheriting from `BaseModel`, each instance gets automatic **data validation**, **type coercion** (e.g. converting `"2001"` to `2001`), and **serialization** for free.

The `RecommendationList` class wraps a list of `Book` objects under a `books` key — this becomes the top-level schema we'll pass to the model.

---

### Cell 2 — Call the Gemini API

```python
from google import genai
from google.colab import userdata

api_key = userdata.get('GOOGLE_API_KEY')
client = genai.Client(api_key=api_key)

response = client.models.generate_content(
    model='gemini-2.5-flash',
    contents='Give me the best 3 novels about someone who does everything they can to reach their goal',
    config={
        'response_mime_type': 'application/json',
        'response_schema': RecommendationList
    }
)
```

We import Google's `genai` SDK and use `google.colab`'s `userdata` to securely load the API key — avoiding hardcoding secrets in the notebook.

The `generate_content` call takes three key arguments:
- **`model`** — which Gemini model to use
- **`contents`** — the prompt sent to the model
- **`config`** — here we set `response_mime_type` to `"application/json"` to force a JSON response, and `response_schema` to our `RecommendationList` class to enforce the exact structure

---

### Cell 3 — Parse and Display the Results

```python
import json

data = json.loads(response.text)

for book in data['books']:
    print(f"Title: {book['title']}")
    print(f"Author: {book['author']}")
    print(f"Published: {book['year']}")
    print(f"Description: {book['description']}")
    print("-" * 20)
```

We parse the JSON string from `response.text` into a Python dictionary using `json.loads`. Then we loop over every book in `data['books']` and print each field cleanly, with a separator line between entries.
