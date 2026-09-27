# AI-901 Practice Exam: Computer Vision, Image Generation & Azure Content Understanding in Microsoft Foundry

**Total Questions: 55**
**Estimated Time: 70 minutes**
**Passing Score: 80% (44/55)**

Difficulty progression: Questions 1-18 (Easy), 19-38 (Medium), 39-55 (Hard)

---

## EASY (Questions 1-18)

---

**Question 1 (True/False)**
True or False: In Microsoft Foundry, computer vision capabilities use multimodal models like GPT-4o that accept both text and image input in a single request.

A) True
B) False

---

**Question 2 (Multiple Choice)**
Which API method is used to send an image for analysis with a multimodal model in Foundry?

A) `client.vision.analyze()`
B) `client.responses.create()`
C) `client.images.generate()`
D) `client.completions.create()`

---

**Question 3 (True/False)**
True or False: Azure Content Understanding can only process PDF documents and scanned forms.

A) True
B) False

---

**Question 4 (Multiple Correct Answers)**
Which of the following content types can Azure Content Understanding process? (Select ALL that apply)

A) Documents and forms
B) Audio files
C) Video files
D) Images
E) All of the above

---

**Question 5 (Compare & Contrast)**
What is the fundamental difference between multimodal vision and image generation in Foundry?

A) Multimodal vision generates images from text; image generation analyzes existing images
B) Multimodal vision analyzes existing images using text+image input; image generation creates new images from text prompts
C) They are the same capability accessed through different endpoints
D) Multimodal vision works only with URLs; image generation works only with base64 data

---

**Question 6 (Code Completion)**
Complete the missing input content to analyze an image using a multimodal model:

```python
response = client.responses.create(
    model="gpt-4o",
    input=[
        {"role": "user", "content": [
            ______________________________,
            {"type": "image_url", "image_url": {"url": image_url}}
        ]}
    ]
)
```

A) `{"type": "text", "text": "What's in this image?"}`
B) `{"type": "prompt", "prompt": "What's in this image?"}`
C) `{"type": "string", "value": "What's in this image?"}`
D) `{"type": "query", "query": "What's in this image?"}`

---

**Question 7 (When to Use What)**
A law firm needs to extract specific fields (client name, case number, filing date) from thousands of legal intake forms that all follow the same template. Which service is the best fit?

A) GPT-4o multimodal vision
B) Azure Content Understanding with a custom model
C) DALL-E image generation
D) Azure Speech service

---

**Question 8 (Matching)**
Match each task to the correct Foundry capability:

| Task | Capability |
|------|------------|
| 1. Create a product photo from a text description | A. Multimodal Vision (GPT-4o) |
| 2. Identify all objects in a security camera still frame | B. Image Generation (DALL-E) |
| 3. Extract invoice totals from scanned receipts | C. Azure Content Understanding |
| 4. Describe what is happening in a photograph | D. Video Generation |

A) 1-B, 2-A, 3-C, 4-A
B) 1-A, 2-B, 3-C, 4-D
C) 1-B, 2-C, 3-A, 4-D
D) 1-D, 2-A, 3-B, 4-C

---

**Question 9 (Multiple Choice)**
In which two formats can images be supplied to a multimodal model in Foundry?

A) File path and binary stream
B) URL and base64-encoded data
C) Blob storage reference and FTP link
D) SharePoint link and local file path

---

**Question 10 (Scenario-Based)**
A museum wants to build an app where visitors photograph an artwork and receive a detailed description including the artist's style, period, and subject matter. Which approach is most appropriate?

A) Train a custom Content Understanding model on art metadata
B) Use a multimodal model (GPT-4o) with a text prompt like "Describe the artistic style, period, and subject of this artwork"
C) Use DALL-E to generate a description of the artwork
D) Use Azure Speech to narrate the artwork details

---

**Question 11 (True/False)**
True or False: Foundry IQ is a retrieval-augmented generation (RAG) service that indexes enterprise content and generates citation-backed responses.

A) True
B) False

---

**Question 12 (Multiple Choice)**
What is the correct high-level pipeline for Foundry IQ?

A) Upload -> Train -> Deploy -> Predict
B) Ingest + Index -> Search + Ground -> Generate answer with citations
C) Collect -> Classify -> Summarize -> Store
D) Scan -> OCR -> Extract -> Export

---

**Question 13 (When to Use What)**
A company wants to let employees ask natural-language questions about internal HR policies scattered across 200+ PDFs in SharePoint. Which service fits best?

A) Azure Content Understanding to extract text from each PDF
B) GPT-4o multimodal vision to read each PDF page
C) Foundry IQ to ingest, index, and generate grounded answers from the PDFs
D) DALL-E to visualize the policies

---

**Question 14 (Multiple Choice)**
Which model family is commonly used for image generation (creating new images from text) in Foundry?

A) GPT-4o
B) DALL-E
C) Whisper
D) Florence

---

**Question 15 (True/False)**
True or False: When using multimodal vision, the model generates a new modified version of the input image.

