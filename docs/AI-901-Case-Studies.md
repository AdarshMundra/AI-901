# AI-901 Case Study Questions

All case study / scenario-based questions from Tests 1–6.  
4 unique case studies, 20 questions total.  
🔴 = You answered incorrectly

---

## Table of Contents
1. [Case Study 1: Verdant Arc — Agricultural AI](#case-study-1-verdant-arc--agricultural-ai) (Test 1 Q61–65 = Test 6 Q61–65)
2. [Case Study 2: Cedarbridge — Education AI](#case-study-2-cedarbridge--education-ai) (Test 3 Q63–67)
3. [Case Study 3: SignalFrame — Broadcast Production](#case-study-3-signalframe--broadcast-production) (Test 4 Q61–65)
4. [Case Study 4: Solstice — Utility / Energy AI](#case-study-4-solstice--utility--energy-ai) (Test 5 Q51–55)

---

## Case Study 1: Verdant Arc — Agricultural AI

**Source:** Test 1 Q61–65 | Test 6 Q61–65 (identical)

### Background

Verdant Arc is an agribusiness that uses AI models to manage greenhouse operations, crop management, and farm recommendations. The company has multiple requirements spanning monitoring, agent tools, document translation, image processing, and structured data extraction from photographs.

**Requirements referenced:** E1–E5, BR1–BR5, TR1–TR5, C1–C5

---

### Q1. Sensor data has shifted — which monitoring signal detects this? 🔴

**Scenario:**  
Verdant Arc replaces the electrical-conductivity sensors at one farm. The new sensors consistently report values that are **18% higher** than the values produced by the sensors represented in the training data. The model continues to return high-confidence recommendations. Verdant Arc must detect this change before recommendations are presented for approval.

**Options:**
- A) Feature attribution
- B) Cohort fairness
- C) Endpoint latency
- D) Data drift

**Answer:** D) Data drift

**Explanation:**  
The new sensors produce values that are systematically different from the training data distribution — this is the textbook definition of **data drift**. Even though the model still returns high-confidence predictions, the input data has fundamentally shifted, making those predictions unreliable.

**Why the others are wrong:**
- **Feature attribution** tells you which features drive predictions — it doesn't detect distribution shifts in input data
- **Cohort fairness** checks whether the model treats different groups equitably — not about sensor calibration
- **Endpoint latency** monitors response time — has nothing to do with data values changing

---

### Q2. An Azure Function calculates nutrient recipes — which agent tool?

**Scenario:**  
The existing Azure Function uses an Azure Storage queue trigger. It reads the farm, crop, growth stage, and sensor values from an input message. When processing finishes, the function writes the calculated nutrient recipe to an output queue. The agent must submit the calculation request and continue the conversation after the result becomes available.

**Options:**
- A) Code Interpreter
- B) Azure Functions tool
- C) OpenAPI tool
- D) File Search

**Answer:** B) Azure Functions tool

**Explanation:**  
The scenario explicitly describes an **existing Azure Function** with queue trigger input/output. The Azure Functions agent tool is designed exactly for this — it lets the agent invoke an existing Azure Function, submit the request, and continue the conversation once the result returns.

**Why the others are wrong:**
- **Code Interpreter** runs sandboxed Python code — it can't call external Azure Functions
- **OpenAPI tool** calls REST APIs defined by an OpenAPI spec — the function uses queue triggers, not HTTP
- **File Search** retrieves content from uploaded files — not relevant to computation

---

### Q3. Translate a Dutch DOCX to English — which operation? 🔴

**Scenario:**  
An employee uploads one Dutch DOCX guide. The application must:
- Translate the guide into English
- Apply the approved agronomy glossary
- Preserve the original document structure and formatting
- Return the translated DOCX directly in the response
- **Avoid using source and target storage containers**

**Options:**
- A) Synchronous document translation
- B) Asynchronous document translation
- C) Text translation
- D) Custom Translator training

**Answer:** A) Synchronous document translation

**Explanation:**  
The key requirement is **"avoid using source and target storage containers"** and **"return the translated DOCX directly in the response."** Synchronous document translation processes a single document in one API call and returns the result inline — no blob storage needed.

**Why the others are wrong:**
- **Asynchronous document translation** requires source and target Azure Blob Storage containers — the scenario explicitly says to avoid this
- **Text translation** works on plain text strings, not DOCX files — it can't preserve document formatting
- **Custom Translator training** is for building a custom translation model — the glossary can be applied without full model training

