# Introduction to Creating RAGs with OpenAI 
## Code and Documentation for the basic LangChain-LLM

This project demonstrates the fundamental concepts of LangChain by building a basic LLM Chain using Google Gemini as the language model. It covers model initialization, prompt templates, output parsers, and translation chains.

---

## Architecture
```
User Input
    ↓
ChatPromptTemplate  →  formats the message with system + user roles
    ↓
ChatGoogleGenerativeAI (gemini-2.5-flash)  →  processes the prompt
    ↓
StrOutputParser  →  extracts clean text from the model response
    ↓
Final Output
```
### Components Used

| Component | Description |
|---|---|
| `ChatGoogleGenerativeAI` | Google Gemini LLM via LangChain |
| `ChatPromptTemplate` | Structures the prompt with system and user roles |
| `StrOutputParser` | Parses the model output into plain string |
| `HumanMessage` | Sends a direct message to the model |
| `LangSmith` | Traces and monitors LangChain calls |

---

##  Project Structure
```
repo-1-langchain-basic/
│
├── notebook.ipynb       ← Main Jupyter notebook with all the code
├── .env.example         ← Template for environment variables (no real keys)
├── requirements.txt     ← Python dependencies
└── README.md            ← Project documentation
```

---

## Installation and Setup

### 1. Clone the repository
```bash
git clone https://github.com/Rogerrdz/Introduction-to-Creating-RAGs-with-OpenAI--code-and-documentation-for-the-basic-LangChain-LLM.git
cd Introduction-to-Creating-RAGs-with-OpenAI--code-and-documentation-for-the-basic-LangChain-LLM.git
```

### 2. Install dependencies
```bash
pip install langchain langchain-text-splitters langchain-community langchain-google-genai bs4 python-dotenv
```

Or using the requirements file:
```bash
pip install -r requirements.txt
```

### 3. Set up your API keys

Copy the `.env.example` file and rename it to `.env`:
```bash
cp .env.example .env
```

Then fill in your API keys inside the `.env` file:
```
GOOGLE_API_KEY=your_google_api_key_here
LANGSMITH_API_KEY=your_langsmith_api_key_here
```

**Where to get the keys:**
- Google API Key → [aistudio.google.com](https://aistudio.google.com) → Get API Key (free)
- LangSmith API Key → [smith.langchain.com](https://smith.langchain.com) → Settings → API Keys (free)

### 4. Run the notebook
```bash
jupyter notebook notebook.ipynb
```

Run all cells in order from top to bottom.

---

## What the Notebook Covers

###  Cell 1 — Install Dependencies
Installs all required libraries using pip.

###  Cell 2 — LangSmith Setup
Enables tracing and monitoring of LangChain calls via LangSmith.

###  Cell 3 — Load Environment Variables
Safely loads API keys from the `.env` file using `python-dotenv`.

###  Cell 4 — Initialize the Model
Creates a `ChatGoogleGenerativeAI` instance using `gemini-2.5-flash`.

###  Cell 5 — First Message
Sends a direct `HumanMessage` to the model and prints the response.
```python
from langchain_core.messages import HumanMessage

response = model.invoke([HumanMessage(content="Hola, ¿qué es LangChain?")])
print(response.content)
```

###  Cell 6 — Prompt Template + Chain
Builds a full LangChain chain using the `|` operator:
```python
chain = prompt | model | StrOutputParser()
response = chain.invoke({"input": "¿Qué es un LLM?"})
```

###  Cell 7 — Translation Chain
Demonstrates reusability of chains by translating text to different languages:
```python
chain.invoke({"language": "English", "text": "Hola, ¿cómo estás?"})
chain.invoke({"language": "French", "text": "Hello, how are you?"})
```

## Example Output
```
Translated to English:
Hello, how are you? My name is Juan and I am learning LangChain.

Translated to French:
Bonjour, j'apprends l'intelligence artificielle.
```

---

## requirements.txt
```
langchain
langchain-community
langchain-text-splitters
langchain-google-genai
bs4
python-dotenv
```

---
##  Security Note

Never upload your `.env` file to GitHub. The `.gitignore` file in this project already excludes it. Only the `.env.example` file (with empty values) is safe to share publicly.

---

##  References

- [LangChain Official Docs](https://docs.langchain.com)
- [LangChain Quickstart Tutorial](https://docs.langchain.com/oss/python/langchain/quickstart)
- [Google AI Studio](https://aistudio.google.com)
- [LangSmith](https://smith.langchain.com)
