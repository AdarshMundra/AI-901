# AWS AIF-C01 (AI Practitioner) Learning Plan

## Exam Details
- **Exam Code:** AIF-C01
- **Duration:** 85 minutes
- **Questions:** 65 (scored) + 15 (unscored)
- **Passing Score:** 700/1000
- **Format:** Multiple choice & multiple response
- **Cost:** $150 USD

---

## Week 1: AI & ML Fundamentals (~20% of exam)

### Day 1-2: Core ML Concepts
- [ ] What is AI vs ML vs Deep Learning — how they relate
- [ ] Supervised Learning — labeled data, classification, regression
- [ ] Unsupervised Learning — unlabeled data, clustering, dimensionality reduction
- [ ] Reinforcement Learning — rewards, trial and error, agents
- [ ] Semi-supervised & Self-supervised Learning
- [ ] ML algorithms: K-Means (clustering), KNN (classification), Decision Trees, SVMs

**AWS Resources:**
- https://aws.amazon.com/what-is/machine-learning/
- https://aws.amazon.com/what-is/artificial-intelligence/

### Day 3-4: ML Workflow & Data
- [ ] ML process: Data Collection → Preprocessing → Training → Evaluation
- [ ] Structured vs Unstructured data
- [ ] Labeled vs Unlabeled data
- [ ] Training, Validation, and Test sets — purpose of each
- [ ] Feature extraction vs Feature selection
- [ ] Feature engineering basics
- [ ] Overfitting (high variance) vs Underfitting (high bias)
- [ ] Bias-Variance tradeoff

**AWS Resources:**
- https://aws.amazon.com/what-is/overfitting/
- https://docs.aws.amazon.com/machine-learning/latest/dg/model-fit-underfitting-vs-overfitting.html

### Day 5: Neural Networks & Deep Learning
- [ ] What are neural networks
- [ ] CNN — Convolutional Neural Networks (images)
- [ ] RNN — Recurrent Neural Networks (sequential data, video)
- [ ] GAN — Generative Adversarial Networks (synthetic data)
- [ ] Diffusion Models (iterative noise removal for image generation)
- [ ] Transformer architecture basics
- [ ] VAE — Variational Autoencoders (latent space)

**AWS Resources:**
- https://aws.amazon.com/what-is/neural-network/

### Day 6: ML Metrics & Evaluation
- [ ] Classification metrics: Precision, Recall, F1-Score, Accuracy
- [ ] Regression metrics: MAE, RMSE, R-squared
- [ ] Confusion matrix
- [ ] Multi-class vs Multi-label classification
- [ ] Runtime efficiency: Average Response Time, Data Throughput
- [ ] NLP vs Computer Vision — what each handles

**AWS Resources:**
- https://docs.aws.amazon.com/sagemaker/latest/dg/autopilot-metrics-validation.html

### Day 7: Review & Practice
- [ ] Review Week 1 notes
- [ ] Take Test 1 (Questions focused on Domain 1)
- [ ] Note weak areas for revisiting

---

## Week 2: Generative AI Fundamentals (~24% of exam)

### Day 8-9: Foundation Models & LLMs
- [ ] What are Foundation Models (FMs) — large, diverse training data
- [ ] What are Large Language Models (LLMs) — a class of FMs
- [ ] LLMs are non-deterministic and generative (not discriminative)
- [ ] Discriminative vs Generative models
- [ ] BERT — Bidirectional Encoder (understanding context, fill-in-the-blank)
- [ ] GPT — Generative Pre-trained Transformer (text generation, text-to-SQL)
- [ ] Stable Diffusion — image generation from text
- [ ] How generative AI creates content (learns patterns, generates new data)

**AWS Resources:**
- https://aws.amazon.com/what-is/large-language-model/
- https://aws.amazon.com/what-is/generative-ai/

### Day 10-11: Inference Parameters & Prompt Engineering
- [ ] Temperature — controls creativity (0 = deterministic, 1 = creative)
- [ ] Top K — number of most-likely candidates for next token
- [ ] Top P — percentage of most-likely candidates for next token
- [ ] Stop Sequences — characters that stop generation
- [ ] Response Length — min/max tokens in response
- [ ] Zero-shot prompting — no examples provided
- [ ] Few-shot prompting — a few examples provided
- [ ] Chain-of-thought prompting — step-by-step reasoning
- [ ] Dynamic prompt engineering — adjusting prompts based on context
- [ ] Negative prompting — specifying what to avoid

**AWS Resources:**
- https://docs.aws.amazon.com/bedrock/latest/userguide/inference-parameters.html
- https://aws.amazon.com/what-is/prompt-engineering/

### Day 12-13: Model Customization & RAG
- [ ] Complexity order: Prompt Engineering → RAG → Fine-tuning
- [ ] Prompt engineering — does NOT change model weights
- [ ] RAG — retrieves external data, does NOT change weights, good for dynamic data
- [ ] Fine-tuning — uses labeled data, DOES change weights
- [ ] Continued Pre-training — uses unlabeled data, DOES change weights
- [ ] RAG vs Agents in Amazon Bedrock
- [ ] Model evaluation: Automatic (BERT Score, F1) vs Human (qualitative)
- [ ] When to use which: RAG for changing data, fine-tuning for domain expertise

