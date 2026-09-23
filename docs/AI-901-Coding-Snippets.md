# AI-901 Coding Snippet Questions

All code-based questions from Tests 1–6, organized by SDK/service area.  
Format: Question → Snippet → Options → Answer → Why  
🔴 = You answered incorrectly

---

## Table of Contents
1. [Azure Text Analytics (Language)](#1-azure-text-analytics-language)
2. [Azure Speech SDK](#2-azure-speech-sdk)
3. [Azure Vision Image Analysis](#3-azure-vision-image-analysis)
4. [Azure Content Understanding](#4-azure-content-understanding)
5. [Foundry SDK (AIProjectClient + Agents)](#5-foundry-sdk-aiprojectclient--agents)
6. [Chat Completions API](#6-chat-completions-api)
7. [Responses API](#7-responses-api)
8. [Multimodal / Vision Chat](#8-multimodal--vision-chat)
9. [Image Generation](#9-image-generation)
10. [Embeddings](#10-embeddings)
11. [Content Safety](#11-content-safety)
12. [Prompt Engineering (Code-Based)](#12-prompt-engineering-code-based)
13. [Workload Mapping (Code-Based)](#13-workload-mapping-code-based)
14. [Miscellaneous SDK Patterns](#14-miscellaneous-sdk-patterns)
15. [Cheat Sheets](#15-cheat-sheets)

---

## 1. Azure Text Analytics (Language)

### Q1. Which method returns the sentiment of a review?

**Source:** Test 1 — Q2 | Test 6 — Q2

```python
import os
from azure.ai.textanalytics import TextAnalyticsClient
from azure.core.credentials import AzureKeyCredential

language_key = os.environ.get("LANGUAGE_KEY")
language_endpoint = os.environ.get("LANGUAGE_ENDPOINT")

client = TextAnalyticsClient(
    endpoint=language_endpoint,
    credential=AzureKeyCredential(language_key)
)

documents = ["The checkout was simple, but support was slow."]
result = client.________(documents, show_opinion_mining=True)
doc = [item for item in result if not item.is_error][0]

print(doc.sentiment)
```

**Options:**
- A) detect_language
- B) analyze_sentiment
- C) recognize_entities
- D) extract_key_phrases

**Answer:** B) analyze_sentiment

**Why:** `analyze_sentiment` returns sentiment labels (positive/negative/neutral/mixed) plus optional opinion mining. `detect_language` = language ID. `recognize_entities` = NER. `extract_key_phrases` = topics.

---

### Q2. What is the correct constructor parameter order for TextAnalyticsClient? 🔴

**Source:** Test 5 — Q26

```python
import os
from azure.core.credentials import AzureKeyCredential
from azure.ai.textanalytics import TextAnalyticsClient

endpoint = os.environ["AZURE_LANGUAGE_ENDPOINT"]
key = os.environ["AZURE_LANGUAGE_KEY"]

________
reviews = ["The support team was very helpful."]
result = text_analytics_client.analyze_sentiment(reviews)
```

**Options:**
- A) `text_analytics_client = TextAnalyticsClient(key, AzureKeyCredential(endpoint))`
- B) `text_analytics_client = TextAnalyticsClient(endpoint, AzureKeyCredential(key))`
- C) `text_analytics_client = TextAnalyticsClient(AzureKeyCredential(key), endpoint)`
- D) `text_analytics_client = AzureKeyCredential(endpoint, key)`

**Answer:** B) `TextAnalyticsClient(endpoint, AzureKeyCredential(key))`

**Why:** Constructor order = **endpoint FIRST**, then `AzureKeyCredential(key)`. Swapping them or wrapping endpoint in credential is wrong.

---

### Q3. Which method extracts organizations, locations, and dates from text? 🔴

**Source:** Test 4 — Q28

```python
from azure.ai.textanalytics import TextAnalyticsClient
from azure.core.credentials import AzureKeyCredential

client = TextAnalyticsClient(
    endpoint=endpoint,
    credential=AzureKeyCredential(key)
)

document = "Contoso signed a contract in Sydney on 12 March."

response = client.________([document])[0]
```

**Options:**
- A) extract_key_phrases
- B) recognize_entities
- C) analyze_sentiment
- D) detect_language

**Answer:** B) recognize_entities

**Why:** Extracts typed entities (organizations, locations, dates). `extract_key_phrases` = keywords. `analyze_sentiment` = tone. `detect_language` = language ID.

---

### Q4. Which method populates doc.entities with .text and .category? 🔴

**Source:** Test 5 — Q35

```python
messages = ["Contoso opened an office in Sydney on Monday."]
________
for doc in result:
    for entity in doc.entities:
        print(entity.text, entity.category)
```

**Options:**
- A) `result = text_analytics_client.detect_language(messages)`
- B) `result = text_analytics_client.extract_key_phrases(messages)`
- C) `result = text_analytics_client.analyze_sentiment(messages)`
- D) `result = text_analytics_client.recognize_entities(messages)`

**Answer:** D) `text_analytics_client.recognize_entities(messages)`

**Why:** Only `recognize_entities` returns `doc.entities` with `.text` and `.category` attributes. Other methods return different structures.

---

### Q5. Which method populates doc.key_phrases?

**Source:** Test 5 — Q49

```python
tickets = ["Delivery was late but the driver was polite."]
________
for doc in result:
    print(doc.key_phrases)
```

**Options:**
- A) `result = text_analytics_client.analyze_sentiment(tickets)`
- B) `result = text_analytics_client.recognize_entities(tickets)`
- C) `result = text_analytics_client.extract_key_phrases(tickets)`
- D) `result = text_analytics_client.detect_language(tickets)`

