# AI-901 Foundry Implementation & Coding Questions

> **Focus:** Domain 2 (55-60% of exam) - Real Azure service names, SDKs, Python code, and implementation details.

---

## SECTION 1: Generative AI - Foundry SDK & OpenAI API (20 Questions)

**Q1.** Which Python package do you install to interact with generative AI models deployed in Microsoft Foundry?

- A) `pip install tensorflow`
- B) `pip install openai`
- C) `pip install boto3`
- D) `pip install transformers`

---

**Q2.** What is the correct way to create an OpenAI client for a model deployed in Microsoft Foundry?

- A)
```python
from openai import OpenAI
client = OpenAI(
    base_url=f"{os.environ['AZURE_OPENAI_ENDPOINT']}/openai",
    api_key=os.environ["AZURE_OPENAI_API_KEY"]
)
```
- B)
```python
from tensorflow import OpenAI
client = OpenAI(key="my-key")
```
- C)
```python
import openai
openai.connect("azure")
```
- D)
```python
from azure.storage import OpenAI
client = OpenAI()
```

---

**Q3.** Which API is the modern, unified way to interact with language models in Azure OpenAI?

- A) Completions API
- B) Embeddings API
- C) **Responses API**
- D) Predictions API

---

**Q4.** Look at this code. What does `temperature=0.7` control?

```python
response = client.responses.create(
    model="gpt-4.1-mini",
    input=[{"role": "user", "content": "Write a poem"}],
    max_output_tokens=300,
    temperature=0.7
)
```

- A) The speed of the response
- B) The creativity/randomness of the output (0.7 = moderately creative)
- C) The number of responses returned
- D) The language of the output

---

**Q5.** In the code below, what is `max_output_tokens=300` doing?

```python
response = client.responses.create(
    model="gpt-4.1-mini",
    input=[{"role": "user", "content": "Summarize this article"}],
    max_output_tokens=300,
    temperature=0.5
)
```

- A) Limits the input to 300 words
- B) Caps the response length to a maximum of 300 tokens
- C) Sets the number of retries to 300
- D) Limits the model to 300 parameters

---

**Q6.** What does `response.output_text` return?

```python
response = client.responses.create(
    model="gpt-4.1-mini",
    input=[{"role": "user", "content": "What is Azure?"}],
)
print(response.output_text)
```

- A) The raw JSON response
- B) The generated text response from the model
- C) The model's configuration
- D) The API key

---

**Q7.** What is the difference between the `system` role and the `user` role in the input messages?

```python
input=[
    {"role": "system", "content": "You are a helpful travel assistant."},
    {"role": "user", "content": "Where should I visit in Japan?"}
]
```

- A) They are the same thing
- B) `system` defines the AI's behavior/rules; `user` is the actual question from the end user
- C) `system` is the user's question; `user` is the AI's response
- D) `system` sets the language; `user` sets the format

---

**Q8.** You deployed a model named `gpt-4.1` in the Foundry portal but gave it the deployment name `my-demo-model`. What value should you pass as the `model` parameter in your code?

- A) `gpt-4.1`
- B) `my-demo-model`
- C) `azure-gpt-4.1`
- D) `openai/gpt-4.1`

---

**Q9.** What is the purpose of a `.env` file in a Foundry client application?

```
AZURE_OPENAI_ENDPOINT=https://myresource.openai.azure.com/openai/v1/
MODEL_DEPLOYMENT_NAME=gpt-4.1-mini
API_KEY=abc123xyz
```

- A) It stores the model's training data
- B) It stores environment variables like endpoint, key, and deployment name securely outside the code
- C) It contains the application's main logic
- D) It stores the model weights locally

---

**Q10.** Which Python package is used to load environment variables from a `.env` file?

- A) `os`
- B) `dotenv` (using `load_dotenv()`)
- C) `json`
- D) `yaml`

---

**Q11.** What does `os.getenv("API_KEY")` do in this code?

```python
from dotenv import load_dotenv
import os
load_dotenv()
api_key = os.getenv("API_KEY")
```

- A) Creates a new API key
- B) Retrieves the value of the `API_KEY` environment variable
- C) Encrypts the API key
- D) Deletes the API key

---

**Q12.** You want the AI to always respond in bullet points and never give medical advice. Where should you put these instructions?