A) True
B) False (the model returns text analysis about the image, not a new image)

---

**Question 16 (Multiple Choice)**
Azure Content Understanding returns extracted information in what format?

A) Unstructured plain text paragraphs
B) Structured key-value pairs, tables, and fields
C) Audio narration of the content
D) A re-created digital version of the original document

---

**Question 17 (Scenario-Based)**
A logistics company receives delivery confirmations as photos of signed paper slips. They need to extract the recipient name and signature date from each photo. Which service should they use?

A) Multimodal vision with GPT-4o
B) Azure Content Understanding
C) Image generation with DALL-E
D) Video Generation

---

**Question 18 (Multiple Choice)**
Which of the following can a multimodal model like GPT-4o do when given an image? (Select ALL that apply)

A) Describe the content of the image
B) Identify objects in the image
C) Read and extract text visible in the image
D) Answer specific questions about the image
E) All of the above

---

### ANSWERS: Questions 1-18

| # | Answer | Explanation |
|---|--------|-------------|
| 1 | **A (True)** | GPT-4o is a multimodal model that natively handles text + image input together in a single API call. |
| 2 | **B** | The same OpenAI Responses API `client.responses.create()` is used for both text-only and multimodal (text+image) requests. There is no separate vision endpoint. |
| 3 | **B (False)** | Content Understanding processes documents, forms, images, audio files, and video files -- not just documents. |
| 4 | **E** | Azure Content Understanding supports documents/forms, images, audio, and video -- all listed options are correct. |
| 5 | **B** | Multimodal vision analyzes existing images (image in, text out). Image generation creates new images (text in, image out). They are opposite directions. |
| 6 | **A** | The content array uses objects with `"type": "text"` for the text portion and `"type": "image_url"` for the image portion. |
| 7 | **B** | Content Understanding with a custom model is ideal for structured, repeatable extraction from templated forms. A custom model can be trained on the specific fields of the legal intake form. |
| 8 | **A** | Creating images = DALL-E (B); identifying objects = multimodal vision (A); extracting invoice data = Content Understanding (C); describing a photo = multimodal vision (A). |
| 9 | **B** | Multimodal models in Foundry accept images as either a URL or base64-encoded image data. |
| 10 | **B** | GPT-4o's multimodal capability can accept the photo and a descriptive prompt to return rich text analysis about art style, period, and subject. No custom training needed. |
| 11 | **A (True)** | Foundry IQ is Microsoft's RAG service that ingests enterprise content, indexes it, and produces grounded answers with citations. |
| 12 | **B** | Foundry IQ follows: Ingest + Index the content, then Search + Ground relevant passages, then Generate an answer with citations. |
| 13 | **C** | Foundry IQ is purpose-built for this: ingest enterprise PDFs from SharePoint, index them, and let users ask natural-language questions with citation-backed answers. |
| 14 | **B** | DALL-E is the model family used for text-to-image generation. GPT-4o is for text generation and multimodal analysis. |
| 15 | **B (False)** | Multimodal vision returns text-based analysis (descriptions, answers, extracted text). It does not output images. |
| 16 | **B** | Content Understanding returns structured output: key-value pairs, tables, and defined fields -- making it ready for downstream automation. |
| 17 | **B** | Azure Content Understanding is designed for extracting structured fields (name, date) from document-like images such as signed delivery slips. While GPT-4o could describe the image, Content Understanding provides reliable structured extraction. |
| 18 | **E** | Multimodal models can describe content, identify objects, read visible text (OCR-like), and answer questions -- all from a single image input. |

---

## MEDIUM (Questions 19-38)

---

**Question 19 (Bug Finding)**
This code is supposed to analyze an image but returns an error. What is wrong?

```python
response = client.responses.create(
    model="gpt-4o",
    input=[
        {"role": "user", "content": "What objects are in this image?"},
        {"role": "user", "content": {"type": "image_url", "image_url": {"url": photo_url}}}
    ]
)
```

A) The model name should be `"dall-e-3"` for image analysis
B) The content for a multimodal request must be a single list combining text and image items, not separate messages
C) The `image_url` key should be `image_path`
D) The role should be `"system"` for image inputs

---

**Question 20 (Architecture Design)**
A healthcare company wants to: (1) digitize patient intake forms, (2) extract medical history fields, (3) let doctors ask questions about a patient's records. Design the correct pipeline.

A) Content Understanding to extract fields -> Foundry IQ to index extracted data -> Multimodal model for doctor Q&A
B) DALL-E to scan forms -> GPT-4o to extract fields -> Speech service for doctor Q&A
C) Multimodal vision for all three steps
D) Content Understanding for all three steps

---

**Question 21 (Code Completion)**
Complete this code to send a base64-encoded image for analysis:

```python
import base64

with open("photo.jpg", "rb") as f:
    img_data = base64.b64encode(f.read()).decode("utf-8")

response = client.responses.create(
    model="gpt-4o",
    input=[
        {"role": "user", "content": [
            {"type": "text", "text": "Describe this image in detail."},
            {"type": "image_url", "image_url": {"url": ___________________________}}
        ]}
    ]
)
```

A) `img_data`
B) `f"data:image/jpeg;base64,{img_data}"`
C) `f"base64://{img_data}"`
D) `f"file://photo.jpg"`

---

**Question 22 (Edge Case)**
A user sends a very blurry, low-resolution photo to a multimodal model and asks "Read all the text on this sign." What is the most likely outcome?

A) The model will refuse the request entirely
B) The model will enhance the image first, then read the text
C) The model will attempt to read the text but may return partial, inaccurate, or uncertain results
D) The model will automatically upscale the image to improve readability

---

**Question 23 (Multi-Service Scenario)**
An insurance company receives claims as: (1) scanned paper forms, (2) photos of vehicle damage, (3) recorded phone statements. They want to automate the entire intake process. Which combination of services is needed?

A) Content Understanding for forms + Multimodal vision for damage photos + Azure Speech for audio transcription
B) GPT-4o for everything
C) DALL-E for forms + Content Understanding for photos + Video Generation for audio
D) Foundry IQ for all three content types

---

**Question 24 (Compare & Contrast)**
How do pre-built and custom models in Azure Content Understanding differ?

A) Pre-built models require training data; custom models do not
B) Pre-built models handle common document types (invoices, receipts, IDs) out of the box; custom models are trained on your specific document layouts
C) Pre-built models are free; custom models require an Enterprise license
D) There is no difference; all models are custom

---

**Question 25 (Data Interpretation)**
Azure Content Understanding processes a receipt and returns this output:

```json
{
  "merchant_name": "Corner Cafe",
  "transaction_date": "2026-03-15",
  "items": [
    {"description": "Latte", "amount": 5.50},
    {"description": "Croissant", "amount": 3.75}
  ],
  "total": 9.25,
  "payment_method": "Visa ending 4821"
}
```

Which statement is TRUE about this output?

A) The service generated this receipt image from structured data
B) The service extracted structured key-value pairs and a table of line items from the receipt image
C) The service translated the receipt into another language
D) The service used DALL-E to recreate the receipt digitally

---

**Question 26 (Order the Steps)**
What is the correct order for building a document processing pipeline with Azure Content Understanding?

1. Deploy the custom model
2. Label training documents with the fields you want to extract
3. Collect sample documents representing your form layout
4. Test extraction accuracy on held-out documents
5. Train the custom model

A) 3 -> 2 -> 5 -> 4 -> 1
B) 2 -> 3 -> 5 -> 1 -> 4
C) 5 -> 3 -> 2 -> 4 -> 1
D) 3 -> 5 -> 2 -> 1 -> 4

---

**Question 27 (Scenario-Based)**
A retail chain has 500 stores and wants shelf cameras to detect when products are out of stock. Each camera sends a still image every 10 minutes. Which approach is most appropriate?

A) Use DALL-E to generate images of what full shelves should look like and compare
B) Use Content Understanding to extract product labels from shelf images
C) Use a multimodal model with a prompt like "Identify any empty shelf sections or missing products in this image" for each camera frame
D) Use Video Generation to predict what the shelf will look like next

---

**Question 28 (Bug Finding)**
This code is supposed to generate a new image, but it is using the wrong approach. What is the issue?

```python
response = client.responses.create(
    model="gpt-4o",
    input=[
        {"role": "user", "content": [
            {"type": "text", "text": "Generate a photo of a sunset over mountains."}
        ]}
    ]
)
```

A) The prompt is too vague for image generation
B) GPT-4o is a multimodal analysis model, not an image generation model; DALL-E should be used for generating images
C) The content should use `"type": "image_prompt"` instead of `"type": "text"`
D) The input format is wrong; it should be a simple string, not a content list

---

**Question 29 (When to Use What)**
A researcher has 10,000 handwritten historical letters and wants to convert them to searchable digital text. Which service is most appropriate?

A) GPT-4o multimodal vision (send each page image with "Transcribe this handwritten text")
B) Azure Content Understanding (extract text from document images)
C) DALL-E (recreate the letters digitally)
D) Either A or B could work, but B is more efficient for batch processing of structured extraction at scale

---

**Question 30 (True/False)**
True or False: Foundry IQ generates answers purely from the language model's training data without referencing the indexed enterprise content.

A) True
B) False

---

**Question 31 (Scenario-Based)**
A city government wants to process building permit applications that arrive as: scanned blueprints (images), filled PDF forms, and applicant ID photos. They need to extract applicant info, permit type, and verify the ID matches the applicant name. Which pipeline is correct?

A) Content Understanding for PDF forms and ID extraction -> Multimodal vision to analyze blueprints -> Custom logic to cross-reference applicant name with ID
B) Multimodal vision for everything with no additional services
C) Foundry IQ to answer questions about the permits
D) Image generation to recreate the blueprints digitally

