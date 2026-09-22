# AI-901 Practice Assessment - Question, Answer & Why Notes

> Based on your practice test results. Focus on questions you got **wrong** - they are marked with a red flag.

---

## Q1. Which THREE pairs are correctly matched? (Speech services)

**Answer:** A, C, F
- A. Speech to Text — converts spoken audio into text
- C. Text to Speech — generates spoken audio from text
- F. Custom speech — can improve recognition for domain-specific words

**Why:** Speech to Text = transcription. Text to Speech = audio generation. Custom speech = domain vocabulary improvement. Don't confuse speech services with sentiment analysis (B), image generation (D), or form extraction (E) — those belong to different AI workloads.

---

## Q2. Fill the blank: `client.________(documents, show_opinion_mining=True)` for sentiment

**Answer:** B. `analyze_sentiment`

**Why:** `analyze_sentiment()` is the `TextAnalyticsClient` method for sentiment. Other methods: `detect_language()` = language, `recognize_entities()` = NER, `extract_key_phrases()` = key phrases. Package: `azure-ai-textanalytics`.

---

## Q3. Voice app improved for different accents, abilities, interaction needs = which principle?

**Answer:** D. Inclusiveness

**Why:** Inclusiveness = designing AI accessible to people with diverse abilities, accents, and needs. Fairness = equal outcomes across groups. They're close, but inclusiveness is about **broad usability/accessibility**, fairness is about **equal treatment in results**.

---

## Q4. Send prompts to deployed model WITHOUT code in portal?

**Answer:** C. Model playground

**Why:** Model playground = interactive no-code testing of deployed models. Agents playground = for agent testing with tools/instructions. Tracing = debugging. Evaluation dashboard = monitoring metrics.

---

## Q5. Correctly matched: Audio analyzer vs Video analyzer capabilities

**Answer:** A, B, D
- A. Audio analyzer — speaker diarization and transcript extraction
- B. Video analyzer — key frame extraction and scene metadata
- D. Video analyzer — RAG-ready markdown with transcript and key frames

**Why:** Audio analyzers focus on transcript-based analysis (diarization, summarization). Video analyzers handle key frames, segmentation, and transcript-aware metadata. Barcode detection (C) = document extraction. Face description (E) = visual context, not audio. Video DOES support transcripts (F is wrong).

---

## Q6. Improve prompt and validate behavior before writing code?

**Answer:** B. Use the Foundry playground

**Why:** Playground = rapid prototyping without code. Don't build full app first (A), create workflow agent (C), or fine-tune model (D) before you even know if the prompt works.

---

## :red_circle: Q7. AI team tells users responses are AI-generated and documents limitations = which principle?

**Answer:** B. Transparency (NOT Accountability)

**Why:** Transparency = helping people understand when AI is used and what its limitations are. Accountability = who is responsible for oversight/governance. Labeling AI output + documenting limits = **disclosure and explanation** = Transparency. Accountability would be about assigning named owners for decisions.

---

## :red_circle: Q8. Company assigns named owners for model approval, monitoring, incident review, rollback?

**Answer:** A. Accountability (NOT Privacy & Security)

**Why:** Accountability = people/teams are responsible for AI system governance. Named owners for approval, monitoring, incidents, and rollback = **governance roles** = Accountability. Privacy = protecting data. Key distinction: **who is answerable** = Accountability.

---

## Q9. True/False on generative AI statements

**Answer:** B. Yes / No / Yes
- Yes: Models trained on large datasets learning patterns
- No: Models do NOT retrieve fixed prewritten answers (they generate probabilistically)
- Yes: Same prompt CAN produce different outputs across runs

**Why:** Generative AI generates from learned patterns, not from a lookup table. Output varies because of probabilistic token sampling.

---

## :red_circle: Q10. Unpredictable traffic, pay-per-token pricing, interactive chat = which deployment?

**Answer:** B. Global Standard (NOT Global Batch)