**Answer:** C) `text_analytics_client.extract_key_phrases(tickets)`

**Why:** Only `extract_key_phrases` populates `doc.key_phrases`. Sentiment returns labels, entities returns entity objects, detect_language returns language codes.

---

## 2. Azure Speech SDK

### Q6. Which method captures one spoken utterance from the microphone?

**Source:** Test 2 — Q8 | Test 6 — Q42

```python
import azure.cognitiveservices.speech as speechsdk

speech_config = speechsdk.SpeechConfig(
    subscription=os.environ.get("SPEECH_KEY"),
    endpoint=os.environ.get("ENDPOINT")
)
speech_config.speech_recognition_language = "en-US"

audio_config = speechsdk.audio.AudioConfig(use_default_microphone=True)
speech_recognizer = speechsdk.SpeechRecognizer(
    speech_config=speech_config,
    audio_config=audio_config
)

result = speech_recognizer.________().get()
print(result.text)
```

**Options:**
- A) speak_text_async
- B) analyze_sentiment
- C) recognize_once_async
- D) create_version

**Answer:** C) recognize_once_async

**Why:** Captures one utterance from microphone, returns transcribed text. `speak_text_async` = TTS (wrong direction). `analyze_sentiment` = Azure Language. `create_version` = agent lifecycle.

---

### Q7. How do you configure the SDK to capture from the default microphone?

**Source:** Test 2 — Q34

```python
import azure.cognitiveservices.speech as speechsdk

audio_config = speechsdk.audio._______

recognizer = speechsdk.SpeechRecognizer(
    speech_config=speech_config,
    audio_config=audio_config
)
```

**Options:**
- A) AudioConfig(use_default_microphone=True)
- B) AudioConfig(filename="meeting.wav")
- C) SpeechConfig.from_subscription(key, region)
- D) AudioConfig(use_default_microphone=False)

**Answer:** A) AudioConfig(use_default_microphone=True)

**Why:** Configures SDK to capture from system's default mic. `filename="meeting.wav"` = reads from file. `use_default_microphone=False` = disables mic.

---

### Q8. Which method does single-utterance async recognition?

**Source:** Test 2 — Q35

```python
recognizer = speechsdk.SpeechRecognizer(
    speech_config=speech_config,
    audio_config=audio_config
)

result_future = recognizer._______()
```

**Options:**
- A) recognize_once_async
- B) start_continuous_recognition_async
- C) speak_text_async
- D) add_target_language

**Answer:** A) recognize_once_async

**Why:** Single-utterance recognition (listens until one complete utterance). `start_continuous_recognition_async` = long-running stream. `speak_text_async` = synthesis (wrong direction).

---

### Q9. Which method converts text to speech?

**Source:** Test 2 — Q31 | Test 6 — Q45

```python
import azure.cognitiveservices.speech as speechsdk

speech_config.speech_synthesis_voice_name = "en-US-Ava:DragonHDLatestNeural"
synthesizer = speechsdk.SpeechSynthesizer(speech_config=speech_config)

result = synthesizer.________("Your order ships today.").get()
```

**Options:**
- A) speak_text_async
- B) recognize_once_async
- C) result.transcribe_text_async
- D) audio_config.read_text

**Answer:** A) speak_text_async

**Why:** `SpeechSynthesizer.speak_text_async()` = TTS. Called on **synthesizer**, NOT recognizer. `recognize_once_async` = wrong direction (STT).

---

### Q10. Which method is plain-text TTS synthesis?

**Source:** Test 2 — Q39

```python
speech_config.speech_synthesis_voice_name = "en-US-Ava:DragonHDLatestNeural"
synthesizer = speechsdk.SpeechSynthesizer(speech_config=speech_config)

result = synthesizer._______("Thanks for calling Contoso.")
```

**Options:**
- A) get_voices_async
- B) speak_text_async
- C) recognize_once_async
- D) start_continuous_recognition_async

**Answer:** B) speak_text_async

**Why:** Plain-text TTS synthesis. `get_voices_async` = lists voices. `recognize_once_async` / `start_continuous_recognition_async` = recognition (wrong direction).

---

### Q11. How do you add a translation target language?

**Source:** Test 2 — Q17

```python
translation_config = speechsdk.translation.SpeechTranslationConfig(
    subscription=speech_key,
    region=service_region
)

translation_config.speech_recognition_language = "en-US"
translation_config._______("fr")
```

**Options:**
- A) speak_text_async
- B) recognize_once_async
- C) remove_target_language
- D) add_target_language

**Answer:** D) add_target_language

**Why:** Appends a target output language to the translation pipeline. `speak_text_async` / `recognize_once_async` = wrong objects. `remove_target_language` = opposite.

---

## 3. Azure Vision Image Analysis

### Q12. Which VisualFeature reads text from an image (OCR)? 🔴

**Source:** Test 4 — Q54

```python
from azure.ai.vision.imageanalysis import ImageAnalysisClient
from azure.ai.vision.imageanalysis.models import VisualFeatures
from azure.core.credentials import AzureKeyCredential

client = ImageAnalysisClient(
    endpoint=endpoint,
    credential=AzureKeyCredential(key)
)

result = client.analyze(
    image_url=image_url,
    visual_features=[________]
)
```

**Options:**
- A) VisualFeatures.READ
- B) VisualFeatures.CAPTION
- C) VisualFeatures.OBJECTS
- D) VisualFeatures.SMART_CROPS

