# Test 6 - QA Notes

**Score: 43/65 (66%)**
**Incorrect: Q1, Q7, Q8, Q10, Q11, Q12, Q20, Q26, Q28, Q29, Q44, Q46, Q48, Q52, Q53, Q54, Q58, Q60, Q61, Q63, Q64, Q65**

---

## :red_circle: Q1. Which THREE pairs are correctly matched? (Speech capabilities)

**Answer:** A. Speech to Text -- converts spoken audio into text, C. Text to Speech -- generates spoken audio from text, F. Custom speech -- can improve recognition for domain-specific words

**Why:** STT = audio to text. TTS = text to audio. Custom speech = adapt recognition for specialized vocabulary. B wrong: TTS doesn't detect sentiment. D wrong: STT doesn't create images. E wrong: Custom speech doesn't extract invoice fields.

---

## Q2. Python app returns sentiment of a review with show_opinion_mining=True. Which method?

**Answer:** B. analyze_sentiment

**Why:** analyze_sentiment returns sentiment labels + opinion mining support. detect_language (A) = language ID. recognize_entities (C) = NER. extract_key_phrases (D) = topics.

---

## Q3. Improving voice app for different accents, physical abilities, interaction needs. Which principle?

**Answer:** D. Inclusiveness

**Why:** Inclusiveness = designing AI for people with wide range of needs, backgrounds, abilities. Fairness = equitable outcomes. Transparency = system understanding. Reliability = dependable operation.

---

## Q4. Deployed chat model, want to send prompts immediately in portal without code. Which experience?

**Answer:** C. Model playground

**Why:** Model playground = interactive testing of deployed models. Deploy model -> land on playground -> test prompts immediately. Agents playground (A) = agent workflows. Tracing (B) = debugging. Evaluation dashboard (D) = measuring quality.

---

## Q5. Which THREE pairs? (Content Understanding analyzers)

**Answer:** A. Audio analyzer -- speaker diarization and transcript extraction, B. Video analyzer -- key frame extraction and scene metadata, D. Video analyzer -- RAG-ready markdown with transcript and key frames

**Why:** Audio = transcript + diarization + sentiment. Video = key frames + scene segmentation + RAG-ready output + transcript (WEBVTT). C wrong: barcode detection = document, not audio. E wrong: face description ≠ audio. F wrong: video DOES support transcripts.

---

## Q6. Improve prompt, compare outputs, validate behavior before writing code. What first?

**Answer:** B. Use the Foundry playground

**Why:** Playground = on-demand rapid prototyping, experimentation, validation before code. Not build full app (A), create workflow agent (C), or fine-tune (D) first.

---

## :red_circle: Q7. AI team tells users responses are AI-generated and documents limitations. This improves ________.

**Answer:** B. Transparency

**Why:** Labeling AI-generated output + documenting limitations = classic transparency. Not fairness (equitable outcomes), inclusiveness (broad usability), or accountability (governance roles).

---

## :red_circle: Q8. Company assigns named owners for model approval, monitoring, incident review, rollback. Which principle?

**Answer:** A. Accountability

**Why:** Named owners for governance decisions = accountability. Who is answerable for design, deployment, governance. Not transparency (explaining system), fairness (equitable outcomes), or privacy/security (data protection).

---

## Q9. Statement combo: GenAI trained on large datasets / GenAI retrieves fixed answers / Same prompt different outputs

**Answer:** B. Yes / No / Yes

**Why:** GenAI IS trained on large datasets and learns patterns. GenAI does NOT work like a fixed lookup table. Same prompt CAN produce different outputs across runs.

---

## :red_circle: Q10. Chat model for interactive support, unpredictable traffic, pay-per-token. Which deployment?

**Answer:** B. Global Standard

**Why:** Global Standard = pay-per-token, interactive workloads, broad Azure reach. Global Batch (A) = async batch processing. Global Provisioned (C) = reserved hourly capacity. Data Zone Batch (D) = batch in specific zone.

---

## :red_circle: Q11. Statement combo: Multimodal vision for image description / Content Understanding for schema fields / Image analyzers for text extraction

**Answer:** A. Yes / Yes / No