---

**Question 32 (Code Completion)**
A developer wants to ask a question about two images at once. Complete the input:

```python
response = client.responses.create(
    model="gpt-4o",
    input=[
        {"role": "user", "content": [
            {"type": "text", "text": "What are the differences between these two images?"},
            ___________________________,
            ___________________________
        ]}
    ]
)
```

A) `{"type": "image_url", "image_url": {"url": url1}}, {"type": "image_url", "image_url": {"url": url2}}`
B) `{"type": "images", "urls": [url1, url2]}`
C) `{"type": "image_pair", "image1": url1, "image2": url2}`
D) `{"type": "image_url", "image_url": {"urls": [url1, url2]}}`

---

**Question 33 (Edge Case)**
A multinational corporation sends invoices in 15 different languages to Azure Content Understanding. What should they consider?

A) They must create 15 separate Content Understanding models, one per language
B) Pre-built invoice models support multiple languages; they should verify their languages are supported and consider custom models for any unsupported ones
C) Content Understanding only works with English documents
D) They must translate all invoices to English before processing

---

**Question 34 (RAG / Foundry IQ)**
An employee asks Foundry IQ: "What is our company's parental leave policy?" The system retrieves relevant passages from the employee handbook and generates a response. What ensures the answer is trustworthy?

A) The model's training data includes general HR knowledge
B) Foundry IQ provides citations back to the specific source documents so the answer can be verified
C) The answer is always 100% accurate because it uses RAG
D) A human reviews every response before it is shown

---

**Question 35 (Compare & Contrast)**
When should you choose Azure Content Understanding over a multimodal model (GPT-4o) for reading a document?

A) When you need creative, open-ended descriptions of document content
B) When you need reliable, structured field extraction (specific key-value pairs) from standardized document types at scale
C) When you want to ask freeform questions about what the document shows
D) When the document contains only images with no text

---

**Question 36 (Multi-Service Scenario)**
An e-commerce company wants to: (1) auto-generate product images from descriptions, (2) let customers upload photos to search for similar products, (3) automatically extract product specs from manufacturer datasheets. Map each need to the correct service.

A) 1-DALL-E, 2-Multimodal Vision, 3-Content Understanding
B) 1-GPT-4o, 2-DALL-E, 3-GPT-4o
C) 1-Content Understanding, 2-DALL-E, 3-Multimodal Vision
D) 1-Multimodal Vision, 2-Content Understanding, 3-DALL-E

---

**Question 37 (Scenario-Based)**
A news agency wants to auto-caption breaking news photos for accessibility. Editors upload a photo and need an immediate natural-language description. Which approach is best?

A) Train a custom Content Understanding model on news photos
B) Use DALL-E to recreate the photo with a caption overlay
C) Use GPT-4o multimodal model with a prompt like "Write an accessible alt-text description of this news photo"
D) Use Foundry IQ to search for descriptions of similar past photos

---

**Question 38 (Architecture Design)**
Design a pipeline where customers email photos of damaged products, and the system (1) extracts the order number from the email, (2) assesses the damage in the photo, (3) auto-generates a replacement order if damage is confirmed.

A) Content Understanding for email parsing -> Multimodal vision for damage assessment -> Business logic for replacement order
B) Multimodal vision for everything including order creation
C) DALL-E to generate a repaired product image -> Content Understanding to compare
D) Foundry IQ to search for similar damage reports

---

### ANSWERS: Questions 19-38