**Answer:** A) VisualFeatures.READ

**Why:** READ = OCR (extract printed/handwritten text). CAPTION = one-sentence description. OBJECTS = detect objects. SMART_CROPS = crop regions.

---

### Q13. Which VisualFeature returns a one-sentence image description?

**Source:** Test 6 — Q50

```python
from azure.ai.vision.imageanalysis import ImageAnalysisClient
from azure.ai.vision.imageanalysis.models import VisualFeatures

result = client.analyze(
    image_url=image_url,
    visual_features=[________]
)
```

**Options:**
- A) VisualFeatures.CAPTION
- B) VisualFeatures.READ
- C) VisualFeatures.OBJECTS
- D) VisualFeatures.PEOPLE

**Answer:** A) VisualFeatures.CAPTION

**Why:** CAPTION = one-sentence natural-language description. READ = OCR text extraction. OBJECTS = object bounding boxes. PEOPLE = person detection.

---

### Q14. What is the correct method for URL-based image analysis?

**Source:** Test 5 — Q46

```python
from azure.ai.vision.imageanalysis.models import VisualFeatures

image_url = "https://contoso.com/menu.jpg"

result = client.________(
    image_url=image_url,
    visual_features=[VisualFeatures.CAPTION, VisualFeatures.READ]
)
```

**Options:**
- A) get_image
- B) analyze_from_url
- C) captions_from_url
- D) detect_visuals

**Answer:** B) analyze_from_url

**Why:** Documented `ImageAnalysisClient` method for URL-based image analysis. Supports multiple visual features in one call. Others are not real methods.

---

### Q15. Which API features detect people and extract text? 🔴

**Source:** Test 5 — Q54

```
POST {endpoint}/computervision/imageanalysis:analyze
    ?api-version=2024-02-01
    &________
```

**Options:**
- A) features=objects,read
- B) features=people,read
- C) features=people,tags
- D) features=caption,read

**Answer:** B) features=people,read

**Why:** `people` = bounding boxes + confidence for detected people. `read` = OCR structured text. `objects` = general objects (not dedicated people detection). `tags` = keywords only.

---

### Q16. How do you enable smart cropping for thumbnails? 🔴

**Source:** Test 6 — Q64

```
POST {endpoint}/vision/v3.2/generateThumbnail
    ?width=600
    &height=600
    &________
```

**Options:**
- A) smartCropping=false
- B) detectOrientation=true
- C) smartCropping=true
- D) visualFeatures=objects

**Answer:** C) smartCropping=true

**Why:** Content-aware cropping preserves most important region. `smartCropping=false` = naive crop. `detectOrientation` = rotation only. `visualFeatures=objects` = wrong API.

---

## 4. Azure Content Understanding

### Q17. Which analyzer ID extracts transcript and summary from audio?

**Source:** Test 3 — Q6

```python
audio_url = "https://example.com/call.mp3"

poller = client.begin_analyze(
    analyzer_id="________",
    inputs=[AnalysisInput(url=audio_url)],
)
result = poller.result()
```

**Options:**
- A) prebuilt-videoSearch
- B) prebuilt-audioSearch
- C) prebuilt-imageSearch
- D) prebuilt-document

**Answer:** B) prebuilt-audioSearch

**Why:** For audio extraction (transcript, summary, speaker labeling). `prebuilt-videoSearch` = video. `prebuilt-imageSearch` = image. `prebuilt-document` = documents.

---

### Q18. Which analyzer ID generates an image description? 🔴

**Source:** Test 2 — Q54

```python
from azure.ai.contentunderstanding.models import AnalysisInput

image_url = "https://raw.githubusercontent.com/.../pieChart.jpg"

poller = client.begin_analyze(
    analyzer_id=________,
    inputs=[AnalysisInput(url=image_url)],
)
result = poller.result()
```

**Options:**
- A) "prebuilt-layout"
- B) "prebuilt-documentSearch"
- C) "prebuilt-image"
- D) "prebuilt-imageSearch"

**Answer:** D) "prebuilt-imageSearch"

**Why:** For image description/search. `prebuilt-image` = base for custom analyzers (not direct use). `prebuilt-layout` = document-oriented. `prebuilt-documentSearch` = document/RAG.

---

### Q19. What property outputs video content as formatted text?

**Source:** Test 3 — Q28

```python
poller = client.begin_analyze(
    analyzer_id="prebuilt-videoSearch",
    inputs=[AnalysisInput(url=video_url)],
)
result = poller.result()

for media in result.contents:
    video_content = media
    print(video_content.________)
```

**Options:**
- A) markdown
- B) deployment_name
- C) temperature
- D) embedding

**Answer:** A) markdown

**Why:** Video content is packaged as richly formatted Markdown for downstream use (RAG-ready).

---

### Q20. How do you read a returned field like "Summary" from the result?

**Source:** Test 4 — Q22

```python
result = poller.result()
content = result.contents[0]
summary = content.fields.get(________)
```

**Options:**
- A) "Summary"
- B) "AnalyzerId"
- C) "Credential"
- D) "Endpoint"

**Answer:** A) "Summary"

**Why:** Extracted fields are accessed by string name. `"Summary"` is the documented key. Others are connection metadata, not result fields.

---

### Q21. What is the correct SDK client for Content Understanding?

**Source:** Test 4 — Q49

```python
from azure.core.credentials import AzureKeyCredential
from azure.ai.contentunderstanding import ________

client = ________(
    endpoint=endpoint,
    credential=AzureKeyCredential(key)
)
```

