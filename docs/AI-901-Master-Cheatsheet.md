# AI-901 Master Cheat Sheet — Final Revision

**Exam:** AI-901 Azure AI Fundamentals | **Passing:** 700/1000 | **Format:** MCQ, drag-drop, case studies  
**Domain 1 (40-45%):** AI Concepts & Capabilities | **Domain 2 (55-60%):** Implement AI Solutions using Microsoft Foundry

---

## 1. Responsible AI — 6 Principles (F-R-P-I-T-A)

| Principle | Core Definition | Key Scenarios / Clues | NOT This |
|---|---|---|---|
| **Fairness** | Treat similar people fairly across groups, avoid bias | Representative data, compare outcomes across demographics, underrepresentation = risk | NOT inclusiveness (separate principle), NOT explaining predictions (that's transparency) |
| **Reliability & Safety** | Perform safely under all conditions | Edge-case testing, adversarial testing, fallback behavior, content filtering, red-team testing | NOT transparency (behavior under unexpected conditions ≠ understandable decisions) |
| **Privacy & Security** | Protect data, control access | RBAC, encryption, managed identity, data minimisation, least-privilege | NOT transparency (encryption ≠ explaining decisions) |
| **Inclusiveness** | Accessible to all abilities and backgrounds | Screen readers, captions, voice+text input, keyboard navigation, multiple interaction modes | NOT fairness (accessible design ≠ equitable treatment) |
| **Transparency** | Users understand how AI works, its capabilities and limitations | Transparency notes, labeling AI output, explaining how predictions are made | NOT fairness, NOT privacy |
| **Accountability** | People remain answerable for AI system behavior | Audit trails, documented approvals, governance sign-off, human review, incident response owners | NOT about hiding info or removing oversight |

### Critical Accountability Rules
- AI should **NOT** be the final authority for decisions that affect people's lives
- Organization remains **accountable** even when using managed AI services
- Log who published a model, why it changed, when it was deployed
- Governance sign-off before deployment = accountability
- Human reviewer required for high-impact cases

### Critical Fairness Rules
- Training data must be **representative** of affected populations
- Compare outcomes across **demographic/sensitive groups** to find bias
- Fairness ≠ Inclusiveness (separate principles)
- Explaining predictions = **transparency**, not fairness

---

## 2. Generative AI Fundamentals

### Model Parameters

| Parameter | What It Controls | Key Facts |
|---|---|---|
| **Temperature** | Randomness/creativity | 0 = deterministic, 1 = creative. Does NOT set conversation size or select grounding |
| **Top-p** | Nucleus sampling diversity | Uses probability mass. Microsoft says alter temp OR top_p, NOT both |
| **Max tokens / max_completion_tokens** | Output length cap | Hard upper bound on generated tokens |
| **Context window** | Input/conversation capacity | Limits how much input the model can consider. NOT a safety threshold |
| **Frequency penalty** | Reduces repeated tokens | Higher = less repetition |
| **Presence penalty** | Encourages new topics | Higher = more diverse topics |
| **System message** | AI's role, behavior, rules | Highest priority. Define persona, boundaries, fallback behavior |

### Key Concepts

| Term | Definition |
|---|---|
| **LLM** | Large Language Model — predicts next token, trained on massive text data |
| **Transformer** | Architecture foundation of modern generative AI |
| **Tokens** | Text broken into small units for processing |
| **Grounding** | Connecting AI responses to factual, verifiable data |
| **Fine-tuning** | Adapting a pre-trained model for specific tasks |
| **RAG** | Retrieval-Augmented Generation — search data first, then generate grounded answer with citations |
| **Foundry IQ** | Microsoft's RAG service for enterprise data |
| **Few-shot prompting** | Provide examples in prompt (NOT retraining — conditions current inference only) |
| **Zero-shot prompting** | Ask without examples, rely on model's training |
| **Base model** | Starting point before any customization or fine-tuning |

### AI Workload Types

| Workload | Type | Example |
|---|---|---|
| Generative AI | Creates new content | Chat, code generation, text creation |
| Traditional AI (classification) | Categorizes/classifies | Spam filter, sentiment classifier — NOT generative |
| AI Agent | Autonomous planner with tools | Multi-step reasoning + tool use + memory |
| Direct model call | Raw inference, no tools | Simple rewrite, summarize, classify |

---

## 3. Text Analytics / NLP (Azure Language)

### SDK Setup
```python
pip install azure-ai-textanalytics

from azure.core.credentials import AzureKeyCredential
from azure.ai.textanalytics import TextAnalyticsClient

client = TextAnalyticsClient(endpoint=endpoint, credential=AzureKeyCredential(key))
# endpoint FIRST, then credential
# All methods accept a LIST of strings: client.method(["text here"])
```

### Methods & Outputs

| Method | Returns | Use When |
|---|---|---|
| `analyze_sentiment(docs)` | `doc.sentiment` (positive/neutral/negative/mixed) + confidence scores | Classify attitude/polarity of text |
| `extract_key_phrases(docs)` | `doc.key_phrases` (list of main concepts) | Find main topics/talking points |
| `recognize_entities(docs)` | `doc.entities` (people, orgs, locations, dates, quantities) | Identify named items (NER) |
| `detect_language(docs)` | `doc.primary_language.name` + `.iso6391_name` + confidence | Which language is the text? |
| `recognize_pii_entities(docs)` | PII entities (emails, phones, IDs) for redaction | Find/redact personal information |

### Technique Matching (MEMORIZE)

| I Need To... | Use This |
|---|---|
| Classify reviews as positive/negative | **Sentiment analysis** |
| Find main topics (not a paragraph) | **Keyword extraction** |
| Identify people, orgs, locations | **Entity detection (NER)** |
| Condense a long report | **Summarization** |
| Determine what language text is in | **Language detection** |

### Key Distinctions
- Keyword extraction = short list of phrases. Summarization = condensed narrative paragraph
- Sentiment analysis outputs = document-level label + confidence scores (not entities or phrases)
- Opinion mining = `show_opinion_mining=True` with analyze_sentiment — returns target + assessment + sentiment per aspect
- Text PII = raw text strings. Conversation PII = structured conversation with speakers/turns

---

## 4. Speech SDK

### SDK Setup
```python
pip install azure-cognitiveservices-speech
import azure.cognitiveservices.speech as speechsdk

speech_config = speechsdk.SpeechConfig(subscription=key, endpoint=url)
```

### Core Classes

| Class | Purpose | Direction |
|---|---|---|
| `SpeechConfig` | Holds subscription key and endpoint | Configuration |
| `AudioConfig` | Input source (microphone or file) | Input |
| `AudioOutputConfig` | Output destination (speaker or file) | Output |
| `SpeechRecognizer` | Converts audio → text (STT) | Audio to Text |
| `SpeechSynthesizer` | Converts text → audio (TTS) | Text to Audio |
| `SpeechTranslationConfig` | Adds target languages | Translation |

### Key Methods

| Task | Code |
|---|---|
| Single utterance STT | `recognizer.recognize_once_async().get()` |
| Continuous STT | `recognizer.start_continuous_recognition_async()` (needs something to keep process alive) |
| Stop continuous | `recognizer.stop_continuous_recognition()` |
| TTS | `synthesizer.speak_text_async(text).get()` |
| Add translation target | `translation_config.add_target_language("fr")` |
| Microphone input | `AudioConfig(use_default_microphone=True)` |
| File input | `AudioConfig(filename="meeting.wav")` |

### Speech Events
- `recognizing` = partial/interim results (while speaking)
- `recognized` = final recognition result (phrase complete)

### Key Distinctions
- **SSML** = customize TTS: pitch, pronunciation, rate, volume (synthesis, NOT recognition)
- **Speaker diarization** = identify who spoke (recognition feature, NOT synthesis)
- **Batch transcription** = prerecorded files (NOT live captions)
- **Voice Live API** = low-latency speech-to-speech for voice agents
- **Custom speech** = improve recognition for domain-specific words (baseline model needs NO custom endpoint)
- Acoustic model = audio signals → phonemes. Language model = phonemes → words

---

## 5. Computer Vision & Image Generation

### Image Analysis 4.0 Features

| Feature | Returns | Use When |
|---|---|---|
| `CAPTION` | One sentence describing entire image | "What is this image?" |
| `DENSE_CAPTIONS` | Region-level captions with bounding boxes | Describe parts of an image |
| `READ` | OCR — structured text from visible text | Signs, labels, printed text |
| `OBJECTS` | Detected objects with bounding boxes | Find and locate specific items |
| `PEOPLE` | Detected people with bounding boxes + confidence | Person detection (use PEOPLE, not OBJECTS) |
| `TAGS` | Descriptive keywords | Categorize/label images |
| `SMART_CROPS` | Suggested crop regions | Content-aware cropping |

```python
pip install azure-ai-vision-imageanalysis
from azure.ai.vision.imageanalysis import ImageAnalysisClient
client = ImageAnalysisClient(endpoint=EP, credential=AzureKeyCredential(key))
result = client.analyze_from_url(image_url, visual_features=[...])
```

### Image Generation Models

| Model | Key Details |
|---|---|
| **DALL-E 3** | Older model, uses `response_format` (URL or base64) |
| **GPT-image-1** | Uses `output_format` (NOT response_format!), always returns `b64_json`, supports inpainting + transparency |
| **GPT-image-1.5** | Improved realism and instruction following |
| **MAI-Image-2** | Microsoft's photorealistic text-to-image |

- `response_format` = DALL-E 3 ONLY. `output_format` = GPT-image-1 ONLY
- Transparent background: `background="transparent"` + `output_format="png"`
- Images playground for generation models (NOT model playground)
- Inpainting = modify selected region of existing image
- Multimodal vision returns TEXT about an image (does NOT generate new images)

### Image Input Formats

| API | Type Field | Image Field |
|---|---|---|
| Chat Completions | `"type": "image_url"` | `"image_url": {"url": url}` |
| Responses API | `"type": "input_image"` | `"image_url": "data:image/jpeg;base64,..."` |
| Azure AI Inference SDK | Use `ImageUrl.load()` | `ImageUrl.load(image_file="x.jpg", image_format="jpeg")` |

---

## 6. Content Understanding (Foundry Tools)

### Analyzer IDs (MEMORIZE THIS TABLE)

| Analyzer ID | Purpose | Type |
|---|---|---|
| `prebuilt-invoice` | Domain-specific invoice extraction (vendor, date, total) | Domain-specific |
| `prebuilt-procurement` | Mixed procurement docs (POs + invoices) | Domain-specific |
| `prebuilt-document` | **BASE** for custom document analyzers | Base |
| `prebuilt-image` | **BASE** for custom image analyzers | Base |
| `prebuilt-documentFields` | Extract key-value pairs from documents | Utility |
| `prebuilt-documentFieldSchema` | **PROPOSE** field schema for new doc types | Utility |
| `prebuilt-documentSearch` | Document content for search/RAG | Utility |
| `prebuilt-audioSearch` | Audio: transcript, summary, speakers | Direct-use |
| `prebuilt-videoSearch` | Video: keyframes, transcript, chapters | Direct-use |
| `prebuilt-imageSearch` | Image descriptions | Direct-use |

### Config Options

| Option | Purpose |
|---|---|
| `enableOcr` | Read scanned PDFs and image-based documents |
| `estimateFieldSourceAndConfidence` | Return page number, bounding box, confidence for fields |
| `enableSegment` | Split document into logical sections |
| `disableFaceBlurring` | Image/video — NOT for document extraction |
| `locales` | Language-specific processing (audio/video, NOT document OCR) |

### GenerationMethod (for ContentFieldDefinition)

| Method | Use When |
|---|---|
| `EXTRACT` | Pull concrete value from document (InvoiceNumber, Name, Total) |
| `GENERATE` | Derive a summary or computed value |
| `CLASSIFY` | Categorize into predefined classes |

### Content Kind Values
- `audioVisual` = audio AND video (NOT "transcript" or "audio")
- `document` = documents and forms
- `image` = images

### SDK Pattern
```python
from azure.ai.contentunderstanding import ContentUnderstandingClient
client = ContentUnderstandingClient(endpoint=EP, credential=AzureKeyCredential(key))

poller = client.begin_analyze(
    analyzer_id="prebuilt-invoice",
    inputs=[AnalysisInput(url=file_url)]
)
result = poller.result()  # NOT wait(), get_result(), or poll_until_done()
```

### Critical Rules
- **Copy prebuilt analyzer for production** — definitions can change across API versions
- `base_analyzer_id` = parent to inherit from (when building custom analyzer)
- `analyzer_id` = this analyzer's own ID (when calling begin_analyze)
- prebuilt-document = base for custom. prebuilt-documentFields = utility for extraction (DIFFERENT!)
- prebuilt-documentFieldSchema proposes schema. prebuilt-documentFields extracts values (DIFFERENT!)

---

## 7. Foundry Portal Workflows

### Portal Navigation

| Path | Purpose |
|---|---|
| **Discover → Models** | Start a **NEW** model deployment |
| **Build → Models** | Manage **EXISTING** deployments |
| **Build → Tools** | Open tool catalog |
| **Model Playground** | Type prompts, see outputs, test models |
| **Agents Playground** | Define instructions, attach tools, test multi-turn agents |
| **Chat Playground** | Test audio models (gpt-4o-mini-audio-preview) |
| **Audio Playground** | Test gpt-realtime voice I/O (NOT gpt-4o-mini-audio-preview!) |
| **Images Playground** | Test image generation models |
| **Code Tab** | View programmatic access snippets |
| **Compare Models** | Side-by-side benchmarking (up to 3 models) |
| **Deployment Details Page** | View endpoint details and keys |

### Deployment Facts

| Fact | Detail |
|---|---|
| Ready state | Status must show **Succeeded** |
| New Foundry toggle | Must be **ON** for current portal steps |
| Partner/community models | Need Azure Marketplace subscription + Cognitive Services Contributor role |
| Azure-sold models | Do **NOT** need Marketplace subscription |
| 404 error | Deployment name mismatch — use deployment name, not base model name |
| model= parameter | Use **deployment name** during inference |

### Deployment Types

| Type | Key Facts |
|---|---|
| Standard | Preferred, widest capabilities, regional/data zone/global |
| Serverless | Pay-as-you-go, **regional ONLY** (cannot be global) |
| Managed compute | Dedicated compute, requires quota, needed for Hugging Face |
| Global Standard | Pay-per-token, interactive, unpredictable traffic |
| Global Batch | Async batch processing (NOT real-time) |
| Global Provisioned | Reserved hourly capacity |

---

## 8. AI Agents

### Agent Components
- **Model** = the LLM powering reasoning
- **Instructions** = system prompt defining behavior, personality, constraints
- **Tools** = external capabilities the agent can invoke

### Agent Tools

| Tool | Purpose |
|---|---|
| Web Search | Real-time public info with citations |
| File Search | Ground agent in uploaded documents |
| Code Interpreter | Python sandbox (math, analysis, charts, CSV) |
| OpenAPI | Connect to external HTTP APIs |
| Azure Functions | Queue-based integration with existing functions |
| Function Calling | Custom functions YOUR app executes (agent suggests, app runs) |
| MCP | Tools from MCP servers maintained by other teams |

### Agent SDK Pattern
```python
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential

# Entra ID ONLY — no API-key auth!
project_client = AIProjectClient(
    endpoint="https://<resource>.services.ai.azure.com/api/projects/<project>",
    credential=DefaultAzureCredential()
)
agent = project_client.agents.get(agent_name="my-agent")
openai_client = project_client.get_openai_client()  # NOT openai_client()

response = openai_client.responses.create(
    input=[{"role": "user", "content": "Hello"}],
    extra_body={"agent": {"name": agent.name, "type": "agent_reference"}}
)
```

### Key Facts
- Agent name **cannot** be changed after creation
- **Prompt agent** = no-code, portal-first, declaratively defined
- When to use agent: needs tools + multistep reasoning
- When to use direct call: simple rewrite, summarize, classify
- Test agents in playground BEFORE deploying to production
- Unsaved changes are **LOST** if you leave the portal

---

## 9. Chat Completions vs Responses API

| Feature | Chat Completions | Responses API |
|---|---|---|
| Prompt parameter | `messages=[{"role":"user", "content":"..."}]` | `input="..."` or `input=[{"role":"user","content":"..."}]` |
| Multi-turn | Manual message array management | `previous_response_id=response.id` |
| Image input type | `"type": "image_url"` | `"type": "input_image"` |
| Output access | `response.choices[0].message.content` | `response.output_text` |
| Agent routing | N/A | `extra_body={"agent": {...}}` |
| Model parameter | `model="deployment-name"` | `model="deployment-name"` |

### Common Code Patterns
```python
# Chat Completions
response = client.chat.completions.create(
    model="deployment-name",
    messages=[
        {"role": "system", "content": "You are helpful."},
        {"role": "user", "content": "Hello"}
    ],
    temperature=0.7,
    max_completion_tokens=200
)

# Responses API
response = client.responses.create(
    model="deployment-name",
    input="Summarize this.",
    temperature=0.7
)
print(response.output_text)

# Payload format (REST)
payload = {
    "model": deployment_name,  # deployment name goes here
    "input": "Summarize this."
}
```

---

## 10. Multimodal Audio

### Audio Input Methods

| Method | Type | Use When |
|---|---|---|
| `input_audio` | Inline encoded data | Send audio bytes directly in request |
| `audio_url` | Cloud-hosted URL | Audio file at accessible cloud location |

```python
# Inline audio input
{"type": "input_audio", "input_audio": {"data": encoded_string, "format": "wav"}}

# URL-based audio input  
{"type": "audio_url", "audio_url": {"url": "https://storage.blob.core.windows.net/audio.mp3"}}
```

### Audio Output
```python
completion = client.chat.completions.create(
    model="gpt-4o-mini-audio-preview",
    modalities=["text", "audio"],                          # Request audio output
    audio={"voice": "alloy", "format": "wav"},             # Voice config
    messages=[{"role": "user", "content": "Reply aloud."}]
)
```

### Key Rules
- `input_audio` = inline data. `audio_url` = URL reference. **Don't swap them!**
- Audio output = `modalities=["text", "audio"]` + `audio={}` config (BOTH required)
- `modalities=["text"]` = text-only (no audio output)
- **Chat playground** for gpt-4o-mini-audio-preview
- **Audio playground** does NOT support gpt-4o-mini-audio-preview
- Prerequisite: chat completions model deployment with audio/image support

---

## 11. SDK Constructor Patterns

| Client | Constructor | Auth |
|---|---|---|
| `TextAnalyticsClient` | `(endpoint, AzureKeyCredential(key))` | API Key |
| `ImageAnalysisClient` | `(endpoint=EP, credential=AzureKeyCredential(key))` | API Key |
| `ContentUnderstandingClient` | `(endpoint=EP, credential=AzureKeyCredential(key))` | API Key |
| `AIProjectClient` | `(endpoint=EP, credential=DefaultAzureCredential())` | **Entra ID ONLY** |
| `SpeechConfig` | `(subscription=key, endpoint=url)` | Subscription key |
| `OpenAI` (Azure) | `(base_url=endpoint, api_key=key)` | API Key |

### Package Install Commands

| Package | Service |
|---|---|
| `azure-ai-textanalytics` | Text Analytics |
| `azure-cognitiveservices-speech` | Speech SDK |
| `azure-ai-vision-imageanalysis` | Image Analysis |
| `azure-ai-contentunderstanding` | Content Understanding |
| `azure-ai-projects` | Foundry Agent SDK |
| `azure-identity` | DefaultAzureCredential |
| `openai` | OpenAI / Responses API |

### Environment Variables
```
AZURE_OPENAI_ENDPOINT    — Azure OpenAI resource URL
MODEL_DEPLOYMENT_NAME    — Deployment name (not model name)
API_KEY                  — API key (use .env + dotenv, NEVER hardcode)
```

---

## 12. Prompt Engineering

### Prompt Structure
```
System Message: role + boundaries + tone + output format + fallback behavior
User Message:   current task/request
```

### Best Practices
- **Specific task** + **constrained answer** + **stated format** + **fallback instruction**
- System prompt defines persona, constraints, what NOT to do
- Few-shot = include example user+assistant pairs in prompt
- After system + user + assistant example, next must be a USER message
- "If you don't know, say I don't know" = good fallback
- Avoid conflicting rules, open boundaries

---

## 13. Common Traps & Gotchas (MEMORIZE THESE)

| Trap | Correct Answer |
|---|---|
| Fairness = Inclusiveness? | **NO** — separate principles |
| AI should be final authority? | **NO** — humans maintain control |
| All models need Marketplace? | **NO** — only partner/community models |
| Audio playground for gpt-4o-mini-audio? | **NO** — use Chat playground |
| documentFields = documentFieldSchema? | **NO** — Fields extracts. FieldSchema proposes |
| Sentiment classifier = generative AI? | **NO** — classification is traditional AI |
| `response_format` for GPT-image-1? | **NO** — use `output_format`. response_format = DALL-E 3 |
| GPT-image-1 returns URL? | **NO** — always `b64_json` |
| AIProjectClient supports API keys? | **NO** — Entra ID only |
| Serverless endpoints can be global? | **NO** — regional ONLY |
| Batch transcription = live captions? | **NO** — batch = prerecorded only |
| SSML = recognition feature? | **NO** — SSML controls TTS (pitch/rate). Diarization = recognition |
| prebuilt-document = utility extractor? | **NO** — it's the BASE for custom analyzers |
| prebuilt-image = for direct image analysis? | **NO** — it's the BASE for custom image analyzers. Use prebuilt-imageSearch directly |
| Content Understanding audio kind = "audio"? | **NO** — use `audioVisual` |
| Transparency = encrypt data? | **NO** — encryption = privacy/security |
| Reliability = understandable decisions? | **NO** — that's transparency |
| "All Yes" impossible in Yes/No questions? | **NO** — some answers are Yes/Yes/Yes |
| Copy prebuilt not needed for production? | **YES** it IS needed — definitions can change across API versions |
| Use model name (not deployment name) for inference? | **NO** — use deployment name |
| Responses API prompt param = "prompt"? | **NO** — it's `input` |
| Explaining predictions = fairness? | **NO** — that's transparency |
| Model lineage = inclusiveness? | **NO** — that's accountability |
| Encryption = accountability? | **NO** — that's privacy/security |

---

## 14. "Which Service?" Quick Decision Tree

| I Need To... | Use This |
|---|---|
| Classify text sentiment | Azure Language — `analyze_sentiment()` |
| Find key topics in text | Azure Language — `extract_key_phrases()` |
| Find people/orgs/locations | Azure Language — `recognize_entities()` |
| Detect text language | Azure Language — `detect_language()` |
| Redact personal info | Azure Language — `recognize_pii_entities()` |
| Condense long text | Azure Language — summarization |
| Transcribe audio to text | Azure Speech — `SpeechRecognizer` |
| Generate spoken audio | Azure Speech — `SpeechSynthesizer` |
| Translate spoken language | Azure Speech — `SpeechTranslationConfig` |
| Extract data from invoices | Content Understanding — `prebuilt-invoice` |
| Extract key-value pairs from forms | Content Understanding — `prebuilt-documentFields` |
| Discover schema for new doc type | Content Understanding — `prebuilt-documentFieldSchema` |
| Process scanned PDFs | Content Understanding — `enableOcr` |
| Analyze what's in an image | Multimodal model (GPT-4o) |
| Generate images from text | Image generation (DALL-E, GPT-image-1) |
| Chat with AI | Deploy model + chat completions / responses API |
| Ground responses in company data | Foundry IQ (RAG) |
| Build autonomous AI with tools | AI Agent in Foundry |
| Test prompts without code | Foundry Playground |
| Test spoken prompts in portal | Chat Playground |
| Compare models side-by-side | Compare Models feature |
| Start new deployment | Discover → Models |
| Manage existing deployments | Build → Models |

---

## 15. Score Tracker — Weakest Areas

| Test | Score | Weakest Topics |
|---|---|---|
| Test 3 | 88% | — |
| Test 4 | 82% | — |
| Test 5 | 69% | Vision, Image Gen, Content Understanding |
| Test 6 | 66% | Content Understanding, Agents, Audio |
| Test 7 | 63% | Content Understanding (6/10 wrong), Audio (4/10 wrong), Foundry Portal |

**Priority review areas:**
1. Content Understanding analyzers (which analyzer for which task)
2. Multimodal audio (input_audio vs audio_url, output settings)
3. Foundry Portal navigation (Discover vs Build, deployment status)
4. Responsible AI principle matching (fairness vs transparency vs accountability)