**Why:** Global Standard = pay-per-token, interactive workloads, unpredictable traffic. Global Batch = async batch processing (NOT for real-time chat). Global Provisioned = reserved hourly capacity. Remember: **interactive + pay-per-token = Global Standard**.

---

## :red_circle: Q11. Multimodal vision vs Content Understanding vs Image analyzer statements

**Answer:** A. Yes / Yes / No
- Yes: Multimodal vision model sufficient for natural-language image descriptions
- Yes: Content Understanding better for schema-defined fields (invoice number, total)
- No: Image analyzers are NOT optimized when main goal is text extraction (use document schema instead)

**Why:** Image analyzers = structured data from images. When you primarily need text extraction, use document field extraction schema, not image analyzer.

---

## :red_circle: Q12. Sentiment classifier = generative AI? Agentic AI uses tools? Generative AI creates content?

**Answer:** D. No / Yes / Yes

**Why:** Sentiment classifier = **traditional AI** (classification/prediction), NOT generative. Agentic AI = uses tools, plans, takes multistep actions. Generative AI = creates new content (text, images). Key: **classification ≠ generation**.

---

## Q13. Code fill: Content Understanding async analyzer, what replaces blank after `await poller.____`?

**Answer:** A. `result()`

**Why:** Pattern is `poller = await client.begin_analyze(...)` then `result = await poller.result()`. Not `wait()`, not `get_result()`, not `poll_until_done()`.

---

## Q14. Match workloads to model types (speech, multimodal, text)

**Answer:** A, C, D
- A. Transcribe calls — speech model
- C. Ask about photo + caption — multimodal model
- D. Generate marketing paragraph — text model

**Why:** Invoice extraction (B) needs more than text-only (visual layout). Image generation (E) ≠ speech. TTS (F) ≠ vision.

---

## Q15. Chat app hallucinating policy details — which TWO factors cause this?

**Answer:** B, E
- B. Missing or poor-quality grounding data
- E. Prompt instructions that don't require source-based answers

**Why:** Hallucinations come from: (1) no good data to ground on, (2) prompts that don't enforce "only answer from sources." Lower temperature (A) actually helps. Latency (C) and deployment type (D) don't cause hallucinations.

---

## Q16. Larger model = richer but slower/costlier. What's the trade-off?

**Answer:** C. Larger models improve quality but can increase latency and cost

**Why:** Quality, latency, and cost often pull in different directions. Benchmark multiple models for your scenario.

---

## Q17. Match AI workloads (generative AI, agentic AI, information extraction)

**Answer:** A, C, E
- A. Generate product description — generative AI
- C. System searches KB and calls tools — agentic AI
- E. Read invoice numbers from scanned forms — information extraction

**Why:** Sentiment detection (B) = text analysis, not speech synthesis. Audio to text (D) = speech, not computer vision. Object detection (F) = computer vision, not text analysis.

---

## Q18. Detect product names, company names, city names in reviews?

**Answer:** B. Entity recognition (NER)

**Why:** NER = identifying people, organizations, locations, products in text. Keyword extraction = important terms (not categorized). Sentiment = positive/negative. Summarization = shorter version.

---

## Q19. Language ID in audio? Diarization identifies speakers? Batch for live captions?

**Answer:** A. Yes / Yes / No

**Why:** Language identification works in audio. Diarization separates speakers. Batch = pre-recorded files, NOT live captions (use real-time transcription for live).

---

## :red_circle: Q20. Computer vision / image-generation capabilities?

**Answer:** B (OCR) and D (Text-to-image generation)

**Why:** OCR = computer vision (reads text from images). Text-to-image = image generation. Entity recognition (A) = NLP. Speech translation (C) = speech. Keyword extraction (E) = NLP. Don't confuse modalities!

---

## Q21. Downstream actions after Content Understanding extraction?

**Answer:** A, C
- A. Send extracted totals/dates into approval workflow
- C. Index extracted markdown/fields in Azure AI Search

**Why:** Content Understanding output feeds into automation workflows and search indexes. Temperature (B) = generation control. Confidence ≠ embeddings (D). Don't discard structure (E).

---