**Options:**
- A) SearchClient
- B) ContentUnderstandingClient
- C) TextAnalyticsClient
- D) ImageAnalysisClient

**Answer:** B) ContentUnderstandingClient

**Why:** SDK entry point for Content Understanding operations. `SearchClient` = Azure AI Search. `TextAnalyticsClient` = Language. `ImageAnalysisClient` = Vision.

---

### Q22. How do you submit a document URL for extraction?

**Source:** Test 4 — Q58

```python
poller = client.begin_analyze(
    analyzer_id="prebuilt-invoice",
    ________
)
result = poller.result()
```

**Options:**
- A) field_schema=[AnalysisInput(url=file_url)],
- B) base_analyzer_id="prebuilt-document",
- C) inputs=[AnalysisInput(url=file_url)],
- D) content_fields=file_url,

**Answer:** C) inputs=[AnalysisInput(url=file_url)],

**Why:** Runtime submission uses `inputs=[AnalysisInput(url=...)]`. `field_schema` = analyzer definition. `base_analyzer_id` = custom analyzer creation.

---

### Q23. What method gets the completed result from an async poller?

**Source:** Test 6 — Q13

```python
async def main():
    async with ContentUnderstandingClient(
        endpoint=endpoint, credential=AzureKeyCredential(key)
    ) as client:
        poller = await client.begin_analyze(
            analyzer_id="prebuilt-invoice",
            inputs=[AnalysisInput(url=file_url)]
        )
        result = await poller.________
        print(result.contents[0].fields["CustomerName"].value)

asyncio.run(main())
```

**Options:**
- A) result()
- B) wait()
- C) get_result()
- D) poll_until_done()

**Answer:** A) result()

**Why:** Azure SDK async pattern: `begin_analyze()` → poller → `await poller.result()`. NOT `wait()`, `get_result()`, or `poll_until_done()`.

---

### Q24. What parameter defines inheritance for a custom image analyzer? 🔴

**Source:** Test 2 — Q60

```python
analyzer = ContentAnalyzer(
    ________,
    description="Custom analyzer for charts and graphs",
    field_schema=field_schema,
    models={"completion": "gpt-4.1"},
)
```

**Options:**
- A) analyzer_id="prebuilt-image"
- B) base_analyzer_id="prebuilt-image"
- C) base_analyzer_id="prebuilt-imageSearch"
- D) parent_analyzer="prebuilt-layout"

**Answer:** B) base_analyzer_id="prebuilt-image"

**Why:** Custom image analyzers inherit from `prebuilt-image`. Parameter is `base_analyzer_id` (not `analyzer_id`). `prebuilt-imageSearch` = for direct prebuilt use, not custom inheritance.

---

### Q25. Which TWO statements correctly describe this custom analyzer schema?

**Source:** Test 2 — Q16

```json
{
  "baseAnalyzerId": "prebuilt-image",
  "fields": {
    "Title": {
      "type": "string"
    },
    "ChartType": {
      "type": "string",
      "method": "classify",
      "enum": ["bar", "line", "pie"]
    }
  }
}
```

**Options:**
- A) Title returns a string value
- B) ChartType uses OCR
- C) ChartType uses classify
- D) baseAnalyzerId uses prebuilt-audio
- E) Title uses enum values

**Answer:** A and C

**Why:** Title returns a **string** value. ChartType uses **classify** method (not OCR). Base is `prebuilt-image` (not audio). Enum belongs to ChartType (not Title).

---

## 5. Foundry SDK (AIProjectClient + Agents)

### Q26. How do you get the OpenAI-compatible client from a project? 🔴

**Source:** Test 2 — Q51 | Test 4 — Q41 | Test 6 — Q28

```python
from azure.identity import DefaultAzureCredential
from azure.ai.projects import AIProjectClient

project = AIProjectClient(
    endpoint=PROJECT_ENDPOINT,
    credential=DefaultAzureCredential(),
)

openai = ________
```

**Options:**
- A) AIProjectClient.get_openai_client()
- B) project.get_openai_client()
- C) project.openai()
- D) AIProjectClient.openai_client()

**Answer:** B) project.get_openai_client()

**Why:** Documented **instance** method. NOT `AIProjectClient.get_openai_client()` (class-level call, wrong). NOT `openai()` or `openai_client()` (wrong names). NOT `responses_client()`.

---

### Q27. What are the correct constructor parameters for AIProjectClient? 🔴

**Source:** Test 4 — Q38

```python
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential

PROJECT_ENDPOINT = "your_project_endpoint"

project = ________
openai = project.get_openai_client()
```

**Options:**
- A) `AIProjectClient(model=PROJECT_ENDPOINT, credential=DefaultAzureCredential())`
- B) `AIProjectClient(agent_name=PROJECT_ENDPOINT, credential=DefaultAzureCredential())`
- C) `AIProjectClient(endpoint=PROJECT_ENDPOINT, credential=DefaultAzureCredential())`
- D) `AIProjectClient(endpoint=PROJECT_ENDPOINT, api_key=DefaultAzureCredential())`

**Answer:** C) `AIProjectClient(endpoint=PROJECT_ENDPOINT, credential=DefaultAzureCredential())`

**Why:** Constructor takes `endpoint=` URL and `credential=DefaultAzureCredential()`. NOT `model=`, `agent_name=`, or `api_key=`.

---

### Q28. What goes inside PromptAgentDefinition to define agent behavior?

**Source:** Test 3 — Q20 | Test 4 — Q47

