# AI-901 Practice Assessment 3 — Q/A/Why Notes

**Total Questions:** 67  
**Correct:** 59 | **Incorrect:** 8  
**Score:** ~88%

:red_circle: = Incorrect answer

---

## Q1
**Q:** Protecting prompts, outputs, and personal data from unauthorized access is a ________ consideration in responsible AI.  
**A:** C. Privacy and security  
**Why:** Privacy and security focus on protecting the confidentiality and integrity of data, including prompts, outputs, and personal information. It is one of Microsoft's six Responsible AI principles.

---

## Q2
**Q:** You need a no-code single-agent solution that you can configure and test directly in the Foundry portal. Which agent type should you create?  
**A:** A. Prompt agent  
**Why:** Prompt agents are declaratively defined, no-code, portal-first agents that combine model configuration, instructions, tools, and prompts. Workflow agents are for orchestration, hosted agents are code-based containers.

---

## Q3
**Q:** Statement 1: Using least-privilege access supports security. Statement 2: Collecting more personal data than necessary improves privacy. Statement 3: Storing prompts without clear governance can increase privacy risk.  
**A:** B. Yes / No / Yes  
**Why:** Least-privilege reduces misuse (Yes). More data = more exposure, not better privacy (No). Unclear retention of prompts with sensitive content increases risk (Yes).

---

## Q4 :red_circle:
**Q:** Match requirements to Foundry capabilities: (1) Create/test agent in portal for support questions, (2) Build lightweight chat app with code, (3) Extract structured info from invoices/forms, (4) Build app with speech capabilities.  
**A:** D. F=Req1, C=Req2, B=Req3, D=Req4  
**Why:** Single-agent solution in portal (F) for Req1. Foundry SDK (C) for code-based chat app. Azure Content Understanding (B) for document extraction. Azure Speech in Foundry Tools (D) for speech. OCR alone is too narrow for structured extraction from invoices/forms — Content Understanding is the better fit.

---

## Q5
**Q:** In Microsoft Foundry, the ________ is the main place to test multi-turn conversations with an agent in the portal.  
**A:** B. Agents playground  
**Why:** The agents playground lets you explore, prototype, and test agents without running code, including multi-turn conversation testing.

---

## Q6
**Q:** Code: `client.begin_analyze(analyzer_id="________")` for audio transcript and summary extraction.  
**A:** B. prebuilt-audioSearch  
**Why:** prebuilt-audioSearch is the Content Understanding analyzer for audio extraction including transcript, summary, and speaker labeling.

---

## Q7
**Q:** Which model type is best for an assistant that must reason through a request and call tools?  
**A:** A. Reasoning chat model  
**Why:** Reasoning chat models support conversational reasoning and tool calling. Embedding models create vectors, image generation creates images, speech synthesis creates audio — none support tool-calling orchestration.

---

## Q8
**Q:** A school plans to release an AI tutor that processes student conversations. Which review is most directly aligned?  
**A:** C. Privacy review  
**Why:** Student conversations can contain sensitive/personal information. Privacy review focuses on how personal conversation data is collected, retained, accessed, and protected.

---

## Q9
**Q:** A designer enters "a futuristic solar-powered cafe on Mars" and wants a brand-new image. Which capability?  
**A:** C. Image generation  
**Why:** Image generation models create images from text prompts. OCR reads text from images, tagging labels existing images, entity recognition extracts entities from text.

---

## Q10
**Q:** Solution must use a model, follow custom instructions, call tools, and maintain agent runtime without hosting infrastructure. Use ____.  
**A:** B. Foundry Agent Service  
**Why:** Foundry Agent Service builds, deploys, and scales AI agents with Microsoft managing hosting, runtime, scaling, identity, and security.

---

## Q11
**Q:** Which TWO input approaches are supported for sending an image to a multimodal model? (Select TWO)  
**A:** B. Public image URL + C. Data URL from a local image file  
**Why:** Microsoft Learn documents both public image URL and data URL (from local file) as supported image input methods for multimodal models.

