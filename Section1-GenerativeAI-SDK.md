# AI-901 Practice Exam: Generative AI Models & OpenAI SDK in Microsoft Foundry

**Total Questions: 55 | Time Suggested: 90 minutes | Pass Mark: 80%**

Difficulty Legend: [E] Easy | [M] Medium | [H] Hard

---

## SECTION A: Foundations & Concepts (Questions 1-12)

**Q1. [E] True or False**
In Azure AI Foundry, the deployment name you assign to a model is always identical to the underlying model name (e.g., `gpt-4o`).

- A) True
- B) False

**Q2. [E] Matching -- Match each term to its definition.**

| Term | Definition |
|------|-----------|
| 1. Foundry Playground | A. Browse and compare available AI models |
| 2. Model Catalog | B. No-code interface for testing prompts |
| 3. Responses API | C. Modern unified API for chat completions |
| 4. Deployment | D. A provisioned instance of a model ready to serve requests |

- A) 1-B, 2-A, 3-C, 4-D
- B) 1-A, 2-B, 3-D, 4-C
- C) 1-B, 2-A, 3-D, 4-C
- D) 1-D, 2-A, 3-C, 4-B

**Q3. [E] Multiple Choice**
Which pip packages are needed to use the OpenAI SDK with Azure AI Foundry and authenticate via Azure Identity?

- A) `pip install openai`
- B) `pip install openai azure-ai-projects`
- C) `pip install openai azure-ai-projects azure-identity`
- D) `pip install azure-openai azure-identity`

**Q4. [E] True or False**
The Foundry Playground requires you to write Python code to test a generative AI model's responses.

- A) True
- B) False

**Q5. [M] Compare & Contrast**
What is the difference between **zero-shot** and **few-shot** prompting?

- A) Zero-shot uses no examples in the prompt; few-shot includes example input-output pairs in the prompt
- B) Zero-shot sends zero API calls; few-shot sends multiple API calls
- C) Zero-shot uses temperature=0; few-shot uses temperature=1
- D) Zero-shot is free; few-shot costs more tokens but they are otherwise identical techniques

**Q6. [E] Configuration**
Which environment variable stores the Azure OpenAI resource URL?

- A) `OPENAI_API_BASE`
- B) `AZURE_OPENAI_ENDPOINT`
- C) `AZURE_API_URL`
- D) `MODEL_ENDPOINT`

**Q7. [M] Multiple Choice**
A developer sets `temperature=0` in their API call. What behavior should they expect?

- A) The model will refuse to generate any output
- B) The model will produce nearly deterministic, consistent output across identical requests
- C) The model will generate the longest possible response
- D) The model will only return single-word answers

**Q8. [E] Multiple Choice**
What does the `max_output_tokens` parameter control?

- A) The maximum number of tokens in the input prompt
- B) The total cost of the API call
- C) The maximum number of tokens the model can generate in its response
- D) The maximum number of API calls per minute

**Q9. [M] Best Practice**
A team stores their API key directly in their Python source file: `api_key = "sk-abc123..."`. What is the recommended best practice?

- A) This is fine for production code
- B) Store the key in a `.env` file and load it with `dotenv` and `os.getenv()`
- C) Store the key in a comment so it is not executed
- D) Encode the key in base64 in the source file

**Q10. [M] Scenario-Based**
A company wants to let non-technical product managers quickly test different system prompts before developers write code. Which Foundry feature should they use?

- A) Azure CLI
- B) Foundry Playground
- C) VS Code terminal
- D) Model Catalog deployment page

**Q11. [M] Compare & Contrast**
What is the difference between a **system prompt** and a **user prompt** in the Responses API input array?

- A) System prompt sets the model's persona/behavior; user prompt provides the actual question or task
- B) System prompt is optional metadata; user prompt is the only thing the model reads
- C) They are interchangeable and have no functional difference
- D) System prompt limits token count; user prompt sets temperature

**Q12. [E] Multiple Choice**
The correct endpoint format for Azure OpenAI is:

- A) `https://<resource>.azure.com/openai/`
- B) `https://<resource>.openai.azure.com/openai/v1/`
- C) `https://openai.azure.com/<resource>/v1/`
- D) `https://<resource>.cognitiveservices.azure.com/openai/`

---

### ANSWERS: Section A (Questions 1-12)