```python
from azure.ai.projects.models import PromptAgentDefinition

agent = project.agents.create_version(
    agent_name=AGENT_NAME,
    definition=________,
)
```

**Options:**
- A) `{"model": "gpt-5-mini", "instructions": "You are a helpful assistant"}`
- B) DefaultAzureCredential()
- C) `PromptAgentDefinition(model="gpt-5-mini", instructions="You are a helpful assistant")`
- D) openai.conversations.create()

**Answer:** C) `PromptAgentDefinition(model="gpt-5-mini", instructions="You are a helpful assistant")`

**Why:** `instructions=` defines the agent's behavior. Must use the typed class, not a raw dict. `conversation` and `credential` are unrelated.

---

### Q29. How do you start a multi-turn conversation for an agent?

**Source:** Test 4 — Q56 | Test 6 — Q30

```python
openai = project.get_openai_client()

conversation = ________

response = openai.responses.create(
    conversation=conversation.id,
    extra_body={"agent_reference": {"name": AGENT_NAME, "type": "agent_reference"}},
    input="Hello, agent!",
)
```

**Options:**
- A) openai.responses.create()
- B) project.agents.create_version()
- C) openai.threads.create()
- D) openai.conversations.create()

**Answer:** D) openai.conversations.create()

**Why:** Creates conversation container for multi-turn state. Pass `conversation.id` to subsequent calls. NOT `responses.create()` (generates response). NOT `threads.create()` (older pattern).

---

### Q30. How do you route a request to a portal-created agent?

**Source:** Test 3 — Q35

```python
conversation = openai.conversations.create()

response = openai.responses.create(
    conversation=conversation.id,
    extra_body=________,
    input="Summarize the customer issue."
)
```

**Options:**
- A) `{"agent_reference": {"name": AGENT_NAME, "type": "agent_reference"}}`
- B) `{"tool": {"name": AGENT_NAME}}`
- C) `{"deployment": {"model": AGENT_NAME}}`
- D) `{"conversation_id": AGENT_NAME}`

**Answer:** A) `{"agent_reference": {"name": AGENT_NAME, "type": "agent_reference"}}`

**Why:** Routes request to the portal-configured agent with all its instructions and tools. The `type` must be `"agent_reference"`.

---

## 6. Chat Completions API

### Q31. How do you preserve the system message in conversation history?

**Source:** Test 6 — Q33

```python
system_message = {"role": "system", "content": "You are a helpful assistant."}
conversation = []

________

user_input = "What is thermodynamics?"
conversation.append({"role": "user", "content": user_input})

response = client.chat.completions.create(
    model="YOUR-DEPLOYMENT-NAME",
    messages=conversation,
    temperature=0.7,
    max_tokens=250
)
```

**Options:**
- A) conversation.clear()
- B) conversation.append(system_message)
- C) conversation.append({"role": "assistant", "content": user_input})
- D) conversation = response.choices[0].message.content

**Answer:** B) conversation.append(system_message)

**Why:** System message goes first in messages array. NOT `clear()` (destroys context). NOT append assistant with user content (wrong role). NOT replace list with string.

---

### Q32. What do you pass to model= in Azure OpenAI? 🔴

**Source:** Test 4 — Q25

```python
from openai import AzureOpenAI

deployment_name = "support-chat-prod"

client = AzureOpenAI(
    azure_endpoint=endpoint,
    api_key=api_key,
    api_version="2024-10-21",
)

response = client.chat.completions.create(
    model=________,
    messages=[{"role": "user", "content": "Summarize this case."}]
)
```

**Options:**
- A) "gpt-4o"
- B) deployment_name
- C) endpoint
- D) api_key

**Answer:** B) deployment_name

**Why:** Azure OpenAI uses `model=` for the **deployment name**, not the model family. Pass the variable holding your deployment identifier.

---

### Q33. Which parameter sets an upper bound on generated output tokens?

**Source:** Test 4 — Q60

```python
response = client.chat.completions.create(
    model="support-chat-prod",
    messages=[{"role": "user", "content": "Give me a one-sentence summary."}],
    temperature=0.2,
    ________=60
)
```

**Options:**
- A) top_p
- B) presence_penalty
- C) max_completion_tokens
- D) frequency_penalty

**Answer:** C) max_completion_tokens

**Why:** Hard upper bound on generated tokens. `top_p` = sampling probability. `presence_penalty` = new topics. `frequency_penalty` = reduce repetition.

---

## 7. Responses API

### Q34. What parameter name sends the prompt in the Responses API?

**Source:** Test 2 — Q53

```python
response = openai_client.responses.create(
    model=DEPLOYMENT_NAME,
    ________="Summarize the benefits of autoscaling."
)

print(response.output_text)
```

**Options:**
- A) input
- B) prompt
- C) message
- D) question

**Answer:** A) input

**Why:** Responses API uses `input=` (not `prompt`, `message`, or `question`). Confirmed by `response.output_text` accessor.

---

### Q35. How do you link a follow-up to a prior response for multi-turn?

**Source:** Test 6 — Q40

```python
response = client.responses.create(
    model="gpt-4o",
    input="Explain what a vector database does."
)

follow_up = client.responses.create(
    model="gpt-4o",
    ________,
    input=[{"role": "user", "content": "Now explain it to a beginner."}]
)
```

**Options:**
- A) tool_choice="auto"
- B) store=False
- C) instructions=response.id
- D) previous_response_id=response.id

**Answer:** D) previous_response_id=response.id

