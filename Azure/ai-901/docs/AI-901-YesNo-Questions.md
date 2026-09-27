# AI-901 Yes/No Statement Combination Questions

All Yes/No statement combo questions extracted from Tests 1–7.  
Organized by topic. Duplicates between tests noted.  
🔴 = You answered incorrectly

---

## Responsible AI

### Reliability & Safety (Test 2 — Q2) 🔴
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Reliability and safety includes testing how an AI system behaves under unexpected conditions. | **Yes** |
| 2 | Reliability and safety is mainly about making system decisions easy for users to understand. | **No** |
| 3 | Monitoring false negatives in harmful-content detection can support reliability and safety. | **Yes** |

**Why:**
- S1: Microsoft defines reliability/safety to include testing under unexpected conditions.
- S2: Making decisions understandable is **transparency**, not reliability/safety.
- S3: Reducing false negatives (missed harmful content) directly supports safer operation.

---

### Privacy & Security (Test 3 — Q3) 🔴
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Using least-privilege access supports security in an AI solution. | **Yes** |
| 2 | Collecting more personal data than necessary improves privacy. | **No** |
| 3 | Storing prompts without clear governance can increase privacy risk. | **Yes** |

**Why:**
- S1: Least-privilege access is a core security best practice.
- S2: Collecting **more** data increases privacy exposure — data minimization is the principle.
- S3: Retained prompts can contain sensitive content; unclear governance = more risk.

---

### Inclusiveness (Test 4 — Q3)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Screen-reader-friendly output can support inclusiveness. | **Yes** |
| 2 | Requiring mouse input for every action improves inclusiveness. | **No** |
| 3 | Offering both voice and text interaction can support inclusiveness. | **Yes** |

**Why:**
- S1: Accessible output helps more people use the system.
- S2: Forcing one input method **excludes** users who can't use it.
- S3: Multiple interaction methods increase inclusiveness.

---

### Inclusiveness (Test 4 — Q10)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Requiring one interaction method for all users supports inclusiveness. | **No** |
| 2 | Providing captions for spoken output can support inclusiveness. | **Yes** |
| 3 | Testing with users who have different abilities can support inclusiveness. | **Yes** |

**Why:**
- S1: A single required method excludes users — inclusive design needs flexible choices.
- S2: Captions provide accessible alternatives to audio.
- S3: Diverse user testing helps identify accessibility barriers.

---

### Transparency (Test 5 — Q9)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Transparency means teams should hide model limitations to avoid confusing users. | **No** |
| 2 | Transparency includes communicating capabilities and limitations clearly. | **Yes** |
| 3 | Transparency notes consider the people who use or are affected by the system. | **Yes** |

**Why:**
- S1: Teams should **reveal** limitations, not hide them.
- S2: Clear communication of capabilities/limitations is central to transparency.
- S3: Transparency notes address both users and affected people.

---

### Transparency (Test 5 — Q30)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Transparency includes helping people understand an AI system's capabilities and limitations. | **Yes** |
| 2 | Transparency is mainly about encrypting stored data. | **No** |
| 3 | Transparency notes can be shared with people who use or are affected by the system. | **Yes** |

**Why:**
- S1: Understanding capabilities/limitations is core transparency.
- S2: Encryption is **privacy/security**, not transparency.
- S3: Transparency notes are designed to be shared with users and affected people.

---

### Fairness (Test 7 — Q11)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Fairness concerns can appear when training data underrepresents part of the population. | **Yes** |
| 2 | Fairness and inclusiveness are identical terms in Microsoft's responsible AI principles. | **No** |
| 3 | Comparing model behavior across demographic groups can help identify fairness issues. | **Yes** |

**Why:**
- S1: Underrepresentation = biased outcomes. Microsoft emphasizes representative data.
- S2: Fairness and inclusiveness are **separate** responsible AI principles, not synonyms.
- S3: Subgroup comparison is a standard fairness assessment method.

---

