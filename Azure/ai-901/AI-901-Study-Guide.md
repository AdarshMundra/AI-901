# AI-901: Microsoft Azure AI Fundamentals - Crash Study Guide

> **Exam Date:** Sunday, September 27, 2026
> **Passing Score:** 700 / 1000
> **Format:** Multiple choice, drag-and-drop, case studies
> **Duration:** ~45-60 minutes

---

## EXAM STRUCTURE (2 Major Domains)

| Domain | Weight |
|--------|--------|
| 1. Identify AI Concepts and Capabilities | 40-45% |
| 2. Implement AI Solutions using Microsoft Foundry | 55-60% |

---

## DOMAIN 1: Identify AI Concepts and Capabilities (40-45%)

### 1.1 Principles of Responsible AI (MEMORIZE THESE 6)

These 6 principles are **heavily tested**. Know each one with examples:

| Principle | What It Means | Example Question Scenario |
|-----------|--------------|--------------------------|
| **Fairness** | AI should treat all people fairly, avoid bias against groups | A hiring model that discriminates based on gender |
| **Reliability & Safety** | AI should perform reliably and safely under all conditions | Self-driving car must work in rain/snow |
| **Privacy & Security** | AI should respect privacy and be secure | Medical AI must protect patient data |
| **Inclusiveness** | AI should empower everyone, engage all people | AI app should be accessible to people with disabilities |
| **Transparency** | Users should understand how AI makes decisions | Users should know when they're talking to a bot |
| **Accountability** | People should be accountable for AI systems | Humans must oversee AI decisions, especially critical ones |

**Memory trick:** **F-R-P-I-T-A** (Fair, Reliable, Private, Inclusive, Transparent, Accountable)

---

### 1.2 AI Model Components and Configurations

#### How Generative AI Models Work
- **Large Language Models (LLMs):** Trained on massive text data, predict next tokens
- **Transformer architecture:** The foundation of modern generative AI
- **Tokens:** Text is broken into tokens (words or sub-words) for processing
- **Training vs Inference:** Training = learning from data; Inference = making predictions
- **Fine-tuning:** Adapting a pre-trained model for specific tasks
- **Grounding:** Connecting AI responses to factual, verifiable data

#### Choosing the Right AI Model
- **Generative AI models** - for content creation, chat, code generation
- **Computer vision models** - for image analysis, object detection
- **Speech models** - for speech-to-text and text-to-speech
- **Multimodal models** - can handle text, images, audio together
- **Image-generation models** - creating images from text prompts (DALL-E)

#### Model Deployment Options & Configuration
- **Temperature:** Controls randomness (0 = deterministic, 1 = creative)
- **Top-p (nucleus sampling):** Controls diversity of responses
- **Max tokens:** Limits response length
- **System message:** Defines the AI's behavior and personality
- **Deployment types:** Standard, Provisioned throughput

---

### 1.3 AI Workloads (Know These Categories)

#### Generative AI & Agentic AI
- **Generative AI:** Creates new content (text, images, code)
- **AI Agents:** Autonomous AI that can plan, use tools, and take actions
- **Single-agent solutions:** One agent handling a task
- **Prompts:** Instructions given to the AI model (system + user prompts)

#### Text Analysis (NLP)
- **Keyword extraction:** Identifying key terms in text
- **Entity detection/recognition (NER):** Identifying people, places, organizations, dates
- **Sentiment analysis:** Determining positive, negative, or neutral tone
- **Summarization:** Condensing long text into key points
- **Language detection:** Identifying what language text is written in

#### Speech
- **Speech recognition (Speech-to-Text/STT):** Converting spoken words to text
- **Speech synthesis (Text-to-Speech/TTS):** Converting text to spoken audio
- **Real-time vs batch transcription**
- **Custom voice models**
- **Speech translation:** Translating spoken language

#### Computer Vision
- **Image classification:** Categorizing an image (e.g., "cat" or "dog")
- **Object detection:** Finding and locating objects with bounding boxes
- **Optical Character Recognition (OCR):** Reading text from images
- **Facial detection:** Detecting faces in images
- **Image generation:** Creating images from text descriptions (DALL-E)
- **Multimodal vision:** Using AI models that understand both text and images

#### Information Extraction
- **Document analysis:** Extracting data from forms, invoices, receipts
- **Image information extraction:** Getting structured data from images
- **Audio/video extraction:** Extracting information from multimedia content
- **Azure Content Understanding:** The service for these tasks in Foundry

---

## DOMAIN 2: Implement AI Solutions using Microsoft Foundry (55-60%)