| # | Answer | Explanation |
|---|--------|-------------|
| 19 | **B** | For multimodal input, the text and image must be combined in a single `content` list within one message. Two separate user messages -- one with text and one with an image object -- is not the correct format. The correct format is: `"content": [{"type": "text", ...}, {"type": "image_url", ...}]` in one message. |
| 20 | **A** | This is a multi-service pipeline: Content Understanding excels at structured extraction from forms, Foundry IQ indexes the extracted data for RAG, and a multimodal model or Foundry IQ allows doctors to query patient records. |
| 21 | **B** | Base64-encoded images must use a data URI format: `data:image/jpeg;base64,{base64_string}`. Simply passing the raw base64 string or a file path will not work. |
| 22 | **C** | Multimodal models attempt to process whatever image they receive. With poor quality input, the model may return partial or uncertain results rather than refusing entirely. It cannot enhance or upscale the image. |
| 23 | **A** | Each content type maps to a specialized service: Content Understanding for structured form extraction, multimodal vision for analyzing damage photos, and Azure Speech for transcribing audio statements. |
| 24 | **B** | Pre-built models handle common document types (invoices, receipts, IDs) without any training. Custom models require you to provide labeled training data for your specific document layouts. |
| 25 | **B** | The JSON output shows structured key-value pairs (merchant name, date, total, payment method) and a table of line items -- this is what Content Understanding extracts from document/receipt images. |
| 26 | **A** | The correct order is: Collect samples (3) -> Label fields (2) -> Train model (5) -> Test accuracy (4) -> Deploy (1). You cannot label without samples, cannot train without labels, and should not deploy without testing. |
| 27 | **C** | A multimodal model with a specific prompt can analyze each shelf image and identify empty sections. This is an image analysis task (not generation, not structured document extraction). |
| 28 | **B** | GPT-4o analyzes images and generates text responses. To generate new images from text descriptions, you must use DALL-E. Sending a "generate an image" prompt to GPT-4o will produce a text description, not an actual image. |
| 29 | **D** | Both can handle handwritten text. GPT-4o multimodal can transcribe handwriting from images. Content Understanding can also extract text. For 10,000 documents at scale, Content Understanding's batch processing and structured output pipelines are more efficient, but both are viable. |
| 30 | **B (False)** | Foundry IQ is a RAG service. It retrieves relevant passages from the indexed enterprise content and uses them to ground the generated answer. It does not rely solely on the model's training data. |
| 31 | **A** | This requires multiple services: Content Understanding for reliable structured extraction from PDFs and IDs, multimodal vision for analyzing non-standard blueprints, and custom logic to cross-reference extracted data. |
| 32 | **A** | You can include multiple `image_url` items in the same content list. Each image is a separate object with `"type": "image_url"`. The model will consider all images together when answering. |
| 33 | **B** | Pre-built models in Content Understanding support multiple languages. The corporation should verify coverage for their specific languages and build custom models only for those not supported out of the box. |
| 34 | **B** | Foundry IQ provides citations pointing to the specific source documents and passages. This allows users to verify the answer against the original source. RAG reduces hallucination but is not infallible, so citations are essential for trust. |
| 35 | **B** | Content Understanding is purpose-built for reliable, repeatable structured extraction (key-value pairs, tables) from known document types at scale. GPT-4o is better for freeform, open-ended analysis of images. |
| 36 | **A** | Generating images = DALL-E; analyzing customer photos to identify products = multimodal vision; extracting structured specs from datasheets = Content Understanding. |
| 37 | **C** | This is a freeform image description task -- exactly what GPT-4o multimodal excels at. Content Understanding is for structured extraction; DALL-E generates images, not captions; Foundry IQ is for enterprise document Q&A. |
| 38 | **A** | Content Understanding parses the email to extract structured fields (order number), multimodal vision assesses damage from the photo, and business logic decides whether to create a replacement order. |

---

## HARD (Questions 39-55)

---

**Question 39 (Bug Finding)**
A developer gets empty results from this Content Understanding + Foundry IQ pipeline. Identify the flaw:

```
1. Scan invoices with Content Understanding -> extract fields
2. Store extracted JSON in Azure Blob Storage
3. Point Foundry IQ at the original scanned invoice images (not the extracted JSON)
4. Employees ask questions like "What was the total from Vendor X in March?"
```

A) Step 1 should use DALL-E instead of Content Understanding
B) Step 3 is wrong: Foundry IQ should index the extracted structured JSON data, not the raw scanned images, for effective search and retrieval
C) Step 2 should store data in SharePoint instead of Blob Storage
D) Step 4 should use multimodal vision instead of Foundry IQ

---

**Question 40 (Architecture Design)**
A pharmaceutical company needs to process clinical trial documents that contain: (1) printed patient data tables, (2) handwritten doctor annotations in margins, (3) embedded charts/graphs showing test results. Design the optimal extraction strategy.

A) Use Content Understanding alone for everything
B) Use Content Understanding for printed tables and structured fields; use GPT-4o multimodal for handwritten annotations and chart interpretation; merge results in a processing pipeline
C) Use GPT-4o multimodal for everything
D) Use DALL-E to recreate the documents cleanly, then process with Content Understanding

---

**Question 41 (Code Completion - Advanced)**
A developer wants to build a loop that processes a folder of images and categorizes each one. Complete the missing code:

```python
import os, base64

categories = {}
image_folder = "./product_images/"

for filename in os.listdir(image_folder):
    filepath = os.path.join(image_folder, filename)
    with open(filepath, "rb") as f:
        img_b64 = base64.b64encode(f.read()).decode("utf-8")

    response = client.responses.create(
        model="gpt-4o",
        input=[
            {"role": "user", "content": [
                {"type": "text", "text": "Categorize this product image. Return ONLY the category name."},
                _______________________________________
            ]}
        ]
    )
    category = response.output_text.strip()
    categories[filename] = category
```

A) `{"type": "image_url", "image_url": {"url": filepath}}`
B) `{"type": "image_url", "image_url": {"url": f"data:image/jpeg;base64,{img_b64}"}}`
C) `{"type": "base64", "data": img_b64}`
D) `{"type": "image_file", "path": filepath}`

---

**Question 42 (Multi-Service Architecture)**
A smart city project involves: traffic cameras capturing intersections (video), parking meters printing receipts, citizens submitting complaints via voice messages, and a public dashboard where officials ask questions about city data. Map each component to the correct service combination.

