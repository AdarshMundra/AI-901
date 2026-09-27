# AWS AIF-C01 (AI Practitioner) Exam Overview

## Exam Domains & Weightings

| Domain | Weight |
|--------|--------|
| 1. Fundamentals of AI and ML | ~20% |
| 2. Fundamentals of Generative AI | ~24% |
| 3. Applications of Foundation Models | ~28% |
| 4. Guidelines for Responsible AI | ~14% |
| 5. Security, Compliance, and Governance for AI Solutions | ~14% |

---

## Key Topics You Must Know

### 1. AI/ML Fundamentals
- **ML types:** Supervised (labeled data), Unsupervised (unlabeled - clustering, dimensionality reduction), Deep Learning (neural networks with many layers), Reinforcement Learning (trial & error, rewards)
- **ML process:** Data Collection → Preprocessing → Training → Evaluation
- **Data splits:** Training set (train model), Validation set (tune hyperparameters), Test set (final evaluation)
- **Neural networks:** CNN (images), RNN (sequential/video), GAN (synthetic data generation), Diffusion models (iterative noise removal)
- **Key concepts:** Overfitting (high variance), Underfitting (high bias), Inference vs Training, Feature extraction vs selection, Labeled vs unlabeled data
- **Metrics:** Precision/Recall/F1 (classification), MAE/RMSE/R-squared (regression), Accuracy (balanced binary classification)

### 2. Generative AI Fundamentals
- **Foundation Models (FMs):** Large models trained on massive diverse data
- **LLMs:** A class of FMs, non-deterministic, text-focused
- **Inference parameters:** Temperature (creativity), Top K (number of candidates), Top P (percentage of candidates), Stop sequences, Response length
- **Complexity order:** Prompt Engineering → RAG → Fine-tuning
- **Model customization:** Fine-tuning (labeled data) and Continued Pre-training (unlabeled data) — these change model weights
- **Prompt engineering:** Zero-shot, Few-shot, Chain-of-thought — these do NOT change model weights
- **RAG:** Retrieves external data to augment prompts — does NOT change model weights
- **Model evaluation:** Automatic (BERT Score, F1 — quantitative) vs Human (qualitative — coherence, relevance)

### 3. AWS Services to Know Cold

| Service | Purpose |
|---------|---------|
| **Amazon Bedrock** | Managed FMs, fine-tuning, RAG, Guardrails, Agents |
| **SageMaker** | Full ML platform (build, train, deploy) |
| **SageMaker Canvas** | No-code ML model building |
| **SageMaker Clarify** | Bias detection & model explainability |
| **SageMaker Data Wrangler** | Data prep, 300+ transformations, dataset splitting |
| **SageMaker Ground Truth** | Human-in-the-loop data labeling |
| **SageMaker Feature Store** | Centralized feature repository |
| **SageMaker Model Cards** | Document model intended use, risk, metrics |
| **SageMaker Model Dashboard** | Track deployed models (aggregates Cards + Monitor + Endpoints) |
| **SageMaker Model Monitor** | Production model quality monitoring |
| **SageMaker JumpStart** | Pre-built ML solutions, one-click deploy |
| **Amazon Q Business** | Enterprise AI assistant (powered by Bedrock) |
| **Amazon Q Developer** | Code suggestions, testing, upgrades in IDEs + Console |
| **Amazon Q in QuickSight** | Natural language BI dashboards |
| **Amazon Comprehend** | NLP — sentiment, entities, PII redaction |
| **Amazon Comprehend Medical** | Clinical text analysis, HIPAA eligible |
| **Amazon Rekognition** | Image/video analysis, object/text/face detection |
| **Amazon Textract** | Extract text/data from documents (OCR++) |
| **Amazon Transcribe** | Speech-to-text (Medical variant for healthcare) |
| **Amazon Polly** | Text-to-speech |
| **Amazon Lex** | Chatbots / conversational interfaces |
| **Amazon Translate** | Text translation |
| **Amazon Personalize** | Recommendations engine |
| **Amazon Forecast** | Time-series forecasting |
| **Amazon Kendra** | Enterprise search |
| **Amazon Connect** | Cloud contact center |
| **Amazon A2I** | Human review of ML predictions |
| **AWS DeepRacer** | Learn RL with autonomous race car |

### 4. SageMaker Deployment Types
- **Real-time:** Low-latency, persistent endpoints
- **Serverless:** Intermittent workloads, tolerates cold starts, scales to zero
- **Asynchronous:** Large payloads (up to 1GB), long processing
- **Batch transform:** Entire datasets at once
- **Bedrock:** On-demand or Batch inference (50% cheaper)

### 5. Responsible AI
- **Bias types:** Human bias (personal beliefs), Algorithmic bias (from training data)
- **Hallucination:** AI generates plausible but factually incorrect content
- **Attacks:** Hijacking (diverts AI to unintended behavior), Jailbreaking (bypasses safety restrictions), Prompt injection (embeds harmful instructions), Exposure (leaks sensitive data)
- **Trade-offs:** Interpretability vs Performance (simpler models = more interpretable, less accurate)
- **Guardrails for Bedrock:** Filter harmful content, redact PII, topic controls
- **AWS AI Service Cards:** Transparency about intended use, limitations, impacts
- **SageMaker Clarify:** Detect bias + explain predictions

### 6. Security & Governance
- **Shared Responsibility Model:** AWS secures infrastructure, customer secures data/access
- **Bedrock data privacy:** Your data is NOT used to improve base FMs, NOT shared with providers
- **AWS Config:** Continuous resource configuration monitoring
- **AWS Artifact:** Compliance reports (including ISV)
- **Trainium:** ML training chip (energy efficient)
- **Inferentia:** ML inference chip (cost effective)
- **GenAI Security Scoping Matrix:** Building from scratch = maximum security ownership
- **Data lineage:** Tracks data flow for privacy/compliance
- **Model Cards + Role Manager + Model Dashboard** = SageMaker governance tools

---

## Quick Tips
- **Bedrock** = managed generative AI service; **SageMaker** = full ML platform
- Prompt engineering does NOT change model weights; fine-tuning DOES
- RAG is for dynamic/changing data; fine-tuning is for domain-specific expertise
- Amazon S3 is the storage for Bedrock datasets
- LLMs are generative (not discriminative) and non-deterministic
- Know the difference between every SageMaker sub-service — they appear heavily