> **Key Rule:** Single file + no storage containers + inline response = **Synchronous**. Batch files + storage containers = **Asynchronous**.

---

### Q4. Smart-crop a thumbnail — which API parameter? 🔴

**Scenario:**  
The application calls the Azure Vision Generate Thumbnail API:
```
POST {endpoint}/vision/v3.2/generateThumbnail
    ?width=600
    &height=600
    &(MISSING CONFIG)
```
The returned image must preserve the most important crop region without requiring employees to define crop coordinates.

**Options:**
- A) smartCropping=false
- B) detectOrientation=true
- C) smartCropping=true
- D) visualFeatures=objects

**Answer:** C) smartCropping=true

**Explanation:**  
`smartCropping=true` enables content-aware cropping that automatically identifies the region of interest and preserves it in the thumbnail. This is exactly what the scenario asks for — intelligent cropping without manual coordinate input.

**Why the others are wrong:**
- **smartCropping=false** disables intelligent cropping — produces a naive center crop
- **detectOrientation=true** only detects image rotation — doesn't affect crop region selection
- **visualFeatures=objects** belongs to the Image Analysis API, not the Generate Thumbnail API

---

### Q5. Extract structured JSON from varied photographs — which component? 🔴

**Scenario:**  
The control-panel and crop-card photographs vary in layout. Some field values appear on digital displays, some beside printed labels, and others are handwritten. The application must return these JSON fields:
- greenhouseId, cropBatch, pH, electricalConductivity
- temperature, recordedAction, observationTime

**Options:**
- A) Azure Vision Read
- B) Multimodal model prompt
- C) Prebuilt image analyzer
- D) Custom image analyzer

**Answer:** D) Custom image analyzer

**Explanation:**  
The scenario requires **structured JSON output with specific named fields** from images with varying layouts. A **custom image analyzer** (Content Understanding) lets you define a field schema (greenhouseId, cropBatch, pH, etc.) and inherits from `prebuilt-image` to handle diverse image formats.

**Why the others are wrong:**
- **Azure Vision Read** extracts raw OCR text — it doesn't produce structured JSON fields
- **Multimodal model prompt** can describe images but doesn't guarantee consistent schema-defined JSON output across varied layouts
- **Prebuilt image analyzer** (`prebuilt-imageSearch`) generates descriptions/search data — it doesn't support custom field schemas

> **Key Rule:** Need specific named JSON fields from varied images → **Custom image analyzer**. Need general description → Multimodal model or prebuilt analyzer.

---

## Case Study 2: Cedarbridge — Education AI

**Source:** Test 3 Q63–67

### Background

Cedarbridge is an educational institution building an AI-based intelligent tutoring assistant. The system needs to handle accessibility, event data analysis, PII redaction, campus image analysis, and grant document processing.

**Requirements referenced:** E5, BR1, TR1 and others

---

### Q6. Accessibility checks pass but need more evidence — which activity?

**Scenario:**  
Automated accessibility checks confirm that the assistant interface includes labels for interactive controls. The project manager wants **additional evidence** that students using supported assistive technologies can complete the full workflow successfully.

**Options:**
- A) Accessibility user testing
- B) Aggregate quality evaluation
- C) Adversarial prompt testing
- D) Model benchmark comparison

**Answer:** A) Accessibility user testing

**Explanation:**  
Automated checks verify that labels exist, but they can't confirm real users with assistive technologies can actually complete workflows end-to-end. **Accessibility user testing** involves real people with disabilities using the system to find usability barriers that automated tools miss.

**Why the others are wrong:**
- **Aggregate quality evaluation** measures model output quality (accuracy, relevance) — not UI accessibility
- **Adversarial prompt testing** checks for prompt injection and harmful outputs — unrelated to assistive technology
- **Model benchmark comparison** compares model performance metrics — doesn't test user interaction

---

### Q7. An event coordinator needs data analysis and a chart — which agent tool?

**Scenario:**  
An event coordinator uploads a CSV file containing room capacity, registrations, actual attendance, and accessibility-seat usage. The coordinator asks the agent to:
- Calculate the 90th-percentile attendance rate
- Identify rooms exceeding 85% capacity
- Compare registrations with actual attendance
- Generate a chart as a PNG file

**Options:**
- A) File Search
- B) OpenAPI tool
- C) Code Interpreter
- D) Web search

**Answer:** C) Code Interpreter

