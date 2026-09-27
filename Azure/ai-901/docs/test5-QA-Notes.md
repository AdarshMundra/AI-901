# Test 5 - QA Notes

**Score: 38/55 (69%)**
**Incorrect: Q1, Q4, Q18, Q20, Q24, Q25, Q26, Q29, Q31, Q35, Q36, Q37, Q50, Q51, Q53, Q54, Q55**

---

## :red_circle: Q1. A team is preparing an AI document-review tool for business users. Which TWO actions best support transparency?

**Answer:** B. Explain known limitations to users & D. Share how outputs should be interpreted

**Why:** Transparency = helping people understand an AI system well enough to use it appropriately. Explaining limitations and sharing interpretation guidance directly support user understanding. Rotating storage keys (A) = privacy/security. Increasing batch size (C) = performance. Moving regions (E) = operational.

---

## Q2. Statement combo: system message = highest-level instructions / user prompt = permanent boundaries / few-shot = example user+assistant interactions

**Answer:** B. Yes / No / Yes

**Why:** System message IS the highest-level instruction layer. User prompt is the current task input, NOT permanent boundaries (those go in system message). Few-shot CAN be expressed through example user/assistant interactions.

---

## Q3. Statement combo: Generative AI creates text/images / Agentic AI limited to one response / Computer vision for spoken audio

**Answer:** A. Yes / No / No