- A) In the user prompt
- B) In the system prompt/instructions
- C) In the `.env` file
- D) In the `temperature` parameter

---

**Q13.** What is a "lightweight client application" in the context of AI-901?

- A) An app with a fancy GUI framework
- B) A small Python script that connects to a Foundry endpoint, sends prompts via SDK/API, and displays results
- C) A mobile application
- D) A machine learning training pipeline

---

**Q14.** Which Foundry portal feature lets you test prompts interactively WITHOUT writing any code?

- A) Model Catalog
- B) Foundry Playground
- C) Azure Monitor
- D) Azure DevOps

---

**Q15.** What does the Foundry **Model Catalog** allow you to do?

- A) Train models from scratch
- B) Browse, compare, and select available AI models for deployment
- C) Delete Azure subscriptions
- D) Monitor network traffic

---

**Q16.** What is the correct endpoint format for an Azure OpenAI resource?

- A) `https://myresource.blob.core.windows.net`
- B) `https://myresource.openai.azure.com/openai/v1/`
- C) `https://myresource.azurewebsites.net`
- D) `https://openai.com/api/v1/`

---

**Q17.** If you call the same prompt twice with `temperature=0.8`, will you get the same response?

- A) Yes, always identical
- B) No, responses may vary because temperature > 0 introduces randomness
- C) Yes, unless you change the model
- D) No, because the API key changes

---

**Q18.** What happens if you set `temperature=0`?

- A) The model refuses to respond
- B) The model produces the most deterministic, consistent responses
- C) The model produces the most creative responses
- D) The model crashes

---

**Q19.** Which method on the OpenAI client do you use to send a prompt and get a response?

- A) `client.chat.send()`
- B) `client.responses.create()`
- C) `client.model.predict()`
- D) `client.generate.text()`

---

**Q20.** In the Foundry Playground, what does the "code" button do?

- A) Deletes your deployment
- B) Shows you the Python code equivalent of your Playground settings and prompts so you can copy it into your app
- C) Opens Visual Studio Code
- D) Compiles the model

---

### Section 1 Answers

| Q | Answer | Explanation |
|---|--------|-------------|
| 1 | **B** | `pip install openai` - the OpenAI Python library is used for Foundry models |
| 2 | **A** | Create `OpenAI` client with `base_url` (endpoint) and `api_key` |
| 3 | **C** | The **Responses API** is the modern unified API for Azure OpenAI |
| 4 | **B** | Temperature 0.7 = moderately creative (0=focused, 1=max creative) |
| 5 | **B** | `max_output_tokens` caps the response length |
| 6 | **B** | `output_text` returns the model's generated text response |
| 7 | **B** | `system` = AI behavior/rules; `user` = the actual question |
| 8 | **B** | Use the **deployment name** you gave it, not the base model name |
| 9 | **B** | `.env` stores config variables securely outside the source code |
| 10 | **B** | `dotenv` package with `load_dotenv()` loads `.env` files |
| 11 | **B** | `os.getenv()` retrieves the value of an environment variable |
| 12 | **B** | Behavior rules go in the **system prompt** |
| 13 | **B** | A small Python script that calls Foundry APIs and displays results |
| 14 | **B** | **Foundry Playground** is the no-code testing interface |
| 15 | **B** | Model Catalog lets you browse, compare, and deploy models |
| 16 | **B** | `https://<resource>.openai.azure.com/openai/v1/` |
| 17 | **B** | Temperature > 0 means responses can vary between calls |
| 18 | **B** | Temperature 0 = most deterministic and consistent output |
| 19 | **B** | `client.responses.create()` is the method to call |
| 20 | **B** | Shows equivalent Python code for your Playground settings |

---

## SECTION 2: AI Agents in Foundry (15 Questions)

**Q21.** Which TWO Python packages must you install to build a client app that calls a Foundry agent?

- A) `pip install azure-ai-projects` and `pip install azure-identity`
- B) `pip install tensorflow` and `pip install keras`
- C) `pip install flask` and `pip install django`
- D) `pip install boto3` and `pip install aws-cli`

---

**Q22.** What class do you use to connect to a Foundry project for agent operations?

- A) `AzureBlobClient`
- B) `AIProjectClient`
- C) `OpenAI`
- D) `SpeechConfig`

---