**Explanation:**  
The task requires **computational analysis** (percentile calculations, comparisons) and **file generation** (PNG chart). Code Interpreter runs sandboxed Python code that can process CSV data, perform calculations, and generate visual outputs like charts.

**Why the others are wrong:**
- **File Search** retrieves content from uploaded files but can't run calculations or generate charts
- **OpenAPI tool** calls external REST APIs — not needed for local data processing
- **Web search** searches the internet — the data is in the uploaded CSV, not online

> **Key Rule:** Computation + file generation → **Code Interpreter**. Content retrieval from documents → **File Search**. External API calls → **OpenAPI tool**.

---

### Q8. Redact PII from support conversation text — which capability? 🔴

**Scenario:**  
Each completed support conversation is converted into **one raw text string** before being passed to the processing application. The application must synchronously return a redacted version of that string and metadata describing every detected sensitive entity.

**Options:**
- A) Key phrase extraction
- B) Text PII redaction
- C) Conversation PII redaction
- D) Sentiment analysis

**Answer:** B) Text PII redaction

**Explanation:**  
The input is described as **"one raw text string"** — not a structured conversation with speaker turns. **Text PII redaction** processes unstructured text, identifies sensitive entities, and returns a redacted version. It works synchronously and includes entity metadata.

**Why the others are wrong:**
- **Key phrase extraction** identifies topics/themes — doesn't redact sensitive data
- **Conversation PII redaction** requires structured conversation format with speaker roles — the scenario says it's been converted to a single raw text string
- **Sentiment analysis** returns tone labels — doesn't redact anything

> **Key Rule:** Raw text string → **Text PII redaction**. Structured conversation with turns → **Conversation PII redaction**.

---

### Q9. Caption + OCR from campus photos — which API features? 🔴

**Scenario:**  
The application already sets language to English and enables gender-neutral captions. It must complete the Image Analysis 4.0 request so that it returns:
- One sentence describing the complete photograph
- Structured OCR results for visible signs and room numbers

**Options:**
- A) features=denseCaptions,objects
- B) features=read,tags
- C) features=caption,smartCrops
- D) features=caption,read

**Answer:** D) features=caption,read

**Explanation:**  
- **caption** = one-sentence description of the entire image (exactly what's needed)
- **read** = structured OCR to extract text from signs and room numbers

**Why the others are wrong:**
- **denseCaptions** generates multiple region-level captions, not one overall sentence
- **objects** detects object bounding boxes — not text extraction
- **tags** returns keywords — not structured OCR text
- **smartCrops** generates crop regions for thumbnails — not relevant

> **Key Rule:** "One sentence describing the image" = **caption**. "Multiple region descriptions" = **denseCaptions**. "Extract text" = **read**.

---

### Q10. Process grant documents with varying layouts — which component? 🔴

**Scenario:**  
The extraction component must process grant files with varying layouts and return:
- Structure-preserving Markdown
- A common JSON schema
- Applicant and institution details
- Requested funding and budget items
- Ethics and governance information
- Project milestones and dates
- Supporting evidence from tables and narrative text

**Options:**
- A) Prebuilt document analyzer
- B) Azure Vision Read model
- C) Content Understanding analyzer
- D) Foundry prompt agent workflow

**Answer:** C) Content Understanding analyzer

**Explanation:**  
The requirements demand **structured field extraction** (specific named fields), **Markdown output**, and handling **varied document layouts**. Content Understanding analyzers support custom field schemas, return both markdown and JSON fields, and handle varied document formats through a single reusable configuration.

**Why the others are wrong:**
- **Prebuilt document analyzer** handles known formats (invoices, receipts) but can't define a custom schema for grant-specific fields like "ethics information" or "project milestones"
- **Azure Vision Read** extracts raw OCR text — no structured fields, no JSON schema
- **Foundry prompt agent workflow** orchestrates multi-step tasks — it's not a document extraction component

> **Key Rule:** Custom fields + varied layouts + structured output → **Content Understanding analyzer**. Known document types (invoice, receipt) → **Prebuilt analyzer**.

---

## Case Study 3: SignalFrame — Broadcast Production

**Source:** Test 4 Q61–65

### Background

SignalFrame is a broadcast production system that uses AI for emergency announcement detection, real-time research, live studio interaction, image generation, and video content analysis.

**Requirements referenced:** E1–E5, BR1–BR5, TR1–TR5, C1–C5

---

### Q11. A model is 98% accurate — should it auto-publish at 95% confidence? 🔴

