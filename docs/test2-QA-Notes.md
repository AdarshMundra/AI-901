# AI-901 Practice Assessment 2 - Question, Answer & Why Notes

> 60 questions total. **14 incorrect** answers marked with :red_circle: — focus your revision there.

---

## Q1. [Correct] AI app should resist ________ (reliability and safety)
**Answer:** C. harmful manipulation
**Why:** Reliability and safety requires AI systems to resist harmful manipulation from adversarial/unexpected prompts. Model cards (A) = transparency. Stakeholder mapping (B) = planning. Explainability (D) = transparency.

---

## Q2. [Correct] Three statements about reliability and safety (Yes/No pattern)
**Answer:** B. Yes / No / Yes
**Why:** Testing under unexpected conditions (S1) = reliability. Making decisions understandable (S2) = transparency, NOT reliability. Monitoring false negatives in harmful-content detection (S3) = reliability.

---

## Q3. [Correct] What does a generative AI model do after training?
**Answer:** B. Learns patterns and generates statistically similar new content
**Why:** Generative AI learns patterns from training data and produces new output statistically related to training examples — it doesn't store fixed responses or copy documents.

---

## Q4. [Correct] Which question aligns to reliability and safety in an AI review?
**Answer:** D. In what situations could the system fail or produce unreliable outcomes?
**Why:** Reliability = failure scenarios and unreliable outcomes. Other options map to: inclusiveness (A), accountability (B), transparency (C).

---

## Q5. [Correct] Code to screen user text for harmful content (ContentSafetyClient)
**Answer:** A. analyze_text
**Why:** Azure AI Content Safety uses `analyze_text` to detect harmful content. summarize (B), extract_entities (C), transcribe_audio (D) are different workloads entirely.

---

## Q6. [Correct] Capture spoken microphone input and show live captions
**Answer:** B. Speech to text
**Why:** Speech to text = real-time speech recognition, converting spoken audio into written text for live captions.

---

## Q7. [Correct] Two actions for moderation pipeline (missing harmful content / blocking safe content)
**Answer:** A. Adjust severity thresholds AND B. Use blocklists where needed
**Why:** Tuning severity thresholds reduces false positives/negatives. Blocklists catch domain-specific harmful terms. Cosmetic changes (accent color, FAQ length, icons) don't affect content moderation.

---

## Q8. [Correct] Code to capture one spoken utterance as text (SpeechRecognizer)
**Answer:** B. `result = speech_recognizer.recognize_once_async().get()`
**Why:** `recognize_once_async().get()` captures a single utterance. The other options (speak_text_async, SpeechSynthesizer, speak_ssml_async) are all synthesis methods — the opposite direction.

---

## Q9. [Correct] Training app must read lesson text aloud
**Answer:** D. Text to Speech
**Why:** Text to Speech converts written text into spoken audio. The app already has text content and needs audio output.

---

## Q10. [Correct] Code to alert when safety score drops below threshold
**Answer:** C. send_alert("Safety threshold breached")
**Why:** Monitoring + alerting is key for operating AI safely. When safety score breaches threshold, send an alert for rapid response.

---

## Q11. [Correct] Most important consideration for medical note summarization AI
**Answer:** A. Test high-risk and unexpected scenarios before deployment
**Why:** In high-risk medical contexts, reliability and safety requires testing edge cases and unexpected conditions before deployment to prevent clinical harm.

---

## Q12. [Correct] During text generation, a model predicts one ________ at a time
**Answer:** C. token
**Why:** GPT-style models do next-token prediction. Text is tokenized and the model generates output iteratively, one token at a time.

---

## Q13. [Correct] Three statements about speech recognition methods (Yes/Yes/Yes)
**Answer:** D. Yes / Yes / Yes
**Why:** `recognize_once_async` = single utterance (S1). `start_continuous_recognition_async` = long-running multi-utterance (S2). Voice Live API = integrated speech recognition + AI + TTS in one interface (S3). All correct.

---

## Q14. [Correct] Three matched pairs: Embedding, Fine-tuning, Prompt
**Answer:** A, C, E
- A. Embedding — numeric representation of semantic meaning
- C. Fine-tuning — adapting model weights with task-specific examples
- E. Prompt — input instructions provided to the model

**Why:** Base model ≠ already customized. Hallucination ≠ guaranteed grounding. Completion tokens ≠ form fields.