| # | Answer | Explanation |
|---|--------|-------------|
| 1 | **B) False** | The deployment name is chosen by the user during deployment and can differ from the model name. You might deploy `gpt-4o` with deployment name `my-gpt4o-prod`. |
| 2 | **A) 1-B, 2-A, 3-C, 4-D** | Playground is no-code testing; Model Catalog is for browsing; Responses API is the modern unified API; Deployment is a provisioned model instance. |
| 3 | **C)** | You need `openai` for the SDK, `azure-ai-projects` for Foundry project integration, and `azure-identity` for Azure authentication. |
| 4 | **B) False** | The Foundry Playground is a no-code interface for testing prompts directly in the browser. |
| 5 | **A)** | Zero-shot gives no examples and relies on the model's training. Few-shot includes example input-output pairs within the prompt to guide the model. |
| 6 | **B)** | The standard environment variable is `AZURE_OPENAI_ENDPOINT`. |
| 7 | **B)** | Temperature=0 makes the model's sampling nearly deterministic, producing consistent outputs for the same input. |
| 8 | **C)** | `max_output_tokens` caps the length of the generated response, not the input or cost directly. |
| 9 | **B)** | Never hardcode secrets. Use a `.env` file with `load_dotenv()` and `os.getenv("API_KEY")`. |
| 10 | **B)** | Foundry Playground lets non-technical users test prompts without writing code. |
| 11 | **A)** | The system prompt defines the model's behavior, tone, and constraints. The user prompt is the actual request or question. |
| 12 | **B)** | The standard Azure OpenAI endpoint format is `https://<resource>.openai.azure.com/openai/v1/`. |

---

## SECTION B: Code Deep Dive (Questions 13-28)

**Q13. [M] Code Output Prediction**
```python
from openai import OpenAI

client = OpenAI(base_url="https://myres.openai.azure.com/openai/v1/", api_key="abc123")
response = client.responses.create(
    model="gpt-4o-deploy",
    input=[
        {"role": "system", "content": "Reply with only the number 42."},
        {"role": "user", "content": "What is the answer?"}
    ],
    temperature=0,
    max_output_tokens=10
)
print(type(response.output_text))
```
What will `type(response.output_text)` print?

- A) `<class 'list'>`
- B) `<class 'dict'>`
- C) `<class 'str'>`
- D) `<class 'int'>`

**Q14. [M] Bug Finding**
```python
from openai import OpenAI
import os
from dotenv import load_dotenv

load_dotenv()

client = OpenAI(
    base_url=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("API_KEY")
)

response = client.responses.create(
    model=os.getenv("MODEL_DEPLOYMENT_NAME"),
    input="What is Python?",
    temperature=0.7
)
print(response.output_text)
```
This code may work but violates the expected input format. What is wrong?

- A) `temperature` should be an integer
- B) The `input` parameter should be a list of role/content dictionaries, not a plain string
- C) `load_dotenv()` is not needed
- D) `output_text` is not a valid attribute

**Q15. [H] Bug Finding**
```python
from openai import OpenAI
import os
from dotenv import load_dotenv

client = OpenAI(
    base_url=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("API_KEY")
)

response = client.responses.create(
    model=os.getenv("MODEL_DEPLOYMENT_NAME"),
    input=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Hello!"}
    ]
)
print(response.output_text)
```
The developer reports that `os.getenv("AZURE_OPENAI_ENDPOINT")` returns `None`. What is the most likely cause?

- A) The `openai` package is not installed
- B) `load_dotenv()` was never called before `os.getenv()`, so the `.env` file was not loaded
- C) The `.env` file must be named `.environment`
- D) `os.getenv` does not exist in Python

**Q16. [M] Fill-in-the-Blank**
Complete the code to create a client and make an API call:
```python
from _______ import OpenAI
import os
from dotenv import load_dotenv

load_dotenv()

client = OpenAI(
    base_url=os.getenv("_______"),
    api_key=os.getenv("API_KEY")
)

response = client.responses._______(
    model=os.getenv("MODEL_DEPLOYMENT_NAME"),
    input=[
        {"role": "system", "content": "You are a coding tutor."},
        {"role": "user", "content": "Explain loops."}
    ],
    temperature=0.5,
    max_output_tokens=200
)
print(response._______)
```

- A) `openai`, `AZURE_OPENAI_ENDPOINT`, `create`, `output_text`
- B) `azure`, `ENDPOINT_URL`, `generate`, `text`
- C) `openai`, `AZURE_OPENAI_ENDPOINT`, `send`, `response_text`
- D) `azure.openai`, `BASE_URL`, `create`, `output_text`

**Q17. [H] Code Output Prediction**
```python
import os
os.environ["TEST_VAR"] = "hello"
val = os.getenv("TEST_VAR_MISSING")
print(val)
```
What prints?