**Scenario:**  
SignalFrame's urgency model correctly identifies 98% of emergency announcements. Management proposes **automatically interrupting broadcasts** when model confidence exceeds 95%.

**Options:**
- A) Mandatory editorial approval
- B) Automatic publication above confidence threshold
- C) Weekly aggregate accuracy review
- D) Anonymous audience feedback collection

**Answer:** A) Mandatory editorial approval

**Explanation:**  
Even at 98% accuracy, automatically interrupting live broadcasts is **high-risk** — a false positive could cause public panic or misinformation. The **Reliability & Safety** and **Accountability** principles of Responsible AI require human oversight for high-stakes decisions. A human editor must approve before interrupting broadcasts.

**Why the others are wrong:**
- **Automatic publication** removes human oversight for a safety-critical action — exactly what Responsible AI warns against
- **Weekly aggregate review** is too slow — by the time you review, wrong broadcasts have already aired
- **Anonymous audience feedback** is reactive, not preventive — damage is already done

> **Key Rule:** High-stakes, irreversible actions (broadcast interruption, medical decisions, safety alerts) → **Always require human approval**, regardless of model confidence.

---

### Q12. Agent needs real-time public government warnings — which tool?

**Scenario:**  
A researcher asks the agent: "What public warnings has the Australian Government issued about the current cyclone, and when was each warning published?" The agent must retrieve **recently published public information** and include citations.

**Options:**
- A) Azure AI Search
- B) File Search
- C) Web search
- D) Code Interpreter

**Answer:** C) Web search

**Explanation:**  
The query asks for **recently published public information** from a government website — this is live, real-time data that wouldn't be in any pre-indexed document store. Web search lets the agent search the internet for current information and return results with citations.

**Why the others are wrong:**
- **Azure AI Search** searches a pre-indexed knowledge base — government warnings wouldn't be pre-loaded
- **File Search** retrieves from uploaded project files — not public web content
- **Code Interpreter** runs Python code — can't browse the internet

> **Key Rule:** Real-time public information → **Web search**. Pre-uploaded internal docs → **File Search**. Pre-indexed enterprise data → **Azure AI Search**.

---

### Q13. Stream spoken Q&A during live broadcast — which interface? 🔴

**Scenario:**  
During a live programme, a presenter asks the studio assistant a spoken question. The application must **stream microphone audio** to the deployed model and **begin playing the model's spoken response before the complete response has been generated**.

**Options:**
- A) Azure Speech batch transcription
- B) GPT Realtime API
- C) GPT-image-1 deployment
- D) Text-embedding deployment

**Answer:** B) GPT Realtime API

**Explanation:**  
The scenario requires **speech-in → speech-out in real-time** with streaming (response starts playing before it's fully generated). The **GPT Realtime API** combines speech recognition, generative AI reasoning, and speech synthesis into a single low-latency streaming interface — exactly what live broadcast needs.

**Why the others are wrong:**
- **Azure Speech batch transcription** processes pre-recorded audio files — not real-time streaming
- **GPT-image-1** generates images from text — wrong modality entirely
- **Text-embedding** converts text to vectors for search — can't process or produce speech

> **Key Rule:** Live speech-in/speech-out streaming → **GPT Realtime API**. Pre-recorded audio → **Batch transcription**. Single utterance → **recognize_once_async**.

---

### Q14. Create a transparent PNG graphic from a logo — which model?

**Scenario:**  
A designer provides a programme logo and the instruction: "Create a new lower-third graphic using the supplied logo, a transparent background, and space for a presenter's name." The result must be returned as a PNG file.

**Options:**
- A) gpt-realtime
- B) gpt-4.1
- C) text-embedding-3-large
- D) gpt-image-1

**Answer:** D) gpt-image-1

**Explanation:**  
The task requires **image generation** with a transparent background and PNG output. **GPT-image-1** is the image generation model that supports `background="transparent"` and `output_format="png"`.

**Why the others are wrong:**
- **gpt-realtime** is for real-time speech interaction — can't generate images
- **gpt-4.1** is a text/chat model — can't create images
- **text-embedding-3-large** creates vector embeddings — can't generate any content

---

### Q15. Analyze recorded broadcasts into structured segments — which component?

**Scenario:**  
Each recorded broadcast must be divided according to individual news stories. For every story, the solution must return:
- Start/end time
- Speaker-labelled transcript phrases
- Headline, summary
- People mentioned, locations mentioned
- Editorial risk rating