**Q23.** Look at this code. What does `project_client.agents.get(agent_name=myAgent)` do?

```python
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential

project_client = AIProjectClient(
    endpoint=myEndpoint,
    credential=DefaultAzureCredential(),
)
agent = project_client.agents.get(agent_name="learning-agent")
```

- A) Creates a new agent
- B) Retrieves an existing agent by its name
- C) Deletes the agent
- D) Deploys a new model

---

**Q24.** What authentication method does `DefaultAzureCredential()` use?

- A) Only API keys
- B) Automatically tries multiple Azure authentication methods (Azure CLI, managed identity, etc.)
- C) Username and password only
- D) No authentication

---

**Q25.** In Foundry, an agent is made up of which THREE components?

- A) Database, Storage, Network
- B) Model, Instructions (system prompt), Tools
- C) CPU, RAM, Disk
- D) HTML, CSS, JavaScript

---

**Q26.** What are "Tools" in a Foundry agent?

- A) Physical hardware
- B) Callable capabilities that let the agent perform actions (search, run code, call APIs)
- C) The model's training data
- D) Azure billing features

---

**Q27.** What is "Knowledge" in a Foundry agent?

- A) The model's parameters
- B) Documents/datasets provided to the agent for retrieval-augmented generation (RAG)
- C) The agent's source code
- D) Azure storage containers

---

**Q28.** How do you call a Foundry agent from Python code?

```python
openai_client = project_client.get_openai_client()
response = openai_client.responses.create(
    input=[{"role": "user", "content": "Help me plan a trip"}],
    extra_body={"agent": {"name": agent.name, "type": "agent_reference"}},
)
```

What does `extra_body={"agent": ...}` do?

- A) Sets the temperature
- B) References a specific agent by name so the request is handled by that agent
- C) Creates a new agent
- D) Deletes the agent

---

**Q29.** Where in the Foundry portal can you find an agent's `agent-id`?

- A) Azure Monitor
- B) In the Playground view of the agent, under the code view / .env variables
- C) In the billing section
- D) In Azure Active Directory

---

**Q30.** Which of the following is an example of a Foundry agent tool?

- A) Code Interpreter
- B) Knowledge sources (RAG)
- C) Custom functions/APIs
- D) All of the above

---

**Q31.** What is the difference between using a **model directly** vs. using an **agent** in Foundry?

- A) No difference
- B) Model = raw inference ("take prompt, generate output"); Agent = packaged worker with instructions, tools, and reusable behavior
- C) Agent is cheaper
- D) Model is more powerful

---

**Q32.** When an agent uses Knowledge (RAG) to answer a question, what is included in the response?

- A) Only the answer text
- B) The answer text plus citations referencing the source documents
- C) The raw document files
- D) The model's training data

---

**Q33.** What does the **Foundry Tool Catalog** do?

- A) Stores models
- B) Lets you discover and manage tools that agents can use
- C) Manages billing
- D) Creates virtual machines

---

**Q34.** You want to create an agent that can execute Python code to analyze uploaded CSV files. Which tool should you add?

- A) Web Search
- B) Code Interpreter
- C) Azure Blob Storage
- D) Text-to-Speech

---

**Q35.** What package provides `DefaultAzureCredential`?

- A) `azure-ai-projects`
- B) `azure-identity`
- C) `openai`
- D) `azure-storage-blob`

---

### Section 2 Answers

| Q | Answer | Explanation |
|---|--------|-------------|
| 21 | **A** | `azure-ai-projects` + `azure-identity` for agent client apps |
| 22 | **B** | `AIProjectClient` connects to Foundry projects |
| 23 | **B** | `.agents.get()` retrieves an existing agent by name |
| 24 | **B** | `DefaultAzureCredential` auto-tries multiple auth methods |
| 25 | **B** | Agent = Model + Instructions + Tools |
| 26 | **B** | Tools = callable actions (APIs, code interpreter, search) |
| 27 | **B** | Knowledge = documents/datasets for RAG grounding |
| 28 | **B** | `extra_body` references a specific agent to handle the request |
| 29 | **B** | Agent ID is in Playground > code view > .env variables |
| 30 | **D** | All of these are valid agent tools |
| 31 | **B** | Model = raw inference; Agent = packaged worker with tools |
| 32 | **B** | RAG responses include citations to source documents |
| 33 | **B** | Tool Catalog = discover and manage agent tools |
| 34 | **B** | Code Interpreter executes code and handles files |
| 35 | **B** | `azure-identity` provides `DefaultAzureCredential` |