- A) `"hello"`
- B) `None`
- C) An empty string `""`
- D) A `KeyError` exception

**Q18. [M] Fill-in-the-Blank**
A developer wants the model to act as a pirate. Which message role should contain the instruction "You are a pirate. Respond in pirate speak."?

```python
input=[
    {"role": "_______", "content": "You are a pirate. Respond in pirate speak."},
    {"role": "user", "content": "Tell me about the weather."}
]
```

- A) `assistant`
- B) `system`
- C) `admin`
- D) `config`

**Q19. [H] Code Refactoring**
A developer wrote this code. Refactor it to follow best practices:
```python
from openai import OpenAI

client = OpenAI(
    base_url="https://myresource.openai.azure.com/openai/v1/",
    api_key="sk-abc123secretkey"
)
response = client.responses.create(
    model="gpt-4o",
    input=[{"role": "user", "content": "Hi"}]
)
```
Which refactored version follows best practices?

- A)
```python
from openai import OpenAI
import os
from dotenv import load_dotenv

load_dotenv()
client = OpenAI(
    base_url=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("API_KEY")
)
response = client.responses.create(
    model=os.getenv("MODEL_DEPLOYMENT_NAME"),
    input=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Hi"}
    ]
)
```

- B)
```python
from openai import OpenAI
client = OpenAI(
    base_url="https://myresource.openai.azure.com/openai/v1/",
    api_key="sk-abc123secretkey"
)
response = client.responses.create(
    model="gpt-4o",
    input="Hi"
)
```

- C)
```python
import openai
openai.api_key = "sk-abc123secretkey"
response = openai.responses.create(model="gpt-4o", input="Hi")
```

- D)
```python
from openai import OpenAI
import os
load_dotenv()
client = OpenAI(base_url=os.getenv("AZURE_OPENAI_ENDPOINT"))
response = client.responses.create(model="gpt-4o", input=[{"role": "user", "content": "Hi"}])
```

**Q20. [M] Error Handling**
What happens if you pass `model="nonexistent-deployment"` to `client.responses.create()`?

- A) The SDK silently returns an empty string
- B) The API returns an error (typically a 404 Not Found or similar) because the deployment does not exist
- C) The SDK automatically falls back to the default model
- D) Python crashes with a `SyntaxError`

**Q21. [M] Multiple Choice**
Which of the following are valid keys in a `.env` file for this SDK setup? (Select ALL that apply)

- A) `AZURE_OPENAI_ENDPOINT`
- B) `MODEL_DEPLOYMENT_NAME`
- C) `API_KEY`
- D) `TEMPERATURE`
- E) A, B, and C only

**Q22. [H] Code Output Prediction**
```python
from openai import OpenAI
import os
from dotenv import load_dotenv

load_dotenv()

client = OpenAI(
    base_url=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("API_KEY")
)

response = client.responses.create(
    model=os.getenv("MODEL_DEPLOYMENT_NAME"),
    input=[
        {"role": "system", "content": "You are a calculator. Only output numbers."},
        {"role": "user", "content": "What is 2+2?"}
    ],
    temperature=0,
    max_output_tokens=5
)

result = response.output_text
print(result.strip())
```
Given `temperature=0` and the system prompt, what is the most likely output?

- A) `"The answer is four"`
- B) `"4"`
- C) `"2+2=4"`
- D) `None`

**Q23. [M] Bug Finding**
```python
from openai import OpenAI
import os
from dotenv import load_dotenv

load_dotenv()

client = OpenAI(
    base_url=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("API_KEY")
)

response = client.responses.create(
    model=os.getenv("MODEL_DEPLOYMENT_NAME"),
    input=[
        {"role": "user", "content": "Hello"},
        {"role": "system", "content": "You are a helpful assistant."}
    ]
)
```
What is the issue with this code?

- A) There is no issue
- B) The system message should come before the user message in the input array
- C) You cannot have both system and user messages
- D) The `input` should be a tuple, not a list

**Q24. [H] Code Output Prediction**
```python
import os
from dotenv import load_dotenv

load_dotenv()

endpoint = os.getenv("AZURE_OPENAI_ENDPOINT")
deploy = os.getenv("MODEL_DEPLOYMENT_NAME")
key = os.getenv("API_KEY")

print(f"Connecting to {endpoint} with deployment {deploy}")
print(f"Key present: {key is not None}")
```
If the `.env` file contains all three variables correctly, what will the second `print` output?

- A) `Key present: True`
- B) `Key present: False`
- C) `Key present: None`
- D) An error