---

## Q12
**Q:** Which two statements align with Microsoft's Azure Direct Models data privacy commitments? (Select TWO)  
**A:** A. Prompts and completions are not available to other customers + B. Customer data is not used to improve products without permission  
**Why:** Microsoft's privacy docs explicitly state these commitments. Prompts are NOT shared with model providers, fine-tuned models are NOT shared across tenants.

---

## Q13
**Q:** An AI team authenticates to Azure resources without storing secrets in code. This strengthens ________.  
**A:** B. Privacy and security  
**Why:** Avoiding stored secrets reduces credential leakage and unauthorized access — a security-focused design decision that also supports data privacy.

---

## Q14
**Q:** Which THREE pairs are correctly matched? (Select THREE)  
**A:** A. Prompt agent — Declaratively defined single agent + C. Agents playground — Tests multi-turn conversations + E. Build > Tools — Opens Foundry Tools catalog  
**Why:** These reflect the portal workflow: create prompt agent, configure tools via Build > Tools, test in playground. Hosted agents are code-based (not no-code), Build > Tools is NOT billing.

---

## Q15
**Q:** A model for chat completions that can accept text and images as input is a ________.  
**A:** C. Multimodal model  
**Why:** Multimodal models handle multiple input types (text, images, audio). Embedding models create vectors, speech models handle audio, vectorizers are retrieval components.

---

## Q16
**Q:** Which TWO capabilities most directly indicate an image generation model? (Select TWO)  
**A:** A. Creates original images + E. Supports inpainting  
**Why:** Image generation models create images from prompts and support editing like inpainting. Vectors, similarity scoring, and retrieval belong to embedding models.

---

## Q17
**Q:** Code to generate a vector from text for semantic search. Which line replaces the missing section?  
**A:** D. `response = client.embeddings.create(input=text, model="text-embedding-3-large")`  
**Why:** The embeddings endpoint creates vector representations. The code prints `response.data[0].embedding` which requires the embeddings API, not images, audio, or responses.

---

## Q18
**Q:** Statement 1: Embedding models convert text into vectors. Statement 2: Image generation models are best for vector similarity search. Statement 3: Multimodal chat models can accept images.  
**A:** B. Yes / No / Yes  
**Why:** Embeddings create vectors (Yes). Image generation creates images, not vectors for search (No). Multimodal models accept text + images (Yes).

---

## Q19
**Q:** Which THREE pairs are correctly matched? (Select THREE)  
**A:** A. Embedding model — converts text into vectors + D. Multimodal chat model — accepts text and image input + F. Image generation model — creates original images from prompts  
**Why:** Each pair matches the correct model capability. Image generation doesn't return similarity vectors, AI Search doesn't create images, speech synthesis doesn't extract invoice fields.

---

## Q20
**Q:** Code for creating a prompt agent with `PromptAgentDefinition`. What replaces the missing section?  
**A:** A. `instructions="You are a helpful assistant that answers general questions",`  
**Why:** Instructions are a core part of agent definition — they define the agent's behavior. Temperature expects a number (not agent name), conversation belongs to runtime, agent_reference is for calling an existing agent.

---

## Q21
**Q:** A RAG chatbot needs two model-related choices. Which TWO? (Select TWO)  
**A:** B. Chat completion model + C. Embedding model  
**Why:** RAG needs embeddings for vector-based retrieval and a chat model to generate grounded responses. Image generation, speech synthesis, and OCR don't address the retrieval+answer pattern.

---

## Q22
**Q:** Code to send text and image to a model. Missing line in UserMessage content list?  
**A:** A. `ImageContentItem(image_url=ImageUrl(image_url))`  
**Why:** ImageContentItem with ImageUrl is the documented pattern for adding image input to a multimodal message. TextContentItem would send URL as plain text, not as image data.