**Why:** Multimodal vision IS sufficient for natural-language image descriptions. Content Understanding IS better for schema-defined field extraction. Image analyzers are NOT optimized for primarily text extraction -- use document field extraction instead.

---

## :red_circle: Q12. Statement combo: Sentiment classifier = generative AI / Agentic AI uses tools / Generative AI creates content

**Answer:** D. No / Yes / Yes

**Why:** Sentiment classifier = traditional AI (classification/prediction), NOT generative. Agentic AI DOES use tools + multistep actions. Generative AI DOES create new content (text, images).

---

## Q13. Analyze invoice PDF, read extracted fields. What replaces `await poller.________`?

**Answer:** A. result()

**Why:** Content Understanding async pattern: `begin_analyze()` -> poller -> `await poller.result()`. Not wait() (B), get_result() (C), or poll_until_done() (D).

---

## Q14. Which THREE pairs? (Model type to task)

**Answer:** A. Transcribe spoken calls -- speech model, C. Ask about product photo + caption -- multimodal model, D. Generate marketing paragraph from keywords -- text model

**Why:** B wrong: invoice extraction from scanned form ≠ text-only (visual layout). E wrong: image generation ≠ speech. F wrong: text-to-speech ≠ vision.

---

## Q15. Which TWO factors increase hallucinations/weak grounding?

**Answer:** B. Missing or poor-quality grounding data & E. Prompt instructions that do not require source-based answers

**Why:** Bad retrieval data + no instruction to stay grounded = model fills gaps from general patterns. Lower temperature (A) = more deterministic. Shorter latency (C) = design choice. Provisioned deployment (D) = throughput model.

---

## Q16. Larger model = richer but slower/expensive. Smaller = faster/cheaper but less nuanced. Which statement?

**Answer:** C. Larger or more capable models often improve response quality, but can increase latency and cost

**Why:** Core trade-off: quality vs latency vs cost. Teams benchmark multiple models. Not "higher quality always reduces cost" (A), "provisioned removes trade-offs" (B), or "cost = region only" (D).

---

## Q17. Which THREE pairs? (Workload matching)

**Answer:** A. Generate product description from bullet points -- generative AI, C. System decides to search + call tools to complete task -- agentic AI, E. Read invoice numbers from scanned forms -- information extraction

**Why:** B wrong: sentiment detection = text analysis, not speech synthesis. D wrong: meeting audio to text = speech, not computer vision. F wrong: object detection in images = computer vision, not text analysis.

---

## Q18. Detect product names, company names, city names in reviews. Which technique?

**Answer:** B. Entity recognition

**Why:** NER = find and categorize named items (products, orgs, locations). Keyword extraction (A) = important phrases, not typed entities. Sentiment (C) = opinion/polarity. Summarization (D) = condense text.

---

## Q19. Statement combo: Language ID in audio / Diarization identifies speakers / Batch transcription for live captions

**Answer:** A. Yes / Yes / No

**Why:** Language identification IS a speech feature. Diarization DOES separate speakers. Batch transcription = prerecorded audio, NOT live low-latency captions (use real-time transcription).

---

## :red_circle: Q20. Which TWO are computer vision or image-generation capabilities?

**Answer:** B. OCR & D. Text-to-image generation

**Why:** OCR = extract text from images (computer vision). Text-to-image = create images from prompts (image generation). Entity recognition (A) = text analysis. Speech translation (C) = speech. Keyword extraction (E) = NLP.

---

## Q21. Which TWO downstream actions for Content Understanding output?

**Answer:** A. Send extracted totals/due dates into approval workflow & C. Index extracted markdown/fields in Azure AI Search

**Why:** Content Understanding output feeds automation workflows and search/RAG pipelines. Not increase temperature (B), replace embeddings with confidence (D), or remove structure (E).

---

## Q22. Statement combo: Task planning breaks goal into steps / Tool use calls external capabilities / Task completion returns final result

**Answer:** B. Yes / Yes / Yes

**Why:** All three are core agentic workflow concepts. Task planning = decompose goals. Tool use = call search/tools. Task completion = return final answer after work.

---

## Q23. User uploads photo, asks model to describe damage and read shipping label. Scenario for ________.

**Answer:** A. multimodal prompting

