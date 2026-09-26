# Test 7 — QA Notes

**Score:** 38/60 ≈ 63%  
**Incorrect:** Q2, Q4, Q5, Q14, Q17, Q23, Q28, Q29, Q32, Q33, Q36, Q37, Q40, Q45, Q46, Q48, Q49, Q52, Q54, Q57, Q59, Q60  
🔴 = You answered incorrectly

---

## Responsible AI — Fairness

### Q1. Training data should be ________ of affected people ✓
**Answer:** B) representative

**Why:** Representative data reduces bias by reflecting the diversity of affected populations. Encryption/compression/anonymization serve other purposes (security, storage, privacy) but don't address representation.

---

### Q3. Evaluate hiring model fairness — which TWO actions? ✓
**Answer:** B, D) Test with representative real-world data + Compare outcomes across demographic groups

**Why:** Fairness evaluation requires representative data AND subgroup comparison. Hiding model names, encryption, and server timeout don't assess equitable treatment.

---

### Q7. Recruiting model scores one age group lower — best fairness response? ✓
**Answer:** D) Evaluate model results across age-based groups

**Why:** Fairness issues are identified by comparing outcomes across affected groups. Increasing endpoints, removing audit trails, or publishing code don't address bias detection.

---

### Q9. Which best describes fairness? ✓
**Answer:** C) The system treats similar people fairly across groups

**Why:** Microsoft defines fairness as avoiding different effects on similarly situated groups. Encryption = privacy/security. Explaining parameters = transparency. Latency = reliability.

---

### Q10. Which TWO strongest indicators of fairness risk? ✓
**Answer:** A, C) Similar applicants receive different outcomes across groups + One affected group barely represented in test data

**Why:** Different outcomes for similar people + underrepresentation are classic fairness red flags. TLS, dark themes, and version numbers are unrelated.

---

### Q11. Yes/No: underrepresentation / fairness=inclusiveness / demographic comparison ✓
**Answer:** B) Yes / No / Yes

**Why:** Underrepresentation causes fairness issues (Yes). Fairness and inclusiveness are **separate** principles (No). Comparing across groups helps identify fairness issues (Yes).

---

### Q12. One practical step to improve fairness reviews? ✓
**Answer:** B) Evaluate results using real-world data from affected groups

**Why:** Microsoft Learn highlights real-world data evaluation as the key fairness step. Password policies, batch size, and disabling feedback don't assess equitable treatment.

---

### Q23. Which THREE pairs correctly matched to fairness? 🔴
**Answer:** A, C, E) Avoid different treatment + representative data for evaluation + compare outcomes across sensitive groups

**Why:** All three are fairness concepts. Transparency ≠ encryption (B wrong). Accountability ≠ GPU capacity (D wrong). Fairness ≠ explaining predictions — that's transparency (F wrong).

---

### Q53. Loan system — different outcomes for similar applicants by demographics ✓
**Answer:** C) Fairness

**Why:** Unequal treatment of similarly situated people across groups is the core fairness concern. Transparency = understandability. Reliability = consistent behavior. Privacy = data protection.

---

### Q56. Yes/No: avoid affecting groups / real-world data / model internals visible ✓
**Answer:** A) Yes / Yes / No

**Why:** Fairness = equitable treatment (Yes). Real-world data helps evaluate fairness (Yes). Making internals visible = **transparency**, not fairness (No).

---

### Fairness Key Takeaways

| Concept | Remember |
|---------|----------|
| Core definition | Treat similar people fairly across groups — avoid different effects |
| Data requirement | Training/evaluation data must be **representative** of affected populations |
| Assessment method | Compare outcomes across demographic/sensitive groups |
| Fairness ≠ inclusiveness | They are **separate** responsible AI principles |
| Fairness ≠ transparency | Explaining predictions is transparency, not fairness |
| Strongest risk signals | Different outcomes for similar people + underrepresented groups in data |

---

## Responsible AI — Accountability

### Q4. Which THREE pairs correctly matched? 🔴
**Answer:** A, C, E) Accountability—assign owners + Privacy/security—RBAC + Accountability—document approvals