**AWS Resources:**
- https://aws.amazon.com/blogs/machine-learning/best-practices-to-build-generative-ai-applications-on-aws/
- https://docs.aws.amazon.com/bedrock/latest/userguide/model-evaluation.html

### Day 14: Review & Practice
- [ ] Review Week 2 notes
- [ ] Take Test 2 (Questions focused on Domain 2)
- [ ] Note weak areas

---

## Week 3: Applications of Foundation Models (~28% of exam)

### Day 15-16: Amazon Bedrock Deep Dive
- [ ] What is Amazon Bedrock — managed FM service
- [ ] Available FMs: Claude, Llama, Jurassic, Stable Diffusion, Amazon Titan
- [ ] Bedrock data privacy — data NOT used to improve FMs, NOT shared with providers
- [ ] Bedrock creates private copies for customization
- [ ] Guardrails — filter harmful content, redact PII, topic controls
- [ ] Watermark detection — identifies Titan Image Generator output
- [ ] Knowledge Bases — RAG implementation
- [ ] Agents — orchestration through cyclical input/output
- [ ] Bedrock inference: On-demand vs Batch (50% cheaper)
- [ ] Amazon S3 as dataset storage for Bedrock

**AWS Resources:**
- https://aws.amazon.com/bedrock/
- https://aws.amazon.com/bedrock/guardrails/

### Day 17-18: Amazon SageMaker Services
- [ ] **SageMaker Studio** — IDEs: JupyterLab, Code Editor, RStudio
- [ ] **SageMaker Canvas** — no-code ML model building
- [ ] **SageMaker Data Wrangler** — data prep, 300+ transformations, balance datasets, create splits
- [ ] **SageMaker Clarify** — bias detection, model explainability, feature importance
- [ ] **SageMaker Ground Truth / Ground Truth Plus** — data labeling, human-in-the-loop
- [ ] **SageMaker Feature Store** — centralized feature repository for sharing/reuse
- [ ] **SageMaker JumpStart** — pre-built solutions, one-click deploy, FM hub
- [ ] **SageMaker Model Cards** — document intended use, risk rating, metrics
- [ ] **SageMaker Model Dashboard** — aggregates Cards + Monitor + Endpoints
- [ ] **SageMaker Model Monitor** — production model quality tracking
- [ ] **SageMaker Role Manager** — IAM role management for ML
- [ ] **SageMaker Automatic Model Tuning** — auto hyperparameter optimization (no mandatory configs)
- [ ] SageMaker deployment types: Real-time, Serverless, Asynchronous, Batch Transform

**AWS Resources:**
- https://aws.amazon.com/sagemaker/
- https://aws.amazon.com/sagemaker/ml-governance/

### Day 19-20: Amazon Q Family & Other AI Services
- [ ] **Amazon Q Business** — enterprise AI assistant (powered by Bedrock), guardrails, topic controls
- [ ] **Amazon Q Developer** — code suggestions, security scanning, upgrades (IDEs + Console)
- [ ] **Amazon Q in QuickSight** — natural language BI dashboards
- [ ] **Amazon Q in Connect** — contact center agent assistance
- [ ] **Amazon Comprehend** — NLP, sentiment, entities, PII redaction
- [ ] **Amazon Comprehend Medical** — clinical text, HIPAA eligible, medical terminologies
- [ ] **Amazon Rekognition** — image/video analysis, text in images (limited to 100 words)
- [ ] **Amazon Textract** — document text extraction, OCR, handwriting, tables
- [ ] **Amazon Transcribe** — speech-to-text (Medical variant for healthcare/HIPAA)
- [ ] **Amazon Polly** — text-to-speech, multiple languages
- [ ] **Amazon Lex** — chatbots, conversational interfaces
- [ ] **Amazon Translate** — text translation
- [ ] **Amazon Personalize** — recommendation engine, similar items
- [ ] **Amazon Forecast** — time-series forecasting
- [ ] **Amazon Kendra** — enterprise search
- [ ] **Amazon Connect** — cloud contact center
- [ ] **Amazon A2I** — human review of ML predictions
- [ ] **AWS DeepRacer** — reinforcement learning with autonomous race car

**AWS Resources:**
- https://aws.amazon.com/q/
- https://aws.amazon.com/comprehend/

### Day 21: Review & Practice
- [ ] Review Week 3 notes
- [ ] Take Test 3
- [ ] Create flashcards for service differentiation

---

## Week 4: Responsible AI + Security + Final Review