## Q22. Agent capabilities: task planning, tool use, task completion?

**Answer:** B. Yes / Yes / Yes — all three are correct

**Why:** Agents plan steps, use tools, and complete tasks with final results. All three are core agent patterns.

---

## Q23. Upload photo + ask to describe damage + read label = ?

**Answer:** A. Multimodal prompting

**Why:** Image + text prompt together = multimodal. Not keyword extraction (text-only), speech synthesis (audio output), or text classification (labeling).

---

## Q24. Gloved technician outdoors, hands-free interaction?

**Answer:** D. Speech-based interaction

**Why:** Can't type with gloves → speech input/output is ideal for hands-free. OCR reads text from images. Keyboard/text requires hands.

---

## Q25. Similar applicants, different approval rates across demographics?

**Answer:** A. Fairness

**Why:** Unequal outcomes for similar groups = **Fairness**. Transparency = explaining how it works. Accountability = who's responsible. Inclusiveness = broad accessibility.

---

## :red_circle: Q26. System message, few-shot, clear syntax — matched pairs?

**Answer:** A, C, E
- A. System message — sets initial instructions and rules
- C. Few-shot examples — provide example interactions to prime behavior
- E. Clear syntax and separators — make sections easier to parse

**Why:** User message (B) is NOT persistent behavior storage. User prompt (D) doesn't replace system message. Assistant message (F) is NOT required before first user request.

---

## Q27. Best image generation prompt for product shot?

**Answer:** D. "Photorealistic studio product shot of blue running shoes on clean white background, soft shadow, e-commerce style"

**Why:** Effective prompts are specific + descriptive: subject + style + scene + composition. Vague prompts produce inconsistent results.

---

## :red_circle: Q28. Get OpenAI client from AIProjectClient — which method?

**Answer:** B. `openai = project.get_openai_client()`

**Why:** Exact method name matters! Not `openai_client()` (A), not `AIProjectClient.get_openai_client()` on class instead of instance (C), not `responses_client()` (D).

---

## :red_circle: Q29. Reliability & safety — which TWO actions?

**Answer:** B, D
- B. Test with adversarial and edge-case inputs
- D. Add fallback behavior or human escalation for risky responses

**Why:** Transparency note (A) = transparency principle. Encryption (C) = privacy & security. Accessibility (E) = inclusiveness. Testing + fallback = **reliability & safety**.

---

## Q30. Multi-turn agent conversation — what creates the conversation?

**Answer:** D. `conversation = openai.conversations.create()`

**Why:** Create conversation first, then pass `conversation.id` to `responses.create()`. Not `responses.create()` (A), not `create_version()` (B), not `threads.create()` (C).

---

## Q31. Portal testing vs SDK — which TWO are accurate?

**Answer:** A, C
- A. Playground lets you prototype without code
- C. SDK builds programmatic chat/agent clients in code

**Why:** SDK doesn't require portal for every request (B). Portal isn't required for conversation state (D). SDK doesn't remove need for deployed model (E).

---

## Q32. Temperature and top_p tuning — which TWO are accurate?

**Answer:** A, D
- A. Lower temperature = more focused and deterministic
- D. max_completion_tokens caps generated output

**Why:** Microsoft recommends altering temperature OR top_p, **not both** (C is wrong). top_p is nucleus sampling, not conversation ID (B). stream controls partial output, doesn't convert to agent request (E).

---

## Q33. Preserve system message in conversation history?

**Answer:** B. `conversation.append(system_message)`

**Why:** Append system message first, then add user turns. Don't `clear()` (A), don't add assistant with user content (C), don't replace list with string (D).

---

## Q34. Restrict access to prompts/outputs, protect data = which principle?

**Answer:** C. Privacy and security

**Why:** Data protection + access control = Privacy & Security. Not reliability (system behavior), not transparency (explaining AI), not inclusiveness (broad access).

---

## Q35. When to use agent vs direct model call?

**Answer:** B, D
- B. Search web and cite results (needs tool)
- D. Look up order via API then decide next action (needs tool + reasoning)