**Why:** Image + text instruction together = multimodal prompting. Not keyword extraction (B, text only), speech synthesis (C, audio), or custom text classification (D, text labels).

---

## Q24. Field technician with gloves outdoors needs hands-free AI interaction. Which style?

**Answer:** D. Speech-based interaction

**Why:** Hands-free + gloves + outdoors = speech input is most appropriate. Not OCR (A, images), keyword extraction (B, text analysis), or text-based (C, requires typing).

---

## Q25. Bank loan-screening tool: similar applicants, different demographic groups, different approval rates. Which principle?

**Answer:** A. Fairness

**Why:** Unequal outcomes for similarly qualified people across groups = fairness issue. Not transparency (explanation), accountability (governance), or inclusiveness (accessibility).

---

## :red_circle: Q26. Which THREE pairs? (Prompt design)

**Answer:** A. System message -- sets initial instructions and rules, C. Few-shot examples -- provide example user/assistant interactions to prime behavior, E. Clear syntax and separators -- make sections easier for model to parse

**Why:** B wrong: user message = current task, NOT persistent behavior. D wrong: user prompt doesn't replace system message. F wrong: assistant message NOT required before first user request.

---

## Q27. Image for store banner -- photorealistic blue running shoes on white background. Best prompt?

**Answer:** D. "Photorealistic studio product shot of blue running shoes on a clean white background, soft shadow, e-commerce style"

**Why:** Describes content AND visual style = effective image prompt. "Blue shoes" (A) = too sparse. "Create a shoe image" (B) = no specifics. "Photorealistic shoes" (C) = missing color/background.

---

## :red_circle: Q28. Lightweight Python chat client using Foundry SDK. Get OpenAI client from AIProjectClient?

**Answer:** B. `openai = project.get_openai_client()`

**Why:** Foundry quickstart: `AIProjectClient` -> `project.get_openai_client()` -> `openai.responses.create()`. Not openai_client() (A, wrong method name), AIProjectClient.get_openai_client() (C, class vs instance), or responses_client() (D, not documented).

---

## :red_circle: Q29. Which TWO actions best address reliability and safety?

**Answer:** B. Test with adversarial and edge-case inputs & D. Add fallback behavior or human escalation for risky responses

**Why:** Reliability/safety = consistent behavior + harm avoidance. Adversarial testing reveals failures. Fallback/escalation catches risky outputs. Transparency note (A) = transparency. Encryption (C) = privacy/security. Accessibility (E) = inclusiveness.

---

## Q30. Multi-turn agent conversation. What creates the conversation?

**Answer:** D. `conversation = openai.conversations.create()`

**Why:** Foundry agent quickstart: create conversation first -> pass `conversation.id` to `responses.create()`. Not responses.create() (A, generates response), agents.create_version() (B, versions agent), or threads.create() (C, older pattern).

---

## Q31. Which TWO compare portal testing vs SDK implementation?

**Answer:** A. Playground lets you prototype without code & C. Foundry SDK builds programmatic chat/agent clients in code

**Why:** B wrong: SDK doesn't require portal for every request. D wrong: portal not required for conversation state. E wrong: SDK still needs deployed model.

---

## Q32. Which TWO are accurate about chat completion tuning?

**Answer:** A. Lower temperature = more focused/deterministic & D. max_completion_tokens = upper bound on generated tokens

**Why:** B wrong: top_p = nucleus sampling, not conversation ID. C wrong: Microsoft says alter temperature OR top_p, not both. E wrong: stream = partial deltas, not agent request conversion.

---

## Q33. Maintaining conversation history, preserve system instructions. What code?

**Answer:** B. `conversation.append(system_message)`

**Why:** System message goes first in messages array. Append it before user turns. Not clear() (A, removes all), append assistant with user content (C, wrong role), or assign response content (D, breaks structure).

---

## Q34. AI processes employee performance notes, restrict access, protect stored data. Which principle?

**Answer:** C. Privacy and security

**Why:** Protecting data + controlling access + preventing unauthorized use = privacy and security. Not reliability (A, dependable behavior), transparency (B, explanation), or inclusiveness (D, broad access).

---

## Q35. Which TWO scenarios best fit agent vs direct model call?

**Answer:** B. Answer question by searching web and citing results & D. Look up order through external API then decide next action