**Why:** Links follow-up to prior response for conversation continuity. NOT `tool_choice` (tool behavior), `store` (persistence), or `instructions=response.id` (wrong usage).

---

## 8. Multimodal / Vision Chat

### Q36. How do you send an image to a model using the Azure AI Inference SDK? 🔴

**Source:** Test 3 — Q22 | Test 5 — Q37

```python
from azure.ai.inference.models import UserMessage, TextContentItem, ImageContentItem, ImageUrl

image_url = "https://contoso.com/shelf.jpg"

messages = [
    UserMessage(content=[
        TextContentItem(text="Describe the products in this image."),
        ________
    ])
]
```

**Options:**
- A) `ImageContentItem(image_url=ImageUrl(image_url))`
- B) `ImageContentItem(text=image_url)`
- C) `{"type": "audio_url", "url": image_url}`
- D) `TextContentItem(text=ImageUrl(image_url))`

**Answer:** A) `ImageContentItem(image_url=ImageUrl(image_url))`

**Why:** Image input = `ImageContentItem` with `image_url=ImageUrl(...)`. NOT `text=` (wrong property). NOT `AudioContentItem` (wrong modality). NOT `TextContentItem` wrapping `ImageUrl`.

---

### Q37. How do you send an image URL in the Chat Completions API format?

**Source:** Test 6 — Q47

```python
response = client.chat.completions.create(
    model=deployment_name,
    messages=[{
        "role": "user",
        "content": [
            {"type": "text", "text": "What damage do you see on this package?"},
            ________
        ]
    }]
)
```

**Options:**
- A) `{"type": "audio", "audio_url": {"url": image_url}}`
- B) `{"type": "ocr", "text": image_url}`
- C) `{"type": "caption", "image": image_url}`
- D) `{"type": "image_url", "image_url": {"url": image_url}}`

**Answer:** D) `{"type": "image_url", "image_url": {"url": image_url}}`

**Why:** Chat Completions API uses `type: "image_url"` with nested `image_url.url`. NOT `audio`, `ocr`, or `caption` types.

---

### Q38. How do you send a base64 image in the Responses API? 🔴

**Source:** Test 6 — Q52

```python
response = client.responses.create(
    model="gpt-4o",
    input=[{
        "role": "user",
        "content": [
            {"type": "input_text", "text": "Describe the damaged area in this image."},
            ________
        ]
    }]
)
```

**Options:**
- A) `{"type": "image", "url": base64_image}`
- B) `{"type": "input_image", "image": base64_image}`
- C) `{"type": "input_image", "image_url": f"data:image/jpeg;base64,{base64_image}"}`
- D) `{"type": "image_url", "url": f"data:image/jpeg;base64,{base64_image}"}`

**Answer:** C) `{"type": "input_image", "image_url": f"data:image/jpeg;base64,{base64_image}"}`

**Why:** Responses API uses `type: "input_image"` (NOT `"image_url"` which is Chat Completions). Local files use data URL format.

> **KEY DISTINCTION:**
> | API | Type Field | Image Field |
> |---|---|---|
> | Chat Completions | `"type": "image_url"` | `"image_url": {"url": url}` |
> | Responses API | `"type": "input_image"` | `"image_url": "data:..."` |

---

### Q39. How do you load a local image file as a data URL? 🔴

**Source:** Test 3 — Q55

```python
from azure.ai.inference.models import ImageUrl

# Load a local JPEG file for a multimodal model
________
```

**Options:**
- A) `data_url = ImageUrl(image_file="receipt.jpg")`
- B) `data_url = TextContentItem(text="receipt.jpg")`
- C) `data_url = ImageUrl.load(image_file="receipt.jpg", image_format="jpeg")`
- D) `data_url = AudioContentItem(input_audio="receipt.jpg")`

**Answer:** C) `ImageUrl.load(image_file="receipt.jpg", image_format="jpeg")`

**Why:** Documented helper that converts local file into a data URL. NOT `ImageUrl(image_file=...)` (no `.load()`). NOT `TextContentItem` or `AudioContentItem`.

---

## 9. Image Generation

### Q40. Which parameter sets the image format for GPT-image-1?

**Source:** Test 4 — Q2

```python
result = client.images.generate(
    model="gpt-image-1",
    prompt="A flat icon of a blue rocket",
    n=1,
    size="1024x1024",
    background="transparent",
    ________="png"
)
```

**Options:**
- A) output_format
- B) response_format
- C) content_type
- D) image_format

**Answer:** A) output_format

**Why:** GPT-image-1 uses `output_format` (not `response_format` which is DALL-E 3 only). PNG required for transparency.

---

### Q41. What is the key for the text prompt in an image generation payload?

**Source:** Test 3 — Q24

```python
payload = {
    "model": deployment_name,
    ________
    "width": 1024,
    "height": 1024
}
```

**Options:**
- A) `"prompt": "A red bicycle in a park",`
- B) `"ocr": "A red bicycle in a park",`
- C) `"objects": ["bicycle", "park"],`
- D) `"caption": True`

**Answer:** A) `"prompt": "A red bicycle in a park",`

**Why:** The `"prompt"` key is the text-to-image generation input. NOT `"ocr"`, `"objects"`, or `"caption"`.

---

### Q42. What is the correct endpoint path for MAI image generation?

**Source:** Test 3 — Q31

```python
endpoint = os.environ["AZURE_ENDPOINT"]
url = f"{endpoint}/________"
```

**Options:**
- A) vision/v1/ocr
- B) speech/v1/synthesize
- C) mai/v1/images/generations
- D) language/v1/entities