A) Video: Video analysis capabilities -> Receipts: Content Understanding -> Voice: Azure Speech -> Dashboard: Foundry IQ
B) Video: DALL-E -> Receipts: GPT-4o -> Voice: Content Understanding -> Dashboard: Multimodal Vision
C) Video: Content Understanding -> Receipts: DALL-E -> Voice: Foundry IQ -> Dashboard: Speech
D) All four components use Foundry IQ exclusively

---

**Question 43 (Edge Case)**
A company processes multi-page contracts (50+ pages) with Content Understanding. The first 5 pages contain party names and terms; pages 6-45 contain standard legal boilerplate; the last 5 pages contain signatures and dates. What is the best strategy?

A) Process the entire 50-page document as one request every time
B) Split processing: extract party names and terms from the first 5 pages, skip boilerplate, extract signatures from the last 5 pages to optimize cost and accuracy
C) Convert the entire contract to a single image and use multimodal vision
D) Use DALL-E to summarize the contract visually

---

**Question 44 (Scenario-Based)**
An agricultural company uses drone images of crop fields. They need to: (1) identify areas with pest damage, (2) estimate crop yield from aerial views, (3) generate reports with specific field coordinates and damage percentages. A general-purpose multimodal model gives vague answers like "some areas appear damaged." What should they do?

A) Switch to DALL-E for more accurate image analysis
B) Use Content Understanding instead of multimodal vision
C) Improve the text prompt with specific instructions (e.g., "Divide the field into quadrants. For each quadrant, estimate the percentage of visible crop damage and describe the type of damage") and potentially fine-tune or combine with specialized computer vision models
D) Use Foundry IQ to search for similar damage patterns

---

**Question 45 (Compare & Contrast)**
A company is choosing between: (A) sending scanned invoices to GPT-4o multimodal with the prompt "Extract vendor, amount, date, and invoice number", or (B) using Azure Content Understanding's pre-built invoice model. For processing 10,000 invoices daily, which statement is most accurate?

A) Both approaches will produce identical results at the same cost
B) GPT-4o is more reliable for structured extraction because it understands context better
C) Content Understanding's pre-built invoice model is optimized for this exact task -- it offers more consistent structured output, better accuracy on standard invoice fields, and is more cost-effective at high volume than general-purpose multimodal calls
D) GPT-4o is the only option because Content Understanding cannot process invoices

---

**Question 46 (RAG Deep Dive)**
A Foundry IQ deployment indexes 50,000 technical manuals. An engineer asks: "What is the torque specification for the Model X-500 turbine blade?" The system returns: "The torque specification is 45 Nm (source: X-500 Maintenance Manual, Rev 3, Page 47)." Which RAG component produced the citation?

A) The language model hallucinated the citation to appear trustworthy
B) The search/grounding step retrieved the specific passage from the indexed manual, and the generation step included the source reference as a citation
C) The engineer manually added the citation after receiving the answer
D) The indexing step pre-generated all possible answers with citations

---

**Question 47 (Bug Finding - Advanced)**
This pipeline has a subtle design flaw. Find it:

```
Pipeline: Customer Support Image Analysis
1. Customer uploads photo of defective product
2. Photo is sent to Content Understanding to extract "defect type"
3. Defect type is used to route to the correct support team
4. Support agent receives the routing and original photo
```

A) Step 2 is the flaw: Content Understanding extracts structured fields from documents/forms, not open-ended defect classification from arbitrary product photos. A multimodal model with a classification prompt would be more appropriate here.
B) Step 1 should require customers to also submit a form
C) Step 3 should use Foundry IQ for routing
D) Step 4 should use DALL-E to enhance the photo

---

**Question 48 (Order the Steps)**
Place these Foundry IQ deployment steps in the correct order:

1. Users query the system with natural-language questions
2. The generation model produces an answer grounded in the retrieved passages with citations
3. Configure data sources (PDFs in Azure Storage, SharePoint sites)
4. The search engine retrieves the most relevant passages for the query
5. Content is ingested, chunked, and indexed for semantic search

A) 3 -> 5 -> 1 -> 4 -> 2
B) 1 -> 3 -> 5 -> 4 -> 2
C) 5 -> 3 -> 4 -> 1 -> 2
D) 3 -> 1 -> 5 -> 2 -> 4

---

**Question 49 (Scenario-Based - Complex)**
A bank processes loan applications that include: a completed application form (PDF), a photo of the applicant's government ID, three months of bank statements (PDFs), and a selfie of the applicant for identity verification. Design the complete processing pipeline and identify where each service is used.

A) Content Understanding for application form field extraction + Content Understanding for ID data extraction + Content Understanding for bank statement parsing + Multimodal vision to compare selfie against ID photo + Business logic for loan decision
B) GPT-4o multimodal for everything
C) Foundry IQ for all document processing + DALL-E for identity verification
D) Content Understanding for all documents + DALL-E to verify identity

---

**Question 50 (True/False - Nuanced)**
True or False: Sending a prompt "Generate a picture of a cat" to GPT-4o via `client.responses.create()` with no image input will cause the model to generate and return an image of a cat.