**Why:** Agents = tool use + multistep actions. Web search = agent tool. API lookup + decision = agent workflow. Rewriting (A), one-sentence summary (C), basic classification (E) = simple direct model calls.

---

## Q36. Foundry prompt agent must answer as travel-policy assistant, refuse unrelated, keep brief. Configure ________.

**Answer:** C. instructions

**Why:** Instructions field = behavior, role, response style for prompt agents. Not WebSearchTool (A, a tool), previous_response_id (B, conversation continuity), or temperature (D, sampling variability).

---

## Q37. Define agent instructions, attach tools, test multi-turn without code. Which portal?

**Answer:** A. Agents playground

**Why:** Agents playground = explore, prototype, test agents with instructions + tools + multi-turn. Model catalog (B) = browse models. Management center (C) = admin. Content safety dashboard (D) = governance.

---

## Q38. Which THREE pairs? (Prompt components)

**Answer:** A. System prompt -- sets assistant behavior and rules, C. Grounding data -- external data used to anchor responses, F. User prompt -- contains end user's request

**Why:** B wrong: user prompt ≠ automatic document retrieval. D wrong: context ≠ hidden deployment policy. E wrong: grounding data ≠ token sampling randomness.

---

## Q39. Which THREE pairs? (Agent tools)

**Answer:** A. Web search -- real-time public web info with citations, D. Code Interpreter -- run Python for math/analysis/charts, F. File Search -- augment agent with uploaded/proprietary documents

**Why:** B wrong: File Search ≠ Python code (that's Code Interpreter). C wrong: OpenAPI ≠ uploaded file vector search (that's File Search). E wrong: MCP server tool = MCP, not Function calling (Function calling = custom functions YOUR app executes).

---

## Q40. Multi-turn chat, continue prior response. What code?

**Answer:** D. `previous_response_id=response.id`

**Why:** Responses API: reference earlier response ID for conversation continuity. Not tool_choice (A, tool behavior), store (B, persistence), or instructions=response.id (C, instructions ≠ response ID).

---

## Q41. Test voice input and spoken responses for gpt-realtime in portal. Which playground?

**Answer:** A. Audio playground

**Why:** GPT Realtime = Audio playground (Chat playground does NOT support gpt-realtime). Not Chat (B), Agents (C, agent workflows), or Vision (D, images).

---

## Q42. Capture speech from microphone, convert to text. Which method on SpeechRecognizer?

**Answer:** C. recognize_once_async

**Why:** `speech_recognizer.recognize_once_async().get()` = capture utterance and return text. speak_text_async (A) = TTS on SpeechSynthesizer. analyze_sentiment (B) = Azure Language. create_version (D) = agent versioning.

---

## Q43. Which THREE pairs? (Text analysis capabilities)

**Answer:** A. Sentiment analysis -- detects opinion/polarity, C. Key phrase extraction -- identifies main talking points, E. Summarization -- produces shorter version of document/conversation

**Why:** B wrong: entity recognition ≠ text-to-audio. D wrong: summarization ≠ bounding boxes. F wrong: key phrase extraction ≠ speaker identification.

---

## :red_circle: Q44. Convert document chunks into vectors for semantic search. Which model type?

**Answer:** C. Embedding model

**Why:** Embedding models = text -> numeric vector representations for similarity search. Chat completion (A) = conversational generation. Image generation (B) = create images. Speech model (D) = audio.

---

## Q45. Listen to spoken request, read back text response. What code for TTS?

**Answer:** B. `synthesizer.speak_text_async("Your order ships today.").get()`

**Why:** SpeechSynthesizer.speak_text_async = text-to-speech. Not recognizer.speak_text_async (A, wrong object). Not result.transcribe_text_async (C, not a synthesis method). Not audio_config.read_text (D, config object, not synthesizer).

---

## :red_circle: Q46. Voice-enabled prompt app. Which TWO steps in the flow?

**Answer:** A. Convert spoken input to text before prompt submission & C. Convert final text response to speech

**Why:** Speech flow: STT -> model processes text -> TTS. Not OCR on microphone (B), object detection on audio (D), or sentiment as required output step (E).

---

## Q47. Vision chat model: text + image URL in same prompt. What code for image?