---

## Q23
**Q:** A model that produces a human-readable sentence describing an existing image is using ________.  
**A:** B. Image captioning  
**Why:** Image captioning generates a caption in human-readable language using complete sentences. OCR extracts existing text, speech synthesis creates audio, entity recognition analyzes text.

---

## Q24
**Q:** Preparing an image-generation request payload. What replaces the missing section?  
**A:** A. `"prompt": "A red bicycle in a park",`  
**Why:** Image generation models use a "prompt" field as the text description that drives image creation. OCR, objects list, and caption are analysis concepts, not generation inputs.

---

## Q25
**Q:** Which TWO statements describe image-generation model capabilities? (Select TWO)  
**A:** A. Create images from text prompts + B. Accept optional images as input in supported workflows  
**Why:** Microsoft docs state image generation models create images from text prompts and optional images. Bounding boxes = computer vision, printed text = OCR, sentiment = text analysis.

---

## Q26 :red_circle:
**Q:** Statement 1: Multimodal model can accept image input. Statement 2: Public image URL can be used for image interpretation. Statement 3: Every multimodal model supports multiple images in same turn.  
**A:** A. Yes / Yes / No  
**Why:** Multimodal models accept image input (Yes). Public URLs are documented as valid input (Yes). Some models support only one image per turn and may retain only the last image — NOT every model supports multiple images (No).

---

## Q27
**Q:** Which THREE pairs are correctly matched? (Select THREE)  
**A:** A. OCR — extracts printed and handwritten text + C. Object detection — returns coordinates for detected objects + E. Image captioning — generates a sentence description  
**Why:** Each matches documented capability. Image generation doesn't return sentiment, speech synthesis doesn't create captions from photos, OCR doesn't create posters.

---

## Q28
**Q:** Video extraction code: `print(video_content.________)` — what property?  
**A:** A. markdown  
**Why:** Microsoft's video quickstart shows `video_content.markdown` for prebuilt-videoSearch results. The service packages video content into richly formatted Markdown.

---

## Q29
**Q:** You need descriptions for separate parts of a photo, not just one overall sentence. Which capability?  
**A:** B. Dense captioning  
**Why:** Dense captioning generates detailed captions for individual objects with bounding box coordinates — unlike regular image captioning which gives one whole-image description.

---

## Q30
**Q:** Which THREE pairs are correctly matched? (Select THREE)  
**A:** A. prebuilt-audioSearch — transcript, summary, speaker labeling + B. prebuilt-videoSearch — keyframes, transcript, chapter segments + C. transcriptPhrases — speaker identification and timing details  
**Why:** Each matches documented Content Understanding analyzer capabilities. prebuilt-imageSearch is NOT for audio speakers, TTS is NOT for video segmentation, prebuilt-layout is NOT for audio transcripts.

---

## Q31
**Q:** Calling a MAI image model: `url = f"{endpoint}/______"` — what endpoint path?  
**A:** C. mai/v1/images/generations  
**Why:** Microsoft's MAI documentation shows image generation requests go to the `mai/v1/images/generations` path. OCR, speech synthesis, and entity recognition use different paths.

---

## Q32
**Q:** AI app analyzes support tickets with personal info. Which two actions best support privacy and security? (Select TWO)  
**A:** A. Apply role-based access control + C. Minimize stored personal data  
**Why:** RBAC reduces unauthorized access. Data minimization reduces exposure. Retaining prompts indefinitely, embedding API keys in code, and sharing real prompts publicly all increase risk.

---

## Q33
**Q:** Which two actions can you perform directly in the agents playground? (Select TWO)  
**A:** A. Configure agent instructions and persona + C. Test multi-turn conversations  
**Why:** The playground is for agent behavior configuration and testing. Rebuilding container images is for hosted agents, resizing subscriptions and creating VPN gateways are Azure admin tasks.

---

