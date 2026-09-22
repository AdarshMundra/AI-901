# AI-901 Practice Assessment 4 — Q/A/Why Notes

**Total Questions:** 65  
**Correct:** 53 | **Incorrect:** 12  
**Score:** ~82%

:red_circle: = Incorrect answer

---

## Q1 :red_circle:
**Q:** Your Python app generated an image using GPT-image-1. Which field contains the image data you decode?  
**A:** C. b64_json  
**Why:** GPT-image-1 series models always return base64-encoded images. The `b64_json` field contains the base64-encoded output image data. Unlike DALL-E 3, GPT-image-1 does NOT return a URL — it always returns base64.

---

## Q2
**Q:** You want a transparent background. Complete: `________="png"`  
**A:** A. output_format  
**Why:** For GPT-image-1, `output_format` specifies PNG or JPEG. Transparent backgrounds require `background="transparent"` + `output_format="png"`. Note: `response_format` is for DALL-E 3, NOT GPT-image-1.

---

## Q3
**Q:** Statement 1: Screen-reader-friendly output supports inclusiveness. Statement 2: Requiring mouse input for every action improves inclusiveness. Statement 3: Voice and text interaction supports inclusiveness.  
**A:** B. Yes / No / Yes  
**Why:** Screen readers broaden access (Yes). Forcing one input method excludes users (No). Multiple interaction methods support diverse needs (Yes).

---

## Q4
**Q:** Which TWO actions best support inclusiveness for a global AI help desk? (Select TWO)  
**A:** A. Provide captions and voice input + C. Test with users who have different abilities  
**Why:** Captions/voice expand interaction methods. Testing with diverse users identifies barriers early. Limiting interaction styles, long data retention, and executive approvers don't improve inclusiveness.

---