> **This is the bigger domain - focus more study time here!**

### 2.1 Generative AI Apps & Agents in Foundry

#### Prompt Engineering (KEY TOPIC)
- **System prompt:** Sets the AI's role, behavior, rules, and constraints
- **User prompt:** The actual question or request from the user
- **Few-shot prompting:** Providing examples in the prompt to guide output
- **Zero-shot prompting:** Asking without examples
- **Clear, specific instructions** produce better results
- **Prompt structure:** Context + Task + Format + Constraints

#### Microsoft Foundry Portal
- **Deploy models** in the Foundry portal (previously Azure AI Studio)
- **Model catalog:** Browse and select available AI models
- **Playground:** Test prompts interactively before coding
- **Foundry SDK:** Python SDK for building AI applications

#### Building Applications
- **Foundry SDK (Python):** Create chat client applications programmatically
- **Lightweight chat client:** Basic app that sends prompts and receives responses
- **API calls:** Understanding REST API patterns for AI services
- **Authentication:** Using API keys or Azure AD for secure access

#### AI Agents
- **Create agents** in the Foundry portal
- **Single-agent solutions:** One agent with specific tools/instructions
- **Agent tools:** Functions the agent can call to perform actions
- **Testing agents:** Validate agent behavior in the portal
- **Client applications for agents:** Building apps that interact with agents

### 2.2 Text & Speech Solutions in Foundry

#### Text Analysis Applications
- Use **Azure Language** in Foundry Tools for:
  - Sentiment analysis
  - Key phrase extraction
  - Named entity recognition
  - Language detection
- Build **Python applications** using the SDK
- Use **general-purpose AI models** for text analysis tasks

#### Speech Solutions
- **Azure Speech in Foundry Tools** (formerly Azure Speech Service)
- **Speech-to-Text:** Transcribe audio to text
- **Text-to-Speech:** Generate spoken audio from text
- **Multimodal models** can respond to spoken prompts directly
- Build **lightweight apps** using the Speech SDK

### 2.3 Computer Vision & Image Generation in Foundry

- **Multimodal models:** Send images + text prompts together
  - "Describe this image"
  - "What objects are in this photo?"
- **Image generation models:** Create images from text descriptions
- **Video generation models:** Create video content
- Build **lightweight vision apps** using the SDK
- Understand when to use vision vs. multimodal approaches

### 2.4 Information Extraction in Foundry

#### Azure Content Understanding in Foundry Tools
- **Document extraction:** Forms, invoices, receipts, IDs
- **Image extraction:** Structured data from images
- **Audio extraction:** Information from audio files
- **Video extraction:** Information from video content
- **Pre-built models** vs **custom models**
- Build **lightweight extraction apps** using Content Understanding SDK

---

## 5-DAY CRASH STUDY PLAN (Mon-Fri before Sunday exam)