**Q25. [M] Multiple Correct Answers**
Which of the following are valid ways to influence the creativity/randomness of the model's output? (Select all that apply)

- A) Setting `temperature=0` for deterministic output
- B) Setting `temperature=1` for more creative output
- C) Changing the system prompt to say "Be creative"
- D) Setting `max_output_tokens=1000`

**Q26. [H] Bug Finding**
```python
from openai import OpenAI
import os
from dotenv import load_dotenv

load_dotenv()

client = OpenAI(
    base_url=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("API_KEY")
)

response = client.responses.create(
    model=os.getenv("MODEL_DEPLOYMENT_NAME"),
    input=[
        {"role": "system", "content": "You are helpful."},
        {"role": "user", "content": "Summarize this article."}
    ],
    temperature=2.5,
    max_output_tokens=500
)
```
What is wrong with this code?

- A) The `max_output_tokens` value is too low
- B) `temperature=2.5` is likely out of the valid range (typically 0 to 2); this may cause an API error
- C) The system message is too short
- D) `input` should be called `messages`

**Q27. [M] Fill-in-the-Blank**
To access the text of the model's response, you use:

```python
response = client.responses.create(...)
text = response._______
```

- A) `text`
- B) `output_text`
- C) `choices[0].message.content`
- D) `content`

**Q28. [M] Order the Steps**
Put these steps in the correct order to make an API call using the OpenAI SDK with Azure AI Foundry:

1. Call `client.responses.create()` with model, input, and parameters
2. Import `OpenAI` from `openai` and `load_dotenv` from `dotenv`
3. Access `response.output_text` to get the result
4. Create the `OpenAI` client with `base_url` and `api_key`
5. Call `load_dotenv()` and use `os.getenv()` to read configuration

- A) 2, 5, 4, 1, 3
- B) 2, 4, 5, 1, 3
- C) 5, 2, 4, 1, 3
- D) 4, 2, 5, 3, 1

---

### ANSWERS: Section B (Questions 13-28)

| # | Answer | Explanation |
|---|--------|-------------|
| 13 | **C) `<class 'str'>`** | `response.output_text` returns a string, even if the content is a number. The model outputs text. |
| 14 | **B)** | The `input` parameter expects a list of dictionaries with `role` and `content` keys, not a plain string. |
| 15 | **B)** | `load_dotenv()` is missing. Without calling it, `os.getenv()` cannot read values from the `.env` file and returns `None`. |
| 16 | **A)** | The correct imports, env var name, method, and response attribute are: `openai`, `AZURE_OPENAI_ENDPOINT`, `create`, `output_text`. |
| 17 | **B) `None`** | `os.getenv()` returns `None` when the environment variable does not exist, unlike `os.environ[]` which raises `KeyError`. |
| 18 | **B) `system`** | The system role defines the model's persona and behavioral instructions. |
| 19 | **A)** | Best practices: use `.env` + `load_dotenv()` for secrets, use `os.getenv()` for deployment name (since deployment name differs from model name), and include a system message. |
| 20 | **B)** | The API will return an error indicating the deployment was not found. The SDK does not silently handle missing deployments. |
| 21 | **E) A, B, and C only** | `AZURE_OPENAI_ENDPOINT`, `MODEL_DEPLOYMENT_NAME`, and `API_KEY` are the standard env vars. `TEMPERATURE` is set in code, not the `.env` file. |
| 22 | **B) `"4"`** | With `temperature=0` and a system prompt saying "Only output numbers," the model will return just `4`. |
| 23 | **B)** | The system message should appear first in the input array, before the user message, to properly set the model's behavior context. |
| 24 | **A) `Key present: True`** | If the `.env` file is properly configured, `os.getenv("API_KEY")` returns a string (not `None`), so `key is not None` evaluates to `True`. |
| 25 | **A, B, C** | Temperature directly controls randomness (A, B). The system prompt can also influence style (C). `max_output_tokens` controls length, not creativity (D is wrong). |
| 26 | **B)** | Temperature typically ranges from 0 to 2. A value of 2.5 is out of range and will likely cause an API validation error. |
| 27 | **B) `output_text`** | The Responses API returns the generated text via `response.output_text`. |
| 28 | **A) 2, 5, 4, 1, 3** | Import first, then load env vars, create client, make the API call, then read the response. |

---

## SECTION C: Prompt Engineering (Questions 29-38)