**Why:** Accountability = ownership + documented approvals. Privacy/security = access control (RBAC). Transparency ≠ encryption (B). Inclusiveness ≠ model lineage (D). Fairness ≠ explaining predictions — that's transparency (F).

---

### Q13. Insurance claims AI — which supports accountability? ✓
**Answer:** B) Keep an audit trail of model changes and approvers

**Why:** Audit trails create traceability and documented ownership. Larger fonts = accessibility. Multilingual voice = inclusiveness. Encryption = privacy/security.

---

### Q15. People remain answerable — which principle? ✓
**Answer:** C) Accountability

**Why:** Accountability = people/organizations remain responsible for AI system behavior. Fairness = equitable treatment. Transparency = understandable decisions. Inclusiveness = accessible design.

---

### Q16. Which TWO support accountability? ✓
**Answer:** A, C) Record who approved deployment + Define human review for high-impact outcomes

**Why:** Accountability needs ownership (who approved) and human oversight (review for high-impact decisions). Image captions = inclusiveness. Token limits and data sources are operational, not governance.

---

### Q17. Yes/No: AI as final authority / logging changes / governance sign-off 🔴
**Answer:** C) No / Yes / Yes

**Why:** AI should **NOT** be final authority for life-affecting decisions (No). Logging who published and why = traceability (Yes). Governance sign-off = formal accountability (Yes).

---

### Q18. Bank loan escalation — which reflects accountability? ✓
**Answer:** D) Require a human reviewer for high-impact cases

**Why:** Human oversight preserves meaningful control over consequential decisions. Hiding rules, replacing reviewers, and short data retention all weaken governance.

---

### Q19. Organization using managed AI services remains ________. ✓
**Answer:** D) accountable

**Why:** Even with managed services, the organization is responsible for governance, monitoring, and outcomes. Anonymous, unbiased, and encrypted describe other concepts.

---

### Q42. Code: preserve review record before deployment ✓
**Answer:** B) audit_log.append(review)

**Why:** Appending to audit log preserves who approved and why — traceability for accountability. print() is temporary. Setting reviewer="system" or reason=None erases governance data.

---

### Q51. Which TWO questions for accountability review? ✓
**Answer:** A, B) Who owns incident response? + Who approves deployment to production?

**Why:** Accountability review focuses on ownership and governance. UI choices (accent color, emojis, voice) don't establish answerability.

---

### Q54. Most closely related to accountability? 🔴
**Answer:** A) Document who changed the model and why

**Why:** Documenting changes/approvals = traceability = accountability. Explaining recommendations = transparency. Encrypting data = privacy. Keyboard navigation = inclusiveness.

---

### Accountability Key Takeaways

| Concept | Remember |
|---------|----------|
| Core definition | People remain answerable for AI system design, deployment, and operation |
| AI ≠ final authority | Humans must maintain meaningful control over high-impact decisions |
| Key practices | Audit trails, documented approvals, governance sign-off, human review |
| Managed services | Organization is STILL accountable even when using managed AI services |
| Lineage data | Track who changed model, why, when deployed — governance data |
| Common mix-ups | Encryption = privacy. Explaining predictions = transparency. Font/voice = inclusiveness |

---

## Text Analytics

### Q20. Classify reviews as positive/neutral/negative ✓
**Answer:** C) Sentiment analysis

**Why:** Sentiment analysis assigns polarity labels (positive/neutral/negative). Keyword extraction = main concepts. Entity detection = named items. Summarization = condensed version.

---

### Q21. Identify people, organizations, locations in support emails ✓
**Answer:** B) Entity detection

**Why:** Entity detection (named entity recognition) categorizes people, places, organizations, dates, quantities. Sentiment = attitude. Keywords = topics. Summarization = shorter version.

---

### Q22. Which THREE pairs correctly matched? ✓
**Answer:** A, C, D) Keyword extraction—main talking points + Entity detection—named items + Summarization—condensed version

**Why:** Each technique has a specific output. Sentiment analysis doesn't categorize people/places (B wrong). Keywords don't assign polarity (E wrong). Summarization doesn't extract entities (F wrong).

---

### Q24. Short condensed version of long incident report ✓
**Answer:** D) Summarization