**Why:** Generative AI DOES create new content from prompts. Agentic AI is NOT limited -- agents call tools, access data, take autonomous multistep actions. Computer vision analyzes IMAGES, not spoken audio (that's speech).

---

## :red_circle: Q4. Few-shot pattern -- what replaces the missing section after a system+user+assistant example?

**Answer:** A. `{"role": "user", "content": "The app kept crashing and nobody replied for two days."}`

**Why:** Few-shot = example user/assistant pairs. After system -> user -> assistant, the next element should be a NEW user message (the real input to classify). Option B (another assistant) breaks the alternation. Option C (system with "Negative") misuses roles. Option D (assistant repeating instruction) doesn't provide new input.

---

## Q5. Users must know they are interacting with AI and understand where the system may be unreliable. Which principle?

**Answer:** D. Transparency

**Why:** Transparency = helping users understand the nature and limits of the system. Disclosing AI use and failure points = transparency. Reliability/safety = performance quality. Accountability = human oversight. Inclusiveness = designing for varied backgrounds.

---

## Q6. Text prompt to produce a brand-new promotional image. Which workload?

**Answer:** C. "Image generation"

**Why:** Input = text prompt, output = new image. That's generative AI image generation. Not OCR (reads text from images), not Speech to Text (audio to text), not entity recognition (identifies entities in text).

---

## Q7. A transparency document should explain how the system works and its ________.

**Answer:** B. capabilities and limitations

**Why:** Microsoft's transparency guidance emphasizes understanding capabilities and limitations. Office location, sales targets, rack position are irrelevant to user understanding of AI behavior.

---

## Q8. Which scenario is the best example of transparency in an AI solution?

**Answer:** A. An invoice app tells users that low-quality scans can reduce extraction accuracy

**Why:** Communicating a specific limitation so people can interpret outputs correctly = transparency. Increasing GPU (B) = infrastructure. Deploying chatbot without disclosure (C) = anti-transparency. Disabling feedback (D) = not transparency.

---

## Q9. Statement combo: Hide model limitations / Communicate capabilities clearly / Transparency notes consider affected people

**Answer:** C. No / Yes / Yes

**Why:** Teams should NOT hide limitations (opposite of transparency). Communicating capabilities/limitations IS central to transparency. Transparency notes DO consider people who use or are affected by the system.

---

## Q10. What should a team prepare to most directly improve transparency?

**Answer:** D. Transparency note

**Why:** Transparency notes explain how AI technology works, choices that affect behavior, and why system context matters. Compute budget (A), network diagram (B), failover runbook (C) are operational artifacts, not transparency artifacts.

---

## Q11. Read printed text from a storefront photo using Azure Vision Image Analysis. Which feature?

**Answer:** A. Read (OCR)

**Why:** Read = extract printed or handwritten text from images. People = detect people. SmartCrops = thumbnail crop regions. Tags = descriptive keywords for whole image.

---

## Q12. Marketing team enters prompt to create brand-new poster images. Which workload?

**Answer:** B. Generative AI

**Why:** Creating new content from a prompt = generative AI. Computer vision = analyze existing images. Text analysis = understand text. Information extraction = pull structured data from content.

---

## Q13. Internal assistant checks policies, looks up order status, decides to refund or escalate. Which workload?

**Answer:** D. Agentic AI

**Why:** Tool use + multistep decision-making + autonomous actions = agentic AI. Goes beyond simple text generation. Text analysis (A) = understand text only. Computer vision (B) = images. Generative AI (C) = content generation without tool use/actions.

---

## Q14. App reads customer reviews and labels each as positive/neutral/negative. Example of?

**Answer:** A. Sentiment analysis

**Why:** Determining emotional tone/opinion in text = sentiment analysis. Core NLP capability in Azure Language. Not OCR (images), speech synthesis (audio), or image generation.

---

## Q15. Warehouse app analyzes photos to detect forklifts, pallets, damaged boxes. Which workload?

**Answer:** B. Computer vision

**Why:** Analyzing image content to identify visual features and objects = computer vision. Input = camera photos, task = detect visual elements.

---

## Q16. Validate prompts and model behavior for a vision workflow before writing production code. Which environment?

**Answer:** A. Model playground

**Why:** Foundry playgrounds = on-demand rapid prototyping, API exploration, technical validation before production code. For prompt engineering, model comparison, parameter tuning.

---

## Q17. Process scanned invoices and return invoice number, vendor name, due date as structured data. Which option?

**Answer:** D. Azure Document Intelligence

**Why:** Intelligent document processing = extracts text, tables, structure, key/value pairs. Has prebuilt invoice model. Not just OCR (reading text) but structured field extraction from documents.

---

## :red_circle: Q18. Which THREE pairs are correctly matched?

**Answer:** A. Generative AI -- creates original marketing copy, C. Computer vision -- detects objects in warehouse photos, E. Agentic AI -- uses tools and multistep actions

**Why:** B is wrong: Speech synthesis = text-TO-speech (not microphone audio to text, that's Speech to Text). D is wrong: Information extraction pulls structured data, doesn't generate images. F is wrong: Text analysis interprets written language, doesn't convert text to audio.

---

## Q19. Foundry chat app must always return customer details in fixed JSON. Best system prompt instruction?

**Answer:** C. Return only JSON with fixed keys

**Why:** System prompt = durable rules (role, boundaries, output format). Microsoft guidance says system message can specify output formats like JSON. Option A = one-off task. Option B = tone only. Option D = task-level instruction.

---

## :red_circle: Q20. Chat request for support assistant that asks clarifying questions. What replaces the missing section?

**Answer:** D. `{"role": "user", "content": "My printer keeps failing after the update."}`

**Why:** After system message, you need a USER message with the actual request. The system prompt already defines fallback behavior. Option A (assistant message before model responds) = wrong pattern. Option B (second system message) = not the task input. Option C (assistant repeating role) = wastes space.

---

## Q21. Which TWO practices help make a system prompt more effective?

**Answer:** A. Keep instructions unambiguous & C. Make fallback behavior explicit

**Why:** Microsoft recommends unambiguous instructions and explicit fallback behavior. Hiding output format (B) = bad. Conflicting rules (D) = pitfall. Open boundaries (E) = less predictable.

---

## Q22. Which user prompt is most effective for classifying feedback into one label?

**Answer:** D. "Classify this feedback as Positive, Neutral, or Negative. Return one label only."

**Why:** Specific task + constrained answer space + stated output format = effective prompt. Vague prompts (A, B, C) leave too much to interpretation.

---

## Q23. Which THREE pairs are correctly matched? (prompt design)

**Answer:** A. System message -- defines role and boundaries, C. User prompt -- carries the current request, E. Fallback instruction -- tells the model what to do when unsure

**Why:** B wrong: Few-shot examples DON'T permanently retrain (only condition current inference). D wrong: Conflicting rules = pitfall, not reliability improvement. F wrong: Assistant messages don't replace user input.

---

## :red_circle: Q24. Revision of "Write about our Q1 results" -- which is most effective?

**Answer:** C. "Summarize the Q1 results for executives in 3 bullet points. Limit the response to 80 words. If revenue is missing, say 'data not provided.'"

**Why:** Specific audience + format + length constraint + fallback behavior = best prompt design. Combines multiple strong elements: concrete task, executive audience, bullet format, word limit, missing-data policy.

---

## :red_circle: Q25. Lightweight Python app reads customer reviews, returns positive/negative. Which service?

**Answer:** A. Azure Language in Foundry Tools

**Why:** Azure Language = cloud-based NLP service for text understanding/analysis. Sentiment analysis is a core capability. Not Speech (B, audio), Vision (C, images), or Search (D, retrieval/indexing).

---

## :red_circle: Q26. Creating a TextAnalyticsClient -- which code is correct?

**Answer:** B. `text_analytics_client = TextAnalyticsClient(endpoint, AzureKeyCredential(key))`

**Why:** Constructor order = endpoint FIRST, then AzureKeyCredential(key). A swaps key/endpoint. C reverses parameter order. D uses AzureKeyCredential as the client itself (wrong class).

---

## Q27. Transparency means AI systems should be ________.

**Answer:** A. understandable

**Why:** Microsoft's core transparency definition = AI systems should be understandable. Not autonomous (B), hidden (C, opposite), or randomized (D).

---

## Q28. App must identify main talking points in support tickets. Best capability?

**Answer:** D. Key phrase extraction

**Why:** Key phrase extraction = identify main concepts/talking points in text. Python method: `extract_key_phrases`. Not OCR (A, images), Speech to Text (B, audio), or entity linking (C, disambiguate entities).

---

## :red_circle: Q29. App must find and redact email addresses and phone numbers. Which capability?

**Answer:** B. PII detection

**Why:** PII detection = identify and redact sensitive personal information (emails, phone numbers, IDs). NER (A) is broader entity extraction, not privacy-focused. Summarization (C) = shorten text. Speech translation (D) = audio.

---

## Q30. Statement combo: Transparency = capabilities/limitations / Transparency = encrypting data / Transparency notes shared with affected people

**Answer:** B. Yes / No / Yes

**Why:** Understanding capabilities/limitations IS transparency. Encrypting data = privacy/security, NOT transparency. Transparency notes CAN be shared with users and affected people.

---

## :red_circle: Q31. Which THREE pairs are correctly matched? (Responsible AI)

**Answer:** A. Transparency -- AI systems should be understandable, C. Transparency Note -- explains how AI technology works, E. Transparency -- helps users understand capabilities

**Why:** B wrong: Explaining limitations = transparency, not privacy/security. D wrong: Accountability = human oversight, NOT removing oversight. F wrong: Fairness = treating people fairly, concealing weaknesses is anti-transparency.

---

## Q32. Live microphone audio converted to text. Which workload?

**Answer:** C. "Speech to Text"

**Why:** Spoken audio input -> written text output = Speech to Text. Not Text to Speech (A, opposite direction), Computer vision (B, images), or OCR (D, text in images).

---

## Q33. Statement combo: Azure Language usable from Foundry + client libraries / detect_language returns confidence score / PII detection converts text to audio

**Answer:** A. Yes / Yes / No

**Why:** Azure Language IS available through Foundry and client libraries. detect_language DOES return language + confidence score. PII detection identifies sensitive text, does NOT convert to audio (that's speech synthesis).

---

## Q34. Which THREE pairs are correctly matched? (Azure Language)

**Answer:** B. detect_language -- returns a language code, D. recognize_entities -- identifies people and organizations, F. PII detection -- identifies sensitive text such as email addresses

**Why:** A wrong: Azure AI Speech ≠ written language detection (that's Azure Language). C wrong: Azure AI Search ≠ primary sentiment API. E wrong: OCR ≠ sentiment assignment.

---

## :red_circle: Q35. Extract entities (organizations, locations) from text. Which method?

**Answer:** D. `result = text_analytics_client.recognize_entities(messages)`

**Why:** recognize_entities = identifies people, places, organizations, dates, quantities. The loop expects `doc.entities` which matches entity recognition output. detect_language (A) = language code. extract_key_phrases (B) = topics. analyze_sentiment (C) = tone labels.

---

## :red_circle: Q36. SDK for captioning product photos and reading text from shelf labels (Vision workloads)?

**Answer:** C. Foundry Tools SDKs

**Why:** Microsoft says use Foundry Tools SDKs for specific AI services (Vision, Speech, Language). Agent Framework (A) = multi-agent orchestration. OpenAI SDK (B) = model compatibility/chat completions. Foundry SDK (D) = Foundry-specific features like agents/evaluations.

---

## :red_circle: Q37. Sending image + prompt to multimodal model. What replaces the missing section?

**Answer:** A. `ImageContentItem(image_url=ImageUrl(image_url))`

**Why:** Image input = ImageContentItem with image_url parameter wrapping ImageUrl object. B (text=image_url) = wrong property. C (audio_url) = wrong modality. D (TextContentItem with ImageUrl) = wrong content type.

---

## Q38. To add Azure Vision Image Analysis to Python, install ________.

**Answer:** C. azure-ai-vision-imageanalysis

**Why:** Microsoft's exact package name for Python Image Analysis SDK. Not azure-ai-inference (A), openai (B), or azure-identity (D, authentication only).

---

## Q39. Which TWO input approaches supported for vision-enabled model?

**Answer:** A. Provide a publicly accessible image URL & D. Send a base64 data URL

**Why:** Microsoft documents two approaches: public URL and base64 data URL. Excel worksheet (B) = not image input. Local file path (C) = not supported directly in message body. Deployment name (E) = identifies model, not image data.

---

## Q40. What must be true about the image URL for analyze_from_url?

**Answer:** C. It must be publicly accessible

**Why:** Microsoft's reference: image_url = "publicly accessible URL of the image to analyze." Not stored in Search (A), not .png only (B), not same as endpoint (D).

---

## Q41. Assistant's role, boundaries, response style belong in the ________ prompt.

**Answer:** B. system

**Why:** System message = high-priority instructions (role, scope, tone, formatting). User prompt = current request. Assistant messages = model replies. Deployment = hosting concept.

---

## Q42. Deploying AI assistant for employees. Which action best supports transparency?

**Answer:** C. Publish capabilities and limitations

**Why:** Transparency = helping people understand the system. Publishing capabilities/limitations directly addresses this. Adding training data (A) = performance. Private endpoint (B) = security. Increase token limit (D) = parameter change.

---

## Q43. Which TWO instructions are good additions to a domain-specific system prompt?

**Answer:** B. If the request is out of scope, say so & D. Use only the approved product glossary

**Why:** Defining boundary behavior + constraining to approved sources = good prompt design. "Answer even without facts" (A) = encourages hallucination. "Brief and comprehensive" (C) = conflicting. "Change rules based on mood" (E) = unstable.

---

## Q44. Which TWO items required to create TextAnalyticsClient?

**Answer:** A. Endpoint & C. API key credential

**Why:** TextAnalyticsClient(endpoint, AzureKeyCredential(key)). Not index name (B, search concept), voice name (D, speech concept), or image size (E, vision concept).

---

## Q45. Which TWO scenarios are text analysis workloads?

**Answer:** A. Identify key phrases in support tickets & C. Detect sentiment in product reviews

**Why:** Both are classic Azure Language NLP capabilities. Transcribing audio (B) = speech. Generating images (D) = generative AI. Extracting invoice totals (E) = document intelligence/information extraction.

---

## Q46. Method to caption image and read text from URL using ImageAnalysisClient?

**Answer:** B. analyze_from_url

**Why:** Microsoft documents `analyze_from_url(image_url, visual_features)` as the method for URL-based image analysis. Supports multiple visual features in one call (CAPTION + READ). get_image (A), captions_from_url (C), detect_visuals (D) are not real methods.

---

## Q47. Package for Azure Language methods (analyze_sentiment, recognize_entities)?

**Answer:** C. azure-ai-textanalytics

**Why:** Direct package for TextAnalyticsClient and all text-analysis methods. Not azure-search-documents (A, search), azure-ai-vision (B, images), or azure-cognitiveservices-speech (D, audio).

---

## Q48. Statement combo: "detail" inside image_url object / "auto" is default / "high" is default

**Answer:** B. Yes / Yes / No

**Why:** Detail property IS inside the image_url object. "auto" IS the default detail setting. "high" is NOT default -- it's optional for more detailed interpretation.

---

## Q49. Return main topics from a short ticket. Which method?

**Answer:** C. `result = text_analytics_client.extract_key_phrases(tickets)`

**Why:** Code expects `doc.key_phrases` output = extract_key_phrases method. analyze_sentiment (A) = labels/scores. recognize_entities (B) = entity categories. detect_language (D) = language code.

---

## :red_circle: Q50. Which THREE pairs are correctly matched? (Vision features)

**Answer:** A. Caption -- generates short description, C. Objects -- returns detected physical objects and location, F. Read (OCR) -- extracts printed or handwritten text

**Why:** B wrong: People detects people, NOT text extraction. D wrong: SmartCrops = image crop regions, NOT audio sentiment. E wrong: Tags = descriptive keywords, NOT caption translation.

---

## :red_circle: Q51. Solstice case study -- telemetry has unnecessary customer data. Which responsible AI practice?

**Answer:** D. Data minimisation

**Why:** Data minimisation = collect/process/retain ONLY information necessary for the defined purpose. Operations team needs performance data, NOT customer names/addresses/account numbers. Cohort fairness (A) = compare model performance across groups. Confidence threshold (B) = decision automation. Transparency note (C) = documentation, doesn't prevent data collection.

---

## Q52. Solstice case study -- MCP tool with OAuth, employee permissions must persist. Which auth method?

**Answer:** A. OAuth identity passthrough

**Why:** Preserves individual user identity and permissions. Each employee's credentials used in agent-MCP communication. Project managed identity (B) = shared identity. Agent identity (C) = single workload identity. API key (D) = shared credential.

---

## :red_circle: Q53. Solstice case study -- identify positive sentiment about restoration + negative about app notifications. Which capability?

**Answer:** C. Opinion mining

**Why:** Opinion mining = aspect-based sentiment linking assessments to SPECIFIC targets. Returns targets + assessments + sentiment labels. Key phrase extraction (A) = identifies phrases but no sentiment. Document sentiment (B) = whole-document/sentence level only (too broad). Custom NER (D) = extracts entities, not sentiment.

---

## :red_circle: Q54. Solstice case study -- drone photo needs bounding boxes for people + OCR for substation text. Which config?

**Answer:** B. features=people,read

**Why:** People feature = detects people with bounding boxes + confidence scores. Read feature = OCR for structured text. Objects (A) = general object categories, NOT dedicated people detection. Tags (C) = image keywords, no text extraction. Caption (D) = image description sentence, no bounding boxes per person.

---

## :red_circle: Q55. Solstice case study -- reusable config for transcript + speaker ID + summary + sentiment + 4 custom fields. Which component?

**Answer:** D. Audio-based custom analyzer

**Why:** Custom Content Understanding analyzer inherits foundational audio processing (transcript, timing) AND adds user-defined field schema for domain-specific fields. prebuilt-audioSearch (A) = no custom fields. prebuilt-callCenter (B) = fixed output, no custom schema. Document-based analyzer (C) = wrong content type for audio.

---

# Key Takeaway Tables

## Responsible AI Principles - Transparency Focus
| Concept | Key Point |
|---|---|
| Transparency | AI systems should be **understandable** |
| Transparency Note | Explains how AI works, capabilities, limitations, intended use |
| Transparency Actions | Explain limitations, share interpretation guidance, publish capabilities |
| NOT Transparency | Encrypting data (privacy/security), rotating keys (security), adding compute |
| Data Minimisation | Collect/retain ONLY necessary data for the purpose |

## Prompt Engineering - Role Hierarchy
| Component | Purpose | Example |
|---|---|---|
| System message | Role, boundaries, tone, output format, fallback behavior | "Return only JSON with fixed keys" |
| User message | Current task/request | "My printer keeps failing after the update" |
| Assistant message | Model-generated replies or few-shot examples | Prior response examples |
| Few-shot | Example user+assistant pairs (NOT retraining) | Input -> Output examples |
| Effective prompts | Specific task + constrained answer + stated format + fallback | "Classify as Positive/Neutral/Negative. One label only." |

## Prompt Design Pitfalls
| Good Practice | Pitfall |
|---|---|
| Keep instructions unambiguous | Conflicting rules |
| Make fallback behavior explicit | Leaving boundaries open |
| State output format explicitly | Hiding format requirements |
| Define scope and boundaries | "Answer everything even without facts" |
| Approved glossary/constraints | "Change rules based on mood" |

## TextAnalyticsClient Methods
| Method | Returns | Use Case |
|---|---|---|
| `analyze_sentiment()` | Sentiment labels + confidence | Review tone classification |
| `recognize_entities()` | Entities + categories (people, orgs, places) | Entity extraction |
| `extract_key_phrases()` | Key phrases / `doc.key_phrases` | Main topics/talking points |
| `detect_language()` | Language code + confidence | Language identification |
| `recognize_pii_entities()` | PII entities for redaction | Email/phone/ID redaction |

## TextAnalyticsClient Setup
```python
# Package: azure-ai-textanalytics
# Order: endpoint FIRST, then AzureKeyCredential(key)
client = TextAnalyticsClient(endpoint, AzureKeyCredential(key))
```

## Azure Vision Image Analysis
| Feature | Purpose |
|---|---|
| READ (OCR) | Extract printed/handwritten text |
| CAPTION | Short image description |
| OBJECTS | Detected physical objects + location |
| PEOPLE | Detect people + bounding boxes + confidence |
| SMART_CROPS | Crop regions for thumbnails |
| TAGS | Descriptive keywords for whole image |

```python
# Package: azure-ai-vision-imageanalysis
# Method: analyze_from_url (URL must be publicly accessible)
result = client.analyze_from_url(image_url=url, visual_features=[VisualFeatures.CAPTION, VisualFeatures.READ])
```

## Multimodal Image Input
| Approach | Supported? |
|---|---|
| Public image URL | Yes |
| Base64 data URL | Yes |
| Local file path in message body | No |
| Detail parameter location | Inside image_url object |
| Default detail setting | "auto" (not "high") |

```python
# Correct pattern:
ImageContentItem(image_url=ImageUrl(image_url))
# NOT: ImageContentItem(text=image_url)
```

## Workload Mapping
| Workload | Key Clue |
|---|---|
| Generative AI | Create NEW content (text, images) from prompts |
| Agentic AI | Tools + multistep decisions + autonomous actions |
| Computer Vision | Analyze photos/images for objects, features |
| Text Analysis | Sentiment, entities, key phrases in written text |
| Speech to Text | Microphone/audio -> written text |
| Image Generation | Text prompt -> new image |
| Information Extraction | Structured fields from documents (invoices, forms) |

## SDK Selection Guide
| SDK | When to Use |
|---|---|
| Foundry Tools SDKs | Specific AI services (Vision, Speech, Language) |
| OpenAI SDK | Max OpenAI compatibility, chat completions |
| Foundry SDK | Foundry-specific features (agents, evaluations) |
| Agent Framework | Multi-agent orchestration systems |

## Opinion Mining vs Document Sentiment
| Feature | Output | Use When |
|---|---|---|
| Document Sentiment | Positive/negative/mixed for whole doc/sentence | Overall tone needed |
| Opinion Mining | Target + assessment + sentiment per aspect | Need sentiment tied to SPECIFIC topics |

## Content Understanding Analyzers
| Analyzer | Use Case |
|---|---|
| prebuilt-audioSearch | Search audio content (transcript + summary) |
| prebuilt-callCenter | Generic call analytics (fixed schema) |
| Audio-based custom analyzer | Audio + custom field schema (domain-specific) |
| Document-based custom analyzer | Documents + custom field schema |

## Authentication Methods (Foundry MCP)
| Method | Identity | Use Case |
|---|---|---|
| OAuth identity passthrough | Individual user | User permissions must persist |
| Project managed identity | Shared project identity | Same access for all |
| Agent identity | Agent's own Entra identity | Workload identity with assigned permissions |
| API key connection | Shared credential | Simple, no user context |