**Options:**
- A) Content Understanding video analyzer
- B) Azure AI Video Indexer account
- C) Azure Speech batch transcription job
- D) Azure Vision Image Analysis request

**Answer:** A) Content Understanding video analyzer

**Explanation:**  
The requirements demand **video segmentation** with **custom fields** (editorial risk rating) plus standard fields (transcript, timestamps, speakers). A **Content Understanding video analyzer** processes video into segments with speaker-labelled transcripts and supports custom field schemas for domain-specific outputs.

**Why the others are wrong:**
- **Azure AI Video Indexer** provides pre-defined video insights but doesn't support custom field schemas like "editorial risk rating"
- **Azure Speech batch transcription** only handles audio-to-text — no video segmentation, no custom fields
- **Azure Vision Image Analysis** processes still images, not video

---

## Case Study 4: Solstice — Utility / Energy AI

**Source:** Test 5 Q51–55

### Background

Solstice is a utility/energy company using AI for outage management, customer service, and field operations. The system handles customer data, agent authentication, feedback analysis, drone image analysis, and call center audio processing.

---

### Q16. Telemetry logs contain customer PII — which practice? 🔴

**Scenario:**  
During pilot testing, Solstice records every model input in Application Insights. The records include customer names, addresses, account numbers, medical-device registrations, model latency, and predicted outage priority. The operations team needs the performance information but does **not** require the direct customer information.

**Options:**
- A) Cohort fairness evaluation
- B) Confidence threshold automation
- C) Public transparency note
- D) Data minimisation

**Answer:** D) Data minimisation

**Explanation:**  
**Data minimisation** is the Responsible AI principle that requires collecting, processing, and retaining only the information necessary for the defined purpose. The ops team needs latency and model results — not customer names, addresses, or account numbers. Those should be excluded from telemetry.

**Why the others are wrong:**
- **Cohort fairness** checks whether the model treats different groups equitably — not about reducing stored data
- **Confidence threshold automation** sets decision boundaries for model outputs — unrelated to data collection
- **Public transparency note** communicates system capabilities to users — doesn't address data over-collection

> **Key Rule:** "Collecting more data than needed" → **Data minimisation**. "Model treats groups unfairly" → **Fairness**. "Users don't understand the system" → **Transparency**.

---

### Q17. MCP server uses OAuth with per-employee permissions — which auth?

**Scenario:**  
The MCP server uses OAuth 2.0 and enforces each employee's existing permissions. A control-room operator can read all active outages, while a customer-service employee can only access assigned accounts. When invoked for the first time, the agent must request consent. Subsequent calls use that employee's authorised identity.

**Options:**
- A) OAuth identity passthrough
- B) Project managed identity
- C) Agent identity
- D) API key connection

**Answer:** A) OAuth identity passthrough

**Explanation:**  
The scenario requires the agent to act **as the employee** — using their specific permissions, requesting their consent, and maintaining their identity across calls. **OAuth identity passthrough** forwards the employee's OAuth token to the MCP server, so the server enforces per-user permissions.

**Why the others are wrong:**
- **Project managed identity** uses a single shared identity — can't enforce per-employee permissions
- **Agent identity** gives the agent its own identity — not the employee's permissions
- **API key connection** provides one shared key — no per-user access control

> **Key Rule:** Per-user permissions + user consent → **OAuth identity passthrough**. Shared service-level access → **Managed identity**.

---

### Q18. Identify positive and negative sentiment about specific targets — which capability? 🔴

**Scenario:**  
A customer submits feedback: "The power returned earlier than expected, but the mobile-app notifications were confusing." Solstice must identify:
- **Positive** sentiment associated with the restoration time
- **Negative** sentiment associated with the mobile-app notifications

**Options:**
- A) Key phrase extraction
- B) Document sentiment analysis
- C) Opinion mining
- D) Custom named entity recognition

**Answer:** C) Opinion mining

**Explanation:**  
**Opinion mining** extends sentiment analysis by linking an expressed assessment (positive/negative) to the **specific target** being discussed. It can associate "positive" with "restoration time" and "negative" with "mobile-app notifications" — target-level sentiment, not just document-level.

**Why the others are wrong:**
- **Key phrase extraction** identifies topics but doesn't assign sentiment to them
- **Document sentiment analysis** returns one overall sentiment for the whole text — can't distinguish that restoration was positive while notifications were negative
- **Custom NER** identifies entity types — doesn't analyze sentiment