**Q29. [M] Scenario-Based**
A developer wants the model to translate English to French. They provide this input:
```python
input=[
    {"role": "user", "content": "Translate 'Hello, how are you?' to French."}
]
```
The model sometimes adds explanations along with the translation. How can the developer ensure ONLY the translation is returned?

- A) Set `temperature=0`
- B) Add a system message: `{"role": "system", "content": "You are a translator. Output only the translated text with no explanation."}`
- C) Set `max_output_tokens=1`
- D) Remove the user message

**Q30. [M] Few-Shot vs Zero-Shot**
Which of the following is a **few-shot** prompt?

- A)
```
Translate the following to Spanish: "Good morning"
```

- B)
```
Translate English to Spanish.
Example: "Hello" -> "Hola"
Example: "Goodbye" -> "Adios"
Now translate: "Good morning"
```

- C)
```
You are a translator.
```

- D)
```
What is the Spanish word for "Good morning"?
```

**Q31. [H] Scenario-Based**
A legal firm wants to use a generative AI model to summarize contracts. They need the model to:
- Never invent clauses that do not exist
- Use formal language
- Keep summaries under 200 words

Which combination of settings and prompts achieves this?

- A) `temperature=1`, no system prompt, `max_output_tokens=5000`
- B) `temperature=0`, system prompt: "You are a legal document summarizer. Summarize only what is present in the document. Use formal language.", `max_output_tokens=300`
- C) `temperature=0.5`, system prompt: "Be creative with legal summaries.", `max_output_tokens=300`
- D) `temperature=0`, no system prompt, `max_output_tokens=50`

**Q32. [M] Best Practice**
Which system prompt is most effective for building a customer support chatbot?

- A) `"You are a chatbot."`
- B) `"You are a friendly customer support agent for Contoso Electronics. Answer questions about product returns and warranties. If you don't know the answer, say 'Let me connect you to a human agent.' Do not discuss topics outside of Contoso products."`
- C) `"Answer questions."`
- D) `"You are an AI. Do whatever the user asks."`

**Q33. [M] True or False**
Few-shot prompting always produces better results than zero-shot prompting.

- A) True
- B) False

**Q34. [H] Multiple Correct Answers**
Which of the following are benefits of using a system prompt? (Select all that apply)

- A) Setting the model's persona and tone
- B) Restricting the topics the model will discuss
- C) Providing formatting instructions for the output
- D) Guaranteeing the model never makes mistakes
- E) Defining the language the model should respond in

**Q35. [M] Compare & Contrast**
Compare these two approaches for getting JSON output:

**Approach 1:** `"Return the data as JSON."`
**Approach 2:** `"Return the data as JSON with this exact format: {\"name\": \"...\", \"age\": ...}. Do not include any text outside the JSON object."`

- A) Both are equally effective
- B) Approach 2 is better because it specifies the exact format and constraints, reducing ambiguity
- C) Approach 1 is better because it gives the model more freedom
- D) Neither approach works with generative AI models

**Q36. [E] Multiple Choice**
In the context of prompt engineering, what does "grounding" a model mean?

- A) Connecting the model to the internet
- B) Providing the model with specific context or data to base its response on, reducing hallucinations
- C) Restarting the model
- D) Training the model from scratch

**Q37. [H] Scenario-Based**
A developer uses this prompt to generate product descriptions:
```python
input=[
    {"role": "system", "content": "You write product descriptions."},
    {"role": "user", "content": "Write a description for a blue wireless mouse."}
]
```
The output is inconsistent in length and style. What is the best way to improve consistency?

- A) Remove the system message entirely
- B) Enhance the system prompt with specific constraints: tone, word count, structure, and target audience
- C) Set `temperature=1` for more consistency
- D) Set `max_output_tokens=10000`

**Q38. [M] Order the Steps**
When designing an effective prompt, what is the recommended order?

1. Add examples (few-shot) if needed
2. Define the system persona and constraints
3. Test and iterate in Foundry Playground
4. Write the specific user request
5. Review output and adjust temperature/max_output_tokens

- A) 2, 4, 1, 3, 5
- B) 4, 2, 1, 3, 5
- C) 3, 2, 4, 1, 5
- D) 1, 2, 3, 4, 5

---

### ANSWERS: Section C (Questions 29-38)

