
# Gemini LLM Q&A App

A lightweight Streamlit web application that uses Google's Gemini 2.0 Flash language model to answer user questions in real time.

## 🧠 Overview

This app provides a simple interface where users can input a question and receive intelligent responses powered by Google's Gemini model, all through a clean Streamlit frontend.

## 📦 Requirements

- Python 3.7 or higher
- Google API Key (get from [Google AI Studio](https://makersuite.google.com/app))
- Required Python packages:
  - streamlit
  - python-dotenv
  - google-generativeai

## 🛠️ Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/gemini-qa-app.git
cd gemini-qa-app
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

### 3. Activate the Virtual Environment

- On **Windows**:
  ```bash
  venv\Scripts\activate
  ```
- On **macOS/Linux**:
  ```bash
  source venv/bin/activate
  ```

### 4. Create `requirements.txt`

```txt
streamlit
python-dotenv
google-generativeai
```

### 5. Install Dependencies

```bash
pip install -r requirements.txt
```

### 6. Set Up Environment Variable

Create a `.env` file in the root directory and add:

```env
GOOGLE_API_KEY=your_api_key_here
```

### 7. Create the Application File

Create a file named `app.py` and paste the following code:

```python
from dotenv import load_dotenv
load_dotenv()

import streamlit as st
import os
import google.generativeai as genai

genai.configure(api_key=os.getenv("GOOGLE_API_KEY"))

model = genai.GenerativeModel("models/gemini-2.0-flash")

def get_gemini_response(question):
    response = model.generate_content(question)
    return response.text

st.set_page_config(page_title="Q&A Demo")
st.header("Gemini LLM Application")

input = st.text_input("Input: ", key="input")
submit = st.button("Ask the question")

if submit:
    response = get_gemini_response(input)
    st.subheader("The Response is")
    st.write(response)
```

### 8. Run the App

```bash
streamlit run app.py
```

## 📄 License

This project is licensed under the MIT License.