**Answer:** D. `{"type": "image_url", "image_url": {"url": image_url}}`

**Why:** Chat completions API: type "image_url" with nested image_url object. Not audio type (A), ocr type (B), or caption type (C).

---

## :red_circle: Q48. Generate new product mockup from text prompt in Foundry. Which deployment?

**Answer:** C. gpt-image-1

**Why:** gpt-image-1 = image generation from prompts. gpt-4o-mini (A) = chat/reasoning. Azure AI Vision (B) = image analysis, not generation. Azure Language (D) = text analysis.

---

## Q49. One approach for structured info from documents, images, call recordings, videos?

**Answer:** C. Azure Content Understanding

**Why:** Multimodal extraction service: documents + images + audio + video -> structured outputs. OCR (A) = text from images only. Sentiment (B) = text opinion. TTS (D) = generate audio.

---

## Q50. Return one-sentence description for uploaded image. Which VisualFeature?

**Answer:** A. VisualFeatures.CAPTION

**Why:** CAPTION = human-readable image description. READ (B) = OCR text extraction. OBJECTS (C) = object detection. PEOPLE (D) = person detection.

---

## Q51. Which THREE pairs? (Vision task types)

**Answer:** A. Image description -- short natural-language caption, B. Visual question answering -- answer "What is the person holding?", D. Visual extraction -- read text or fields from image