### Accountability (Test 7 — Q17) 🔴
| # | Statement | Answer |
|---|-----------|--------|
| 1 | In an accountable AI solution, the AI system should be the final authority for decisions that affect people's lives. | **No** |
| 2 | Logging who published a model and why it changed supports accountability. | **Yes** |
| 3 | Governance sign-off before deployment supports accountability. | **Yes** |

**Why:**
- S1: Microsoft says AI should **not** be the final authority — humans must maintain control.
- S2: Logging changes and publishers = traceability = accountability.
- S3: Governance sign-off = formal responsibility and oversight.

---

### Fairness (Test 7 — Q56)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Fairness means an AI system should avoid affecting similar groups differently. | **Yes** |
| 2 | Using real-world evaluation data can help assess fairness. | **Yes** |
| 3 | Fairness is mainly about making model internals visible to end users. | **No** |

**Why:**
- S1: Core fairness definition — equitable treatment across groups.
- S2: Real-world data is critical for fairness evaluation (Microsoft Learn).
- S3: Making internals visible = **transparency**, not fairness.

---

## Generative / Agentic / Traditional AI Concepts

### Generative AI Behavior (Test 1 Q9 = Test 6 Q9)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Generative AI models are trained on large datasets and learn patterns from that data. | **Yes** |
| 2 | A generative AI model responds by retrieving one fixed prewritten answer for each prompt. | **No** |
| 3 | The same prompt can produce different outputs across different runs. | **Yes** |

**Why:**
- S1: GenAI is built on large datasets and learns patterns.
- S2: GenAI does NOT work like a fixed lookup table — it generates unique content.
- S3: Stochastic sampling means identical prompts can produce different outputs.

---

### AI Solution Types (Test 1 Q12 = Test 6 Q12) 🔴
| # | Statement | Answer |
|---|-----------|--------|
| 1 | A sentiment classifier that labels text as positive or negative is a generative AI solution. | **No** |
| 2 | An agentic AI solution can use tools or external systems to take multistep actions toward a goal. | **Yes** |
| 3 | A generative AI solution can create new content such as text or images. | **Yes** |

