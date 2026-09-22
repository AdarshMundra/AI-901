# AI-901 Coding Snippet Questions

All code-based questions from Test 1-6, organized by SDK/service area.

---

## Table of Contents
1. [Azure Text Analytics (Language)](#azure-text-analytics-language)
2. [Azure Speech SDK](#azure-speech-sdk)
3. [Azure Vision Image Analysis](#azure-vision-image-analysis)
4. [Azure Content Understanding](#azure-content-understanding)
5. [Foundry SDK (AIProjectClient + Agents)](#foundry-sdk-aiprojectclient--agents)
6. [Chat Completions API](#chat-completions-api)
7. [Responses API](#responses-api)
8. [Multimodal / Vision Chat](#multimodal--vision-chat)
9. [Image Generation](#image-generation)
10. [Embeddings](#embeddings)
11. [Content Safety](#content-safety)
12. [Prompt Engineering (Code-Based)](#prompt-engineering-code-based)
13. [Workload Mapping (Code-Based)](#workload-mapping-code-based)
14. [Miscellaneous SDK Patterns](#miscellaneous-sdk-patterns)

---

## Azure Text Analytics (Language)

### T1-Q2 / T6-Q2: Sentiment Analysis Method
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
result = client.analyze_sentiment(documents, show_opinion_mining=True)  # <-- ANSWER
doc = [item for item in result if not item.is_error][0]
print(doc.sentiment)
```
**Answer:** `analyze_sentiment`
**Why:** Returns sentiment labels (positive/negative/neutral/mixed) + optional opinion mining. `detect_language` = language ID. `recognize_entities` = NER. `extract_key_phrases` = topics.

---

### T5-Q26: TextAnalyticsClient Constructor (Parameter Order)
```python
import os
from azure.core.credentials import AzureKeyCredential
from azure.ai.textanalytics import TextAnalyticsClient

endpoint = os.environ["AZURE_LANGUAGE_ENDPOINT"]
key = os.environ["AZURE_LANGUAGE_KEY"]

text_analytics_client = TextAnalyticsClient(endpoint, AzureKeyCredential(key))  # <-- ANSWER
reviews = ["The support team was very helpful."]
result = text_analytics_client.analyze_sentiment(reviews)
```
**Answer:** `TextAnalyticsClient(endpoint, AzureKeyCredential(key))`
**Why:** Constructor order = **endpoint FIRST**, then `AzureKeyCredential(key)`. Swapping them (key first) or wrapping endpoint in credential = wrong.

---

### T4-Q28: Named Entity Recognition
```python
from azure.ai.textanalytics import TextAnalyticsClient
from azure.core.credentials import AzureKeyCredential

client = TextAnalyticsClient(endpoint=endpoint, credential=AzureKeyCredential(key))
document = "Contoso signed a contract in Sydney on 12 March."

response = client.recognize_entities([document])[0]  # <-- ANSWER
```
**Answer:** `recognize_entities`
**Why:** Extracts typed entities (organizations, locations, dates). `extract_key_phrases` = keywords. `analyze_sentiment` = tone. `detect_language` = language ID.

---

### T5-Q35: Entity Extraction with doc.entities Loop
```python
messages = ["Contoso opened an office in Sydney on Monday."]
result = text_analytics_client.recognize_entities(messages)  # <-- ANSWER
for doc in result:
    for entity in doc.entities:
        print(entity.text, entity.category)
```
**Answer:** `text_analytics_client.recognize_entities(messages)`
**Why:** Only `recognize_entities` returns `doc.entities` with `.text` and `.category` attributes. Other methods return different structures.

---

### T5-Q49: Key Phrase Extraction with doc.key_phrases Loop
```python
tickets = ["Delivery was late but the driver was polite."]
result = text_analytics_client.extract_key_phrases(tickets)  # <-- ANSWER
for doc in result:
    print(doc.key_phrases)
```
**Answer:** `text_analytics_client.extract_key_phrases(tickets)`
**Why:** Only `extract_key_phrases` populates `doc.key_phrases`. Sentiment returns labels, entities returns entity objects, detect_language returns language codes.

---

## Azure Speech SDK

### T2-Q8 / T6-Q42: Speech-to-Text (Microphone Recognition)
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

result = speech_recognizer.recognize_once_async().get()  # <-- ANSWER
print(result.text)
```
**Answer:** `recognize_once_async`
**Why:** Captures one utterance from microphone, returns transcribed text. `speak_text_async` = TTS (wrong direction). `analyze_sentiment` = Azure Language. `create_version` = agent lifecycle.

---

### T2-Q34: AudioConfig for Default Microphone
```python
import azure.cognitiveservices.speech as speechsdk

audio_config = speechsdk.audio.AudioConfig(use_default_microphone=True)  # <-- ANSWER

recognizer = speechsdk.SpeechRecognizer(
    speech_config=speech_config,
    audio_config=audio_config
)
```
**Answer:** `AudioConfig(use_default_microphone=True)`
**Why:** Configures SDK to capture from system's default mic. `filename="meeting.wav"` = reads from file. `use_default_microphone=False` = disables mic.

---

### T2-Q35: Single Utterance Async Recognition
```python
recognizer = speechsdk.SpeechRecognizer(
    speech_config=speech_config,
    audio_config=audio_config
)

result_future = recognizer.recognize_once_async()  # <-- ANSWER
```
**Answer:** `recognize_once_async`
**Why:** Single-utterance recognition (listens until one complete utterance). `start_continuous_recognition_async` = long-running stream. `speak_text_async` = synthesis.

---

### T2-Q31 / T6-Q45: Text-to-Speech Synthesis
```python
import azure.cognitiveservices.speech as speechsdk

speech_config.speech_synthesis_voice_name = "en-US-Ava:DragonHDLatestNeural"
synthesizer = speechsdk.SpeechSynthesizer(speech_config=speech_config)

result = synthesizer.speak_text_async("Your order ships today.").get()  # <-- ANSWER
```
**Answer:** `synthesizer.speak_text_async(text).get()`
**Why:** `SpeechSynthesizer.speak_text_async()` = TTS. Called on **synthesizer**, NOT recognizer. `recognize_once_async` = wrong direction (STT).

---

### T2-Q39: TTS speak_text_async Method Name
```python
speech_config.speech_synthesis_voice_name = "en-US-Ava:DragonHDLatestNeural"
synthesizer = speechsdk.SpeechSynthesizer(speech_config=speech_config)

result = synthesizer.speak_text_async("Thanks for calling Contoso.")  # <-- ANSWER
```
**Answer:** `speak_text_async`
**Why:** Plain-text TTS synthesis. `get_voices_async` = lists voices. `recognize_once_async` / `start_continuous_recognition_async` = recognition (wrong direction).

---

### T2-Q17: Speech Translation Target Language
```python
translation_config = speechsdk.translation.SpeechTranslationConfig(
    subscription=speech_key,
    region=service_region
)

translation_config.speech_recognition_language = "en-US"
translation_config.add_target_language("fr")  # <-- ANSWER
```
**Answer:** `add_target_language`
**Why:** Appends a target output language to the translation pipeline. `speak_text_async` / `recognize_once_async` = wrong objects. `remove_target_language` = opposite.

---

## Azure Vision Image Analysis

### T4-Q54 / T6-Q50: VisualFeatures.READ (OCR)
```python
from azure.ai.vision.imageanalysis import ImageAnalysisClient
from azure.ai.vision.imageanalysis.models import VisualFeatures

result = client.analyze(
    image_url=image_url,
    visual_features=[VisualFeatures.READ]  # <-- ANSWER for OCR
)
```
**Answer:** `VisualFeatures.READ` for reading text, `VisualFeatures.CAPTION` for description
**Why:** READ = OCR (extract printed/handwritten text). CAPTION = one-sentence image description. OBJECTS = detect objects. PEOPLE = detect people. SMART_CROPS = crop regions.

---

### T5-Q46: analyze_from_url Method
```python
from azure.ai.vision.imageanalysis.models import VisualFeatures

image_url = "https://contoso.com/menu.jpg"

result = client.analyze_from_url(  # <-- ANSWER
    image_url=image_url,
    visual_features=[VisualFeatures.CAPTION, VisualFeatures.READ]
)
```
**Answer:** `analyze_from_url`
**Why:** Documented `ImageAnalysisClient` method for URL-based image analysis. Supports multiple visual features in one call. `get_image`, `captions_from_url`, `detect_visuals` = not real methods.

---

### T5-Q54: Image Analysis API Query String (People + OCR)
```
POST {endpoint}/computervision/imageanalysis:analyze
    ?api-version=2024-02-01
    &features=people,read    <-- ANSWER
```
**Answer:** `features=people,read`
**Why:** `people` = bounding boxes + confidence for detected people. `read` = OCR structured text. `objects` = general objects (not dedicated people detection). `tags` = keywords only. `caption` = description sentence.

---

### T6-Q64: Smart Cropping Thumbnail API
```
POST {endpoint}/vision/v3.2/generateThumbnail
    ?width=600
    &height=600
    &smartCropping=true    <-- ANSWER
```
**Answer:** `smartCropping=true`
**Why:** Content-aware cropping preserves most important region. `smartCropping=false` = naive crop. `detectOrientation` = rotation only. `visualFeatures=objects` = wrong API endpoint.

---

## Azure Content Understanding

### T3-Q6: Audio Analyzer ID
```python
audio_url = "https://example.com/call.mp3"

poller = client.begin_analyze(
    analyzer_id="prebuilt-audioSearch",  # <-- ANSWER
    inputs=[AnalysisInput(url=audio_url)],
)
result = poller.result()
```
**Answer:** `"prebuilt-audioSearch"`
**Why:** For audio extraction (transcript, summary, speaker labeling). `prebuilt-videoSearch` = video. `prebuilt-imageSearch` = image. `prebuilt-document` = documents.

---

### T2-Q54: Image Analyzer ID
```python
from azure.ai.contentunderstanding.models import AnalysisInput

image_url = "https://raw.githubusercontent.com/.../pieChart.jpg"

poller = client.begin_analyze(
    analyzer_id="prebuilt-imageSearch",  # <-- ANSWER
    inputs=[AnalysisInput(url=image_url)],
)
result = poller.result()
```
**Answer:** `"prebuilt-imageSearch"`
**Why:** For image description/search. `prebuilt-image` = base for custom analyzers (not direct use). `prebuilt-layout` = document-oriented. `prebuilt-documentSearch` = document/RAG.

---

### T3-Q28: Video Result Property (markdown)
```python
poller = client.begin_analyze(
    analyzer_id="prebuilt-videoSearch",
    inputs=[AnalysisInput(url=video_url)],
)
result = poller.result()

for media in result.contents:
    video_content = media
    print(video_content.markdown)  # <-- ANSWER
```
**Answer:** `markdown`
**Why:** Video content is packaged as richly formatted Markdown for downstream use (RAG-ready).

---

### T4-Q22: Reading Summary Field from Result
```python
result = poller.result()
content = result.contents[0]
summary = content.fields.get("Summary")  # <-- ANSWER
```
**Answer:** `"Summary"`
**Why:** Extracted fields are accessed by string name. `"Summary"` is the documented key. `"AnalyzerId"`, `"Credential"`, `"Endpoint"` = connection metadata, not result fields.

---

### T4-Q49: ContentUnderstandingClient Setup
```python
from azure.core.credentials import AzureKeyCredential
from azure.ai.contentunderstanding import ContentUnderstandingClient  # <-- ANSWER

client = ContentUnderstandingClient(  # <-- ANSWER
    endpoint=endpoint,
    credential=AzureKeyCredential(key)
)
```
**Answer:** `ContentUnderstandingClient`
**Why:** SDK entry point for Content Understanding operations. `SearchClient` = Azure AI Search. `TextAnalyticsClient` = Language. `ImageAnalysisClient` = Vision.

---

### T4-Q58: Submitting Document URL for Extraction
```python
poller = client.begin_analyze(
    analyzer_id="prebuilt-invoice",
    inputs=[AnalysisInput(url=file_url)],  # <-- ANSWER
)
result = poller.result()
```
**Answer:** `inputs=[AnalysisInput(url=file_url)]`
**Why:** Runtime submission uses `inputs=[AnalysisInput(url=...)]`. `field_schema` = analyzer definition. `base_analyzer_id` = custom analyzer creation.

---

### T6-Q13: Async Poller result() Method
```python
async def main():
    async with ContentUnderstandingClient(
        endpoint=endpoint, credential=AzureKeyCredential(key)
    ) as client:
        poller = await client.begin_analyze(
            analyzer_id="prebuilt-invoice",
            inputs=[AnalysisInput(url=file_url)]
        )
        result = await poller.result()  # <-- ANSWER
        print(result.contents[0].fields["CustomerName"].value)
```
**Answer:** `result()`
**Why:** Azure SDK async pattern: `begin_analyze()` -> poller -> `await poller.result()`. NOT `wait()`, `get_result()`, or `poll_until_done()`.

---

### T2-Q60: Custom Analyzer Base ID
```python
analyzer = ContentAnalyzer(
    base_analyzer_id="prebuilt-image",  # <-- ANSWER
    description="Custom analyzer for charts and graphs",
    field_schema=field_schema,
    models={"completion": "gpt-4.1"},
)
```
**Answer:** `base_analyzer_id="prebuilt-image"`
**Why:** Custom image analyzers inherit from `prebuilt-image`. Parameter is `base_analyzer_id` (not `analyzer_id`). `prebuilt-imageSearch` = for direct prebuilt use, not custom inheritance.

---

## Foundry SDK (AIProjectClient + Agents)

### T2-Q51 / T4-Q41 / T6-Q28: Get OpenAI Client
```python
from azure.identity import DefaultAzureCredential
from azure.ai.projects import AIProjectClient

project = AIProjectClient(
    endpoint=PROJECT_ENDPOINT,
    credential=DefaultAzureCredential(),
)

openai = project.get_openai_client()  # <-- ANSWER
```
**Answer:** `project.get_openai_client()`
**Why:** Documented method to get OpenAI-compatible client. NOT `openai_client()` (wrong name), NOT `AIProjectClient.get_openai_client()` (class vs instance), NOT `responses_client()`.

---

### T4-Q38: Creating AIProjectClient
```python
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential

PROJECT_ENDPOINT = "your_project_endpoint"

project = AIProjectClient(endpoint=PROJECT_ENDPOINT, credential=DefaultAzureCredential())  # <-- ANSWER
openai = project.get_openai_client()
```
**Answer:** `AIProjectClient(endpoint=PROJECT_ENDPOINT, credential=DefaultAzureCredential())`
**Why:** Constructor takes `endpoint=` URL and `credential=DefaultAzureCredential()`. NOT `model=`, `agent_name=`, or `api_key=DefaultAzureCredential()`.

---

### T3-Q20 / T4-Q47: Prompt Agent Definition
```python
from azure.ai.projects.models import PromptAgentDefinition

agent = project.agents.create_version(
    agent_name=AGENT_NAME,
    definition=PromptAgentDefinition(
        model="gpt-5-mini",
        instructions="You are a helpful assistant",  # <-- ANSWER
    ),
)
```
**Answer:** `PromptAgentDefinition(model=MODEL_NAME, instructions="...")`
**Why:** `instructions=` defines the agent's behavior. Core field that distinguishes configured agent from bare model.

---

### T4-Q56 / T6-Q30: Creating a Multi-Turn Conversation
```python
openai = project.get_openai_client()

conversation = openai.conversations.create()  # <-- ANSWER

response = openai.responses.create(
    conversation=conversation.id,
    extra_body={"agent_reference": {"name": AGENT_NAME, "type": "agent_reference"}},
    input="Hello, agent!",
)
```
**Answer:** `openai.conversations.create()`
**Why:** Creates conversation container for multi-turn state. Pass `conversation.id` to subsequent `responses.create()`. NOT `responses.create()` (generates response), NOT `threads.create()` (older pattern).

---

### T3-Q35: Calling Portal-Created Agent from Python
```python
conversation = openai.conversations.create()

response = openai.responses.create(
    conversation=conversation.id,
    extra_body={"agent_reference": {"name": AGENT_NAME, "type": "agent_reference"}},  # <-- ANSWER
    input="Summarize the customer issue."
)
```
**Answer:** `{"agent_reference": {"name": AGENT_NAME, "type": "agent_reference"}}`
**Why:** Routes request to the portal-configured agent with all its instructions and tools. NOT `{"tool": ...}`, `{"deployment": ...}`, or `{"conversation_id": ...}`.

---

## Chat Completions API

### T6-Q33: Preserving System Message in Conversation History
```python
system_message = {"role": "system", "content": "You are a helpful assistant."}
conversation = []

conversation.append(system_message)  # <-- ANSWER

user_input = "What is thermodynamics?"
conversation.append({"role": "user", "content": user_input})

response = client.chat.completions.create(
    model="YOUR-DEPLOYMENT-NAME",
    messages=conversation,
    temperature=0.7,
    max_tokens=250
)
```
**Answer:** `conversation.append(system_message)`
**Why:** System message goes first in messages array. NOT `clear()` (destroys context), NOT append assistant with user content (wrong role), NOT replace list with string.

---

### T4-Q25: Azure Deployment Name as model Parameter
```python
deployment_name = "support-chat-prod"

response = client.chat.completions.create(
    model=deployment_name,  # <-- ANSWER (pass the variable, not a model family name)
    messages=[{"role": "user", "content": "Summarize this case."}]
)
```
**Answer:** `deployment_name`
**Why:** Azure OpenAI uses `model=` for the **deployment name**, not the model family. Pass the variable holding your deployment identifier.

---

### T4-Q60: max_completion_tokens Parameter
```python
response = client.chat.completions.create(
    model="support-chat-prod",
    messages=[{"role": "user", "content": "Give me a one-sentence summary."}],
    temperature=0.2,
    max_completion_tokens=60  # <-- ANSWER
)
```
**Answer:** `max_completion_tokens`
**Why:** Hard upper bound on generated tokens. `top_p` = sampling probability. `presence_penalty` = new topics. `frequency_penalty` = reduce repetition.

---

## Responses API

### T2-Q53: Responses API Input Parameter
```python
response = openai_client.responses.create(
    model=DEPLOYMENT_NAME,
    input="Summarize the benefits of autoscaling."  # <-- ANSWER
)
print(response.output_text)
```
**Answer:** `input`
**Why:** Responses API uses `input=` (not `prompt`, `message`, or `question`). Confirmed by `response.output_text` accessor.

---

### T6-Q40: Multi-Turn with previous_response_id
```python
response = client.responses.create(
    model="gpt-4o",
    input="Explain what a vector database does."
)

follow_up = client.responses.create(
    model="gpt-4o",
    previous_response_id=response.id,  # <-- ANSWER
    input=[{"role": "user", "content": "Now explain it to a beginner."}]
)
```
**Answer:** `previous_response_id=response.id`
**Why:** Links follow-up to prior response for conversation continuity. NOT `tool_choice` (tool behavior), `store` (persistence), or `instructions=response.id` (wrong usage).

---

## Multimodal / Vision Chat

### T3-Q22 / T5-Q37: ImageContentItem (Azure AI Inference SDK)
```python
from azure.ai.inference.models import UserMessage, TextContentItem, ImageContentItem, ImageUrl

image_url = "https://contoso.com/shelf.jpg"

messages = [
    UserMessage(content=[
        TextContentItem(text="Describe the products in this image."),
        ImageContentItem(image_url=ImageUrl(image_url))  # <-- ANSWER
    ])
]
```
**Answer:** `ImageContentItem(image_url=ImageUrl(image_url))`
**Why:** Image input = `ImageContentItem` with `image_url=ImageUrl(...)`. NOT `text=image_url` (wrong property), NOT `AudioContentItem` (wrong modality), NOT `TextContentItem` wrapping `ImageUrl`.

---

### T6-Q47: Vision Chat (Chat Completions API format)
```python
response = client.chat.completions.create(
    model=deployment_name,
    messages=[{
        "role": "user",
        "content": [
            {"type": "text", "text": "What damage do you see on this package?"},
            {"type": "image_url", "image_url": {"url": image_url}}  # <-- ANSWER
        ]
    }]
)
```
**Answer:** `{"type": "image_url", "image_url": {"url": image_url}}`
**Why:** Chat Completions API uses `type: "image_url"` with nested `image_url.url`. NOT `audio`, `ocr`, or `caption` types.

---

### T6-Q52: Base64 Image in Responses API
```python
response = client.responses.create(
    model="gpt-4o",
    input=[{
        "role": "user",
        "content": [
            {"type": "input_text", "text": "Describe the damaged area in this image."},
            {"type": "input_image", "image_url": f"data:image/jpeg;base64,{base64_image}"}  # <-- ANSWER
        ]
    }]
)
```
**Answer:** `{"type": "input_image", "image_url": f"data:image/jpeg;base64,{base64_image}"}`
**Why:** Responses API uses `type: "input_image"` (NOT `"image_url"` which is chat completions). Local files = data URL format.

### KEY DISTINCTION: Chat Completions vs Responses API Image Input
| API | Type Field | Image Field |
|---|---|---|
| Chat Completions | `"type": "image_url"` | `"image_url": {"url": url}` |
| Responses API | `"type": "input_image"` | `"image_url": "data:image/jpeg;base64,..."` |

---

### T3-Q55: Loading Local Image as Data URL
```python
from azure.ai.inference.models import ImageUrl

data_url = ImageUrl.load(image_file="receipt.jpg", image_format="jpeg")  # <-- ANSWER
```
**Answer:** `ImageUrl.load(image_file="receipt.jpg", image_format="jpeg")`
**Why:** Documented helper that converts local file into a data URL for `ImageContentItem`. NOT `ImageUrl(image_file=...)` (no `.load()`), NOT `TextContentItem`, NOT `AudioContentItem`.

---

## Image Generation

### T4-Q2: GPT-image-1 Transparent Background
```python
result = client.images.generate(
    model="gpt-image-1",
    prompt="A flat icon of a blue rocket",
    n=1,
    size="1024x1024",
    background="transparent",
    output_format="png"  # <-- ANSWER
)
```
**Answer:** `output_format`
**Why:** GPT-image-1 uses `output_format` (not `response_format` which is DALL-E 3 only). PNG required for transparency.

---

### T3-Q24: Image Generation Payload Prompt Key
```python
payload = {
    "model": deployment_name,
    "prompt": "A red bicycle in a park",  # <-- ANSWER
    "width": 1024,
    "height": 1024
}
```
**Answer:** `"prompt": "A red bicycle in a park"`
**Why:** The `"prompt"` key is the text-to-image generation input. NOT `"ocr"`, `"objects"`, or `"caption"`.

---

### T3-Q31: MAI Image Model Endpoint Path
```python
endpoint = os.environ["AZURE_ENDPOINT"]
url = f"{endpoint}/mai/v1/images/generations"  # <-- ANSWER
```
**Answer:** `mai/v1/images/generations`
**Why:** MAI image generation models use this path. NOT `vision/v1/ocr`, `speech/v1/synthesize`, or `language/v1/entities`.

---

## Embeddings

### T3-Q17: OpenAI SDK Embeddings
```python
from openai import OpenAI

client = OpenAI(
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
    base_url="https://YOUR-RESOURCE-NAME.openai.azure.com/openai/v1/"
)

text = "Contoso invoice 1024 is overdue"
response = client.embeddings.create(input=text, model="text-embedding-3-large")  # <-- ANSWER
print(response.data[0].embedding[:5])
```
**Answer:** `client.embeddings.create(input=text, model="text-embedding-3-large")`
**Why:** Returns `response.data[0].embedding` (vector array). NOT images.generate, audio.transcriptions, or chat.completions.

---

### T2-Q21: Azure AI Inference EmbeddingsClient
```python
from azure.ai.inference import EmbeddingsClient
from azure.core.credentials import AzureKeyCredential

client = EmbeddingsClient(endpoint=endpoint, credential=AzureKeyCredential(key))

response = client.embed(  # <-- ANSWER
    input=["invoice number", "bill identifier", "customer address"]
)
print(len(response.data[0].embedding))
```
**Answer:** `embed`
**Why:** `EmbeddingsClient.embed()` = generate embedding vectors. `complete` = wrong client. `get_model_info` = metadata. `send_request` = low-level transport.

---

## Content Safety

### T2-Q5: Content Safety analyze_text
```python
from azure.ai.contentsafety import ContentSafetyClient
from azure.ai.contentsafety.models import AnalyzeTextOptions
from azure.core.credentials import AzureKeyCredential

client = ContentSafetyClient(endpoint, AzureKeyCredential(key))
request = AnalyzeTextOptions(text=user_text)

result = client.analyze_text(request)  # <-- ANSWER
print(result)
```
**Answer:** `analyze_text`
**Why:** Submits text for moderation, returns harm-category scores. `summarize_text`, `extract_entities`, `transcribe_audio` = different workloads.

---

## Prompt Engineering (Code-Based)

### T5-Q4: Few-Shot Pattern (Next Message After Example Pair)
```python
messages = [
    {"role": "system", "content": "Classify sentiment as Positive, Neutral, or Negative."},
    {"role": "user", "content": "The setup was easy and the support team helped immediately."},
    {"role": "assistant", "content": "Positive"},
    {"role": "user", "content": "The app kept crashing and nobody replied for two days."}  # <-- ANSWER
]
```
**Answer:** `{"role": "user", "content": "The app kept crashing and nobody replied for two days."}`
**Why:** Few-shot = system -> user/assistant pairs -> NEW user message (the real input to classify). Must maintain user->assistant alternation pattern.

---

### T5-Q20: Chat Request Missing User Message
```python
messages = [
    {"role": "system", "content": "You are a support assistant. If key details are missing, ask one clarifying question before answering."},
    {"role": "user", "content": "My printer keeps failing after the update."}  # <-- ANSWER
]

response = client.chat.completions.create(model="gpt-4.1-mini", messages=messages)
```
**Answer:** `{"role": "user", "content": "My printer keeps failing after the update."}`
**Why:** After system message, need a USER message with the actual request. System prompt already defines behavior; what's missing is the user's input.

---

## Workload Mapping (Code-Based)

### T5-Q6: Image Generation Workload
```python
prompt = "Create a winter sale poster with skis and snow"
goal = "produce a brand-new image"

workload = "Image generation"  # <-- ANSWER
print(workload)
```
**Answer:** `"Image generation"`
**Why:** Text prompt input -> new image output = image generation workload.

---

### T5-Q32: Speech to Text Workload
```python
scenario = "live microphone audio"
goal = "convert spoken words to text"

workload = "Speech to Text"  # <-- ANSWER
print(workload)
```
**Answer:** `"Speech to Text"`
**Why:** Spoken audio input -> written text output = Speech to Text.

---

## Miscellaneous SDK Patterns

### T3-Q38: Avoiding Hard-Coded API Key
```python
import os
from openai import AzureOpenAI

endpoint = os.getenv("AZURE_OPENAI_ENDPOINT")
key = os.getenv("AZURE_OPENAI_KEY")  # <-- ANSWER

client = AzureOpenAI(
    azure_endpoint=endpoint,
    api_key=key,
    api_version="2024-10-21"
)
```
**Answer:** `os.getenv("AZURE_OPENAI_KEY")`
**Why:** Environment variable avoids hard-coding secrets. NOT `"my-secret-key"` (hard-coded), NOT `print(...)` (prints literal string), NOT `endpoint` (wrong value).

---

### T2-Q46: ChatCompletionsClient.complete() Method
```python
from azure.ai.inference import ChatCompletionsClient
from azure.ai.inference.models import SystemMessage, UserMessage
from azure.core.credentials import AzureKeyCredential

client = ChatCompletionsClient(endpoint=endpoint, credential=AzureKeyCredential(key))

response = client.complete(  # <-- ANSWER
    messages=[
        SystemMessage("You are a helpful assistant."),
        UserMessage("Write a two-sentence description of solar panels.")
    ]
)
print(response.choices[0].message.content)
```
**Answer:** `complete`
**Why:** `ChatCompletionsClient.complete()` = send chat messages, receive completion. `embed` = vectors. `get_model_info` = metadata.

---

### T2-Q10: Safety Score Alert Pattern
```python
safety_score = result["safety_score"]

if safety_score < 0.90:
    send_alert("Safety threshold breached")  # <-- ANSWER
else:
    print("Safety check passed")
```
**Answer:** `send_alert("Safety threshold breached")`
**Why:** Operational response to safety degradation. Communicates breach to operators for investigation.

---

### T2-Q16: Content Understanding Custom Analyzer Schema (JSON)
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
**Key Facts:** Title returns a **string** value. ChartType uses **classify** method (not OCR). Base is `prebuilt-image` (not audio). Enum belongs to ChartType (not Title).

---

# Quick Reference: SDK Method Cheat Sheet

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

# Quick Reference: Constructor Patterns

```python
# TextAnalyticsClient: endpoint FIRST, then credential
TextAnalyticsClient(endpoint, AzureKeyCredential(key))

# AIProjectClient: named params
AIProjectClient(endpoint=EP, credential=DefaultAzureCredential())

# ContentUnderstandingClient: same pattern
ContentUnderstandingClient(endpoint=EP, credential=AzureKeyCredential(key))

# Image Analysis: same pattern
ImageAnalysisClient(endpoint=EP, credential=AzureKeyCredential(key))
```

# Quick Reference: Analyzer IDs

| Analyzer ID | Content Type |
|---|---|
| `prebuilt-audioSearch` | Audio (transcript, summary) |
| `prebuilt-videoSearch` | Video (key frames, transcript, RAG) |
| `prebuilt-imageSearch` | Image (description, search) |
| `prebuilt-image` | Base for custom image analyzers |
| `prebuilt-invoice` | Invoice field extraction |
| `prebuilt-procurement` | Mixed procurement docs |
| `prebuilt-documentSearch` | Document RAG/search ingestion |

# Quick Reference: Key Parameter Names

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