**Why:** Summarization condenses longer content into a shorter version. Keywords = important phrases (not a narrative). Entity detection = named items. Sentiment = attitude.

---

### Q26. Which TWO outputs of sentiment analysis? ✓
**Answer:** B, E) Document-level sentiment label + Confidence scores

**Why:** Sentiment analysis returns labels (positive/neutral/negative) with confidence scores at document and sentence level. Organization categories and entities come from entity detection. Key phrases from keyword extraction.

---

### Q27. Code: client.________(documents) for sentiment ✓
**Answer:** C) analyze_sentiment

**Why:** Code prints `doc.sentiment` — only `analyze_sentiment` returns sentiment labels. Match the output property to the correct method.

---

### Q28. Short list of main topics (not a rewritten paragraph) 🔴
**Answer:** D) Keyword extraction

**Why:** Keyword extraction returns a list of main concepts/phrases — not a narrative paragraph. "Not a rewritten paragraph" rules out summarization. Entity detection finds named items. Sentiment = polarity.

---

### Q30. Reviews (positive/negative) + condensed transcript — which TWO? ✓
**Answer:** B, D) Summarization + Sentiment analysis

**Why:** Sentiment analysis for polarity classification. Summarization for condensing the transcript. Two different requirements = two different techniques.

---

### Q50. Yes/No: keyword extraction / entity detection / summarization for sentiment ✓
**Answer:** A) Yes / Yes / No

**Why:** Keywords identify main concepts (Yes). Entity detection categorizes people/orgs (Yes). Summarization condenses content — sentiment analysis assigns polarity labels (No).

---

### Q58. Code: client.________(documents) for key phrases ✓
**Answer:** A) extract_key_phrases

**Why:** Code prints `doc.key_phrases` — only `extract_key_phrases` returns key phrases. Match the output property to the correct method.

---

### Text Analytics Key Takeaways

| Technique | What It Does | Output |
|-----------|-------------|--------|
| Sentiment analysis | Classifies attitude/polarity | positive/neutral/negative + confidence scores |
| Entity detection (NER) | Identifies named items | people, orgs, locations, dates, quantities |
| Keyword extraction | Finds main concepts | list of key phrases/talking points |
| Summarization | Condenses long content | shorter version of original text |

| SDK Method | Purpose |
|-----------|---------|
| `analyze_sentiment` | Returns `doc.sentiment` |
| `extract_key_phrases` | Returns `doc.key_phrases` |
| `recognize_entities` | Returns `doc.entities` |
| `detect_language` | Returns `doc.primary_language` |

---

## Content Understanding

### Q5. Suggest field schema for new form type 🔴
**Answer:** C) prebuilt-documentFieldSchema

**Why:** documentFieldSchema is the schema-proposal utility — discovers structure in new document types. documentFields extracts key-value pairs. prebuilt-invoice is for known invoice formats. documentSearch is for search/RAG.

---

### Q6. Scanned expense forms — OCR + field location/confidence ✓
**Answer:** A, B) enableOcr + estimateFieldSourceAndConfidence

**Why:** enableOcr reads image-based PDFs. estimateFieldSourceAndConfidence returns page number, bounding box, and confidence for extracted fields.

---

### Q14. Stable production behavior across API versions 🔴
**Answer:** B) Create a copy of the prebuilt analyzer and use the copy

**Why:** Microsoft warns that prebuilt analyzer definitions can change across API versions. Copying the analyzer locks in the definition for stable production use. Don't rely on prebuilt directly in production.

---

### Q29. Code: GenerationMethod for InvoiceNumber field 🔴
**Answer:** C) method=GenerationMethod.EXTRACT

**Why:** InvoiceNumber is a concrete value pulled from the document — use EXTRACT. GENERATE = derived/summary values. CLASSIFY = categorize into classes. enum defines allowed categories.

---

### Q36. Code: base_analyzer_id for custom business forms 🔴
**Answer:** A) prebuilt-document

**Why:** prebuilt-document is the base analyzer for custom document/form analyzers. prebuilt-image is for image analyzers. prebuilt-documentFields is a utility (extracts key-value pairs), NOT a base for custom analyzers.

---

### Q52. Extract structured invoice fields with minimal setup 🔴
**Answer:** C) prebuilt-invoice