A) True
B) False

---

**Question 51 (Data Interpretation - Advanced)**
A Foundry IQ system returns this response to the query "What safety equipment is required in Zone B?":

```json
{
  "answer": "Zone B requires hard hats, steel-toed boots, and safety goggles at all times. High-visibility vests are required during night shifts.",
  "citations": [
    {"source": "Safety Manual v4.2", "page": 12, "passage": "All personnel entering Zone B must wear hard hats, steel-toed boots, and safety goggles."},
    {"source": "Night Operations Addendum", "page": 3, "passage": "High-visibility vests are mandatory for all night-shift workers in Zones A, B, and C."}
  ]
}
```

Which statement is TRUE?

A) The answer about night-shift vests applies only to Zone B, as stated
B) The second citation actually says high-visibility vests apply to Zones A, B, and C -- the generated answer correctly applies this to Zone B, but a careful reader should note the vests are not exclusive to Zone B
C) The citations prove the answer is 100% fabricated
D) Foundry IQ cannot provide multiple citations for a single answer

---

**Question 52 (Architecture Design - Complex)**
Design a complete automated insurance claim processing system that handles:
- Phone call recordings of accident descriptions
- Photos of vehicle damage from multiple angles
- Scanned police reports
- The system should estimate repair costs and flag potential fraud

Which architecture is correct?

A) Azure Speech for call transcription -> Multimodal vision for damage assessment across multiple photos -> Content Understanding for police report field extraction -> GPT-4o to synthesize all inputs, estimate costs, and flag inconsistencies suggesting fraud -> Foundry IQ to search historical claims for similar fraud patterns
B) Content Understanding for everything
C) Foundry IQ for everything
D) DALL-E to reconstruct the accident -> Multimodal vision to verify

---

**Question 53 (Edge Case - Advanced)**
A multimodal model is given two images of the same warehouse shelf taken one hour apart, with the prompt: "Compare these images and list any inventory changes." The model responds: "Box C is missing from the second image." However, Box C was simply moved behind Box D and is partially occluded. What does this reveal about multimodal vision limitations?

A) The model is broken and should be replaced
B) Multimodal models interpret visible image content and cannot reliably infer occluded objects or 3D spatial relationships from 2D images. Critical inventory systems should use additional verification (e.g., RFID, barcode scans) rather than relying solely on visual analysis.
C) The model needs to be retrained on warehouse images
D) This is a DALL-E limitation, not a multimodal vision limitation

---

**Question 54 (Multi-Service Integration)**
An enterprise deploys this system and users report that Foundry IQ answers are outdated (referencing old policy versions). The enterprise updates policies quarterly. What is the root cause and fix?

A) Root cause: the language model's training data is outdated. Fix: use a newer model version.
B) Root cause: the Foundry IQ index has not been refreshed with the latest policy documents. Fix: set up a regular re-indexing pipeline that ingests updated documents from the source (e.g., SharePoint) on a schedule matching the quarterly update cycle.
C) Root cause: multimodal vision cannot read the new documents. Fix: switch to Content Understanding.
D) Root cause: the citations are pointing to the wrong documents. Fix: delete all citations.

---

**Question 55 (Comprehensive Scenario)**
A global manufacturing company wants an AI system that:
1. Inspects products on the assembly line using cameras (detect defects in real time)
2. Processes incoming supplier invoices in 12 languages
3. Allows engineers to ask questions about 10,000+ technical specification documents
4. Generates marketing images of new products before physical prototypes exist
5. Transcribes and extracts action items from recorded safety meetings

Match each requirement to the optimal service:

A) 1-Multimodal Vision, 2-Content Understanding, 3-Foundry IQ, 4-DALL-E, 5-Azure Speech + GPT-4o
B) 1-Content Understanding, 2-Multimodal Vision, 3-DALL-E, 4-Foundry IQ, 5-Azure Speech
C) 1-DALL-E, 2-Foundry IQ, 3-Content Understanding, 4-Multimodal Vision, 5-Azure Speech
D) 1-Multimodal Vision, 2-Multimodal Vision, 3-Multimodal Vision, 4-Multimodal Vision, 5-Multimodal Vision

---

### ANSWERS: Questions 39-55