### Day 1 (Monday) - AI Fundamentals & Responsible AI
- [ ] Complete: [Introduction to AI concepts](https://learn.microsoft.com/en-us/training/modules/get-started-ai-fundamentals/)
- [ ] Memorize the 6 Responsible AI principles (F-R-P-I-T-A)
- [ ] Complete: [Introduction to generative AI and agents](https://learn.microsoft.com/en-us/training/modules/fundamentals-generative-ai/)
- [ ] Review: Prompt engineering basics (system vs user prompts, temperature, top-p)

### Day 2 (Tuesday) - NLP, Speech & Vision Concepts
- [ ] Complete: [Introduction to NLP concepts](https://learn.microsoft.com/en-us/training/modules/introduction-language/)
- [ ] Complete: [Introduction to AI speech concepts](https://learn.microsoft.com/en-us/training/modules/introduction-ai-speech/)
- [ ] Complete: [Introduction to computer vision concepts](https://learn.microsoft.com/en-us/training/modules/introduction-computer-vision/)

### Day 3 (Wednesday) - Information Extraction, RAG & Azure Setup
- [ ] Complete: [Introduction to AI-powered information extraction](https://learn.microsoft.com/en-us/training/modules/introduction-information-extraction/)
- [ ] Complete: [Introduction to RAG concepts](https://learn.microsoft.com/en-us/training/modules/rag-fundamentals/)
- [ ] Complete: [Get started with AI in Azure](https://learn.microsoft.com/en-us/training/modules/get-started-with-ai-in-azure/)

### Day 4 (Thursday) - Hands-on with Foundry (THE BIG DAY)
- [ ] Complete: [Get started with generative AI and agents in Azure](https://learn.microsoft.com/en-us/training/modules/get-started-with-generative-ai-and-agents/)
- [ ] Complete: [Get started with text analysis in Azure](https://learn.microsoft.com/en-us/training/modules/get-started-text-analysis-azure/)
- [ ] Complete: [Get started with speech in Azure](https://learn.microsoft.com/en-us/training/modules/get-started-speech-azure/)

### Day 5 (Friday) - More Hands-on & Review
- [ ] Complete: [Get started with computer vision in Azure](https://learn.microsoft.com/en-us/training/modules/get-started-vision-azure/)
- [ ] Complete: [Get started with information extraction in Azure](https://learn.microsoft.com/en-us/training/modules/get-started-information-extraction/)
- [ ] Complete: [Get started with Microsoft Foundry IQ](https://learn.microsoft.com/en-us/training/modules/get-started-foundry-iq/)

### Day 6 (Saturday) - Practice & Weak Areas
- [ ] Take the **Practice Assessment** on [AI Skills Navigator](https://aiskillsnavigator.microsoft.com/credentials/cert-83587e0a0754cfee561ade3e27d9fa1cdaf15ae03be52d2413b2b858d1b4eda4)
- [ ] Try the [Exam Sandbox](https://go.microsoft.com/fwlink/?linkid=2226877) to get familiar with the exam interface
- [ ] Review all wrong answers and weak topics
- [ ] Re-read this study guide focusing on weak areas
- [ ] Review Domain 2 again (55-60% of the exam!)

### Day 7 (Sunday) - Exam Day!
- [ ] Quick review of Responsible AI principles
- [ ] Quick review of key Azure services and when to use each
- [ ] Quick review of Foundry portal concepts
- [ ] Take the exam with confidence!

---

## KEY TERMS CHEAT SHEET

| Term | Definition |
|------|-----------|
| **Microsoft Foundry** | The unified platform for building AI solutions on Azure (formerly Azure AI Studio) |
| **Foundry Tools** | Pre-built Azure AI services available in Foundry (Speech, Language, Content Understanding, etc.) |
| **Foundry SDK** | Python SDK for building AI applications |
| **Foundry IQ** | Helps AI agents retrieve relevant enterprise data (RAG-based) |
| **LLM** | Large Language Model - foundation of generative AI |
| **RAG** | Retrieval-Augmented Generation - grounding AI with external data |
| **NER** | Named Entity Recognition - identifying people, places, etc. in text |
| **OCR** | Optical Character Recognition - reading text from images |
| **STT/TTS** | Speech-to-Text / Text-to-Speech |
| **Content Understanding** | Azure service for extracting info from documents, images, audio, video |
| **Multimodal** | AI models that work with multiple input types (text + images + audio) |
| **Tokens** | Units of text that LLMs process |
| **Temperature** | Controls randomness in AI output (low=focused, high=creative) |
| **Top-p** | Controls diversity of word selection in AI output |
| **Grounding** | Connecting AI responses to factual data sources |
| **Fine-tuning** | Customizing a pre-trained model for specific use cases |
| **AI Agent** | Autonomous AI that can plan, reason, and use tools |

---

## QUICK TIPS FOR THE EXAM

1. **Domain 2 is 55-60%** of the exam - prioritize hands-on Foundry knowledge
2. **Responsible AI** questions are almost guaranteed - know all 6 principles cold
3. **Know WHEN to use WHICH service** - this is the most common question pattern
4. **Python basics** are expected - understand basic SDK usage patterns
5. **REST APIs, SDKs, and CLIs** may appear - know the basics
6. **Read questions carefully** - look for keywords like "most appropriate" or "first step"
7. **Passing score is 700/1000** - you don't need to be perfect

---

## OFFICIAL RESOURCES

- [Learning Path 1: AI Concepts](https://learn.microsoft.com/en-us/training/paths/ai-concepts/)
- [Learning Path 2: Get Started with AI Apps & Agents on Azure](https://learn.microsoft.com/en-us/training/paths/get-started-ai-apps-agents/)
- [AI-901 Exam Page](https://learn.microsoft.com/en-us/credentials/certifications/exams/ai-901/)
- [AI-901 Study Guide](https://learn.microsoft.com/credentials/certifications/resources/study-guides/ai-901)
- [Practice Assessment (AI Skills Navigator)](https://aiskillsnavigator.microsoft.com/credentials/cert-83587e0a0754cfee561ade3e27d9fa1cdaf15ae03be52d2413b2b858d1b4eda4)
- [Exam Sandbox (Try the interface)](https://go.microsoft.com/fwlink/?linkid=2226877)