**Why:** prebuilt-invoice is the domain-specific analyzer for invoices — extracts vendor name, dates, totals with minimal setup. Use the specialized analyzer when the document type is known.

---

### Q55. Code: analyzer_id for invoice extraction ✓
**Answer:** C) analyzer_id="prebuilt-invoice"

**Why:** For invoice extraction, use the purpose-built prebuilt-invoice analyzer. prebuilt-document is the base for custom analyzers. prebuilt-documentFieldSchema proposes schemas. prebuilt-documentFields extracts generic key-values.

---

### Q57. Pull loose key-value pairs from mixed forms (no predefined schema) 🔴
**Answer:** A) prebuilt-documentFields

**Why:** documentFields extracts key-value pairs without needing a predefined schema. prebuilt-invoice is domain-specific (too narrow for mixed forms). documentFieldSchema proposes schemas (doesn't extract values).

---

### Q59. Which THREE pairs correctly matched? 🔴
**Answer:** A, C, D) prebuilt-invoice extracts invoice data + documentFieldSchema proposes schema + enableOcr for scanned docs

**Why:** documentFields extracts key-value pairs — does NOT propose schemas (B wrong). estimateFieldSourceAndConfidence returns field location, NOT speaker diarization (E wrong). prebuilt-document is for custom document analyzers, NOT audio (F wrong).

---

### Q60. Yes/No: documentFieldSchema / estimateFieldSourceAndConfidence / documentFields for audio 🔴
**Answer:** A) Yes / Yes / No

**Why:** documentFieldSchema proposes field schemas (Yes). estimateFieldSourceAndConfidence returns page/bounding box/confidence (Yes). documentFields extracts document key-value pairs — NOT audio transcription (No).

---

### Content Understanding Key Takeaways

| Analyzer | Purpose |
|----------|---------|
| `prebuilt-invoice` | Domain-specific invoice extraction (vendor, date, total) |
| `prebuilt-document` | **Base** for custom document analyzers |
| `prebuilt-documentFields` | Extract key-value pairs from documents (utility) |
| `prebuilt-documentFieldSchema` | **Propose** field schema for new document types |
| `prebuilt-documentSearch` | Document content for search/RAG workflows |
| `prebuilt-image` | **Base** for custom image analyzers |

| Config Option | Purpose |
|---------------|---------|
| `enableOcr` | Read image-based PDFs and scanned documents |
| `estimateFieldSourceAndConfidence` | Return page number, bounding box, confidence for fields |

| GenerationMethod | When to Use |
|------------------|-------------|
| `EXTRACT` | Pull concrete value from document (InvoiceNumber, Name) |
| `GENERATE` | Derive a summary or computed value |
| `CLASSIFY` | Categorize into predefined classes |

| Critical Rule | Detail |
|---------------|--------|
| Copy prebuilt for production | Prebuilt definitions can change across API versions — copy for stability |
| Base vs utility | `prebuilt-document` = base for custom. `prebuilt-documentFields` = utility for extraction |

---

## Foundry Portal

### Q2. After opening deployed model in playground — which TWO? 🔴
**Answer:** C, D) Type a prompt and see outputs + Select the Code tab for programmatic access

**Why:** These are the two documented post-deployment playground actions. Endpoint keys are on the deployment details page (not playground). Marketplace subscription is a deployment prerequisite. TPM reallocation is in quota management.

---

### Q8. Code: model="ops-assistant" in responses.create() ✓
**Answer:** D) model="ops-assistant",

**Why:** Deployment name maps to the `model` parameter during inference. This is the documented routing field from the Code tab sample.

---

### Q31. Start new model deployment — which path? ✓
**Answer:** B) Discover → Models

**Why:** Microsoft's deployment guide says Discover → Models is the entry point for new deployments. Build → Models is for managing existing deployments.

---

### Q32. Benchmark models side by side 🔴
**Answer:** C) Compare models

**Why:** Compare mode in the model playground runs synchronized input across up to 3 models for side-by-side evaluation. Agents playground is for agent prototyping. Metrics is for observability, not live comparison.

---

### Q33. Deployment status before treating as ready 🔴
**Answer:** D) Succeeded

