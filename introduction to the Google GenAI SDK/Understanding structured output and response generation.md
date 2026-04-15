**LLMS always respone by text-free, and this is great for making creative things, But it's a nightmare for those who want to build a stucture thing like an book classification that is relying on the author, year, description, etc**

### Why it's a nightmare?

**Imagine that you are bulding a project that is about the *user* ask: What is the best 3 novels to read for someone who is 16 years old?, The AI respone well be text-free as we said, But what if you don't want that? what if you ant to make the AI only respone by structered thing like: `author: ..., year: ..., description:....`**

## And this is where *Structured output* come from

### Defining data structures with Pydantic

**To enforce the structure we need we will use `Pydantic` library, And it's better that telling the AI in the prompt: `reply by the author name only and...`**

```
from pydantic import BaseModel

class Book(BaseModel):
  title: str
  author: str
  year: int
  description: str  

class RecommendationList(BaseModel):
  books: list[Book]
```

**first thing we imported the `BaseModel` from `pydantic`
Then we put our structure: `title -> author -> year -> description`, And we define each one it we want it srting or integer *Side Note:* if the year (int) is str *example:* '1949', `pydantic` library will make it `int`, so it's like: `'1949' -> 1949`
And the `RecommendationList` class is about: structue the library**

### The GenAI Client and Configuration