---

## SECTION 3: Azure Language in Foundry Tools - Text Analysis (15 Questions)

**Q36.** Which Python package do you install for Azure Language text analysis SDK?

- A) `pip install azure-cognitiveservices-speech`
- B) `pip install azure-ai-textanalytics`
- C) `pip install openai`
- D) `pip install azure-storage-blob`

---

**Q37.** What class do you use to create a text analytics client?

```python
from azure.ai.textanalytics import TextAnalyticsClient
from azure.core.credentials import AzureKeyCredential

client = TextAnalyticsClient(
    endpoint=endpoint,
    credential=AzureKeyCredential(key)
)
```

- A) `OpenAI`
- B) `TextAnalyticsClient`
- C) `SpeechRecognizer`
- D) `AIProjectClient`

---

**Q38.** What does `AzureKeyCredential(key)` do in the code above?

- A) Encrypts the text
- B) Wraps your API key into a credential object for authentication
- C) Creates a new API key
- D) Deletes the resource

---

**Q39.** Which method detects the language of text using the Azure Language SDK?

```python
result = client.detect_language(["Bonjour, comment allez-vous?"])[0]
print(result.primary_language.name)
print(result.primary_language.iso6391_name)
print(result.primary_language.confidence_score)
```

- A) `client.analyze_sentiment()`
- B) `client.detect_language()`
- C) `client.extract_key_phrases()`
- D) `client.recognize_entities()`

---

**Q40.** What does `result.primary_language.iso6391_name` return?

- A) The full language name (e.g., "French")
- B) The ISO 639-1 language code (e.g., "fr")
- C) The confidence score
- D) The original text

---

**Q41.** Which method detects personally identifiable information (PII) in text?

- A) `client.detect_language()`
- B) `client.recognize_pii_entities()`
- C) `client.analyze_sentiment()`
- D) `client.extract_key_phrases()`

---

**Q42.** What does `result.redacted_text` contain after calling `recognize_pii_entities()`?

```python
text = "Maria called from 020 7946 0958"
result = client.recognize_pii_entities([text])[0]
print(result.redacted_text)
```

- A) The original text unchanged
- B) The text with PII replaced by asterisks (e.g., "***** called from ************")
- C) An empty string
- D) The detected entities only

---

**Q43.** What is the endpoint format for Azure Language in Foundry Tools?

- A) `https://<resource>.openai.azure.com/`
- B) `https://<resource>.cognitiveservices.azure.com/`
- C) `https://<resource>.blob.core.windows.net/`
- D) `https://<resource>.azurewebsites.net/`

---

**Q44.** When should you use the **Azure Language SDK** instead of the **OpenAI API** for text analysis?

- A) When you need creative writing
- B) When you need consistent, structured output values (language codes, confidence scores, redacted text)
- C) When you want to generate images
- D) When you need speech recognition

---

**Q45.** What does `confidence_score` represent in Azure Language SDK results?

- A) The cost of the API call
- B) A value between 0 and 1 indicating how confident the service is in its result
- C) The number of characters analyzed
- D) The response time in seconds

---

**Q46.** You need to find all person names, organization names, and locations in a document. Which Azure Language SDK method should you use?

- A) `client.detect_language()`
- B) `client.recognize_entities()`
- C) `client.recognize_pii_entities()`
- D) `client.analyze_sentiment()`

---

**Q47.** What does the `[0]` do in `client.detect_language([text])[0]`?

- A) Sets the language to English
- B) Gets the first result from the returned list (since the SDK accepts a list of documents)
- C) Selects the first word
- D) Sets confidence threshold to 0

---

**Q48.** Which TWO approaches can you use for text analysis in Microsoft Foundry?

- A) OpenAI Responses API (general-purpose model) AND Azure Language SDK (dedicated NLP service)
- B) Azure Blob Storage AND Azure SQL
- C) TensorFlow AND PyTorch
- D) Azure Monitor AND Azure DevOps

---

**Q49.** What is the key difference between OpenAI API and Azure Language SDK for text analysis?