### Day 22-23: Responsible AI (~14% of exam)
- [ ] Bias types: Human bias, Algorithmic bias, Data bias
- [ ] Hallucination — plausible but incorrect AI output
- [ ] Fairness, Explainability, Controllability, Transparency
- [ ] Interpretability vs Performance trade-offs
- [ ] AI attacks: Hijacking, Jailbreaking, Prompt Injection, Exposure
- [ ] AWS AI Service Cards — transparency about service use/limitations
- [ ] Guardrails for Amazon Bedrock — content filtering, PII redaction
- [ ] SageMaker Clarify — bias detection and model explainability
- [ ] RLHF — Reinforcement Learning from Human Feedback
- [ ] Amazon A2I — human review workflows
- [ ] Human evaluation vs Automated evaluation
- [ ] Best practices: guardrails, transparency, continuous monitoring
- [ ] GenAI Security Scoping Matrix — risk management discipline

**AWS Resources:**
- https://aws.amazon.com/machine-learning/responsible-ai/
- https://docs.aws.amazon.com/prescriptive-guidance/latest/llm-prompt-engineering-best-practices/common-attacks.html

### Day 24-25: Security, Compliance & Governance (~14% of exam)
- [ ] AWS Shared Responsibility Model — AWS secures infrastructure, customer secures data/access
- [ ] Bedrock data privacy — encrypted in transit/at rest, PrivateLink support
- [ ] AWS Config — continuous resource configuration monitoring
- [ ] AWS Artifact — compliance reports, ISV reports, email notifications
- [ ] AWS Audit Manager — audit evidence collection
- [ ] Amazon Inspector — security assessment
- [ ] AWS Trainium — ML training chip, energy efficient (25% more efficient)
- [ ] AWS Inferentia — ML inference chip, cost effective
- [ ] IAM service roles for access control (per-team roles for Bedrock)
- [ ] Data residency vs Data logging
- [ ] Threat detection vs Vulnerability management
- [ ] Data lineage — tracking data flow for compliance
- [ ] SageMaker governance tools: Role Manager + Model Cards + Model Dashboard
- [ ] GenAI Security Scoping Matrix — building from scratch = max security ownership
- [ ] Hybrid, Cloud, and Private deployment models
- [ ] Regional vs Global AWS services

**AWS Resources:**
- https://aws.amazon.com/compliance/shared-responsibility-model/
- https://aws.amazon.com/blogs/security/securing-generative-ai-an-introduction-to-the-generative-ai-security-scoping-matrix/

### Day 26-27: Full Practice Tests
- [ ] Take Test 4 (full 65 questions)
- [ ] Review all incorrect answers across all tests
- [ ] Identify patterns in mistakes — which domains need more work
- [ ] Re-study weak areas

### Day 28: Final Review
- [ ] Review AIF-C01-Study-Guide.md
- [ ] Quick review of all service differentiations
- [ ] Focus on commonly confused services:
  - Comprehend vs Comprehend Medical
  - Textract vs Rekognition (text extraction)
  - Transcribe vs Transcribe Medical
  - Ground Truth vs A2I
  - Clarify vs Model Monitor
  - Model Cards vs Model Dashboard
  - Fine-tuning vs RAG vs Prompt Engineering
  - Trainium (training) vs Inferentia (inference)
- [ ] Rest well before exam day

---

## Study Resources

### AWS Official
- [AWS AI Practitioner Exam Guide](https://aws.amazon.com/certification/certified-ai-practitioner/)
- [AWS Skill Builder - AI Practitioner Learning Path](https://explore.skillbuilder.aws/)
- [AWS Well-Architected ML Lens](https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/machine-learning-lens.html)

### Your Practice Tests
- `Test1.md` — 65 questions with explanations
- `Test2.md` — 65 questions with explanations
- `Test3.md` — 65 questions with explanations
- `Test4.md` — 65 questions with explanations
- **Total: 260 practice questions available**

### Key Pages to Bookmark
- https://aws.amazon.com/what-is/machine-learning/
- https://aws.amazon.com/what-is/generative-ai/
- https://aws.amazon.com/bedrock/
- https://aws.amazon.com/sagemaker/
- https://aws.amazon.com/machine-learning/responsible-ai/
- https://aws.amazon.com/compliance/shared-responsibility-model/

---

## High-Frequency Exam Topics (based on 260 practice questions)

These topics appeared most frequently across all practice tests:

1. **SageMaker sub-services** — know every one and its specific purpose
2. **Amazon Bedrock** — customization, privacy, guardrails, inference types
3. **Inference parameters** — Temperature, Top K, Top P, Stop sequences
4. **ML types** — Supervised vs Unsupervised vs RL vs Deep Learning
5. **Overfitting/Underfitting** — bias/variance relationship
6. **RAG vs Fine-tuning vs Prompt Engineering** — when to use each
7. **Amazon Q variants** — Business, Developer, QuickSight, Connect
8. **AI security attacks** — hijacking, jailbreaking, prompt injection, exposure
9. **AWS AI services** — Comprehend, Rekognition, Textract, Transcribe, Polly, Lex
10. **Shared Responsibility Model** — what AWS vs customer manages