**Why:** Simple tasks (rewrite, summarize, classify) = direct model call. Multi-step + tools needed = agent.

---

## Q36. Agent must always act as travel-policy assistant, refuse unrelated = configure what?

**Answer:** C. Instructions

**Why:** Instructions define agent role, behavior, constraints. Not WebSearchTool (A = action tool), not previous_response_id (B = multi-turn), not temperature (D = randomness).

---

## Q37. Define agent instructions, attach tools, test multi-turn WITHOUT code?

**Answer:** A. Agents playground

**Why:** Agents playground = no-code agent testing. Model catalog = browse models. Management center = admin. Content safety dashboard = governance.

---

## Q38. System prompt, user prompt, grounding data — matched pairs?

**Answer:** A, C, F
- A. System prompt — sets behavior and rules
- C. Grounding data — external data to anchor responses
- F. User prompt — contains end user's request

**Why:** User prompt (B) doesn't store persistent behavior. User prompt (D) doesn't replace system message. Grounding data (E) is NOT sampling control.

---

## Q39. Agent tools: web search, code interpreter, file search matched?

**Answer:** A, D, F
- A. Web search — real-time web info with citations
- D. Code Interpreter — Python for math, analysis, charts
- F. File Search — ground agent in uploaded documents

**Why:** File Search (B) ≠ Python execution. OpenAPI (C) = HTTP APIs, not document search. Function calling (E) ≠ MCP servers (MCP is separate).

---

## Q40. Multi-turn with Responses API — continue prior response?

**Answer:** D. `previous_response_id=response.id`

**Why:** This links the follow-up to the prior turn. Not tool_choice (A), not store (B), not instructions=response.id (C).

---

## Q41. Test voice input/spoken responses with gpt-realtime in portal?

**Answer:** A. Audio playground

**Why:** Audio playground supports gpt-realtime models. Chat playground does NOT support gpt-realtime. Not Agents or Vision playground.

---

## Q42. Speech recognition from microphone — which method?

**Answer:** C. `recognize_once_async`

**Why:** `SpeechRecognizer.recognize_once_async().get()` = single utterance STT. Not `speak_text_async` (A = TTS, wrong class). Not `analyze_sentiment` (B = Language SDK). Not `create_version` (D = agent versioning).

---

## Q43. Text analysis techniques matched

**Answer:** A, C, E
- A. Sentiment analysis — detects opinion/polarity
- C. Key phrase extraction — identifies main talking points
- E. Summarization — shorter version of document

**Why:** Entity recognition (B) ≠ audio generation. Summarization (D) ≠ bounding boxes. Key phrase extraction (F) ≠ speaker diarization.

---

## :red_circle: Q44. Convert document chunks into vectors for semantic search?

**Answer:** C. Embedding model

**Why:** Embedding models convert text to vector representations for similarity search. Chat model (A) = conversation. Image generation (B) = visuals. Speech model (D) = audio.

---

## Q45. STT from file then TTS response — complete the code?

**Answer:** B. `synthesizer.speak_text_async("Your order ships today.").get()`

**Why:** Use `synthesizer` (SpeechSynthesizer) for TTS, not `recognizer` (A). Result object (C) can't synthesize. AudioConfig (D) is configuration, not synthesis.

---

## :red_circle: Q46. Voice-enabled app flow — which TWO steps?

**Answer:** A, C
- A. Convert spoken input to text before prompt submission (STT)
- C. Convert final text response to speech (TTS)

**Why:** OCR on microphone stream (B) = wrong modality. Object detection on audio (D) = wrong modality. Sentiment (E) = optional, not core flow.

---

## Q47. Send image URL in multimodal chat — content format?

**Answer:** D. `{"type": "image_url", "image_url": {"url": image_url}}`

**Why:** Vision-enabled chat uses `type: "image_url"` with nested `image_url.url`. Not audio (A), not ocr (B), not caption (C).

---

## :red_circle: Q48. Generate product mockup image from text = which deployment?

**Answer:** C. gpt-image-1