**Answer:** C) mai/v1/images/generations

**Why:** MAI image generation models use this path. NOT `vision/v1/ocr`, `speech/v1/synthesize`, or `language/v1/entities`.

---

## 10. Embeddings

### Q43. How do you create embeddings with the OpenAI SDK?

**Source:** Test 3 — Q17

```python
from openai import OpenAI

client = OpenAI(
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
    base_url="https://YOUR-RESOURCE-NAME.openai.azure.com/openai/v1/"
)

text = "Contoso invoice 1024 is overdue"

# Generate a vector embedding
________

print(response.data[0].embedding[:5])
```

**Options:**
- A) `response = client.images.generate(model="gpt-image-1", prompt=text)`
- B) `response = client.audio.transcriptions.create(file=text)`
- C) `response = client.responses.create(model="gpt-4.1", input=text)`
- D) `response = client.embeddings.create(input=text, model="text-embedding-3-large")`

**Answer:** D) `client.embeddings.create(input=text, model="text-embedding-3-large")`

**Why:** Returns `response.data[0].embedding` (vector array). NOT images.generate, audio.transcriptions, or responses.create.

---

### Q44. What method generates embeddings on EmbeddingsClient?

**Source:** Test 2 — Q21

```python
from azure.ai.inference import EmbeddingsClient
from azure.core.credentials import AzureKeyCredential

client = EmbeddingsClient(endpoint=endpoint, credential=AzureKeyCredential(key))

response = client._______(
    input=["invoice number", "bill identifier", "customer address"]
)
print(len(response.data[0].embedding))
```

**Options:**
- A) complete
- B) get_model_info
- C) send_request
- D) embed

**Answer:** D) embed

**Why:** `EmbeddingsClient.embed()` = generate embedding vectors. `complete` = wrong client. `get_model_info` = metadata. `send_request` = low-level transport.

---

## 11. Content Safety

### Q45. Which method screens text for harmful content?

**Source:** Test 2 — Q5

```python
from azure.ai.contentsafety import ContentSafetyClient
from azure.ai.contentsafety.models import AnalyzeTextOptions
from azure.core.credentials import AzureKeyCredential

client = ContentSafetyClient(endpoint, AzureKeyCredential(key))
request = AnalyzeTextOptions(text=user_text)

result = client.________(request)
print(result)
```

**Options:**
- A) analyze_text
- B) summarize_text
- C) extract_entities
- D) transcribe_audio

**Answer:** A) analyze_text

**Why:** Submits text for moderation, returns harm-category scores. `summarize_text`, `extract_entities`, `transcribe_audio` = different workloads entirely.

---

## 12. Prompt Engineering (Code-Based)

### Q46. What message comes after a few-shot example pair? 🔴

**Source:** Test 5 — Q4

```python
messages = [
    {"role": "system", "content": "Classify sentiment as Positive, Neutral, or Negative."},
    {"role": "user", "content": "The setup was easy and the support team helped immediately."},
    {"role": "assistant", "content": "Positive"},
    ________
]
```

**Options:**
- A) `{"role": "user", "content": "The app kept crashing and nobody replied for two days."}`
- B) `{"role": "assistant", "content": "Negative"}`
- C) `{"role": "system", "content": "Negative"}`
- D) `{"role": "assistant", "content": "Classify sentiment"}`

**Answer:** A) `{"role": "user", "content": "The app kept crashing..."}`

**Why:** Few-shot = system → user/assistant example pairs → NEW **user** message (the real input to classify). Must maintain user→assistant alternation. The next message after an assistant example must be a user message.

---

### Q47. What is missing after a system message to complete a chat request? 🔴

**Source:** Test 5 — Q20

```python
messages = [
    {
        "role": "system",
        "content": "You are a support assistant. If key details are missing, ask one clarifying question before answering."
    },
    ________
]

response = client.chat.completions.create(
    model="gpt-4.1-mini",
    messages=messages
)
```

**Options:**
- A) `{"role": "assistant", "content": "Please provide more details."}`
- B) `{"role": "system", "content": "The user forgot the product name."}`
- C) `{"role": "assistant", "content": "I am a support assistant."}`
- D) `{"role": "user", "content": "My printer keeps failing after the update."}`

**Answer:** D) `{"role": "user", "content": "My printer keeps failing after the update."}`

**Why:** After a system message, you need a **user** message with the actual request. The system prompt defines behavior; what's missing is the user's input to trigger a response.

---

## 13. Workload Mapping (Code-Based)

### Q48. What workload produces a brand-new image from a text prompt?

**Source:** Test 5 — Q6

```python
prompt = "Create a winter sale poster with skis and snow"
goal = "produce a brand-new image"

workload = ________
print(workload)
```

**Options:**
- A) "OCR"
- B) "Speech to Text"
- C) "Image generation"
- D) "Entity recognition"

**Answer:** C) "Image generation"

**Why:** Text prompt input → new image output = image generation workload.

---

### Q49. What workload converts live microphone audio to text?

**Source:** Test 5 — Q32

```python
scenario = "live microphone audio"
goal = "convert spoken words to text"

workload = ________
print(workload)
```

**Options:**
- A) "Text to Speech"
- B) "Computer vision"
- C) "Speech to Text"
- D) "OCR"

**Answer:** C) "Speech to Text"

