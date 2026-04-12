# Google Colab + Streamlit Setup Guide

## What is Google Colab?

Google Colab is a cloud-based environment provided by Google that allows you to run Python code using CPU and GPU resources.

* CPU is suitable for small tasks.
* GPU can be used for heavier computations (for a limited time).

---

## What We Will Learn

In this guide, we will:

* Create a simple Streamlit web app
* Install the Google Generative AI SDK

---

## Step 1: Install Required Libraries

```python
!pip install streamlit google-genai
```

In Google Colab, the `!` symbol is used to run shell commands (like installing packages).

---

## Step 2: Create the Streamlit App File

```python
%%writefile app.py
import streamlit as st

st.title("Book Finder Setup")
st.write("Environment configured successfully.")
```

### Explanation:

* `%%writefile app.py` creates a file named `app.py`
* `import streamlit as st` imports the Streamlit library
* `st.title()` displays a title on the web page
* `st.write()` displays text content

---

## Step 3: Run the Streamlit Server

```python
!streamlit run app.py &>/dev/null &
```

### Explanation:

* `!streamlit run app.py` runs the app
* `&>/dev/null` hides logs and output
* `&` runs the process in the background so the cell doesn't keep running forever

---

## Step 4: Expose the App Using LocalTunnel

```python
!npm install localtunnel
!npx localtunnel --port 8501
```

### Explanation:

* Installs LocalTunnel
* Exposes your local Streamlit server to the internet
* The app runs on port `8501` by default

---

## Final Result

You will get a public URL that allows you to access your Streamlit app from anywhere 🌍

---

## Notes

* This setup is temporary (Colab sessions expire)
* Useful for testing and prototyping
* Not recommended for production deployment