## Q34
**Q:** Where do you open the tool catalog to add web search or file search to an agent?  
**A:** A. Build > Tools  
**Why:** In the Foundry portal, Build > Tools opens the tool catalog where you browse, configure, and add tools to agents. Monitor > Metrics is for observability, not tool configuration.

---

## Q35
**Q:** Calling a portal-defined agent from Python using `extra_body`. What replaces the missing section?  
**A:** A. `{"agent_reference": {"name": AGENT_NAME, "type": "agent_reference"}}`  
**Why:** The agent_reference pattern in extra_body targets the previously created agent, preserving its portal-defined instructions and capabilities. Tool, deployment, and conversation_id are wrong concepts.

---

## Q36 :red_circle:
**Q:** Which TWO capabilities commonly return bounding box coordinates? (Select TWO)  
**A:** B. Object detection + C. People detection  
**Why:** Both object detection and people detection return bounding box coordinates for detected items. Image captioning describes the image in words. Text-to-image generation creates new images. Sentiment analysis is text-based.

---

## Q37
**Q:** AI chatbot receives customer account numbers. Which design choice best reduces privacy risk?  
**A:** D. Limit retention and restrict access to authorized users  
**Why:** Combines two practical controls: keep less sensitive data and tightly control who can access what remains. Permanent storage, public demos with real data, embedded API keys, and broad developer access all increase risk.

---

## Q38
**Q:** Avoid hard-coding an AI service key. What replaces the missing section for `key = ________`?  
**A:** B. `os.getenv("AZURE_OPENAI_KEY")`  
**Why:** Environment variables avoid hard-coding secrets in source code. "my-secret-key" is hard-coded, print() doesn't assign, and endpoint is the URL not the key.

---

## Q39
**Q:** Which two actions align with Microsoft's documented test workflow for a single agent? (Select TWO)  
**A:** A. Send follow-up prompt to check multi-turn behavior + B. Review tracing data for model calls and tool use  
**Why:** Multi-turn testing and tracing are documented parts of agent development. Replacing with workflow, resizing CPU, or deleting the model are disruptive/unrelated.

---

## Q40
**Q:** Code to send text + image to a multimodal model. Missing line?  
**A:** A. `ImageContentItem(image_url=ImageUrl(image_url))`  
**Why:** Same documented pattern — ImageContentItem + ImageUrl for image input in multimodal requests. TextContentItem sends as text, AudioContentItem is wrong modality, embeddings is different API.

---

## Q41
**Q:** Which THREE pairs are correctly matched? (Select THREE)  
**A:** B. ImageContentItem — adds image input to a user message + D. ImageUrl.load — creates a data URL from a local image file + E. Model playground — validates prompts with a deployed model  
**Why:** Each maps to documented SDK/portal behavior. Embedding models don't accept image chat input, TextContentItem doesn't load files, AudioContentItem is for audio not images.

---

## Q42
**Q:** Retail team wants semantic similarity search for product descriptions. Which model?  
**A:** B. Embedding model  
**Why:** Embedding models convert text into vectors for semantic comparison in vector space. Image generation, speech synthesis, and OCR serve different purposes.

---

## Q43
**Q:** Store owner uploads a street sign photo and wants text extracted. Which capability?  
**A:** A. OCR  
**Why:** OCR extracts printed or handwritten text from images — perfect for signs, labels, and posters. Object detection finds objects, image generation creates images, sentiment analysis is text-based.

---

## Q44
**Q:** Where to test image prompts quickly before writing code?  
**A:** B. Model playground  
**Why:** Foundry playgrounds provide instant prototyping and API exploration with deployed models. AI Search indexers, embedding deployments, and Speech Studio serve different purposes.

---

## Q45
**Q:** Which TWO content items belong together in a user message for image interpretation? (Select TWO)  
**A:** A. TextContentItem + B. ImageContentItem  
**Why:** The documented pattern uses TextContentItem for the question/instruction and ImageContentItem for the image. AudioContentItem and InputAudio are for audio, embedding vectors are for retrieval.