**Why:** `gpt-image-1` = image generation model. gpt-4o-mini (A) = chat/reasoning. Azure AI Vision (B) = image analysis. Azure Language (D) = text analysis.

---

## Q49. Extract structured info from documents, images, audio, AND video?

**Answer:** C. Azure Content Understanding

**Why:** Content Understanding = multimodal extraction across ALL content types. OCR (A) = only images/docs. Sentiment (B) = only text. TTS (D) = audio output.

---

## Q50. Image caption with Vision SDK — which VisualFeature?

**Answer:** A. `VisualFeatures.CAPTION`

**Why:** CAPTION = human-readable image description. READ (B) = OCR text. OBJECTS (C) = object detection. PEOPLE (D) = person detection.

---

## Q51. Image description, visual Q&A, visual extraction — matched?

**Answer:** A, B, D
- A. Image description — generate caption
- B. Visual Q&A — "What is the person holding?"
- D. Visual extraction — read text/fields from image

**Why:** Visual extraction (C) ≠ creating new poster (that's generation). Image description (E) ≠ speaker turns (audio). Visual Q&A (F) ≠ email sentiment (text analysis).

---

## :red_circle: Q52. Send local base64 image via Responses API?

**Answer:** C. `{"type": "input_image", "image_url": f"data:image/jpeg;base64,{base64_image}"}`

**Why:** Responses API uses `type: "input_image"` with `image_url` containing data URI. Chat completions uses `type: "image_url"` (D = wrong API). Field names matter!

---

## :red_circle: Q53. Respond quickly + avoid harmful outputs = which TWO evaluation criteria?

**Answer:** B (Latency) and E (Safety)

**Why:** "Respond quickly" = latency. "Avoid harmful outputs" = safety. Accuracy (A) is important but not specifically emphasized here. Keyword extraction (C) and translation (D) are workloads, not evaluation criteria.

---

## :red_circle: Q54. Chat, classification, extraction — matched tasks?

**Answer:** A, C, D
- A. Chat — interactive Q&A
- C. Classification — assigning ticket to category
- D. Extraction — pulling fields from form

**Why:** Summarization (B) ≠ extracting invoice number (that's extraction). Translation (E) = cross-language, not same-language tone change (that's rewriting). Rewriting (F) = same language style change, not English→Japanese (that's translation).

---

## Q55. Process invoices/tax forms, return structured fields?

**Answer:** B. Azure Content Understanding

**Why:** Content Understanding = structured extraction from documents/forms with schema. Vision (A) = image analysis. Search (C) = indexing/retrieval. Multimodal model (D) = general prompting, less reliable for structured output.

---

## Q56. Temperature, top_p, context window, max tokens — matched?

**Answer:** B, D, E
- B. top_p — nucleus sampling over highest-probability tokens
- D. Max tokens — caps generated response length
- E. Context window — limits input/conversation history the model can consider

**Why:** Temperature (A) controls randomness, NOT conversation size. Context window (C) is NOT content safety threshold. Temperature (F) is NOT grounding source selector.

---

## Q57. Analyze shelf photos for product count, brand presence, out-of-stock?

**Answer:** A. Azure Content Understanding image analyzer

**Why:** Content Understanding lets you define schemas and extract structured data from images. Microsoft lists shelf analysis as a direct use case. Multimodal prompt (B) = free-form, not structured. OCR (D) = text only.

---

## :red_circle: Q58. Mixed procurement mailbox (invoices + POs + other) — which prebuilt analyzer?

**Answer:** C. prebuilt-procurement

**Why:** prebuilt-procurement = broader analyzer for mixed procurement docs. prebuilt-invoice (A) = invoices only. prebuilt-purchaseOrder (B) = POs only. prebuilt-documentSearch (D) = RAG/search, not business field extraction.

---

## Q59. Try prebuilt analyzer on sample data before coding?

**Answer:** B. Content Understanding Studio

**Why:** Studio = browse analyzers, test on sample data, review extracted results. Not Search (A = downstream), not function calling (C = orchestration), not embedding deployment (D = vectorization).

---

## :red_circle: Q60. Confidence, source, object field, array field, spans — matched?

**Answer:** A, C, E
- A. confidence — estimated reliability of predicted field value
- C. Object field — nested structure (e.g., TotalAmount with Amount + CurrencyCode)
- E. spans — positions in markdown content

**Why:** source (B) ≠ temperature (it's field position traceability). Array field (D) ≠ single scalar value (arrays are for repeated structures like line items). Markdown (F) is NOT only for currency fields.

---

## :red_circle: Q61. New sensors report 18% higher — which monitoring signal?

**Answer:** D. Data drift

**Why:** Data drift = input distribution changed from training data. Model still returns high confidence but inputs are shifted. Feature attribution (A) = explains which features influenced result. Cohort fairness (B) = comparing across groups. Endpoint latency (C) = response speed.

---

## Q62. Agent calls existing Azure Function via queue — which tool?

**Answer:** B. Azure Functions tool

**Why:** Azure Functions tool uses queue-based integration: agent → input queue → function processes → output queue → agent continues. Code Interpreter (A) = sandbox Python. OpenAPI (C) = needs REST API wrapper. File Search (D) = document retrieval.

---

## :red_circle: Q63. Single Dutch DOCX → English, preserve formatting, no storage containers?

**Answer:** A. Synchronous document translation

**Why:** Synchronous = one document in, translated document returned directly. Async (B) = requires blob storage containers. Text translation (C) = plain text only, loses formatting. Custom Translator training (D) = training a model, not translating.

---

## :red_circle: Q64. Generate thumbnail preserving most important region without manual crop?

**Answer:** C. `smartCropping=true`

**Why:** smartCropping=true = content-aware cropping around area of interest. false (A) = no smart cropping. detectOrientation (B) = rotation, not cropping. visualFeatures=objects (D) = detection, not thumbnail cropping.

---

## :red_circle: Q65. Varied photo layouts, extract specific JSON fields from images?

**Answer:** D. Custom image analyzer

**Why:** Custom analyzer = define your own field schema (greenhouseId, pH, etc.) on top of base image analyzer. Azure Vision Read (A) = raw OCR, no field mapping. Multimodal prompt (B) = inconsistent structured output. Prebuilt image analyzer (C) = doesn't have your custom fields.

---

## KEY TAKEAWAYS FROM YOUR WRONG ANSWERS

### Responsible AI Confusion Points
| Principle | Think of it as... |
|-----------|------------------|
| **Transparency** | "Users know it's AI and understand how it works" |
| **Accountability** | "Named humans are responsible for AI decisions" |
| **Fairness** | "Equal outcomes across demographic groups" |
| **Privacy & Security** | "Data protection and access control" |
| **Inclusiveness** | "Accessible to all abilities and backgrounds" |
| **Reliability & Safety** | "Works safely under all conditions" |

### Service Selection Confusion Points
| When you need... | Use this |
|------------------|----------|
| Structured extraction from any content type | Azure Content Understanding |
| Free-form image description | Multimodal model |
| Text from images (OCR only) | Azure Vision Read |
| Custom fields from varied image layouts | Custom image analyzer |
| Mixed procurement docs | prebuilt-procurement (NOT prebuilt-invoice) |
| Generate new images | gpt-image-1 (NOT gpt-4o) |
| Vectors for semantic search | Embedding model |
| Single doc translation with formatting | Synchronous document translation |

### Code Pattern Confusion Points
| Pattern | Correct Way |
|---------|-------------|
| Get OpenAI client from project | `project.get_openai_client()` |
| Continue multi-turn (Responses API) | `previous_response_id=response.id` |
| Create conversation for agent | `openai.conversations.create()` |
| STT single utterance | `recognizer.recognize_once_async().get()` |
| TTS output | `synthesizer.speak_text_async(text).get()` |
| Content Understanding result | `await poller.result()` |
| Local image in Responses API | `type: "input_image"` with data URI |
| Local image in Chat Completions | `type: "image_url"` with nested url |