| # | Answer | Explanation |
|---|--------|-------------|
| 29 | **B)** | A system message with explicit instructions to output only the translation is the most reliable way to constrain the model's behavior. |
| 30 | **B)** | Few-shot prompting includes examples of the expected input-output pattern before the actual request. Option B shows two translation examples before the task. |
| 31 | **B)** | Low temperature (0) reduces hallucination, the system prompt constrains behavior to factual summarization, and `max_output_tokens=300` roughly limits output length. |
| 32 | **B)** | An effective system prompt is specific: it names the company, defines the scope, instructs fallback behavior, and sets boundaries. |
| 33 | **B) False** | Few-shot is not always better. For simple tasks, zero-shot can work well. Few-shot adds token cost and sometimes introduces bias. It depends on the task complexity. |
| 34 | **A, B, C, E** | System prompts set persona (A), restrict topics (B), define formatting (C), and specify language (E). They cannot guarantee zero mistakes (D). |
| 35 | **B)** | Specific format instructions with an example structure give the model a clear target, leading to more consistent and parseable output. |
| 36 | **B)** | Grounding provides the model with relevant context or data to base its answers on, reducing the chance of fabricated (hallucinated) information. |
| 37 | **B)** | A detailed system prompt with tone, word count, structure, and audience constraints is the best way to achieve consistent outputs. |
| 38 | **A) 2, 4, 1, 3, 5** | Define persona first, write the request, add examples if needed, test in Playground, then tune parameters. |

---

## SECTION D: Scenarios & Architecture (Questions 39-47)

**Q39. [M] Scenario-Based**
A startup wants to build a customer FAQ bot. They have 50 common questions and answers. What is the most effective prompting approach?

- A) Zero-shot with no context
- B) Few-shot prompting with a selection of example Q&A pairs in the system/user messages
- C) Set `temperature=1` and hope for the best
- D) Train a brand new model from scratch

**Q40. [H] Scenario-Based**
A healthcare company wants to use Azure AI Foundry to help doctors draft patient notes. Which combination of decisions is most appropriate?

- A) Use `temperature=1` for creative medical notes; skip system prompt
- B) Use `temperature=0`, include a system prompt enforcing medical terminology standards, restrict output to note-taking format, and ensure the deployment is in a HIPAA-compliant Azure region
- C) Use the Foundry Playground in production to serve live patients
- D) Set `max_output_tokens=10` to keep notes brief

**Q41. [M] Configuration**
A developer has this `.env` file:
```
AZURE_OPENAI_ENDPOINT=https://contoso.openai.azure.com/openai/v1/
MODEL_DEPLOYMENT_NAME=contoso-gpt4o
API_KEY=abc123def456
```
In their code, they write `model="gpt-4o"`. Will this work?

- A) Yes, the model name and deployment name are the same thing
- B) No, they must use the deployment name `contoso-gpt4o`, not the model name `gpt-4o`
- C) Yes, Azure automatically resolves model names to deployments
- D) No, because the API key is wrong

**Q42. [M] Best Practice**
Which file should NEVER be committed to a Git repository?

- A) `app.py`
- B) `requirements.txt`
- C) `.env`
- D) `README.md`

**Q43. [H] Error Handling**
A developer's code raises an `AuthenticationError` when calling `client.responses.create()`. Which of the following could cause this? (Select all that apply)

- A) The `API_KEY` environment variable is empty or incorrect
- B) The `.env` file has a typo in the key name (e.g., `APIKEY` instead of `API_KEY`)
- C) The API key has been rotated/revoked in the Azure portal
- D) The `temperature` is set too high

**Q44. [M] Scenario-Based**
An e-commerce company wants to generate product descriptions in English, Spanish, and French from a single API call. What is the best approach?

- A) Make three separate API calls, one per language
- B) Use a system prompt: "You are a multilingual product description writer. For each product, output the description in English, Spanish, and French, clearly labeled."
- C) Set `temperature=3` to enable multilingual output
- D) This is not possible with generative AI

**Q45. [M] True or False**
The Foundry Model Catalog allows you to browse and compare models from multiple providers, not just OpenAI models.

- A) True
- B) False

**Q46. [H] Scenario-Based**
A developer is building a code review assistant. They want the model to:
- Only review Python code
- Point out bugs and suggest fixes
- Never write new features

Which system prompt is best?

- A) `"You review code."`
- B) `"You are a Python code review assistant. Analyze the provided Python code for bugs, errors, and improvements. Suggest fixes for each issue found. Do not add new features or functionality. If the code is not Python, respond with 'I only review Python code.'"`
- C) `"Write Python code for the user."`
- D) `"You are an AI."`

**Q47. [M] Multiple Choice**
Which of these is NOT a parameter of `client.responses.create()`?

- A) `model`
- B) `input`
- C) `temperature`
- D) `learning_rate`

---

### ANSWERS: Section D (Questions 39-47)