**Why:** Microsoft's deployment guide says verify status shows "Succeeded" before using the deployment. Pending/Draft = incomplete. Running ≠ the documented ready state.

---

### Q34. Partner/community model prerequisites — which TWO? ✓
**Answer:** B, E) Cognitive Services Contributor role + Azure Marketplace subscription permissions

**Why:** Partner/community models specifically require Marketplace access and proper RBAC permissions. AI Search, tracing, and video playground are unrelated to deployment prerequisites.

---

### Q35. Code: "model": deployment_name in payload ✓
**Answer:** A) "model": deployment_name,

**Why:** Deployment name goes in the "model" field during inference. Same pattern across all API calls — model routes to the specific deployment.

---

### Q37. Yes/No: every model needs Marketplace / playground prompts / Code tab 🔴
**Answer:** C) No / Yes / Yes

**Why:** Only partner/community models need Marketplace — not ALL models (No). Playground supports prompt testing (Yes). Code tab shows programmatic access (Yes).

---

### Q38. Which banner toggle should be on? ✓
**Answer:** B) New Foundry

**Why:** Microsoft says ensure "New Foundry" toggle is on for current portal steps. AgentOps = tracing feature. Global Standard = deployment type. Compare models = playground feature.

---

### Q48. Which THREE pairs correctly matched? 🔴
**Answer:** B, D, F) Discover→Models for deployment + Deployment details page for endpoint keys + Code tab for programmatic access

**Why:** New Foundry toggle is for current portal (not classic — A wrong). Build→Models manages existing deployments, not Marketplace subscription (C wrong). Video playground is for video models only, not every text model (E wrong).

---

### Foundry Portal Key Takeaways

| Portal Path | Purpose |
|-------------|---------|
| Discover → Models | Start a **new** model deployment |
| Build → Models | Manage **existing** deployments |
| Playground | Type prompts, see outputs, test models |
| Code tab | View programmatic access details |
| Deployment details page | View endpoint details and keys |
| Compare models | Side-by-side model benchmarking (up to 3) |

| Key Fact | Detail |
|----------|--------|
| New Foundry toggle | Must be ON for current portal steps |
| Deployment ready state | Status must show **Succeeded** |
| Partner/community models | Need Marketplace subscription + Cognitive Services Contributor role |
| Azure-sold models | Do NOT need Marketplace subscription |

---

## Multimodal Audio

### Q25. What is audio_url? ✓
**Answer:** C) Lets the model read audio from an accessible cloud location

**Why:** audio_url is for URL-based audio input from cloud storage. It doesn't request spoken output (that's modalities), doesn't deploy models, and doesn't record microphone input.

---

### Q39. Test spoken prompts without code? ✓
**Answer:** B) Chat playground

**Why:** Chat playground lets you record audio prompts, attach audio files, and enter text prompts. Microsoft directs you to Chat playground for gpt-4o-mini-audio-preview testing.

---

### Q40. Code: inline audio data structure 🔴
**Answer:** D) {"type": "input_audio", "input_audio": {"data": encoded_string, "format": "wav"}}

**Why:** Inline audio uses `input_audio` type with nested data + format. `audio_url` is for cloud-hosted files by URL (not inline). `audio` and `speech_input` are fake types.

---

### Q41. Spoken prompt + spoken answer — which TWO? ✓
**Answer:** C, E) input_audio in user content + modalities=["text", "audio"]

**Why:** input_audio sends the spoken prompt. modalities=["text", "audio"] requests spoken output. image_url is for images. OCR is for documents. Agent memory is for agent workflows.

---

### Q43. Audio at cloud location — content type? ✓
**Answer:** C) audio_url

**Why:** Cloud-hosted audio uses `audio_url` type. `input_audio` is for inline encoded data. `input_voice` and `speech_url` are not real field names.

---

### Q44. Yes/No: audio modality in chat completions / Chat playground recording / Audio playground for gpt-4o-mini ✓
**Answer:** A) Yes / Yes / No

**Why:** Audio extends existing chat completions API (Yes). Chat playground supports audio recording (Yes). Audio playground does NOT support gpt-4o-mini-audio-preview — use Chat playground (No).

---