---

## Q46
**Q:** In the Foundry model catalog, to narrow models by features like reasoning or tool calling, use the ________ filter.  
**A:** D. Capabilities  
**Why:** The Capabilities filter specifically narrows by model features like reasoning and tool calling. Collection groups by source, Benchmark compares performance, Deployment groups by hosting style.

---

## Q47
**Q:** Azure AI model inference API lets developers talk with different models without changing the underlying ________.  
**A:** B. Code  
**Why:** The API provides a common interface so developers can work with different deployed models without changing their code. Image format, token limits, and speech locale are different concepts.

---

## Q48
**Q:** Upload call recording, extract transcript, summary, and speaker labeling. Which analyzer?  
**A:** B. prebuilt-audioSearch  
**Why:** prebuilt-audioSearch is specifically for audio extraction: transcript, summary, and speaker labeling. prebuilt-videoSearch is for video, prebuilt-imageSearch for images, prebuilt-read for documents.

---

## Q49
**Q:** Team uploads training videos and wants keyframes, transcript, and chapter segments. Which analyzer?  
**A:** A. prebuilt-videoSearch  
**Why:** prebuilt-videoSearch extracts keyframes, transcript, and chapter segments from video. prebuilt-audioSearch lacks video-specific outputs like keyframes and chapters.

---

## Q50
**Q:** Statement 1: You can test unsaved changes in agents playground. Statement 2: Unsaved changes are preserved if you leave. Statement 3: You need to save for conversation history and evaluations.  
**A:** B. Yes / No / Yes  
**Why:** You can test unsaved changes (Yes). Unsaved changes are LOST if you leave the portal (No). Saved versions are required for conversation history, monitoring, and evaluations (Yes).

---

## Q51
**Q:** Users upload a product photo and ask "What damage is visible?" Which model type?  
**A:** B. Multimodal chat model  
**Why:** Requires accepting both visual input (photo) and text question in the same interaction. Embedding models create vectors, speech models handle audio, image generation creates images — none interpret uploaded photos conversationally.

---

## Q52
**Q:** After naming a prompt-based agent, which property can no longer be changed?  
**A:** C. Agent name  
**Why:** Microsoft's documentation states the agent name cannot be changed after creation. Instructions, attached tools, and knowledge sources can all be iterated on during development.

---

## Q53
**Q:** If an image is in an accessible cloud location, you can pass its public ________ as input.  
**A:** C. URL  
**Why:** A public URL points to the image's location, allowing the model to access and process it. Embeddings are vectors, transcripts are audio output, vector indexes are search structures.

---

## Q54
**Q:** Which TWO outputs are directly associated with audio extraction in Content Understanding? (Select TWO)  
**A:** A. Speaker labeling + B. Transcript phrases  
**Why:** prebuilt-audioSearch performs speaker labeling, and transcriptPhrases contain transcription with speaker identification and timing. TTS is generation (not extraction), image generation is wrong modality.

---

## Q55 :red_circle:
**Q:** Local JPEG file to send as image input. Code: `from azure.ai.inference.models import ImageUrl` — missing line?  
**A:** C. `data_url = ImageUrl.load(image_file="receipt.jpg", image_format="jpeg")`  
**Why:** `ImageUrl.load()` is the documented helper that converts a local file into a data URL for multimodal input. `ImageUrl(image_file=...)` is NOT the correct pattern — must use `.load()` with both file path and format.

---

## Q56
**Q:** You want a video divided into logical sections like scenes. Which analyzer schema property?  
**A:** C. enableSegment  
**Why:** `enableSegment` in the analyzer schema enables segmentation of content into logical sections. systemPrompt is for generative AI behavior, returnDetails controls detail level, temperature is a model parameter.

---