| # | Answer | Explanation |
|---|--------|-------------|
| 39 | **B)** | Few-shot with example Q&A pairs gives the model a pattern to follow, producing more accurate and consistent FAQ answers. |
| 40 | **B)** | Healthcare requires deterministic output (temp=0), strict formatting via system prompts, and compliance considerations. Playground is for testing, not production. |
| 41 | **B)** | You must use the deployment name (`contoso-gpt4o`), not the base model name (`gpt-4o`). Deployment name is what you set during provisioning. |
| 42 | **C)** | `.env` files contain secrets (API keys, endpoints) and must be in `.gitignore`, never committed to source control. |
| 43 | **A, B, C** | All three cause authentication failures. An empty/wrong key (A), a typo in the env var name so it reads `None` (B), and a revoked key (C) all fail auth. Temperature (D) does not affect authentication. |
| 44 | **B)** | A well-crafted system prompt can instruct the model to produce multilingual output in a single call, which is both efficient and effective. |
| 45 | **A) True** | The Model Catalog in Azure AI Foundry includes models from OpenAI, Meta (Llama), Mistral, Microsoft, and other providers. |
| 46 | **B)** | This system prompt is specific about scope (Python only), task (review, not write), and includes an explicit boundary for non-Python input. |
| 47 | **D) `learning_rate`** | `learning_rate` is a training parameter, not an inference/API call parameter. The Responses API accepts `model`, `input`, `temperature`, `max_output_tokens`, etc. |

---

## SECTION E: Advanced & Edge Cases (Questions 48-55)

**Q48. [H] Error Handling**
What happens if `max_output_tokens` is set to a value larger than the model's context window allows for output?

- A) The model ignores the parameter silently
- B) The API may return an error or the model will simply stop at its maximum capacity
- C) The model generates infinite text
- D) The parameter is automatically reduced to 100

**Q49. [H] Code Refactoring**
A developer has duplicated API call logic in 5 different files. What is the best refactoring approach?

- A) Keep the duplication for readability
- B) Create a helper function that accepts the user prompt and optional parameters, then reuse it across files
- C) Copy-paste is a valid software engineering pattern
- D) Delete 4 of the 5 files

**Q50. [H] Edge Case**
```python
response = client.responses.create(
    model=os.getenv("MODEL_DEPLOYMENT_NAME"),
    input=[
        {"role": "system", "content": ""},
        {"role": "user", "content": "Hello"}
    ],
    temperature=0
)
```
What happens when the system prompt content is an empty string?

- A) The API raises an error because system content cannot be empty
- B) The model behaves as if no system prompt was provided, using its default behavior
- C) The model returns an empty response
- D) Python raises a `TypeError`

**Q51. [H] Multiple Correct Answers**
Which of the following are true about the Responses API? (Select all that apply)

- A) It is described as the modern unified API for Azure OpenAI
- B) It uses `response.output_text` to access generated text
- C) It requires the `model` parameter to specify a deployment name
- D) It can only be used with GPT-4 models
- E) The `input` parameter accepts a list of role/content dictionaries

**Q52. [H] Scenario-Based**
A company deploys two models in Azure AI Foundry:
- `fast-model` (GPT-4o-mini, low cost, faster)
- `quality-model` (GPT-4o, higher cost, better quality)

For a real-time customer chat feature where speed matters but quality is acceptable, which deployment should they use and why?

- A) `quality-model` because quality always matters most
- B) `fast-model` because real-time chat prioritizes low latency and the quality is acceptable for conversational use
- C) Both simultaneously in every request
- D) Neither; they should use the Foundry Playground instead

**Q53. [H] Bug Finding**
```python
from openai import OpenAI
import os
from dotenv import load_dotenv

load_dotenv()

client = OpenAI(
    base_url=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("API_KEY")
)

messages = []
messages.append({"role": "system", "content": "You are helpful."})
messages.append({"role": "user", "content": "What is 1+1?"})

response = client.responses.create(
    model=os.getenv("MODEL_DEPLOYMENT_NAME"),
    input=messages,
    temperature=0,
    max_output_tokens=10
)

answer = response.output_text
messages.append({"role": "assistant", "content": answer})
messages.append({"role": "user", "content": "Now add 3 to that."})

response2 = client.responses.create(
    model=os.getenv("MODEL_DEPLOYMENT_NAME"),
    input=messages,
    temperature=0,
    max_output_tokens=10
)
print(response2.output_text)
```
This code attempts multi-turn conversation. Is there a bug?