**Why:**
- S1: Sentiment classification is **traditional/discriminative AI** (assigns labels, doesn't generate).
- S2: Agentic AI is defined by goal-oriented behavior, tool use, and multistep actions.
- S3: Generative AI creates novel outputs like text and images.

---

### AI Workload Types (Test 5 — Q3)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Generative AI is commonly used to create new text or images from prompts. | **Yes** |
| 2 | Agentic AI is limited to returning one response and cannot use tools or multistep actions. | **No** |
| 3 | Computer vision is the best fit for analyzing spoken audio from a microphone. | **No** |

**Why:**
- S1: GenAI creates content from prompts.
- S2: Agentic AI **can** use tools and multistep actions — that's its defining feature.
- S3: Spoken audio is a **speech** workload, not vision.

---

### AI Model Concepts (Test 2 — Q15)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Generative AI models are trained on large datasets to learn patterns. | **Yes** |
| 2 | A base model is already customized for a specific use case. | **No** |
| 3 | Embeddings can be used to represent semantic similarity between inputs. | **Yes** |

**Why:**
- S1: Standard GenAI training description.
- S2: A base model is the **starting point** before fine-tuning — NOT customized.
- S3: Embeddings are vector representations where distance correlates with semantic similarity.

---

### Model Types (Test 3 — Q18)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Embedding models convert text into vectors for semantic comparison. | **Yes** |
| 2 | Image generation models are the best choice for vector similarity search. | **No** |
| 3 | Multimodal chat models can accept images as input. | **Yes** |

**Why:**
- S1: Embeddings = dense vector representations for semantic comparison/retrieval.
- S2: Image generation creates images from prompts — doesn't produce vectors for search.
- S3: Multimodal chat models accept text + images/audio as input.

---

## Prompt Engineering

### Prompt Roles (Test 5 — Q2)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | In chat-based prompting, the system message usually provides the highest-level instructions. | **Yes** |
| 2 | A user prompt is the best place to define permanent app-wide boundaries for every conversation. | **No** |
| 3 | Few-shot prompting can use example user and assistant interactions. | **Yes** |

**Why:**
- S1: System messages provide the highest-level instructions.
- S2: Permanent boundaries belong in the **system message**, not user prompt.
- S3: Few-shot uses example user/assistant pairs to demonstrate expected behavior.

---

## Speech

### Speech Capabilities (Test 1 Q19 = Test 6 Q19)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Language identification can detect which spoken language is present in audio. | **Yes** |
| 2 | Diarization can identify which speaker said a segment of transcribed speech. | **Yes** |
| 3 | Batch transcription is the best choice for live low-latency captions during a webinar. | **No** |

**Why:**
- S1: Azure Speech supports language identification in transcription.
- S2: Diarization distinguishes speakers and attributes transcript segments.
- S3: Batch transcription is for **prerecorded** audio — real-time transcription is needed for live captions.

---

### Speech SDK Methods (Test 2 — Q13) 🔴
| # | Statement | Answer |
|---|-----------|--------|
| 1 | recognize_once_async is intended for a single utterance. | **Yes** |
| 2 | start_continuous_recognition_async is the better choice for long-running multi-utterance input. | **Yes** |
| 3 | Voice Live API combines speech recognition, generative AI, and text-to-speech in one interface. | **Yes** |

**Why:**
- S1: API docs confirm recognize_once_async handles single utterances.
- S2: start_continuous_recognition_async is for multi-utterance scenarios.
- S3: Voice Live API integrates all three capabilities for voice agents.

> ⚠️ All three are Yes — don't assume one must be No!

---

### Speech Concepts (Test 2 — Q28)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Speech recognition converts spoken audio into text. | **Yes** |
| 2 | Text to speech generates synthesized audio from text. | **Yes** |
| 3 | Speaker diarization is used to control pitch and speaking rate of generated audio. | **No** |

**Why:**
- S1: Speech-to-text = converting audio to text.
- S2: TTS = converting text to speech.
- S3: Diarization **identifies speakers** (recognition feature). Pitch/rate control is done via **SSML** (synthesis feature).

---

## Vision & Content Understanding

### Vision vs Content Understanding (Test 1 Q11 = Test 6 Q11) 🔴
| # | Statement | Answer |
|---|-----------|--------|
| 1 | A multimodal vision model is sufficient when you need a natural-language description of what is present in an image. | **Yes** |
| 2 | Azure Content Understanding is the better choice when you need schema-defined fields such as invoice number and total from varied files. | **Yes** |
| 3 | Image analyzers are optimized when your main goal is extracting and analyzing text from images instead of using a document field extraction schema. | **No** |

**Why:**
- S1: Vision models provide natural-language descriptions of images.
- S2: Content Understanding is designed for **schema-defined structured extraction**.
- S3: Image analyzers are NOT optimized for text extraction — document field schemas are better.

---

### Multimodal Vision Input (Test 3 — Q26) 🔴
| # | Statement | Answer |
|---|-----------|--------|
| 1 | A deployed multimodal model can accept image input in addition to text. | **Yes** |
| 2 | A public image URL can be used as input for image interpretation. | **Yes** |
| 3 | Every multimodal model supports multiple images in the same chat turn. | **No** |

**Why:**
- S1: Multimodal models accept text + images.
- S2: Public image URLs are valid input.
- S3: Multiple-image support **varies by model** — not universal.

---

### Vision Capabilities (Test 3 — Q58)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | OCR can extract readable text from an image. | **Yes** |
| 2 | Image generation models are used to return bounding boxes around detected objects. | **No** |
| 3 | Object detection can identify objects and their coordinates in an image. | **Yes** |

**Why:**
- S1: OCR extracts printed/handwritten text from images.
- S2: Image generation **creates** images — it doesn't analyze them for object locations.
- S3: Object detection returns bounding box coordinates for each detected object.

---

### Vision Chat Detail Parameter (Test 5 — Q48)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | The "detail" parameter is placed inside the "image_url" object in a vision chat request. | **Yes** |
| 2 | "auto" is the default detail setting. | **Yes** |
| 3 | "high" is the default detail setting. | **No** |

**Why:**
- S1: detail goes inside the image_url object.
- S2: "auto" is the default.
- S3: "high" is optional, not the default.

---

### Content Understanding — Analyzers (Test 2 — Q59)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Content Understanding in Foundry Tools can process images into a user-defined output format. | **Yes** |
| 2 | The quickstart uses prebuilt-imageSearch to generate an image description. | **Yes** |
| 3 | prebuilt-layout is the documented base analyzer for building a custom image analyzer. | **No** |

**Why:**
- S1: Content Understanding processes images into user-defined output formats.
- S2: Quickstart uses prebuilt-imageSearch for image descriptions.
- S3: Custom image analyzers use **prebuilt-image** as base, not prebuilt-layout (that's for documents).

---

### Content Understanding — SDK (Test 4 — Q8)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | delete_analyzer is the SDK method used to submit content for analysis. | **No** |
| 2 | A custom analyzer for images should use base_analyzer_id="prebuilt-video". | **No** |
| 3 | Content Understanding analyzers can return structured outputs such as markdown, JSON fields, and segments. | **Yes** |

**Why:**
- S1: SDK uses **begin_analyze** to submit content, not delete_analyzer.
- S2: Image analyzers inherit from **prebuilt-image**, not prebuilt-video.
- S3: Analyzers return markdown, JSON fields, and segments as documented.

---

### Content Understanding — Video/Audio (Test 3 — Q61)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | transcriptPhrases can include speaker identification and timing information. | **Yes** |
| 2 | prebuilt-videoSearch can extract keyframes and chapter segments from video. | **Yes** |
| 3 | Content Understanding audio extraction is used to convert text into spoken audio. | **No** |

**Why:**
- S1: transcriptPhrases contain speaker IDs and precise timing.
- S2: prebuilt-videoSearch extracts keyframes, transcripts, and chapters.
- S3: Audio extraction analyzes speech into structured info. Converting text to audio = **speech synthesis** (different capability).

---

### Azure Language (Test 5 — Q33)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Azure Language in Foundry Tools can be used from Microsoft Foundry and through client libraries. | **Yes** |
| 2 | detect_language returns a language prediction with a confidence score. | **Yes** |
| 3 | PII detection is the feature used to convert text into spoken audio. | **No** |

**Why:**
- S1: Azure Language is available through Foundry and client libraries.
- S2: detect_language returns language code + confidence score.
- S3: PII detection identifies sensitive info. Text-to-speech is a **speech** capability.

---

### Text Analytics (Test 7 — Q50)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Keyword extraction identifies main concepts in text. | **Yes** |
| 2 | Entity detection can categorize items such as people and organizations. | **Yes** |
| 3 | Summarization is the best technique for assigning positive, neutral, or negative labels. | **No** |

**Why:**
- S1: Key phrase extraction finds main talking points/concepts.
- S2: Named entity recognition categorizes people, orgs, locations, etc.
- S3: **Sentiment analysis** assigns polarity labels — not summarization.

---

### Content Understanding (Test 7 — Q60) 🔴
| # | Statement | Answer |
|---|-----------|--------|
| 1 | prebuilt-documentFieldSchema can propose a field schema for a new document type. | **Yes** |
| 2 | estimateFieldSourceAndConfidence can return page number, bounding box, and confidence for extracted fields. | **Yes** |
| 3 | prebuilt-documentFields is mainly used to transcribe audio recordings. | **No** |

**Why:**
- S1: documentFieldSchema is the schema-proposal utility analyzer.
- S2: estimateFieldSourceAndConfidence returns source location + confidence for fields.
- S3: documentFields extracts key-value pairs from **documents** — not audio transcription.

---

## Agents & Foundry

### Agent Capabilities (Test 1 Q22 = Test 6 Q22)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Task planning can break a user goal into smaller steps for the agent to execute. | **Yes** |
| 2 | Tool use means the agent can call external capabilities such as search or other configured tools. | **Yes** |
| 3 | Task completion can include returning a final result after the agent has used tools and finished the requested work. | **Yes** |

**Why:**
- S1: Task planning decomposes goals into steps.
- S2: Tool use enables calling external capabilities.
- S3: Task completion = returning final answer after planning + execution.

> ⚠️ All three are Yes!

---

### Foundry Portal (Test 3 — Q50) 🔴
| # | Statement | Answer |
|---|-----------|--------|
| 1 | You can test unsaved changes to a prompt-based agent in the agents playground. | **Yes** |
| 2 | If you leave the Foundry portal, unsaved agent changes are preserved automatically. | **No** |
| 3 | You need to save changes if you want conversation history and full evaluations tied to that version. | **Yes** |

**Why:**
- S1: Playground supports testing unsaved draft changes.
- S2: Unsaved changes are **LOST** if you leave — no automatic preservation.
- S3: Saved changes required for conversation history, monitoring, and evaluations.

---

### Foundry Portal (Test 7 — Q37) 🔴
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Every Foundry model requires an Azure Marketplace subscription before deployment. | **No** |
| 2 | After deployment, you can type a prompt and see outputs in the playground. | **Yes** |
| 3 | The Code tab shows details about programmatic access to the deployment. | **Yes** |

**Why:**
- S1: Only **partner/community** models need Marketplace subscription — not all models.
- S2: Playground lets you type prompts and see outputs after deployment.
- S3: Code tab shows programmatic access details — documented post-deployment step.

---

### Agent SDK (Test 4 — Q44)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Agent creation and versioning remain on the project client. | **Yes** |
| 2 | A conversation can persist history across turns. | **Yes** |
| 3 | PromptAgentDefinition is the runtime object that stores chat history after each message. | **No** |

**Why:**
- S1: Creation and versioning stay on project client.
- S2: Conversations persist multi-turn history.
- S3: PromptAgentDefinition defines agent model/instructions at **setup**, not runtime chat state.

---

### Foundry SDK Auth & APIs (Test 2 — Q48)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | The Python AIProjectClient library supports API-key authentication instead of Entra ID for client construction. | **No** |
| 2 | The Responses API examples use input to send the prompt text. | **Yes** |
| 3 | In a basic chat-completions conversation, the request usually ends with a user message to trigger the model response. | **Yes** |

**Why:**
- S1: Python AIProjectClient uses **Entra ID only** — no API-key auth.
- S2: Responses API uses `responses.create(..., input="...")`.
- S3: Chat-completions should end with a user message so the model knows it's the assistant's turn.

---

## Multimodal Audio

### Audio Capabilities (Test 7 — Q44)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Audio-enabled models introduce the audio modality into the existing /chat/completions API. | **Yes** |
| 2 | In the Foundry Chat playground, you can record audio prompts and attach audio files. | **Yes** |
| 3 | The documented place to test gpt-4o-mini-audio-preview is the Audio playground, not the Chat playground. | **No** |

**Why:**
- S1: Audio extends the existing chat completions API — no separate API needed.
- S2: Chat playground supports audio recording and file attachment.
- S3: Audio playground does **not** support gpt-4o-mini-audio-preview — use **Chat playground** instead.

---

## Deployment & Image Generation

### Deployment Options (Test 4 — Q16)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | Standard deployment in Foundry resources supports regional, data zone, and global processing. | **Yes** |
| 2 | Serverless API endpoints can be created as global deployments. | **No** |
| 3 | Managed compute requires compute quota and is billed per compute uptime. | **Yes** |

**Why:**
- S1: Standard deployment supports regional, data zone, or global processing.
- S2: Serverless API endpoints are **regional only**, not global.
- S3: Managed compute requires quota and charges per compute uptime.

---

### Image Generation (Test 4 — Q35)
| # | Statement | Answer |
|---|-----------|--------|
| 1 | When you use an image-generation model like gpt-image-1 in Foundry, you are presented with the images playground. | **Yes** |
| 2 | The response_format parameter is supported for GPT-image-1 series models. | **No** |
| 3 | To get a transparent background on an image generation request, you set background to transparent and use PNG output. | **Yes** |

**Why:**
- S1: Foundry routes image-generation models to the images playground.
- S2: response_format is for **DALL-E 3**, not GPT-image-1 (which uses output_format).
- S3: Transparent backgrounds need `background="transparent"` + PNG output.

---

## Model Parameters & Field Properties (Test 6 — Matching Style)

### Model Parameters (Test 6 — Q56)
Match the parameter to its correct description. Select 3 correct pairs:

| Parameter | Description | Correct? |
|-----------|-------------|----------|
| Temperature | Sets the maximum conversation size before truncation | ❌ No — temperature controls output randomness |
| **top_p** | **Uses nucleus sampling over the highest-probability tokens** | ✅ **Yes** |
| Context window | Acts as the content safety threshold | ❌ No — context window is about token capacity |
| **Max tokens** | **Caps how much text can be generated in a response** | ✅ **Yes** |
| **Context window** | **Limits how much input or conversation history the model can consider** | ✅ **Yes** |
| Temperature | Selects the external grounding source | ❌ No — temperature doesn't select grounding sources |

---

### Content Understanding Field Properties (Test 6 — Q60)
Match the property to its correct description. Select 3 correct pairs:

| Property | Description | Correct? |
|----------|-------------|----------|
| **confidence** | **Estimated reliability of a predicted field value** | ✅ **Yes** |
| source | Model temperature setting | ❌ No — source identifies field position in content |
| **Object field** | **Nested structure such as TotalAmount with Amount and CurrencyCode** | ✅ **Yes** |
| Array field | Single scalar value such as InvoiceDate | ❌ No — array fields contain repeated structures (like line items) |
| **spans** | **Positions associated with the field value in markdown content** | ✅ **Yes** |
| markdown | Reserved output used only for currency fields | ❌ No — markdown is general extracted content representation |

---

## Quick-Reference: Common Traps

| Trap | Remember |
|------|----------|
| "All Yes" is valid | Q13 (Speech SDK), Q22 (Agent capabilities) — all three statements can be Yes |
| Transparency ≠ Privacy | Transparency = communicate limitations. Encryption = privacy/security |
| Reliability ≠ Transparency | Reliability = behavior under unexpected conditions. Transparency = understandable decisions |
| Base model ≠ customized | Base models are starting points before fine-tuning |
| Batch transcription ≠ live | Batch = prerecorded. Real-time transcription = live captions |
| Diarization ≠ SSML | Diarization identifies speakers. SSML controls pitch/rate |
| prebuilt-image ≠ prebuilt-layout | Image analyzers use prebuilt-image. Document analyzers use prebuilt-layout |
| response_format ≠ output_format | DALL-E 3 = response_format. GPT-image-1 = output_format |
| Sentiment classifier = traditional AI | Classification is discriminative, not generative |
| AIProjectClient = Entra ID only | No API-key auth for Python AIProjectClient |
| Serverless = regional only | Serverless API endpoints cannot be global |
| Content Understanding audio ≠ TTS | Audio extraction = analyze speech. TTS = generate speech |
| Fairness ≠ Inclusiveness | Separate principles — fairness=equitable treatment, inclusiveness=accessible design |
| AI ≠ final authority | Accountability requires humans maintain control over high-impact decisions |
| Not all models need Marketplace | Only partner/community models require Azure Marketplace subscription |
| Audio playground ≠ gpt-4o-mini-audio | Use Chat playground for gpt-4o-mini-audio-preview, NOT Audio playground |
| documentFields ≠ documentFieldSchema | Fields=extract key-value pairs. FieldSchema=propose schema for new doc types |