**Why:** C wrong: visual extraction ≠ generate new poster (that's image generation). E wrong: image description ≠ speaker turns (that's diarization). F wrong: VQA ≠ email sentiment (that's text analysis).

---

## :red_circle: Q52. Local JPEG to multimodal model via Responses API. Base64 image input code?

**Answer:** C. `{"type": "input_image", "image_url": f"data:image/jpeg;base64,{base64_image}"}`

**Why:** Responses API uses `type: "input_image"` + `image_url` with data URL. Not "image" type (A), "input_image" with "image" key (B), or chat-style "image_url" type (D, that's for chat completions, not Responses API).

---

## :red_circle: Q53. Support assistant must respond quickly + avoid harmful outputs. Which TWO evaluation criteria?

**Answer:** B. Latency & E. Safety

**Why:** "Respond quickly" = latency. "Avoid harmful outputs" = safety. Accuracy (A) = not directly emphasized here. Keyword extraction (C) = capability, not criteria. Translation (D) = capability, not criteria.

---

## :red_circle: Q54. Which THREE pairs? (Task types)

**Answer:** A. Chat -- interactive back-and-forth Q&A, C. Classification -- assigning ticket to category, D. Extraction -- pulling key fields from form

**Why:** B wrong: summarization ≠ extracting invoice number (that's extraction). E wrong: casual -> formal English = rewriting, not translation (same language). F wrong: English -> Japanese = translation, not rewriting (cross-language).

---

## Q55. Process invoices/tax forms from many templates, return structured fields. Which option?

**Answer:** B. Azure Content Understanding

**Why:** Content Understanding document analyzers = extract fields/relationships from diverse documents/forms. Azure AI Vision (A) = image analysis. Azure AI Search (C) = indexing/retrieval. Multimodal model (D) = general prompting, not schema-based extraction.

---

## Q56. Which THREE pairs? (Model parameters)

**Answer:** B. top_p -- nucleus sampling over highest-probability tokens, D. Max tokens -- caps generated text, E. Context window -- limits input/conversation history

**Why:** A wrong: temperature = randomness, NOT conversation size. C wrong: context window ≠ safety threshold. F wrong: temperature ≠ grounding source selection.

---

## Q57. Analyze shelf photos, return structured fields (product count, brand, out-of-stock). Best fit?

**Answer:** A. Azure Content Understanding image analyzer

**Why:** Schema-defined structured extraction from images. Shelf analysis = documented use case. Multimodal prompt (B) = free-form, not structured. Speech (C) = wrong modality. OCR-only (D) = text only, not full visual understanding.

---

## :red_circle: Q58. Mixed mailbox: purchase orders, invoices, procurement docs. One prebuilt analyzer?

**Answer:** C. prebuilt-procurement

**Why:** prebuilt-procurement = broader analyzer for all procurement document types. prebuilt-invoice (A) = invoices only. prebuilt-purchaseOrder (B) = POs only. prebuilt-documentSearch (D) = RAG/search-oriented, not domain-specific extraction.

---

## Q59. Try prebuilt analyzer on sample data, review results before integrating. Where first?

**Answer:** B. Content Understanding Studio

**Why:** Studio = try prebuilt analyzers, build/test custom analyzers, review results. Not AI Search (A, indexing), Function calling (C, orchestration), or Embedding deployment (D, vectorization).

---

## :red_circle: Q60. Which THREE pairs? (Content Understanding field properties)

**Answer:** A. confidence -- estimated reliability of predicted field value, C. Object field -- nested structure (TotalAmount with Amount + CurrencyCode), E. spans -- positions of field value in markdown content

**Why:** B wrong: source = position identifier, NOT temperature. D wrong: array field = repeated structures (line items), NOT single scalar. F wrong: markdown = broad content representation, NOT currency-only.

---

## :red_circle: Q61. Verdant Arc case study -- new sensors report 18% higher values. Which monitoring signal?

**Answer:** D. Data drift

**Why:** Data drift = detect changes in production input distribution vs training data. Model returns high confidence but inputs shifted. Feature attribution (A) = explains influence. Cohort fairness (B) = group comparisons. Endpoint latency (C) = response time.

---

## Q62. Verdant Arc -- agent must submit calculation to queue-triggered Azure Function. Which tool?

**Answer:** B. Azure Functions tool

**Why:** Azure Functions tool = queue-based integration (input queue -> function -> output queue). Reuses existing architecture. Code Interpreter (A) = sandbox Python. OpenAPI (C) = needs REST API wrapper. File Search (D) = document retrieval.

---

## :red_circle: Q63. Verdant Arc -- translate one Dutch DOCX, apply glossary, preserve formatting, return directly, no storage containers.

**Answer:** A. Synchronous document translation

**Why:** Synchronous = one document in multipart request, translated doc returned directly, supports glossary, preserves formatting, NO storage containers. Asynchronous (B) = requires blob containers. Text translation (C) = plain text only, no doc formatting. Custom Translator training (D) = trains model, doesn't translate.

---

## :red_circle: Q64. Verdant Arc -- Generate Thumbnail preserving most important crop region. Missing config?

**Answer:** C. smartCropping=true

**Why:** smartCropping=true = identify area of interest, crop around most important region. smartCropping=false (A) = disables smart crop. detectOrientation (B) = rotation, not cropping. visualFeatures=objects (D) = object detection, not thumbnail config.

---

## :red_circle: Q65. Verdant Arc -- varied photo layouts, return specific JSON fields. Which component?

**Answer:** D. Custom image analyzer

**Why:** Custom Content Understanding image analyzer = inherit image processing + add user-defined field schema. Azure Vision Read (A) = raw OCR, no field mapping. Multimodal prompt (B) = requires custom prompt logic. Prebuilt image analyzer (C) = no organization-specific field schema.

---

# Key Takeaway Tables

## Responsible AI Principle Quick Matcher
| Scenario | Principle |
|---|---|
| Tell users it's AI, document limitations | Transparency |
| Named owners for approval/monitoring/rollback | Accountability |
| Different accents, abilities, interaction needs | Inclusiveness |
| Similar applicants, different approval rates | Fairness |
| Restrict access, protect stored data | Privacy and Security |
| Test adversarial inputs, add fallback behavior | Reliability and Safety |

## Speech SDK Pattern
| Object | Method | Purpose |
|---|---|---|
| SpeechRecognizer | `recognize_once_async().get()` | STT: microphone -> text |
| SpeechSynthesizer | `speak_text_async(text).get()` | TTS: text -> spoken audio |
| Custom speech | N/A | Improve recognition for domain-specific words |

## Deployment Options
| Option | Use Case |
|---|---|
| Global Standard | Interactive, pay-per-token, unpredictable traffic |
| Global Provisioned | Reserved hourly capacity, predictable high volume |
| Global Batch | Async batch processing, prerecorded content |
| Data Zone Batch | Batch in specific data zone |

## Foundry Playgrounds
| Playground | Use Case |
|---|---|
| Model playground | Test deployed model prompts, compare outputs |
| Agents playground | Define instructions, attach tools, test multi-turn agents |
| Audio playground | Test gpt-realtime voice I/O (Chat playground does NOT support gpt-realtime) |

## Foundry SDK Pattern
```python
# AIProjectClient -> get_openai_client() -> responses.create()
project = AIProjectClient(endpoint=EP, credential=DefaultAzureCredential())
openai = project.get_openai_client()  # NOT openai_client()

# Multi-turn with agent:
conversation = openai.conversations.create()
response = openai.responses.create(conversation=conversation.id, ...)

# Multi-turn with Responses API:
follow_up = client.responses.create(previous_response_id=response.id, ...)
```

## Content Understanding Async Pattern
```python
poller = await client.begin_analyze(analyzer_id="prebuilt-invoice", inputs=[...])
result = await poller.result()  # NOT wait(), get_result(), poll_until_done()
```

## Responses API vs Chat Completions API - Image Input
| API | Type Field | Image Field |
|---|---|---|
| Chat Completions | `"type": "image_url"` | `"image_url": {"url": url}` |
| Responses API | `"type": "input_image"` | `"image_url": "data:image/jpeg;base64,..."` |

## Agent Tools
| Tool | Purpose |
|---|---|
| Web search | Real-time public web info with citations |
| File Search | Ground agent in uploaded/proprietary documents |
| Code Interpreter | Run Python in sandbox (math, analysis, charts) |
| OpenAPI tool | Connect to external HTTP APIs via OpenAPI spec |
| Azure Functions tool | Queue-based integration with existing Azure Functions |
| Function calling | Custom functions YOUR app executes and returns results |
| MCP | Connect to tools on MCP server maintained by another team |

## Model Types
| Model Type | Purpose |
|---|---|
| Chat completion | Conversational generation, instruction following |
| Embedding | Text -> vector representations for semantic search |
| Image generation (gpt-image-1) | Create images from text prompts |
| Speech | STT, TTS, transcription |
| Multimodal | Image + text together |

## Evaluation Criteria vs Capabilities
| Evaluation Criteria | Capabilities (NOT criteria) |
|---|---|
| Latency, Safety, Accuracy, Cost | Keyword extraction, Translation, Sentiment analysis |

## Task Type Distinctions
| Task | What It Does | NOT |
|---|---|---|
| Summarization | Condenses text shorter | Extracting a specific field |
| Extraction | Pulls specific fields/facts | Summarizing overall content |
| Translation | Changes LANGUAGE (EN -> JP) | Changing tone in same language |
| Rewriting | Changes tone/style SAME language | Cross-language conversion |
| Classification | Assigns category labels | Open-ended generation |

## Prebuilt Analyzers
| Analyzer | Scope |
|---|---|
| prebuilt-procurement | Mixed procurement docs (POs, invoices, etc.) |
| prebuilt-invoice | Invoices specifically |
| prebuilt-purchaseOrder | Purchase orders specifically |
| prebuilt-documentSearch | RAG/search-oriented document ingestion |

## Content Understanding Field Properties
| Property | Meaning |
|---|---|
| confidence | Estimated reliability of predicted value |
| source | Position identifier in content (NOT temperature) |
| spans | Positions of field value in markdown |
| Object field | Nested structure (e.g., TotalAmount -> Amount + CurrencyCode) |
| Array field | Repeated structures (e.g., line items), NOT single scalar |

## Monitoring Signals
| Signal | Detects |
|---|---|
| Data drift | Input distribution change vs training data |
| Feature attribution | How features influenced a result |
| Cohort fairness | Performance differences across groups |
| Endpoint latency | Response time changes |

## Document Translation
| Option | When |
|---|---|
| Synchronous | One doc, direct response, no storage containers, glossary supported |
| Asynchronous | Batch, multiple docs, requires blob storage containers |
| Text translation | Plain text strings only, no document formatting |

## Traditional AI vs Generative AI
| Traditional AI | Generative AI |
|---|---|
| Classification, prediction, scoring | Creates NEW content (text, images) |
| Sentiment classifier = traditional | Chatbot, image generator = generative |
| Fixed labels from predefined set | Novel outputs from learned patterns |