| # | Answer | Explanation |
|---|--------|-------------|
| 39 | **B** | The pipeline correctly extracts data with Content Understanding and stores it, but then points Foundry IQ at the raw images instead of the extracted JSON. Foundry IQ should index the structured extracted data for effective search and retrieval. Raw scanned images are not useful for text-based Q&A. |
| 40 | **B** | Different content types in the same document require different tools. Content Understanding handles printed structured data reliably. GPT-4o multimodal is better for interpreting handwritten notes and charts/graphs. A pipeline combining both yields the best results. |
| 41 | **B** | For local files, you must read the file, base64-encode it, and use the data URI format: `data:image/jpeg;base64,{encoded_data}`. A local file path cannot be passed as a URL to the API. |
| 42 | **A** | Video analysis for traffic cameras, Content Understanding for structured receipt extraction, Azure Speech for voice-to-text transcription of complaints, and Foundry IQ for the Q&A dashboard over aggregated city data. |
| 43 | **B** | Processing 50 pages when only 10 contain relevant data wastes compute and cost. Splitting extraction to target specific page ranges (first 5 for terms, last 5 for signatures) is more efficient and often more accurate. |
| 44 | **C** | When a general multimodal model gives vague answers, prompt engineering is the first line of improvement. More specific, structured prompts with explicit instructions yield dramatically better results. For production agricultural use, specialized vision models may also be needed. |
| 45 | **C** | Content Understanding's pre-built invoice model is purpose-built for invoice field extraction. At 10,000 invoices/day, it provides more consistent structured output, higher accuracy on standard fields, and better cost efficiency than routing each invoice through a general-purpose multimodal model. |
| 46 | **B** | In the RAG pipeline, the search/grounding step retrieves the specific passage from the indexed content, and the generation step incorporates this as a citation. Citations trace back to actual indexed content, unlike hallucinated references. |
| 47 | **A** | Content Understanding is designed for extracting structured fields from known document types (invoices, forms, IDs). Classifying arbitrary defect types from product photos is an open-ended visual analysis task better suited to a multimodal model with a classification prompt. Using the wrong service for the task type leads to poor results. |
| 48 | **A** | Configure data sources (3) -> Ingest and index (5) -> Users query (1) -> Search retrieves relevant passages (4) -> Model generates grounded answer with citations (2). You must set up the data pipeline before users can query it. |
| 49 | **A** | Each component maps to its ideal service: Content Understanding for structured extraction from forms, IDs, and bank statements; multimodal vision for the open-ended task of comparing a selfie to an ID photo; and business logic for the final decision. |
| 50 | **B (False)** | GPT-4o is a text generation model (with multimodal input). Sending a text-only prompt asking it to "generate a picture" will return text (perhaps a description), not an actual image. Image generation requires DALL-E or a similar generation model. |
| 51 | **B** | Close reading of the citations reveals the night-shift vest requirement applies to Zones A, B, and C -- not exclusively Zone B. The generated answer is technically correct for Zone B but a careful reader should note the broader scope. This illustrates why citations are important: they allow verification beyond the summarized answer. |
| 52 | **A** | This is a complex multi-service architecture: Speech for audio transcription, multimodal vision for visual damage assessment, Content Understanding for structured police report extraction, GPT-4o to synthesize and reason across all inputs, and Foundry IQ to search historical claim patterns for fraud detection. |
| 53 | **B** | Multimodal models work with 2D pixel data and cannot reliably understand 3D spatial relationships, occlusion, or objects hidden behind other objects. This is a fundamental limitation. Critical systems should use complementary verification methods rather than relying solely on visual AI. |
| 54 | **B** | Foundry IQ answers are grounded in its index. If the index is not refreshed when source documents are updated, the system will continue referencing the old versions. The fix is a scheduled re-indexing pipeline synchronized with the document update cycle. |
| 55 | **A** | 1-Multimodal Vision for real-time defect detection from camera images; 2-Content Understanding for structured multilingual invoice processing; 3-Foundry IQ for RAG-based Q&A over technical specs; 4-DALL-E for generating marketing images from text descriptions; 5-Azure Speech for transcription + GPT-4o for extracting action items from the transcript. |

---

## SCORING

| Score | Rating | Recommendation |
|-------|--------|----------------|
| 50-55 | **Excellent (91-100%)** | You have strong mastery of vision, content understanding, and multi-service architecture in Foundry. |
| 44-49 | **Pass (80-90%)** | Solid understanding. Review any missed questions, especially architecture and edge case scenarios. |
| 36-43 | **Needs Work (65-79%)** | Focus on: when to use Content Understanding vs multimodal vision, Foundry IQ's RAG pipeline, and multi-service design patterns. |
| 28-35 | **Below Passing (50-64%)** | Revisit the core differences between analysis (vision), generation (DALL-E), and extraction (Content Understanding). Study the API input format for multimodal models. |
| Below 28 | **Significant Review Needed** | Start with the fundamentals: what each service does, the input/output of each, and the basic API patterns. |

---

## KEY CONCEPTS SUMMARY

| Capability | Input | Output | Best For |
|------------|-------|--------|----------|
| **Multimodal Vision (GPT-4o)** | Image + text prompt | Text analysis | Open-ended image description, Q&A, comparison |
| **Image Generation (DALL-E)** | Text prompt | New image | Creating visuals from descriptions |
| **Video Generation** | Text/image prompt | New video | Creating video content |
| **Content Understanding** | Documents, images, audio, video | Structured key-value data | Reliable field extraction at scale |
| **Foundry IQ (RAG)** | Enterprise content + user query | Grounded answer + citations | Enterprise Q&A over large document collections |