## Q57 :red_circle:
**Q:** In Content Understanding, the contents object for audio-only and video inputs uses kind set to ________.  
**A:** C. audioVisual  
**Why:** The documented kind value is "audioVisual" for both audio-only and video inputs in Content Understanding. "transcript" is an output element inside the result, not the top-level kind value. "document" and "image" are different modalities.

---

## Q58
**Q:** Statement 1: OCR extracts text from images. Statement 2: Image generation returns bounding boxes. Statement 3: Object detection identifies objects and coordinates.  
**A:** B. Yes / No / Yes  
**Why:** OCR reads text (Yes). Image generation creates images, doesn't return bounding boxes (No). Object detection returns objects with bounding box coordinates (Yes).

---

## Q59
**Q:** Which THREE pairs are correctly matched? (Select THREE)  
**A:** A. RBAC — limits data access to authorized users + C. Managed identity — helps avoid embedding secrets in code + E. Private endpoint — reduces exposure to public internet  
**Why:** Each connects a real security control to its correct purpose. Transparency ≠ encryption, Fairness ≠ network isolation, Inclusiveness ≠ credential rotation.

---

## Q60
**Q:** AI assistant processes employee HR documents, reduce unauthorized access risk. Which consideration?  
**A:** B. Role-based access control  
**Why:** RBAC directly controls who can access data and system functions — the most immediate privacy/security need for HR document processing. Model interpretability is transparency, sentiment analysis and image captioning are AI capabilities not security controls.

---

## Q61
**Q:** Statement 1: transcriptPhrases include speaker ID and timing. Statement 2: prebuilt-videoSearch extracts keyframes and chapters. Statement 3: Content Understanding audio extraction converts text into spoken audio.  
**A:** A. Yes / Yes / No  
**Why:** transcriptPhrases have speaker ID and timing (Yes). prebuilt-videoSearch does keyframes and chapters (Yes). Audio extraction analyzes spoken content — converting text to audio is speech SYNTHESIS, not extraction (No).

---

## Q62
**Q:** Which TWO statements correctly describe Content Understanding extraction for audio and video? (Select TWO)  
**A:** A. It can transcribe speech from audio and video inputs + D. It can return transcript phrases with timing information  
**Why:** Content Understanding transcribes speech and returns transcript phrases with timing. It doesn't train custom foundation models, and converting text to audio is speech synthesis (different workload).

---

## Q63
**Q:** Cedarbridge scenario: Automated accessibility checks pass, PM wants evidence students using assistive tech can complete the workflow. Which activity?  
**A:** A. Accessibility user testing  
**Why:** User testing with representative users using assistive technologies (screen readers, keyboard-only, voice input) exposes barriers that automated checks miss. Supports the inclusiveness principle.

---

## Q64
**Q:** Cedarbridge scenario: Event coordinator uploads CSV, needs percentile calculations, capacity analysis, and chart generation. Which agent tool?  
**A:** C. Code Interpreter  
**Why:** Code Interpreter runs Python in a sandboxed environment — can load CSV, perform statistical calculations, filter data, and generate charts. File Search only retrieves passages, OpenAPI needs existing API, Web search accesses public internet.

---

## Q65 :red_circle:
**Q:** Cedarbridge scenario: Each support conversation is converted into one raw text string. Must synchronously return redacted version and metadata about detected sensitive entities. Which Azure Language capability?  
**A:** B. Text PII redaction  
**Why:** Text PII redaction processes unstructured text strings and returns detected entities with categories, offsets, lengths, confidence scores, and a redacted version. Conversation PII redaction is for structured conversational input with speakers/turns — but the input here has already been flattened into one raw text string.

---

## Q66 :red_circle:
**Q:** Cedarbridge scenario: Image Analysis 4.0 request must return one sentence describing the photo AND structured OCR results for visible signs/room numbers. Which features?  
**A:** D. features=caption,read  
**Why:** `caption` returns a one-sentence description of the overall image. `read` performs OCR and returns visible text as structured results. denseCaptions gives region-level captions (not one overall sentence), tags gives keywords (not a sentence), smartCrops identifies cropping regions (not OCR).