## Q5
**Q:** Which THREE pairs are correctly matched? (Select THREE)  
**A:** A. Inclusiveness — supports users with different abilities + C. Fairness — avoids disadvantaging groups + E. Transparency — helps users understand system behavior  
**Why:** Each maps the correct principle. Privacy ≠ explaining limitations (that's transparency). Accountability ≠ encryption (that's privacy/security). Reliability ≠ captions (that's inclusiveness).

---

## Q6
**Q:** AI kiosk used in noisy factory and quiet office. Which change improves inclusiveness?  
**A:** A. Add text and speech interaction  
**Why:** Text works in noisy environments, speech helps when typing is inconvenient. Multiple interaction modes = more inclusive. Log retention, publishing approver, and hourly sign-in don't improve access.

---

## Q7
**Q:** AI resume assistant review — which TWO findings are strongest inclusiveness concerns? (Select TWO)  
**A:** A. Interface doesn't work with screen readers + C. Spoken guidance has no captions  
**Why:** Both create direct accessibility barriers. Fewer age-group examples = fairness concern. Undocumented owner = accountability. Unencrypted data = privacy/security.

---

## Q8
**Q:** Statement 1: delete_analyzer submits content for analysis. Statement 2: Custom image analyzer uses base_analyzer_id="prebuilt-video". Statement 3: Analyzers can return markdown, JSON fields, segments.  
**A:** D. No / No / Yes  
**Why:** `begin_analyze` submits content, not `delete_analyzer` (No). Image analyzers inherit from `prebuilt-image`, not prebuilt-video (No). Analyzers do return structured outputs like markdown, JSON, segments (Yes).

---

## Q9
**Q:** Which question is most directly tied to inclusiveness?  
**A:** C. Can people with different abilities use the system effectively?  
**Why:** Inclusiveness = empowering people with different abilities. Encryption = privacy/security. Model limitations = transparency. Deployment approval = accountability.

---

## Q10
**Q:** Statement 1: Requiring one interaction method supports inclusiveness. Statement 2: Captions for spoken output supports inclusiveness. Statement 3: Testing with different abilities supports inclusiveness.  
**A:** C. No / Yes / Yes  
**Why:** One method excludes users (No). Captions provide accessible alternatives (Yes). Diverse user testing finds barriers (Yes).

---

## Q11
**Q:** Deployed image generation model — where to test prompt changes visually in Foundry?  
**A:** B. Images playground  
**Why:** Foundry routes image-generation models like gpt-image-1 to the images playground for visual experimentation before code. Not the general model playground — specifically the images playground.

---

## Q12
**Q:** Preferred deployment option with widest capabilities including regional/data zone/global processing?  
**A:** C. Standard deployment in Foundry resources  
**Why:** Microsoft describes it as the preferred option with widest capabilities: regional, data zone, OR global processing + standard and provisioned throughput. Serverless is regional only. Managed compute needs quota and is for specific scenarios like Hugging Face.

---

## Q13
**Q:** Deploy a Hugging Face model on dedicated compute. Which deployment option?  
**A:** B. Managed compute  
**Why:** Managed compute hosts models on dedicated compute, requires compute quota, and is the required option for certain collections like Hugging Face. Standard deployment is preferred when possible but not available for Hugging Face.

---

## Q14
**Q:** More focused and deterministic answers — lower ________.  
**A:** A. temperature  
**Why:** Lower temperature = more focused/deterministic output. Microsoft recommends adjusting temperature OR top_p, not both. presence_penalty affects topic novelty, frequency_penalty reduces repetition — neither directly controls determinism.

---

## Q15
**Q:** Concise and more focused chat response. Which TWO configuration choices? (Select TWO)  
**A:** A. Lower temperature + C. Set max_completion_tokens  
**Why:** Temperature controls randomness/focus. max_completion_tokens caps output length. Don't increase both temperature AND top_p together. presence_penalty doesn't shorten answers.

---

## Q16
**Q:** Statement 1: Standard deployment supports regional/data zone/global. Statement 2: Serverless API endpoints can be global. Statement 3: Managed compute requires quota, billed per uptime.  
**A:** B. Yes / No / Yes  
**Why:** Standard supports all processing types (Yes). Serverless is regional ONLY (No). Managed compute requires quota and is billed per compute uptime (Yes).

---

## Q17
**Q:** Cap generated text including visible output and reasoning tokens. Which parameter?  
**A:** A. max_completion_tokens  
**Why:** Sets upper bound on total generated tokens (visible output + reasoning). presence_penalty = topic novelty, temperature = randomness, top_p = nucleus sampling — none are hard output limits.

---

## Q18
**Q:** Sample from tokens within a chosen probability mass (top 10%). Adjust ________.  
**A:** D. top_p  
**Why:** top_p = nucleus sampling. Setting 0.1 means only tokens in the top 10% probability mass are considered. frequency_penalty = repetition control, temperature = randomness, max_completion_tokens = output length cap.

---

## Q19
**Q:** Which THREE pairs are correctly matched? (Select THREE)  
**A:** C. begin_analyze — submits content for analysis + E. AnalysisInput(url=file_url) — supplies file input + F. field_schema — defines structured fields to extract  
**Why:** These are the core Content Understanding SDK concepts. delete_analyzer is for cleanup (not analysis). AzureKeyCredential is for auth (not storing results). prebuilt-audio is NOT base analyzer for images.

---

## Q20
**Q:** Which TWO arguments are part of the begin_analyze call? (Select TWO)  
**A:** A. analyzer_id + E. inputs  
**Why:** `begin_analyze(analyzer_id=..., inputs=[...])` is the documented pattern. field_schema belongs to analyzer definition. AzureKeyCredential is for client creation. base_analyzer_id is for custom analyzer setup.

---

## Q21
**Q:** Statement 1: OCR extracts text from images. Statement 2: Speech to Text transcribes audio. Statement 3: Named entity recognition creates summaries.  
**A:** A. Yes / Yes / No  
**Why:** OCR reads text from images (Yes). STT transcribes spoken audio (Yes). NER identifies entities (people, places, dates) — summarization is a DIFFERENT task (No).

---

## Q22
**Q:** Reading returned summary field: `content.fields.get(________)`  
**A:** A. "Summary"  
**Why:** Content Understanding quickstart shows accessing fields by name like "Summary" from `content.fields`. AnalyzerId, Credential, and Endpoint are request/setup metadata, not extracted field names.

---

## Q23
**Q:** Training video with spoken narration and text on slides. Which TWO extraction techniques? (Select TWO)  
**A:** A. OCR + B. Speech to Text  
**Why:** OCR extracts visible text from slide frames. Speech to Text transcribes spoken narration from audio track. Text to Speech is generation (not extraction). Sentiment analysis and image generation don't extract information from video.

---

## Q24
**Q:** AI support assistant for employees with different vision, hearing, and motor needs. Which design choice = inclusiveness?  
**A:** B. Alternative input and output methods  
**Why:** Voice commands, screen readers, adaptive keyboards accommodate diverse needs. Encryption = privacy/security. Model disclosure = transparency. Human approval = accountability.

---

## Q25 :red_circle:
**Q:** Azure OpenAI deployment call: `model=__________`. What value?  
**A:** B. deployment_name  
**Why:** Azure OpenAI uses the `model` parameter to refer to the Azure deployment NAME you created, not the base model family name. Always pass the deployment name variable, not a literal like "gpt-4o".

---

## Q26
**Q:** Customer support calls recorded — need written transcripts for searching. Which capability?  
**A:** C. Speech to Text  
**Why:** Converts spoken audio into written text transcripts. Text to Speech creates audio FROM text (opposite direction). Speech Translation adds translation (not needed here). OCR reads text from images, not audio.

---

## Q27 :red_circle:
**Q:** After `client.begin_analyze(...)`, call poller's ________ method for final output.  
**A:** C. result()  
**Why:** `poller.result()` waits for the long-running operation to complete and returns the AnalysisResult. `get_analyzer()` retrieves analyzer config. `delete_analyzer()` removes the analyzer. `begin_create_analyzer()` creates a new analyzer.

---

## Q28 :red_circle:
**Q:** Identify organizations, locations, and dates in a sentence. Which TextAnalyticsClient method?  
**A:** B. recognize_entities  
**Why:** Named entity recognition extracts categorized entities (organizations, locations, dates, quantities). `extract_key_phrases` = main talking points. `analyze_sentiment` = emotional tone. `detect_language` = language identification.

---

## Q29
**Q:** Analyze documents, images, audio, and videos with user-defined schema. Which tool?  
**A:** B. Azure Content Understanding  
**Why:** Content Understanding handles all content types (documents, images, audio, video) and transforms them into structured, searchable data with user-defined schemas. Azure AI Vision is image-only. AI Search is retrieval. TTS generates audio.

---

## Q30
**Q:** Which TWO pieces of information can Azure AI Video Indexer extract from video? (Select TWO)  
**A:** A. Transcript of spoken words + B. OCR text from video frames  
**Why:** Video Indexer analyzes both audio (transcripts) and visual (OCR text from frames) streams. TTS generates audio (doesn't extract). Form key-value pairs = Document Intelligence. Smart crops = image composition, not extraction.

---

## Q31
**Q:** Azure OpenAI image model best for realism, instruction following, multimodal context, improved speed/cost?  
**A:** C. gpt-image-1.5  
**Why:** Microsoft's model comparison describes gpt-image-1.5 with exactly these attributes. Whisper = audio/transcription. Azure AI Vision = image analysis (not generation). Phi-4-mini = not an image generation model.

---

## Q32
**Q:** Modify one selected region of an existing image in the images playground. Use ________.  
**A:** D. Inpainting  
**Why:** Inpainting transforms parts of an image while keeping the rest intact. Documented for gpt-image-1 in the images playground. OCR reads text, entity recognition analyzes text, speech translation handles audio.

---

## Q33
**Q:** See image progress sooner instead of waiting for final result. Which TWO settings? (Select TWO)  
**A:** B. stream=True + E. partial_images=2  
**Why:** `stream=True` enables streaming responses. `partial_images` controls how many intermediate images are returned before the final result. quality="high" slows generation. background and output_format affect appearance, not progress delivery.

---

## Q34
**Q:** App supports keyboard, voice, captions, screen-reader output. Emphasizing ________.  
**A:** C. Inclusiveness  
**Why:** Multiple input/output modes = inclusive design for users with different abilities. Transparency = understanding system behavior. Accountability = responsibility/oversight. Privacy/security = data protection.

---

## Q35
**Q:** Statement 1: gpt-image-1 uses images playground. Statement 2: response_format supported for GPT-image-1. Statement 3: Transparent background = background="transparent" + PNG.  
**A:** D. Yes / No / Yes  
**Why:** Foundry routes image models to images playground (Yes). response_format is for DALL-E 3, NOT GPT-image-1 (No). Transparent backgrounds need background="transparent" + PNG output (Yes).

---

## Q36
**Q:** Which THREE pairs are correctly matched? (Select THREE)  
**A:** A. Serverless API — pay-as-you-go + C. Standard deployment — supports global processing + E. frequency_penalty — reduces repeated tokens  
**Why:** Each is documented correctly. Managed compute DOES require quota (not "no quota"). top_p = nucleus sampling (not repetition penalty). presence_penalty = topic novelty (not token count limit).

---

## Q37 :red_circle:
**Q:** Microsoft model in Foundry for photorealistic images from natural language prompts?  
**A:** C. MAI-Image-2  
**Why:** MAI-Image-2 is Microsoft's text-to-image model capable of photorealistic synthesis. Azure AI Content Safety = moderation. Whisper = audio/transcription. Phi-4-mini = language model, not image generation.

---

## Q38 :red_circle:
**Q:** AIProjectClient constructor — what replaces `project = ________`?  
**A:** C. `AIProjectClient(endpoint=PROJECT_ENDPOINT, credential=DefaultAzureCredential())`  
**Why:** The constructor uses `endpoint=` for the project endpoint and `credential=` for DefaultAzureCredential. NOT `model=`, NOT `agent_name=`, NOT `api_key=`. The parameter names must be exact.

---

## Q39
**Q:** After creating AIProjectClient, which method returns client for Responses and Conversations?  
**A:** B. project.get_openai_client()  
**Why:** Returns the OpenAI client used for Responses and Conversations operations. Agent creation/versioning stays on project client, but runtime chat goes through the OpenAI client.

---

## Q40
**Q:** Object used to identify which Foundry agent handles the request in Python response-call pattern?  
**A:** A. agent_reference  
**Why:** `extra_body={"agent_reference": {"name": AGENT_NAME, "type": "agent_reference"}}` routes the request to the specific agent. conversation = chat session state. PromptAgentDefinition = agent creation. PROJECT_ENDPOINT = project location.

---

## Q41
**Q:** Runtime client for agent chat: `openai = ________`  
**A:** B. project.get_openai_client()  
**Why:** Called on the project INSTANCE (not the class). `AIProjectClient.get_openai_client()` is wrong (class-level call). `project.openai()` and `AIProjectClient.openai_client()` are not documented methods.

---

## Q42
**Q:** Translation assistant assumes all users can hear audio clearly. This ignores ________.  
**A:** B. Inclusiveness  
**Why:** Assuming one interaction method works for everyone fails to account for different abilities. Inclusiveness requires alternative outputs like captions/text. Accountability = responsibility. Fairness = equitable treatment. Transparency = system understanding.

---

## Q43
**Q:** Which THREE pairs are correctly matched? (Select THREE)  
**A:** B. get_openai_client() — returns client for Responses/Conversations + D. conversations.create() — starts multi-turn conversation + F. AIProjectClient — connects to Foundry project endpoint  
**Why:** These map to the lightweight client flow. PromptAgentDefinition doesn't store chat history (that's conversation). PROJECT_ENDPOINT doesn't contain instructions. create_version() doesn't send messages (that's responses.create).

---

## Q44
**Q:** Statement 1: Agent creation/versioning on project client. Statement 2: Conversation persists history across turns. Statement 3: PromptAgentDefinition stores chat history after each message.  
**A:** A. Yes / Yes / No  
**Why:** Creation/versioning = project client (Yes). Conversations persist multi-turn history (Yes). PromptAgentDefinition = agent definition at creation time, NOT runtime chat history (No).

---

## Q45
**Q:** Extract printed or handwritten text from a street sign image. Use ________.  
**A:** A. OCR  
**Why:** OCR reads visible text from images — signs, labels, posters, scanned pages. Entity recognition works on existing text. Speech translation handles audio. Image generation creates images.

---

## Q46
**Q:** Preconfigured code snippet referencing your agent for browser IDE. Where in Foundry?  
**A:** D. Code tab in the agent playground chat pane  
**Why:** The Code tab provides snippets referencing your agent and supports opening in VS Code for the Web. Monitor = observability. Quotas = capacity limits. Connections = resource connectivity.

---

## Q47
**Q:** Creating agent with PromptAgentDefinition. What replaces `definition=________`?  
**A:** C. `PromptAgentDefinition(model="gpt-5-mini", instructions="You are a helpful assistant")`  
**Why:** Must be a PromptAgentDefinition instance (not a plain dict). DefaultAzureCredential is for auth. conversations.create() is for runtime chat, not agent definition.

---

## Q48 :red_circle:
**Q:** Python app sending document URLs to Content Understanding. Which client first?  
**A:** A. ContentUnderstandingClient  
**Why:** ContentUnderstandingClient is the Python SDK entry point for Content Understanding. TextAnalyticsClient = Azure Language. ImageAnalysisClient = Azure Vision. SearchClient = Azure AI Search. Each belongs to a different service.

---

## Q49
**Q:** Setting up Content Understanding SDK client. Import and class name?  
**A:** B. ContentUnderstandingClient  
**Why:** `from azure.ai.contentunderstanding import ContentUnderstandingClient` — the documented class for Content Understanding operations. SearchClient, TextAnalyticsClient, and ImageAnalysisClient are from different SDKs.

---

## Q50 :red_circle:
**Q:** Which TWO approaches for generating images with Azure OpenAI in Foundry? (Select TWO)  
**A:** A. Image generation API + D. Responses API  
**Why:** Microsoft documents two supported approaches: the Image generation API and the Responses API. OCR extracts text (doesn't generate images). Azure AI Search indexes content. Speech SDK handles audio.

---

## Q51
**Q:** Which THREE pairs are correctly matched? (Select THREE)  
**A:** B. Images playground — visual experiments for image models + D. output_format="png" — transparent background requests + F. b64_json — base64 image data in response  
**Why:** Azure AI Search doesn't create images. response_format is NOT supported for GPT-image-1. OCR doesn't do inpainting.

---

## Q52
**Q:** Which THREE pairs are correctly matched? (Select THREE)  
**A:** A. Key phrase extraction — main talking points + C. OCR — extracts text from images + E. Speech to Text — converts audio to text  
**Why:** Text to Speech converts text TO audio (not FROM). Entity recognition identifies entities, doesn't summarize. Image generation creates images, doesn't extract invoice fields.

---

## Q53
**Q:** Content Understanding quickstart — which one-time resource configuration is required?  
**A:** D. Model deployment defaults  
**Why:** The Content Understanding resource must be connected to Foundry model deployments. Quickstart lists model deployment defaults as prerequisite. AI Search index, Cosmos DB, and speech voice profile are not required.

---

## Q54 :red_circle:
**Q:** Read text from image using Azure AI Vision. `visual_features=[________]`  
**A:** A. VisualFeatures.READ  
**Why:** READ is the OCR feature for extracting printed/handwritten text. CAPTION generates a description sentence. OBJECTS detects physical items. SMART_CROPS suggests cropping regions. None of the others read text.

---

## Q55 :red_circle:
**Q:** Scanned supplier invoices — extract invoice number, vendor name, total amount as structured fields. Which service?  
**A:** B. Azure AI Document Intelligence  
**Why:** Document Intelligence extracts structured fields, tables, and document structure from invoices/forms. OCR only reads raw text but doesn't understand document structure or return typed fields. Speech to Text and sentiment analysis are wrong modalities.

---

## Q56
**Q:** Support follow-up questions in same chat. `conversation = ________`  
**A:** D. openai.conversations.create()  
**Why:** Creates the conversation object for multi-turn context. responses.create() generates a response (used after conversation exists). chat.completions.create() is not the current agent pattern. create_version() is agent management.

---

## Q57
**Q:** Follow-up in same chat with same agent. Which TWO values in responses.create()? (Select TWO)  
**A:** B. conversation=conversation.id + E. extra_body={"agent_reference": {"name": AGENT_NAME, "type": "agent_reference"}}  
**Why:** conversation.id keeps it in the same chat. agent_reference routes to the specific agent. model= is for direct model calls. tool_choice and deployment_id are not part of the minimal agent pattern.

---

## Q58
**Q:** Submit document URL for extraction: `client.begin_analyze(analyzer_id=..., ________)`  
**A:** C. inputs=[AnalysisInput(url=file_url)],  
**Why:** `inputs=[AnalysisInput(url=...)]` is the documented pattern. field_schema = analyzer definition (not runtime). base_analyzer_id = custom analyzer setup. content_fields is not a documented parameter.

---

## Q59
**Q:** Custom analyzer for image chart extraction. Which TWO choices? (Select TWO)  
**A:** B. base_analyzer_id="prebuilt-image" + D. Call begin_create_analyzer  
**Why:** Image scenarios use prebuilt-image (not prebuilt-audio). begin_create_analyzer creates the custom analyzer. delete_analyzer is for cleanup. AzureKeyCredential is for auth (not schema storage).

---

## Q60
**Q:** Compact response — parameter that sets upper bound: `________=60`  
**A:** C. max_completion_tokens  
**Why:** Directly caps generated output tokens. top_p = sampling control. presence_penalty = topic novelty. frequency_penalty = repetition reduction. None of the others set a hard output limit.

---

## Q61 :red_circle:
**Q:** SignalFrame scenario: Model is 98% accurate for emergencies. Management wants auto-publish above 95% confidence. Which control instead?  
**A:** A. Mandatory editorial approval  
**Why:** High confidence doesn't guarantee correctness in all contexts. Human review before public-safety decisions ensures accountability and safety. Automatic publication removes required human oversight. Weekly reviews are after-the-fact. Anonymous feedback can't identify the responsible approver.

---

## Q62
**Q:** SignalFrame scenario: Agent must retrieve recently published public government warnings with citations. Which tool?  
**A:** C. Web search  
**Why:** Web search retrieves current public information with inline citations. Azure AI Search requires pre-indexed content. File Search works on uploaded files. Code Interpreter does calculations, not web retrieval.

---

## Q63 :red_circle:
**Q:** SignalFrame scenario: Live programme, stream microphone audio, play spoken response before generation completes. Which interface?  
**A:** B. GPT Realtime API  
**Why:** Supports low-latency speech-in/speech-out interactions via WebRTC/WebSocket. Model accepts and produces audio natively — no separate STT/TTS/generation pipeline needed. Batch transcription is async (too slow). gpt-image-1 is for images. text-embedding is for vectors.

---

## Q64
**Q:** SignalFrame scenario: Create lower-third graphic with logo, transparent background, PNG output. Which model?  
**A:** D. gpt-image-1  
**Why:** Image generation model that creates visuals from text + optional image input. Supports PNG output and transparent background. gpt-realtime = audio. gpt-4.1 = language model. text-embedding-3-large = vectors.

---

## Q65
**Q:** SignalFrame scenario: Divide recorded broadcast into news stories with timestamps, speaker transcripts, headline, summary, people, locations, risk rating. Which component?  
**A:** A. Content Understanding video analyzer  
**Why:** Custom analyzer processes audiovisual content with segmentation (divides into stories), transcript phrases with speaker IDs and timing, plus user-defined fields (headline, summary, entities, risk). All in one analyzer rather than multi-component pipeline.

---

## Key Takeaway Tables

### Incorrect Answers Summary

| Q# | Your Answer | Correct Answer | Key Lesson |
|---|---|---|---|
| Q1 | prompt | b64_json | GPT-image-1 always returns base64 images, not URLs |
| Q25 | "gpt-4o" | deployment_name | Azure OpenAI model= parameter needs deployment NAME, not base model name |
| Q27 | get_analyzer() | result() | poller.result() waits for and returns analysis output |
| Q28 | analyze_sentiment | recognize_entities | Extracting orgs/locations/dates = NER, not sentiment |
| Q37 | Azure AI Content Safety | MAI-Image-2 | Content Safety = moderation. MAI-Image-2 = Microsoft's photorealistic text-to-image |
| Q38 | agent_name=... | endpoint=... | AIProjectClient uses endpoint= and credential=, not agent_name= |
| Q48 | ImageAnalysisClient | ContentUnderstandingClient | Content Understanding has its OWN client, not Vision's ImageAnalysisClient |
| Q50 | Image gen API + OCR | Image gen API + Responses API | Two ways to generate images: Image generation API or Responses API |
| Q54 | VisualFeatures.CAPTION | VisualFeatures.READ | READ = OCR (text extraction). CAPTION = sentence description |
| Q55 | OCR | Azure AI Document Intelligence | Structured invoice fields = Document Intelligence. Raw text = OCR |
| Q61 | Auto-publish above threshold | Mandatory editorial approval | High confidence ≠ guaranteed correctness. Human review for safety decisions |
| Q63 | Batch transcription | GPT Realtime API | Live speech-to-speech = GPT Realtime API. Batch = async, too slow for live |

### GPT-image-1 vs DALL-E 3

| Feature | GPT-image-1 / 1.5 | DALL-E 3 |
|---|---|---|
| Response format | Always b64_json (base64) | Supports response_format (URL or base64) |
| Output format param | output_format (png/jpeg) | Not applicable |
| Transparent background | background="transparent" + output_format="png" | Not supported |
| Inpainting | Supported | Not supported |
| Streaming/partial | stream=True + partial_images | Not supported |

### Image Generation Models

| Model | Best For |
|---|---|
| gpt-image-1 | General image generation, inpainting, transparency |
| gpt-image-1.5 | Realism, instruction following, multimodal context, speed/cost |
| MAI-Image-2 | Microsoft's photorealistic text-to-image model |
| DALL-E 3 | Older model, URL responses, no inpainting |

### Deployment Options

| Option | Key Characteristics |
|---|---|
| Standard (Foundry resources) | Preferred. Widest capabilities: regional/data zone/global + standard/provisioned throughput |
| Serverless API endpoint | Pay-as-you-go. Regional ONLY (not global). No compute quota needed |
| Managed compute | Dedicated compute. Requires compute quota. Billed per uptime. Required for Hugging Face |

### Chat Completion Parameters

| Parameter | Controls | Use When |
|---|---|---|
| temperature | Randomness/focus | More focused = lower value |
| top_p | Nucleus sampling (probability mass) | Limit token candidates by probability |
| max_completion_tokens | Hard output length cap | Want compact responses |
| frequency_penalty | Reduces repeated tokens | Avoid verbatim repetition |
| presence_penalty | Encourages new topics | Want topic diversity |

### Azure OpenAI Key Rule
```python
# CORRECT — use deployment name variable
response = client.chat.completions.create(
    model=deployment_name,  # "support-chat-prod"
    ...
)

# WRONG — don't use base model name
response = client.chat.completions.create(
    model="gpt-4o",  # This is NOT the deployment name
    ...
)
```

### TextAnalyticsClient Methods

| Method | Purpose |
|---|---|
| recognize_entities | Extract orgs, locations, dates, quantities (NER) |
| recognize_pii_entities | Detect PII (personal info) |
| extract_key_phrases | Main talking points/concepts |
| analyze_sentiment | Positive/negative/neutral tone |
| detect_language | Identify language of text |

### OCR vs Document Intelligence

| Service | Returns | Best For |
|---|---|---|
| OCR (VisualFeatures.READ) | Raw text from images | Street signs, labels, posters |
| Azure AI Document Intelligence | Structured fields, tables, document structure | Invoices, receipts, forms with typed fields |

### Content Understanding Client Selection

| Client | Service | Use For |
|---|---|---|
| ContentUnderstandingClient | Content Understanding | Multimodal extraction (docs, images, audio, video) |
| TextAnalyticsClient | Azure Language | Text analysis (NER, sentiment, key phrases) |
| ImageAnalysisClient | Azure Vision | Image analysis (caption, read, objects) |
| SearchClient | Azure AI Search | Index and query documents |

### Foundry Agent Lightweight Client Flow
```
1. project = AIProjectClient(endpoint=..., credential=DefaultAzureCredential())
2. openai = project.get_openai_client()
3. conversation = openai.conversations.create()
4. response = openai.responses.create(
       conversation=conversation.id,
       extra_body={"agent_reference": {"name": AGENT_NAME, "type": "agent_reference"}},
       input="Your question here"
   )
```

### Live Audio Interfaces

| Interface | Best For |
|---|---|
| GPT Realtime API | Live speech-to-speech, low latency, WebRTC/WebSocket |
| Azure Speech batch transcription | Async processing of recorded audio files |
| Content Understanding (prebuilt-audioSearch) | Extract transcript/summary/speakers from audio files |