### Q45. Prerequisite for chat completions with audio 🔴
**Answer:** D) A chat completions model deployment with support for audio and images

**Why:** You need a deployed model that supports audio/image modalities. AI Search, OCR training, and Foundry Agent Service are not prerequisites for basic multimodal chat.

---

### Q46. Which THREE pairs correctly matched? 🔴
**Answer:** B, D, E) audio_url for cloud audio + modalities for text+audio response + input_audio for inline encoded data

**Why:** input_audio is for inline data, NOT URL references (A wrong — swaps roles). Chat playground tests models, doesn't deploy them (C wrong). Audio playground does NOT support gpt-4o-mini-audio-preview (F wrong).

---

### Q47. Code: request spoken audio output ✓
**Answer:** B) modalities=["text", "audio"], audio={"voice": "alloy", "format": "wav"},

**Why:** Spoken output needs BOTH modalities=["text", "audio"] AND audio config with voice+format. modalities=["text"] is text-only. audio alone without modalities is incomplete.

---

### Q49. Which TWO actions for spoken prompt? 🔴
**Answer:** B, D) Add input_audio content item with data and format + Add a text content item to guide the model

**Why:** input_audio sends encoded audio. Text items provide instructions alongside audio. image_url is for images (not audio). OCR is for document text extraction. Audio format doesn't go in model name.

---

### Multimodal Audio Key Takeaways

| Input Method | Type | Use When |
|-------------|------|----------|
| `input_audio` | Inline encoded data | Audio bytes sent directly in request |
| `audio_url` | Cloud-hosted URL | Audio file at accessible cloud location |
| Text content item | Text instruction | Guide model on how to handle audio |

| Output Setting | Purpose |
|----------------|---------|
| `modalities=["text", "audio"]` | Request spoken audio + text response |
| `audio={"voice": "alloy", "format": "wav"}` | Configure voice and audio format |

| Key Rule | Detail |
|----------|--------|
| Chat playground for audio testing | Use Chat playground, NOT Audio playground for gpt-4o-mini-audio-preview |
| Prerequisite | Need a chat completions model deployment with audio/image support |
| Input vs output | Input audio = message content. Output audio = response settings (modalities + audio) |
| input_audio ≠ audio_url | Inline data vs URL reference — don't swap them |

---

## Master Cheat Sheet — Weakest Areas

### Content Understanding Analyzers (6/10 incorrect)

```
prebuilt-invoice         → Known invoice extraction (minimal setup)
prebuilt-document        → BASE for custom document analyzers
prebuilt-documentFields  → Extract key-value pairs (utility)
prebuilt-documentFieldSchema → PROPOSE schema for new doc types
prebuilt-documentSearch  → Document content for search/RAG
prebuilt-image           → BASE for custom image analyzers

enableOcr                → Read scanned PDFs / image-based docs
estimateFieldSourceAndConfidence → Page number + bounding box + confidence

GenerationMethod.EXTRACT  → Pull concrete value (InvoiceNumber)
GenerationMethod.GENERATE → Derive summary/computed value
GenerationMethod.CLASSIFY → Categorize into classes

CRITICAL: Copy prebuilt analyzer for production — definitions can change across API versions!
```

### Audio Input/Output (4/10 incorrect)

```
INPUT:  input_audio  → inline encoded data  ({"type": "input_audio", "input_audio": {"data": ..., "format": "wav"}})
INPUT:  audio_url    → cloud-hosted URL      ({"type": "audio_url", "audio_url": {"url": "https://..."}})
OUTPUT: modalities=["text", "audio"] + audio={"voice": "alloy", "format": "wav"}

Chat playground = test audio models (NOT Audio playground for gpt-4o-mini-audio-preview)
```

### Principle Matching Traps

```
Accountability: assign owners, audit trails, document approvals, governance sign-off, human review
Transparency:   explain predictions, make behavior understandable, disclose limitations
Fairness:       equitable treatment, representative data, compare outcomes across groups
Privacy/Security: encryption, RBAC, access control, data protection
Inclusiveness:  accessible design, screen readers, keyboard navigation, multilingual support
Reliability:    consistent behavior, testing under unexpected conditions, safe operation
```