- A) OpenAI is free, Language SDK costs money
- B) OpenAI results can vary between calls (probabilistic); Language SDK returns consistent, structured values
- C) They produce identical results
- D) Language SDK only works with English

---

**Q50.** What is the `entity.category` field in PII detection results?

- A) The redacted text
- B) The type of PII detected (e.g., "PhoneNumber", "Address", "PersonName")
- C) The confidence score
- D) The language code

---

### Section 3 Answers

| Q | Answer | Explanation |
|---|--------|-------------|
| 36 | **B** | `pip install azure-ai-textanalytics` for Azure Language SDK |
| 37 | **B** | `TextAnalyticsClient` is the main class for text analysis |
| 38 | **B** | `AzureKeyCredential` wraps the API key for auth |
| 39 | **B** | `client.detect_language()` detects the language of text |
| 40 | **B** | `iso6391_name` returns the ISO code like "fr", "en", "es" |
| 41 | **B** | `client.recognize_pii_entities()` detects PII |
| 42 | **B** | `redacted_text` has PII replaced with asterisks |
| 43 | **B** | `https://<resource>.cognitiveservices.azure.com/` |
| 44 | **B** | Use Language SDK when you need structured, consistent results |
| 45 | **B** | Confidence score = 0 to 1 indicating result confidence |
| 46 | **B** | `recognize_entities()` for NER (people, orgs, locations) |
| 47 | **B** | `[0]` gets the first result since SDK accepts a list of docs |
| 48 | **A** | Two approaches: OpenAI API (general) + Language SDK (dedicated) |
| 49 | **B** | OpenAI = probabilistic/varying; Language SDK = consistent/structured |
| 50 | **B** | `entity.category` = the type of PII (PhoneNumber, Address, etc.) |

---

## SECTION 4: Azure Speech in Foundry Tools (15 Questions)

**Q51.** What is the exact Azure service name for speech-to-text and text-to-speech?

- A) Azure Translator
- B) **Azure Speech** (with Speech-to-Text API and Text-to-Speech API)
- C) Azure Language
- D) Azure Content Understanding

---

**Q52.** Which Python package do you install for Azure Speech SDK?

- A) `pip install openai`
- B) `pip install azure-ai-textanalytics`
- C) `pip install azure-cognitiveservices-speech`
- D) `pip install azure-ai-projects`

---

**Q53.** What class do you use to configure the Azure Speech service?

```python
import azure.cognitiveservices.speech as speechsdk
speech_config = speechsdk.SpeechConfig(
    subscription=speech_key,
    endpoint=endpoint_url
)
```

- A) `OpenAI`
- B) `TextAnalyticsClient`
- C) `speechsdk.SpeechConfig`
- D) `AIProjectClient`

---

**Q54.** What class performs speech-to-text (speech recognition)?

- A) `speechsdk.SpeechSynthesizer`
- B) `speechsdk.SpeechRecognizer`
- C) `TextAnalyticsClient`
- D) `OpenAI`

---

**Q55.** What class performs text-to-speech (speech synthesis)?

- A) `speechsdk.SpeechRecognizer`
- B) `speechsdk.SpeechSynthesizer`
- C) `TextAnalyticsClient`
- D) `AIProjectClient`

---

**Q56.** Look at this code. What does `use_default_microphone=True` do?

```python
audio_config = speechsdk.audio.AudioConfig(use_default_microphone=True)
speech_recognizer = speechsdk.SpeechRecognizer(
    speech_config=speech_config,
    audio_config=audio_config
)
```

- A) Plays audio through speakers
- B) Captures audio input from the computer's default microphone for speech recognition
- C) Records audio to a file
- D) Mutes the microphone

---

**Q57.** What does `use_default_speaker=True` do in text-to-speech?

```python
audio_config = speechsdk.audio.AudioOutputConfig(use_default_speaker=True)
speech_synthesizer = speechsdk.SpeechSynthesizer(
    speech_config=speech_config,
    audio_config=audio_config
)
```

- A) Records from microphone
- B) Plays the synthesized speech audio through the computer's default speaker
- C) Saves to a file
- D) Streams to the cloud

---

**Q58.** How do you set the voice for text-to-speech?

```python
speech_config.speech_synthesis_voice_name = 'en-US-Ava:DragonHDLatestNeural'
```

What does this line do?