---

## Q15. [Correct] Three statements about generative AI, base models, embeddings
**Answer:** B. Yes / No / Yes
**Why:** Models trained on large datasets (Yes). Base model has NOT been customized (No — saying it has is wrong). Embeddings represent semantic similarity (Yes).

---

## Q16. [Correct] Two statements about Content Understanding custom analyzer schema
**Answer:** A. Title returns a string value AND C. ChartType uses classify
**Why:** Schema shows Title with `"type": "string"` and ChartType with `"method": "classify"` plus enum list.

---

## Q17. [Correct] Code for translation config to add French as target language
**Answer:** D. add_target_language
**Why:** `SpeechTranslationConfig.add_target_language()` adds output translation languages. Set recognition language first, then add target languages.

---

## :red_circle: Q18. [Incorrect] Responses API sends user prompt in the ________ parameter
**Answer:** A. input
**Why:** The Responses API uses `responses.create(model=..., input="...")`. The parameter is **"input"**, NOT "content", "prompt", or "message". This is specific to the modern Responses API.

---

## Q19. [Correct] Two true statements about how generative AI models work
**Answer:** A. Prompts influence the model's generated output AND C. Fine-tuning can adapt model weights
**Why:** Prompts guide generation. Fine-tuning adapts weights. Models don't "always" return identical answers. Models don't automatically know proprietary data.

---

## :red_circle: Q20. [Incorrect] A model not customized or fine-tuned is called a ________
**Answer:** C. base model
**Why:** A **base model** = not yet customized or fine-tuned. It's the starting point before task-specific adaptation. Not grounded response, agent session, or vector store.

---

## Q21. [Correct] Code to create semantic vectors with EmbeddingsClient
**Answer:** D. embed
**Why:** `EmbeddingsClient.embed()` generates embedding vectors. "complete" is for text generation, not embeddings.

---

## Q22. [Correct] Convert live customer calls into written text
**Answer:** B. Speech to Text
**Why:** Speech to text converts spoken audio into written text for transcription, supporting both live and prerecorded audio.

---

## :red_circle: Q23. [Incorrect] Two capabilities that are part of speech recognition
**Answer:** A. Real-time transcription AND B. Batch transcription
**Why:** Both real-time and batch transcription = **speech recognition (STT)**. Neural voice output, SSML voice styling, and audio synthesis all belong to **speech synthesis (TTS)**. Key: recognition = audio→text, synthesis = text→audio.

---

## Q24. [Correct] Three matched pairs: Responsible AI and services
**Answer:** A, C, E
- A. Reliability and safety — responds safely to unexpected conditions
- C. Azure AI Content Safety — detects harmful content
- E. Harms modeling — identifies potential harm scenarios

