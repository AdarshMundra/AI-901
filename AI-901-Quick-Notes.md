# AI-901 Quick Notes (Last-Minute Revision)

---

## 6 RESPONSIBLE AI PRINCIPLES (F-R-P-I-T-A)

```
F - Fairness        -> No bias, treat all people equally
R - Reliability      -> Works safely under all conditions
P - Privacy          -> Protect data, inform users about collection
I - Inclusiveness    -> Accessible to everyone, all abilities
T - Transparency     -> Users understand how AI decides
A - Accountability   -> Humans oversee AI, governance in place
```

---

## GENERATIVE AI BASICS

- **LLM** = Large Language Model, predicts next token
- **Tokens** = text broken into small units for processing
- **Temperature** = 0 (deterministic) to 1 (creative)
- **Top-p** = controls word diversity
- **Max tokens** = limits response length
- **System prompt** = defines AI role/behavior/rules
- **User prompt** = the actual question
- **Few-shot** = give examples in prompt
- **Zero-shot** = no examples, just ask
- **Grounding** = connecting AI to factual data
- **Fine-tuning** = adapting pre-trained model for specific task
- **RAG** = Retrieval-Augmented Generation = search data first, then generate answer

---

## AI WORKLOADS - KNOW WHICH IS WHICH

### Text / NLP
| Task | What It Does |
|------|-------------|
| Sentiment analysis | Positive / Negative / Neutral |
| Key phrase extraction | Important terms from text |
| NER | People, places, orgs, dates |
| Summarization | Shorten long text |
| Language detection | Which language is this? |

### Speech
| Task | What It Does |
|------|-------------|
| STT (Speech-to-Text) | Voice -> written text |
| TTS (Text-to-Speech) | Written text -> voice |
| Speech translation | Translate spoken language |

### Computer Vision
| Task | What It Does |
|------|-------------|
| Image classification | Label the whole image ("cat") |
| Object detection | Find + locate objects with bounding boxes |
| OCR | Read text from images/docs |
| Face detection | Detect faces in images |
| Image generation | Text -> new image (DALL-E) |

### Information Extraction
| Task | What It Does |
|------|-------------|
| Document extraction | Data from forms, invoices, receipts |
| Image extraction | Structured data from images |
| Audio/Video extraction | Info from multimedia |

---

## AZURE SERVICES - QUICK MAP

```
Microsoft Foundry (formerly Azure AI Studio)
  |
  |-- Model Catalog     -> browse & select models
  |-- Playground         -> test prompts without code
  |-- Foundry SDK        -> Python SDK for building apps
  |-- Foundry IQ         -> RAG for enterprise data (citations!)
  |
  |-- Foundry Tools:
       |-- Azure Language         -> NLP (sentiment, NER, key phrases, language detection)
       |-- Azure Speech           -> STT, TTS, speech translation
       |-- Content Understanding  -> Extract from docs, images, audio, video
```

---

## WHICH SERVICE TO USE? (CHEAT SHEET)

| I need to... | Use this |
|-------------|----------|
| Analyze sentiment of text | Azure Language |
| Detect language | Azure Language |
| Extract key phrases | Azure Language |
| Find people/places/orgs in text | Azure Language (NER) |
| Transcribe speech to text | Azure Speech (STT) |
| Generate spoken audio from text | Azure Speech (TTS) |
| Read text from scanned docs | OCR / Content Understanding |
| Extract data from invoices/forms | Content Understanding |
| Extract info from video/audio | Content Understanding |
| Analyze what's in an image | Multimodal model |
| Generate images from text | Image generation model (DALL-E) |
| Chat with AI | Deploy model + Foundry SDK |
| Ground responses in company data | Foundry IQ (RAG) |
| Build an AI agent | Foundry portal agent builder |
| Test prompts without code | Foundry Playground |

---

## AI AGENTS - KEY POINTS

- Agents = autonomous AI that plans + uses tools + takes actions
- Created in the Foundry portal
- Need: instructions + tools + behavior rules
- Test in portal before deploying
- Build client apps using Foundry SDK
- Single-agent = one agent handles one task

---

## RAG (Retrieval-Augmented Generation)

```
User Question
     |
     v
[RETRIEVE] -> Search enterprise data/documents
     |
     v
[AUGMENT] -> Add retrieved info to prompt
     |
     v
[GENERATE] -> LLM generates grounded answer with citations
```

- **Why RAG?** Reduces hallucinations, provides citations, uses up-to-date data
- **Foundry IQ** = Microsoft's RAG service for enterprise data

---

## MODEL DEPLOYMENT FLOW

```
1. Go to Foundry portal
2. Browse Model Catalog
3. Select a model
4. Deploy it (Standard or Provisioned)
5. Test in Playground
6. Build app with Foundry SDK (Python)
7. Use API key or Azure AD for auth
```

---

## PROMPT ENGINEERING TIPS

```
Good prompt = Context + Task + Format + Constraints

System prompt example:
  "You are a helpful customer service agent for Contoso.
   Only answer questions about Contoso products.
   If you don't know, say 'I don't know.'
   Be polite and concise."

User prompt example:
  "What is the return policy for electronics?"
```

---

## MULTIMODAL = MULTI-INPUT

- Text + Image -> "Describe this image"
- Text + Audio -> "Respond to this spoken question"  
- One model handles multiple types of input
- Key for vision tasks and spoken interaction

---

## EXAM DAY REMINDERS

- **Passing: 700/1000** (you can miss ~30%)
- **Domain 1: 40-45%** (concepts, responsible AI)
- **Domain 2: 55-60%** (Foundry hands-on - BIGGER!)
- Read questions carefully - look for "MOST appropriate" or "FIRST"
- If stuck, eliminate obviously wrong answers first
- Responsible AI questions = almost guaranteed
- "Which service" questions = most common pattern
- Know Python SDK basics (not deep coding)
- Know REST API concepts (endpoints, keys)