> **Key Rule:** "Overall tone of the text" → **Document sentiment**. "Sentiment about specific aspects/targets" → **Opinion mining**. Use `show_opinion_mining=True` with `analyze_sentiment()`.

---

### Q19. Detect people + OCR text from drone photos — which API features? 🔴

**Scenario:**  
The application submits each drone photograph to the Image Analysis 4.0 endpoint. The response must contain:
- A bounding box and confidence score for every detected **person**
- Structured OCR results for visible substation text

```
POST {endpoint}/computervision/imageanalysis:analyze
    ?api-version=2024-02-01
    &________
```

**Options:**
- A) features=objects,read
- B) features=people,read
- C) features=people,tags
- D) features=caption,read

**Answer:** B) features=people,read

**Explanation:**  
- **people** = dedicated people detection with bounding boxes and confidence scores
- **read** = OCR to extract structured text from visible signs/labels

**Why the others are wrong:**
- **objects** detects general objects — not the dedicated people detector (less accurate for person detection)
- **tags** returns keyword labels — not structured OCR text
- **caption** returns a sentence description — not person bounding boxes

> **Key Rule:** Need person detection specifically → use **people** (not objects). Need text extraction → use **read**.

---

### Q20. Process calls with custom fields + transcript — which component? 🔴

**Scenario:**  
Solstice requires one reusable configuration that returns:
- A transcript with speaker identification and timing
- A call summary
- Overall sentiment
- **Outage identifier** (custom)
- **Medical-equipment dependency** (custom)
- **Requested assistance** (custom)
- **Promised action** (custom)

The final four fields use Solstice-specific definitions.

**Options:**
- A) prebuilt-audioSearch
- B) prebuilt-callCenter
- C) Document-based custom analyzer
- D) Audio-based custom analyzer

**Answer:** D) Audio-based custom analyzer

**Explanation:**  
The scenario needs standard audio features (transcript, speaker ID, timing) **plus custom domain-specific fields** (outage ID, medical-equipment dependency). An **audio-based custom analyzer** inherits from `prebuilt-audio` for the standard features and adds a user-defined field schema for the four custom fields.

**Why the others are wrong:**
- **prebuilt-audioSearch** provides standard transcript/summary but doesn't support custom field schemas
- **prebuilt-callCenter** is not a documented prebuilt analyzer ID
- **Document-based custom analyzer** processes documents, not audio — wrong modality

> **Key Rule:** Standard features + custom fields → **Custom analyzer** (inherits from prebuilt base). Standard features only → **Prebuilt analyzer**.

---

## Key Patterns Across All Case Studies

| Pattern | Answer | Remember |
|---------|--------|----------|
| Input data distribution changed | **Data drift** | Sensors/data shifted from training distribution |
| Call existing Azure Function | **Azure Functions tool** | Queue trigger = Azure Functions, not OpenAPI |
| Single doc translation, no storage | **Synchronous translation** | Async needs blob storage containers |
| Content-aware thumbnail crop | **smartCropping=true** | Generate Thumbnail API parameter |
| Structured JSON from varied images | **Custom image analyzer** | Custom field schema + prebuilt-image base |
| Automated checks pass, need real proof | **Accessibility user testing** | Real users with assistive tech |
| Compute + generate charts from CSV | **Code Interpreter** | Runs Python, produces files |
| Raw text PII redaction | **Text PII redaction** | Conversation PII needs structured turns |
| One sentence + OCR | **features=caption,read** | caption = sentence, read = OCR |
| Varied docs + custom schema | **Content Understanding analyzer** | Not prebuilt (can't customize) |
| High-stakes auto-action | **Human approval required** | Never auto-publish safety-critical |
| Real-time public web info | **Web search** | Not File Search or AI Search |
| Live speech-in/speech-out streaming | **GPT Realtime API** | Not batch transcription |
| Image generation + transparency | **gpt-image-1** | output_format="png", background="transparent" |
| Video segments + custom fields | **Content Understanding video** | Not Video Indexer (no custom schema) |
| Excess PII in telemetry | **Data minimisation** | Collect only what's needed |
| Per-user OAuth permissions | **OAuth identity passthrough** | Not managed identity (shared) |
| Sentiment about specific targets | **Opinion mining** | Not document sentiment (one score) |
| People detection + OCR | **features=people,read** | people (not objects) for person detection |
| Audio + custom fields | **Audio-based custom analyzer** | Inherits prebuilt-audio + custom schema |