- A) Sets the language to detect
- B) Selects a specific neural voice (Ava, US English, HD neural) for speech synthesis
- C) Sets the speech recognition language
- D) Changes the model deployment

---

**Q59.** What method starts continuous speech recognition?

- A) `speech_recognizer.recognize_once()`
- B) `speech_recognizer.start_continuous_recognition()`
- C) `speech_recognizer.listen()`
- D) `speech_recognizer.transcribe()`

---

**Q60.** What method converts text to spoken audio asynchronously?

- A) `speech_synthesizer.speak_text_async(text).get()`
- B) `speech_synthesizer.recognize(text)`
- C) `speech_synthesizer.convert(text)`
- D) `speech_synthesizer.read(text)`

---

**Q61.** What does `evt.result.text` contain in this event handler?

```python
def recognized_handler(evt):
    print(f"Recognized: {evt.result.text}")

speech_recognizer.recognized.connect(recognized_handler)
```

- A) The audio waveform
- B) The transcribed text from recognized speech
- C) The API key
- D) The model name

---

**Q62.** What is the difference between `recognizing` and `recognized` events?

- A) They are the same
- B) `recognizing` = interim/partial results while still speaking; `recognized` = final result after speech is complete
- C) `recognizing` is for TTS; `recognized` is for STT
- D) `recognizing` starts; `recognized` stops

---

**Q63.** How does `ResultReason.SynthesizingAudioCompleted` help in error handling?

```python
if speech_synthesis_result.reason == speechsdk.ResultReason.SynthesizingAudioCompleted:
    print("Speech synthesized successfully")
elif speech_synthesis_result.reason == speechsdk.ResultReason.Canceled:
    print("Speech synthesis canceled")
```

- A) It checks if the model was deployed
- B) It confirms that text-to-speech audio was successfully generated
- C) It checks the network connection
- D) It validates the API key

---

**Q64.** What are the TWO types of speech-to-text transcription?

- A) Fast and slow
- B) **Real-time transcription** (live audio stream/microphone) and **Batch transcription** (pre-recorded audio files)
- C) English and multilingual
- D) Free and paid

---

**Q65.** You need to transcribe thousands of pre-recorded customer service calls stored in Azure Blob Storage. Which transcription type should you use?

- A) Real-time transcription
- B) Batch transcription
- C) Live captioning
- D) Speech translation

---

### Section 4 Answers

| Q | Answer | Explanation |
|---|--------|-------------|
| 51 | **B** | **Azure Speech** with Speech-to-Text API and Text-to-Speech API |
| 52 | **C** | `pip install azure-cognitiveservices-speech` |
| 53 | **C** | `speechsdk.SpeechConfig` configures the speech service |
| 54 | **B** | `speechsdk.SpeechRecognizer` does speech-to-text |
| 55 | **B** | `speechsdk.SpeechSynthesizer` does text-to-speech |
| 56 | **B** | Captures audio from the default microphone |
| 57 | **B** | Plays synthesized audio through the default speaker |
| 58 | **B** | Selects a specific neural voice for TTS |
| 59 | **B** | `start_continuous_recognition()` for ongoing STT |
| 60 | **A** | `speak_text_async(text).get()` for async TTS |
| 61 | **B** | `evt.result.text` = the transcribed text |
| 62 | **B** | `recognizing` = partial; `recognized` = final |
| 63 | **B** | Confirms TTS audio was successfully generated |
| 64 | **B** | Real-time (live) and Batch (pre-recorded files) |
| 65 | **B** | Batch transcription for large volumes of stored audio |

---

## SECTION 5: Vision, Content Understanding & Mixed Scenarios (15 Questions)

**Q66.** To send an image along with a text prompt to a deployed model, you use a:

- A) Speech model
- B) Text-only model
- C) **Multimodal model** that accepts both text and image input
- D) Image generation model

---

**Q67.** What is **Azure Content Understanding** in Foundry Tools used for?

- A) Only text analysis
- B) Extracting structured information from documents, forms, images, audio, and video
- C) Speech recognition only
- D) Model deployment

---

**Q68.** A company has thousands of scanned invoices. They need to extract vendor name, date, and total. Which service should they use?

- A) Azure Language
- B) Azure Speech
- C) **Azure Content Understanding** in Foundry Tools
- D) OpenAI Responses API

---

**Q69.** Match each Azure service to its SDK package:

| Service | Package |
|---------|---------|
| Generative AI models | ? |
| Text analysis (NLP) | ? |
| Speech (STT/TTS) | ? |
| Agent client apps | ? |

- A) `openai` / `azure-ai-textanalytics` / `azure-cognitiveservices-speech` / `azure-ai-projects`
- B) `tensorflow` / `spacy` / `pydub` / `flask`
- C) `azure-storage` / `azure-sql` / `azure-network` / `azure-compute`
- D) All use `openai` package

---

**Q70.** Match each class to its purpose:

| Class | Purpose |
|-------|---------|
| `OpenAI` | ? |
| `TextAnalyticsClient` | ? |
| `SpeechRecognizer` | ? |
| `SpeechSynthesizer` | ? |
| `AIProjectClient` | ? |

- A) Generative AI / NLP text analysis / Speech-to-Text / Text-to-Speech / Agent project management
- B) All do the same thing
- C) Database / Storage / Compute / Network / Identity
- D) None of the above

---

**Q71.** You are building a voice assistant. The user speaks, the AI processes the question using enterprise data, and responds with speech. Fill in the services:

1. User speaks → **___** converts to text
2. Text goes to **___** for RAG-based answer
3. Answer text converted to audio by **___**

- A) Azure Speech (STT) → Foundry IQ (RAG) + Generative model → Azure Speech (TTS)
- B) Azure Language → Azure Blob → Azure Monitor
- C) Content Understanding → OpenAI → Azure Speech
- D) Azure Speech (TTS) → Azure Language → Azure Speech (STT)

---

**Q72.** What is the correct order of steps to build a Foundry AI application?

- A) Write code → Deploy model → Create resource
- B) Create Foundry resource → Create project → Deploy model from catalog → Test in Playground → Build client app with SDK
- C) Install Python → Run code → Hope it works
- D) Create database → Deploy VM → Install model

---

**Q73.** Which endpoint format belongs to which service?

| Endpoint | Service |
|----------|---------|
| `<resource>.openai.azure.com` | ? |
| `<resource>.cognitiveservices.azure.com` | ? |

- A) Azure OpenAI (generative models) / Azure Language & Speech (Foundry Tools)
- B) Azure Storage / Azure Compute
- C) Both are the same
- D) Azure DevOps / Azure Monitor

---

**Q74.** You need to build a solution that:
1. Extracts text from scanned receipts
2. Detects the language of the extracted text
3. Analyzes the sentiment

Which combination of services do you need?

- A) Azure Content Understanding (extract from receipts) → Azure Language (detect language + sentiment)
- B) Azure Speech → Azure Blob Storage
- C) OpenAI only
- D) Azure Monitor → Azure DevOps

---

**Q75.** What does **Voice Live** capability in Azure Speech enable?

- A) Only speech-to-text
- B) Creating speech-capable agents that can have spoken conversations
- C) Image generation
- D) Text analysis

---

**Q76.** Which authentication credential is used with Azure Language SDK vs. Foundry agent SDK?

- A) Both use `DefaultAzureCredential`
- B) Language SDK uses `AzureKeyCredential(key)` / Agent SDK uses `DefaultAzureCredential()`
- C) Both use API keys directly
- D) Neither needs authentication

---

**Q77.** Complete this code to perform sentiment analysis using the OpenAI Responses API:

```python
response = client.responses.create(
    model=deployment_name,
    input=[
        {"role": "___", "content": "You are a sentiment analysis assistant. Respond with only: positive, negative, or neutral."},
        {"role": "___", "content": "The food was amazing and the service was excellent!"}
    ],
)
```

- A) `system` and `user`
- B) `user` and `system`
- C) `assistant` and `user`
- D) `admin` and `client`

---

**Q78.** You ran `client.detect_language()` on "Bonjour" and got `confidence_score: 0.98`. What does this mean?

- A) 98% of the text was analyzed
- B) The service is 98% confident in its language detection result
- C) The text is 98% French
- D) The API used 98% of its quota

---

**Q79.** What Python import do you need for EVERY Azure Speech application?

- A) `import openai`
- B) `import azure.cognitiveservices.speech as speechsdk`
- C) `from azure.ai.textanalytics import TextAnalyticsClient`
- D) `from azure.ai.projects import AIProjectClient`

---