- A) Yes, you cannot reuse the `messages` list
- B) Yes, the second call should use a different client
- C) No, this is a correct pattern for maintaining conversation context by appending messages and resending the full history
- D) Yes, `temperature=0` prevents multi-turn conversations

**Q54. [H] Configuration**
A developer needs to switch from a test deployment to a production deployment. Which single change is sufficient if the code uses environment variables correctly?

- A) Rewrite all Python files with the new deployment name
- B) Update the `MODEL_DEPLOYMENT_NAME` value in the `.env` file (and `AZURE_OPENAI_ENDPOINT` / `API_KEY` if the resource differs)
- C) Reinstall the `openai` pip package
- D) Change the `temperature` parameter

**Q55. [H] Scenario-Based**
A school wants students to practice math by chatting with an AI tutor. The AI should:
- Only discuss math topics
- Show step-by-step solutions
- Use encouraging language
- Never give the final answer without showing work

Which configuration achieves this?

- A)
```python
input=[{"role": "user", "content": "Solve 5x + 3 = 18"}]
temperature=1
```

- B)
```python
input=[
    {"role": "system", "content": "You are a friendly math tutor for students. Only discuss math topics. Always show step-by-step solutions before giving the final answer. Use encouraging language like 'Great question!' and 'You're on the right track!' If asked about non-math topics, politely redirect to math."},
    {"role": "user", "content": "Solve 5x + 3 = 18"}
]
temperature=0.3
max_output_tokens=500
```

- C)
```python
input=[
    {"role": "system", "content": "You are an AI."},
    {"role": "user", "content": "Solve 5x + 3 = 18 step by step"}
]
temperature=0
```

- D)
```python
input=[{"role": "user", "content": "Math tutor: solve 5x + 3 = 18"}]
temperature=0.5
```

---

### ANSWERS: Section E (Questions 48-55)

| # | Answer | Explanation |
|---|--------|-------------|
| 48 | **B)** | The API either returns a validation error or the model generates up to its actual limit and stops. It does not produce infinite output. |
| 49 | **B)** | A shared helper function (e.g., `def call_model(user_prompt, system_prompt, temp, max_tokens)`) reduces duplication and makes changes easier. |
| 50 | **B)** | An empty system prompt is generally accepted; the model proceeds as if no behavioral instruction was given, using its default persona. |
| 51 | **A, B, C, E** | The Responses API is the modern unified API (A), uses `output_text` (B), requires a deployment name for `model` (C), and takes a list of role/content dicts for `input` (E). It is not limited to GPT-4 (D is false). |
| 52 | **B)** | For real-time chat where latency matters, the faster, lower-cost model is the pragmatic choice when quality meets the threshold. |
| 53 | **C)** | This is the correct multi-turn pattern: append the assistant's response and the new user message to the list, then send the full history. No bug here. |
| 54 | **B)** | Since the code reads configuration from environment variables, updating the `.env` file is the only change needed. This is a key benefit of externalizing configuration. |
| 55 | **B)** | Option B has a detailed system prompt covering all requirements (math only, step-by-step, encouraging, redirect non-math), moderate temperature for natural language, and reasonable token limit. |

---

## SCORING GUIDE

| Score | Grade | Assessment |
|-------|-------|------------|
| 50-55 correct (91-100%) | **Expert** | You have a thorough understanding of Azure AI Foundry, the OpenAI SDK, and prompt engineering. Exam-ready. |
| 44-49 correct (80-89%) | **Proficient** | Solid grasp of the fundamentals with good practical knowledge. Review missed topics. |
| 33-43 correct (60-79%) | **Developing** | You understand the basics but need to strengthen code-level and scenario-based knowledge. |
| 22-32 correct (40-59%) | **Foundational** | Review SDK documentation, practice writing code, and study prompt engineering patterns. |
| Below 22 (< 40%) | **Beginning** | Start with the fundamentals: read the Azure AI Foundry docs, set up a local dev environment, and work through official tutorials. |

**Key Topics to Review If You Scored Below 80%:**
- **Sections A/B weak:** Focus on SDK mechanics -- `OpenAI` client setup, `.env` configuration, `responses.create()` parameters, and `output_text` access pattern.
- **Section C weak:** Study prompt engineering -- system vs. user roles, few-shot vs. zero-shot, and how temperature affects output.
- **Section D weak:** Practice scenario analysis -- matching business requirements to technical configurations.
- **Section E weak:** Build real projects -- multi-turn conversations, error handling, and deployment management.

---

*Practice exam aligned with AI-901 objectives: Generative AI Models & OpenAI SDK in Microsoft Foundry*