---

## Q67 :red_circle:
**Q:** Cedarbridge scenario: Process grant files with varying layouts, return structure-preserving Markdown, common JSON schema, and specific field extraction. Which component?  
**A:** C. Content Understanding analyzer  
**Why:** A Content Understanding custom analyzer defines content type, elements to extract, and user-defined fields to return. It preserves structure in Markdown while returning structured JSON. A prebuilt document analyzer extracts general content but doesn't contain custom business schemas. Azure Vision Read only does OCR without semantic interpretation.

---

## Key Takeaway Tables

### Incorrect Answers Summary

| Q# | Your Answer | Correct Answer | Key Lesson |
|---|---|---|---|
| Q4 | C=Req1, F=Req2 (reversed) | F=Req1, C=Req2 | Portal agent = Single-agent solution (F), Code-based app = Foundry SDK (C) |
| Q26 | Yes/No/Yes | Yes/Yes/No | Public image URLs ARE supported. NOT every multimodal model supports multiple images per turn |
| Q36 | Image captioning + Text-to-image | Object detection + People detection | Bounding boxes come from detection tasks, not captioning or generation |
| Q55 | ImageUrl(image_file=...) | ImageUrl.load(image_file=..., image_format=...) | Use `.load()` method with format parameter for local files |
| Q57 | transcript | audioVisual | Contents object kind for audio/video is "audioVisual", not "transcript" |
| Q65 | Conversation PII redaction | Text PII redaction | Flattened text string = Text PII. Structured multi-turn = Conversation PII |
| Q66 | denseCaptions,objects | caption,read | caption = one sentence. read = OCR. denseCaptions = region-level (wrong granularity) |
| Q67 | Prebuilt document analyzer | Content Understanding analyzer | Custom schemas with varying layouts = Content Understanding, not prebuilt analyzer |

### Content Understanding Analyzer IDs

| Analyzer ID | Input Type | Key Outputs |
|---|---|---|
| prebuilt-audioSearch | Audio (MP3, WAV) | Transcript, summary, speaker labeling |
| prebuilt-videoSearch | Video (MP4) | Keyframes, transcript, chapter segments |
| prebuilt-imageSearch | Images | Image descriptions, searchable understanding |
| prebuilt-document | Documents | General content, layout, structure |
| Custom analyzer | Any supported | User-defined fields, Markdown, JSON schema |

### Content Kind Values

| Kind | Used For |
|---|---|
| audioVisual | Audio-only AND video inputs |
| document | Document inputs |
| image | Image inputs |

### Image Analysis 4.0 Features

| Feature | What It Returns |
|---|---|
| caption | One sentence describing the entire image |
| denseCaptions | Detailed captions for individual regions/objects |
| read | OCR — structured text from visible signs/text |
| tags | Descriptive keywords |
| objects | Detected objects with bounding boxes |
| smartCrops | Suggested crop regions |

### Text PII vs Conversation PII

| Capability | Input Format | Best For |
|---|---|---|
| Text PII redaction | Raw text string | Flattened/unstructured text, synchronous processing |
| Conversation PII redaction | Structured conversation (speakers/turns) | Multi-speaker chat transcripts with turn structure |

### Bounding Box Capabilities

| Capability | Returns Bounding Boxes? |
|---|---|
| Object detection | Yes |
| People detection | Yes |
| Dense captioning | Yes (with region descriptions) |
| Image captioning | No (whole-image sentence only) |
| Image generation | No (creates images, doesn't analyze) |

### Local Image Input Pattern
```python
# CORRECT — use .load() with format
data_url = ImageUrl.load(image_file="receipt.jpg", image_format="jpeg")

# WRONG — no .load(), no format
data_url = ImageUrl(image_file="receipt.jpg")
```