**Q80.** A developer writes this code but gets an error. What's wrong?

```python
from openai import OpenAI
client = OpenAI(
    base_url=endpoint,
    api_key=os.getenv("API_KEY")
)
response = client.responses.create(
    model="gpt-4.1",  # The actual model name, NOT the deployment name
    input=[{"role": "user", "content": "Hello"}],
)
```

- A) The `openai` package is wrong
- B) The `model` parameter should be the **deployment name** (the name you gave when deploying), not the base model name
- C) The `input` format is wrong
- D) The `base_url` should be removed

---

### Section 5 Answers

| Q | Answer | Explanation |
|---|--------|-------------|
| 66 | **C** | Multimodal models accept text + image together |
| 67 | **B** | Content Understanding extracts from docs, images, audio, video |
| 68 | **C** | Content Understanding for document/form extraction |
| 69 | **A** | `openai` / `azure-ai-textanalytics` / `azure-cognitiveservices-speech` / `azure-ai-projects` |
| 70 | **A** | Each class maps to its specific service purpose |
| 71 | **A** | Azure Speech STT → Foundry IQ + model → Azure Speech TTS |
| 72 | **B** | Resource → Project → Deploy → Playground → SDK app |
| 73 | **A** | `.openai.azure.com` = Azure OpenAI; `.cognitiveservices.azure.com` = Language/Speech |
| 74 | **A** | Content Understanding (extract) → Language (detect + sentiment) |
| 75 | **B** | Voice Live enables spoken conversation agents |
| 76 | **B** | Language uses `AzureKeyCredential`; Agents use `DefaultAzureCredential` |
| 77 | **A** | `system` (defines behavior) then `user` (the actual input) |
| 78 | **B** | 98% confidence in the language detection result |
| 79 | **B** | `import azure.cognitiveservices.speech as speechsdk` |
| 80 | **B** | Must use **deployment name**, not the base model name |

---

## QUICK REFERENCE: SDK CHEAT SHEET

```
SERVICE                  PACKAGE                              MAIN CLASS
─────────────────────────────────────────────────────────────────────────
Generative AI models     pip install openai                   OpenAI
Text Analysis (NLP)      pip install azure-ai-textanalytics   TextAnalyticsClient
Speech (STT & TTS)       pip install azure-cognitiveservices-speech   SpeechRecognizer / SpeechSynthesizer
Agent Apps               pip install azure-ai-projects        AIProjectClient
Auth (key-based)         pip install azure-core               AzureKeyCredential
Auth (Azure AD)          pip install azure-identity           DefaultAzureCredential
Env Variables            pip install python-dotenv            load_dotenv()
```

```
ENDPOINT FORMATS
─────────────────────────────────────────────────────────────────────────
Azure OpenAI:    https://<resource>.openai.azure.com/openai/v1/
Azure Language:  https://<resource>.cognitiveservices.azure.com/
Azure Speech:    (uses endpoint from Foundry resource)
Foundry Project: https://<resource>.services.ai.azure.com/api/projects/<name>
```

```
KEY METHODS
─────────────────────────────────────────────────────────────────────────
Generative AI:  client.responses.create(model=, input=[], temperature=, max_output_tokens=)
Language:       client.detect_language([text])
                client.recognize_pii_entities([text])
                client.recognize_entities([text])
                client.analyze_sentiment([text])
Speech STT:     speech_recognizer.start_continuous_recognition()
Speech TTS:     speech_synthesizer.speak_text_async(text).get()
Agents:         project_client.agents.get(agent_name=)
                openai_client.responses.create(input=[], extra_body={"agent": ...})
```

---

## SCORING

| Section | Questions | Your Score |
|---------|-----------|------------|
| 1. Generative AI & OpenAI SDK | /20 | ___ |
| 2. Agents in Foundry | /15 | ___ |
| 3. Azure Language SDK | /15 | ___ |
| 4. Azure Speech SDK | /15 | ___ |
| 5. Vision, Content Understanding & Mixed | /15 | ___ |
| **TOTAL** | **/80** | **___** |

### Score Interpretation
- **72-80 (90%+):** Exam ready - Domain 2 is solid
- **64-71 (80-89%):** Good - review weak sections
- **56-63 (70-79%):** Borderline - focus on SDK details and code patterns
- **Below 56 (<70%):** Needs more study on implementation details