**Why:** Spoken audio input → written text output = Speech to Text. NOT OCR (that's for images).

---

## 14. Miscellaneous SDK Patterns

### Q50. How do you avoid hard-coding an API key?

**Source:** Test 3 — Q38

```python
import os
from openai import AzureOpenAI

endpoint = os.getenv("AZURE_OPENAI_ENDPOINT")
key = ________

client = AzureOpenAI(
    azure_endpoint=endpoint,
    api_key=key,
    api_version="2024-10-21"
)
```

**Options:**
- A) "my-secret-key"
- B) os.getenv("AZURE_OPENAI_KEY")
- C) print("AZURE_OPENAI_KEY")
- D) endpoint

**Answer:** B) os.getenv("AZURE_OPENAI_KEY")

**Why:** Environment variable avoids hard-coding secrets. NOT `"my-secret-key"` (hard-coded). NOT `print(...)` (prints literal string). NOT `endpoint` (wrong value).

---

### Q51. What method sends chat messages on ChatCompletionsClient?

**Source:** Test 2 — Q46

```python
from azure.ai.inference import ChatCompletionsClient
from azure.ai.inference.models import SystemMessage, UserMessage
from azure.core.credentials import AzureKeyCredential

client = ChatCompletionsClient(endpoint=endpoint, credential=AzureKeyCredential(key))

response = client._______(
    messages=[
        SystemMessage("You are a helpful assistant."),
        UserMessage("Write a two-sentence description of solar panels.")
    ]
)
print(response.choices[0].message.content)
```

**Options:**
- A) embed
- B) get_model_info
- C) complete
- D) send_request

**Answer:** C) complete

**Why:** `ChatCompletionsClient.complete()` = send chat messages, receive completion. `embed` = vectors. `get_model_info` = metadata.

---

### Q52. What do you do when a safety score drops below the threshold?

**Source:** Test 2 — Q10

```python
safety_score = result["safety_score"]

if safety_score < 0.90:
    ________
else:
    print("Safety check passed")
```

**Options:**
- A) user_prompt = "hello"
- B) print(model_name.upper())
- C) send_alert("Safety threshold breached")
- D) endpoint = None

**Answer:** C) send_alert("Safety threshold breached")

**Why:** Operational response to safety degradation. Communicates breach to operators for investigation.

---

## 15. Cheat Sheets

### SDK Method Quick Reference

| SDK / Client | Method | Purpose |
|---|---|---|
| `TextAnalyticsClient` | `analyze_sentiment()` | Sentiment labels + opinion mining |
| `TextAnalyticsClient` | `recognize_entities()` | NER (people, orgs, locations) |
| `TextAnalyticsClient` | `extract_key_phrases()` | Main topics/talking points |
| `TextAnalyticsClient` | `detect_language()` | Language code + confidence |
| `SpeechRecognizer` | `recognize_once_async().get()` | STT: single utterance |
| `SpeechSynthesizer` | `speak_text_async(text).get()` | TTS: text to audio |
| `SpeechTranslationConfig` | `add_target_language("fr")` | Add translation target |
| `ImageAnalysisClient` | `analyze_from_url()` | Analyze image from public URL |
| `ImageAnalysisClient` | `analyze()` | Analyze image (general) |
| `ContentUnderstandingClient` | `begin_analyze()` | Start async extraction |
| poller | `result()` | Get completed analysis |
| `ContentSafetyClient` | `analyze_text()` | Text moderation |
| `EmbeddingsClient` | `embed()` | Generate vectors |
| `ChatCompletionsClient` | `complete()` | Chat completion |
| `AIProjectClient` | `get_openai_client()` | Get OpenAI-compatible client |
| openai | `conversations.create()` | Start multi-turn conversation |
| openai | `responses.create()` | Send prompt / generate response |

### Constructor Patterns

```python
# TextAnalyticsClient: endpoint FIRST, then credential
TextAnalyticsClient(endpoint, AzureKeyCredential(key))

# AIProjectClient: named params, Entra ID only
AIProjectClient(endpoint=EP, credential=DefaultAzureCredential())

# ContentUnderstandingClient: same pattern
ContentUnderstandingClient(endpoint=EP, credential=AzureKeyCredential(key))

# Image Analysis: same pattern
ImageAnalysisClient(endpoint=EP, credential=AzureKeyCredential(key))
```

### Analyzer IDs

| Analyzer ID | Content Type |
|---|---|
| `prebuilt-audioSearch` | Audio (transcript, summary) |
| `prebuilt-videoSearch` | Video (key frames, transcript, RAG) |
| `prebuilt-imageSearch` | Image (description, search) |
| `prebuilt-image` | Base for custom image analyzers |
| `prebuilt-invoice` | Invoice field extraction |
| `prebuilt-procurement` | Mixed procurement docs |
| `prebuilt-documentSearch` | Document RAG/search ingestion |

### Key Parameter Names

| Parameter | API | Purpose |
|---|---|---|
| `output_format` | GPT-image-1 | Image format (png/jpeg) |
| `response_format` | DALL-E 3 | Image format (DALL-E only) |
| `max_completion_tokens` | Chat completions | Cap generated tokens |
| `previous_response_id` | Responses API | Multi-turn continuation |
| `input` | Responses API | Prompt text |
| `instructions` | PromptAgentDefinition | Agent behavior rules |
| `smartCropping` | Generate Thumbnail API | Content-aware crop |
| `base_analyzer_id` | Custom analyzer | Parent prebuilt analyzer |

### Chat Completions vs Responses API — Image Input

| API | Type Field | Image Field |
|---|---|---|
| Chat Completions | `"type": "image_url"` | `"image_url": {"url": url}` |
| Responses API | `"type": "input_image"` | `"image_url": "data:image/jpeg;base64,..."` |