**Why:** Fairness ≠ encryption (that's privacy). Transparency ≠ assigning owners (that's accountability). Inclusiveness ≠ blocking self-harm content (that's safety).

---

## Q25. [Correct] After analyzing image with prebuilt-imageSearch, code reads ________ field
**Answer:** D. Summary
**Why:** The quickstart reads `content.fields.get("Summary")` for image descriptions. Transcript = audio. ChartType = custom analyzers.

---

## :red_circle: Q26. [Incorrect] Fine-tune pitch, speaking rate, pronunciation for synthesized voice
**Answer:** A. SSML
**Why:** **SSML (Speech Synthesis Markup Language)** customizes synthesized speech: pitch, pronunciation, speaking rate, volume. Speaker diarization = separating speakers (recognition). OCR = reading text from images. Batch transcription = recognition.

---

## Q27. [Correct] Two practices that support reliability and safety before release
**Answer:** A. Red-team testing AND C. Harms modeling
**Why:** Red-team testing probes vulnerabilities. Harms modeling anticipates failures. Both support safer deployment. Brand review, logo refresh, color palette = cosmetic.

---

## Q28. [Correct] Three statements about speech capabilities (Yes/Yes/No)
**Answer:** A. Yes / Yes / No
**Why:** Speech recognition converts audio→text (Yes). TTS generates audio from text (Yes). Speaker diarization does NOT control pitch/rate (No — that's SSML).

---

## :red_circle: Q29. [Incorrect] Three correctly matched speech pairs
**Answer:** A, B, C
- A. Speech to Text — converts spoken audio into text
- B. Text to Speech — converts text into synthesized audio
- C. Speaker diarization — separates speakers in audio

**Why:** SSML customizes synthesis (doesn't train recognition). Batch transcription = recognition feature (not neural voice output). Speech Translation translates spoken language (doesn't detect sentiment).

---

## :red_circle: Q30. [Incorrect] Three correctly matched Foundry SDK pairs
**Answer:** B, D, F
- B. `get_openai_client()` — returns an OpenAI-compatible client
- D. model parameter — should use the deployment name
- F. `openai.conversations.create()` — creates conversation for multi-turn chat

**Why:** AIProjectClient is entry point but doesn't send chat requests directly (that's the OpenAI client). `previous_response_id` is NOT required for first request. `az login` authenticates but does NOT create deployments.

---

## Q31. [Correct] Code to speak a string using Azure Speech
**Answer:** A. `result = speech_synthesizer.speak_text_async(text).get()`
**Why:** `speak_text_async(text).get()` is the standard TTS pattern. Other options use recognition methods or non-existent translation methods.

---

## Q32. [Correct] Feature to show which participant spoke each section of audio
**Answer:** B. Speaker diarization
**Why:** Diarization identifies and separates different speakers, attributing each segment to the correct participant.

---

## Q33. [Correct] Two statements describing speech synthesis capabilities
**Answer:** A. It can generate human-like voice output from text AND C. It can be customized with SSML
**Why:** TTS converts text→speech and supports SSML customization. Transcription and speaker identification are recognition features. Synthesis is NOT limited to one fixed voice.

---

## Q34. [Correct] Code to listen from default microphone (AudioConfig)
**Answer:** A. `AudioConfig(use_default_microphone=True)`
**Why:** `AudioConfig(use_default_microphone=True)` configures live microphone capture. `filename="meeting.wav"` reads from file instead.

---

## Q35. [Correct] Code to capture one short spoken command asynchronously
**Answer:** A. recognize_once_async
**Why:** `recognize_once_async` = single utterance async recognition. `start_continuous_recognition_async` = long-running. `speak_text_async` = synthesis.

---

## Q36. [Correct] Add capability to read text replies aloud through speaker
**Answer:** C. Text to speech
**Why:** App already has text responses → need TTS to convert to audio. Speech translation, Voice Live API, entity recognition serve different purposes.

---

## :red_circle: Q37. [Incorrect] Three matched speech capability pairs
**Answer:** A, B, C
- A. Speech to text — real-time transcription
- B. Text to speech — reads text aloud with human-like voice
- C. Voice Live API — low-latency speech-to-speech interactions for voice agents

**Why:** Custom endpoints are OPTIONAL, only for custom speech models. Microsoft's baseline model requires NO custom endpoint. The user incorrectly selected E (custom endpoint required for baseline) instead of C.

---

## :red_circle: Q38. [Incorrect] Two actions to try speech to text in Foundry and get starter code
**Answer:** A. Select Playgrounds and open a speech playground AND C. Switch to the Code tab to get sample code
**Why:** Quickstart flow: open speech playground → switch to **Code tab** for SDK starter code. The JSON tab shows raw responses, not SDK code. The user incorrectly selected D (Add Azure Speech MCP Server) instead of C.

---

## Q39. [Correct] Code to play text through speaker (SpeechSynthesizer method)
**Answer:** B. speak_text_async
**Why:** `speak_text_async` = async method for synthesizing plain text to audio. `get_voices_async` only lists available voices. recognize methods = STT.

---

## Q40. [Correct] Azure Speech feature for low-latency speech-to-speech voice agents
**Answer:** C. Voice Live API
**Why:** Voice Live API = low-latency, high-quality speech-to-speech for voice agents. Integrates recognition + generative AI + TTS in one real-time interface.

---

## Q41. [Correct] Package to install for Foundry SDK project client
**Answer:** B. azure-ai-projects
**Why:** `pip install azure-ai-projects>=2.0.0` for AIProjectClient. Other packages (search, language, vision) are for different workloads.

---

## Q42. [Correct] Component for dense numeric representation of text (semantic similarity)
**Answer:** D. Embedding
**Why:** Embeddings = dense numeric vectors representing semantic meaning. Similar meanings → nearby points in vector space. Completion tokens, stop sequences, temperature = generation parameters.

---

## Q43. [Correct] Two setup actions for AIProjectClient with DefaultAzureCredential
**Answer:** C. Install azure-ai-projects>=2.0.0 AND E. Run az login
**Why:** Need the package installed + signed in via `az login` for DefaultAzureCredential to work. Search indexes, vision packages, speech deployments are NOT prerequisites.

---

## :red_circle: Q44. [Incorrect] Two actions in documented multi-turn agent flow in Foundry
**Answer:** A. Create conversation with `openai.conversations.create()` AND E. Include agent_reference when calling `responses.create()`
**Why:** Documented flow: create conversation FIRST → then call `responses.create()` with agent_reference. `previous_response_id` and `chat.completions.create` with extra_body are different API patterns. The user missed option A.

---

## :red_circle: Q45. [Incorrect] Most likely cause of 404 error calling a model from Foundry client
**Answer:** C. The model value does not match the deployment name
**Why:** 404 = deployment not found = model name in request doesn't match actual deployment name. HTTPS in endpoint (D) is normal expected behavior, NOT an error cause. **Always use the deployment name you assigned, not the base model name.**

---

## Q46. [Correct] Code for ChatCompletionsClient to send prompt and receive generated text
**Answer:** C. complete
**Why:** Azure AI Inference SDK uses `complete` method on ChatCompletionsClient. `embed` = embeddings. `get_model_info` = metadata. `send_request` = low-level transport.

---

## Q47. [Correct] Correct Entra ID token scope for lightweight Foundry client
**Answer:** D. `https://ai.azure.com/.default`
**Why:** Responses API examples specify `https://ai.azure.com/.default` for Entra ID auth. Graph, Search, Management scopes target different Azure resources.

---

## Q48. [Correct] Three statements: AIProjectClient auth, Responses API param, chat-completions ending
**Answer:** C. No / Yes / Yes
**Why:** AIProjectClient only supports Entra ID, NOT API-key auth (No). Responses API uses "input" parameter (Yes). Chat-completions conversations should end with user message (Yes).

---

## Q49. [Correct] Service to extract structured product details from shelf photos
**Answer:** B. Azure Content Understanding
**Why:** Content Understanding processes images into structured, user-defined output formats with field schemas. Speech, Search, Agent Service serve different purposes.

---

## Q50. [Correct] Best description of fine-tuning in generative AI
**Answer:** B. Training a base model's weights with task-specific examples
**Why:** Fine-tuning adapts a pre-trained model by adjusting weights on task-specific data. Different from prompt engineering (changing request), retrieval (adding external knowledge), or streaming (changing delivery).

---

## :red_circle: Q51. [Incorrect] Code to retrieve OpenAI-compatible client from AIProjectClient
**Answer:** D. get_openai_client
**Why:** `project.get_openai_client()` returns the OpenAI-compatible client. `conversations.create()` is an operation ON the client after it's created, NOT the method to retrieve it. **Remember: get the client first, then use it.**

---

## Q52. [Correct] baseAnalyzerId value for custom chart image analyzer
**Answer:** C. prebuilt-image
**Why:** Custom image analyzers inherit from `prebuilt-image` as the base. `prebuilt-imageSearch` = direct prebuilt use. `prebuilt-layout` = documents. `prebuilt-read` = OCR.

---

## Q53. [Correct] Parameter name for prompt text in Responses API
**Answer:** A. input
**Why:** `responses.create(input=...)` — the parameter is "input". NOT "prompt", "message", or "question".

---

## :red_circle: Q54. [Incorrect] Analyzer ID for image description in Python quickstart
**Answer:** D. prebuilt-imageSearch
**Why:** The quickstart uses `prebuilt-imageSearch` as the analyzer_id for generating image descriptions. `prebuilt-image` (C) is the **base analyzer for custom inheritance**, NOT the direct prebuilt analyzer for descriptions. Key distinction!

---

## Q55. [Correct] Two Azure setup actions required before using Content Understanding for images
**Answer:** B. Create a Microsoft Foundry resource AND D. Deploy the required models
**Why:** Need a Foundry resource + deployed LLM models (GPT, embeddings) before using Content Understanding. Speech resources, Search indexes, SSML config are unrelated.

---

## Q56. [Correct] Approach to extract Title and ChartType fields from chart images
**Answer:** A. Create a custom analyzer based on prebuilt-image
**Why:** Custom analyzer inheriting from `prebuilt-image` with user-defined field schema for structured extraction. Speech, SSML, TTS are completely different workloads.

---

## Q57. [Correct] Reliability and safety consideration for student-facing chat app
**Answer:** B. Content filtering and stress testing
**Why:** Content filtering blocks unsafe outputs. Stress testing validates behavior under risky prompts. Bias review = fairness. Explainability = transparency. Accessibility = inclusiveness.

---

## :red_circle: Q58. [Incorrect] Three matched Content Understanding pairs
**Answer:** B, D, E
- B. prebuilt-imageSearch — generates an image description
- D. baseAnalyzerId — identifies the parent analyzer to inherit from
- E. prebuilt-image — base image analyzer for custom image extraction

**Why:** The user selected fieldSchema (C) instead of prebuilt-image (E). While fieldSchema does define fields, the correct three are B, D, E as most directly tied to image analyzer creation and the quickstart flow.

---

## Q59. [Correct] Three Content Understanding statements (Yes/Yes/No)
**Answer:** C. Yes / Yes / No
**Why:** Content Understanding processes images into user-defined formats (Yes). Quickstart uses `prebuilt-imageSearch` for descriptions (Yes). `prebuilt-layout` is NOT the base for custom image analyzers — `prebuilt-image` is (No).

---

## :red_circle: Q60. [Incorrect] Code for custom analyzer constructor (base_analyzer_id parameter)
**Answer:** B. `base_analyzer_id="prebuilt-image"`
**Why:** The custom analyzer uses `ContentAnalyzer(base_analyzer_id="prebuilt-image", ...)`. The user selected `analyzer_id="prebuilt-image"` (A), confusing the analyzer's own ID with the parent reference. **Parameter name is `base_analyzer_id`, not `analyzer_id`.**

---

## KEY TAKEAWAYS FROM YOUR WRONG ANSWERS

### Speech Recognition vs Synthesis — STOP MIXING THEM UP

| Recognition (STT) | Synthesis (TTS) |
|-------------------|-----------------|
| `SpeechRecognizer` | `SpeechSynthesizer` |
| `recognize_once_async()` | `speak_text_async()` |
| Real-time transcription | Neural voice output |
| Batch transcription | SSML customization |
| Speaker diarization | Voice selection |
| Audio → Text | Text → Audio |

### Content Understanding Analyzer IDs — KNOW THE DIFFERENCE

| Analyzer ID | Purpose |
|-------------|---------|
| `prebuilt-imageSearch` | Direct prebuilt use for image descriptions (use this to GET descriptions) |
| `prebuilt-image` | Base analyzer for CUSTOM image analyzers (use this as `base_analyzer_id`) |
| `prebuilt-layout` | Document layout extraction |
| `prebuilt-read` | OCR text extraction |
| `prebuilt-procurement` | Mixed procurement documents |
| `prebuilt-invoice` | Invoice-specific extraction |

### Foundry SDK Flow — MEMORIZE THIS ORDER

```
1. pip install azure-ai-projects azure-identity
2. az login (for DefaultAzureCredential)
3. project = AIProjectClient(endpoint=..., credential=DefaultAzureCredential())
4. openai = project.get_openai_client()        ← get_openai_client, NOT openai_client
5. conversation = openai.conversations.create() ← for multi-turn
6. response = openai.responses.create(
       input="...",                              ← parameter is "input", NOT "prompt"
       previous_response_id=response.id,         ← for follow-up turns (NOT required for first)
       extra_body={"agent_reference": {...}}      ← only when calling an agent
   )
```

### Common Traps

| Trap | Correct Answer |
|------|---------------|
| Responses API prompt parameter | `input` (not "prompt" or "message") |
| Model not customized or fine-tuned | **base model** |
| SSML is for... | Customizing TTS output (pitch, rate, pronunciation) |
| 404 error calling model | Deployment name mismatch (use deployment name, not model name) |
| `base_analyzer_id` vs `analyzer_id` | `base_analyzer_id` = parent to inherit from; `analyzer_id` = this analyzer's own ID |
| `prebuilt-imageSearch` vs `prebuilt-image` | `prebuilt-imageSearch` = use directly; `prebuilt-image` = inherit from for custom |
