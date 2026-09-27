# AWS AIF-C01 Practice Test 1

---

### Question 1
**Domain:** Fundamentals of Generative AI

> Which of the following represents a valid use case for a generative AI-powered model?

- A) Using generative AI to create photorealistic images from textual descriptions :white_check_mark:
- B) Classifying medical images to detect anomalies or diagnose diseases using generative AI
- C) Applying generative AI for financial analysis to forecast stock market trends
- D) Utilizing generative AI to predict housing prices based on historical market data

**Correct Answer: A**

**Explanation:**

This is a legitimate use case for a generative AI model. Generative models such as DALL-E, Midjourney, and Stable Diffusion are designed to transform text prompts into high-quality, photorealistic images. These models use advanced techniques like Generative Adversarial Networks (GANs) or diffusion models to generate novel visual content based on the input description.

**Why the other options are incorrect:**

- **B)** Classifying medical images involves discriminative models designed for classification and detection, such as Convolutional Neural Networks (CNNs). These are trained to recognize patterns in labeled data for diagnostic purposes, not for generating new content.
- **C)** Financial analysis and stock market forecasting rely on time-series analysis and statistical methods (e.g., LSTM networks, ARIMA models) designed to interpret historical data and predict future outcomes -- not generative AI.
- **D)** Predicting housing prices involves analyzing structured data using regression models or supervised learning algorithms to find patterns and forecast values, which is fundamentally different from generating new content.

---

### Question 2
**Domain:** Guidelines for Responsible AI

> The admissions committee at an Ivy League university has noticed an increasing use of generative AI tools by applicants to draft their application essays. The committee aims to implement measures to detect the use of AI in essay creation to ensure all submissions reflect the genuine thoughts and abilities of the applicants.
>
> What specific issue is the admissions committee primarily trying to address by detecting the use of generative AI in application essays?

- A) Hallucination
- B) Bias
- C) Misinterpretation
- D) Plagiarism :white_check_mark:

**Correct Answer: D**

**Explanation:**

Plagiarism involves presenting someone else's work, ideas, or creations as one's own without proper attribution. Detecting the use of generative AI tools to produce essays helps the committee identify instances where applicants might have submitted content that is not genuinely their own, thus maintaining the integrity of the admissions process.

**Why the other options are incorrect:**

- **A) Hallucination** -- In AI, "hallucination" refers to the creation of false information. The committee is focused on detecting essays not genuinely authored by applicants, not on factual accuracy.
- **B) Bias** -- Bias in AI-generated outputs involves content that unfairly favors or discriminates against certain groups, which is not the same issue as ensuring originality.
- **C) Misinterpretation** -- Misinterpretation occurs when meaning or intent of a text is misunderstood. The committee's primary goal is to verify that the content is original, not that it is correctly interpreted.

---

### Question 3
**Domain:** Applications of Foundation Models

> A company has fine-tuned a Foundation Model on Amazon Bedrock, and the training data includes some confidential information. The company wants to ensure that the customized model's responses do not contain any of this confidential information.
>
> What is the most efficient approach to achieve this goal?

- A) Delete the customized model, remove confidential information from the training data, and fine-tune the model again
- B) Mask the confidential information from the model responses by leveraging Amazon Bedrock Guardrails :white_check_mark:
- C) Swap Amazon Bedrock with Amazon SageMaker and rebuild the model using Amazon SageMaker built-in algorithms
- D) Use encryption to protect the confidential information in the model responses

**Correct Answer: B**

**Explanation:**

Amazon Bedrock Guardrails detects sensitive information such as personally identifiable information (PIIs) in input prompts or model responses. You can also configure sensitive information specific to your use case using regular expressions (regex). This option dynamically scans and redacts confidential information from the model's responses, providing a practical and efficient solution without needing to retrain or delete the model.

**Why the other options are incorrect:**

- **A)** Retraining from scratch is highly resource-intensive and time-consuming. The cost and effort may outweigh the benefits when more efficient methods exist.
- **C)** Swapping to Amazon SageMaker involves significant model development, training, and testing effort -- not an efficient solution.
- **D)** Encryption protects data during storage and transmission but does not prevent the model from generating responses that contain confidential information in the output.

---

### Question 4
**Domain:** Fundamentals of AI and ML

> A financial services company is building machine learning models to predict customer churn and detect fraudulent transactions. The team needs to understand which methods fall under supervised learning.
>
> Which of the following are examples of supervised learning? (Select TWO)

- A) Neural network :white_check_mark:
- B) Linear regression :white_check_mark:
- C) Clustering
- D) Association rule learning
- E) Document classification

**Correct Answer: A, B**

**Explanation:**

Supervised learning algorithms train on sample data that specifies both the algorithm's input and output (labeled data).

- **Linear regression** is a supervised learning model that predicts a value from a continuous scale based on one or more inputs (e.g., predicting house prices).
- **Neural networks** are more complex supervised learning techniques that take given inputs and perform one or more layers of mathematical transformation to produce a given outcome (e.g., predicting a digit from a handwritten image).

**Why the other options are incorrect:**

- **C) Clustering** -- An unsupervised learning technique that groups data inputs so they may be categorized as a whole.
- **D) Association rule learning** -- An unsupervised learning technique that uncovers rule-based relationships between inputs (e.g., market basket analysis).
- **E) Document classification** -- An example of semi-supervised learning, which applies both supervised and unsupervised learning techniques together.

---

### Question 5
**Domain:** Applications of Foundation Models

> A company needs large, high-quality, and labeled datasets for training its machine learning models. Which Amazon SageMaker service helps build high-quality training datasets?

- A) Amazon SageMaker Canvas
- B) Amazon SageMaker Feature Store
- C) Amazon SageMaker Ground Truth :white_check_mark:
- D) Amazon SageMaker JumpStart

**Correct Answer: C**

**Explanation:**

Amazon SageMaker Ground Truth helps you build high-quality training datasets for your machine learning models. With Ground Truth, you can use workers from Amazon Mechanical Turk, a vendor company, or a private workforce, along with machine learning, to create labeled datasets. You can choose from built-in task types or build custom labeling workflows.

**Why the other options are incorrect:**

- **A) SageMaker Canvas** -- A no-code interface for creating ML models without writing code. Not a data labeling service.
- **B) SageMaker Feature Store** -- A repository to store, share, and manage features for ML models -- not for labeling data.
- **D) SageMaker JumpStart** -- An ML hub for evaluating, comparing, and deploying Foundation Models and pre-built solutions -- not for dataset labeling.

---

### Question 6
**Domain:** Applications of Foundation Models

> A financial services company needs to monitor and track the performance and usage of ML models hosted on endpoints in Amazon SageMaker for real-time credit risk assessments and fraud detection.
>
> What do you recommend?

- A) Amazon SageMaker Model Dashboard :white_check_mark:
- B) Amazon SageMaker Ground Truth
- C) Amazon SageMaker Clarify
- D) Amazon SageMaker JumpStart

**Correct Answer: A**

**Explanation:**

Amazon SageMaker Model Dashboard is a centralized portal accessible from the SageMaker console where you can view, search, and explore all models in your account. You can track which models are deployed for inference, whether in batch transform jobs or hosted on endpoints. It helps track performance metrics such as CPU, GPU, disk, and memory utilization in real time.

**Why the other options are incorrect:**

- **B) SageMaker Ground Truth** -- Used for human-in-the-loop data labeling, not model monitoring.
- **C) SageMaker Clarify** -- Helps identify potential bias during data preparation and provides model explainability, not endpoint monitoring.
- **D) SageMaker JumpStart** -- An ML hub for Foundation Models and pre-built solutions, not a monitoring dashboard.

---

### Question 7
**Domain:** Fundamentals of AI and ML

> A company is developing an NLP solution and exploring model architectures for tasks such as language translation, summarization, and text generation. They need to understand how Transformer models process and generate text.
>
> Which of the following best summarizes the way Transformer models work?

- A) Transformer models work by learning a compact representation of data called latent space
- B) Transformer models work by training two neural networks in a competitive manner
- C) Transformer models create new data by iteratively making controlled random changes to an initial data sample
- D) Transformer models use a self-attention mechanism and implement contextual embeddings :white_check_mark:

**Correct Answer: D**

**Explanation:**

Transformer models rely on a mechanism called self-attention to process input data, allowing them to understand and generate language effectively. Self-attention allows the model to weigh the importance of different words in a sentence, capturing complex dependencies regardless of word position. Positional encodings provide word order information, and the encoder-decoder architecture enables effective sequence processing and generation.

**Why the other options are incorrect:**

- **A)** Describes Variational Autoencoders (VAEs), which learn a compact latent space representation using encoder-decoder neural networks.
- **B)** Describes Generative Adversarial Networks (GANs), which train a generator and discriminator in competition.
- **C)** Describes Diffusion models, which corrupt data with noise and learn to reverse the process to generate new data.

---

### Question 8
**Domain:** Fundamentals of Generative AI

> A data analytics company needs to store and retrieve embeddings efficiently for NLP and document search use cases using Knowledge Bases in Amazon Bedrock.
>
> Which is the default vector database supported by Knowledge Bases for Amazon Bedrock?

- A) MongoDB
- B) Redis Enterprise Cloud
- C) Amazon Aurora
- D) OpenSearch Serverless vector store :white_check_mark:

**Correct Answer: D**

**Explanation:**

Knowledge Bases for Amazon Bedrock handles the entire ingestion workflow of converting documents into embeddings and storing them in a vector database. It supports popular databases including Amazon OpenSearch Serverless, Pinecone, Redis Enterprise Cloud, Amazon Aurora, and MongoDB. **If you do not have an existing vector database, Amazon Bedrock creates an OpenSearch Serverless vector store for you** -- making it the default.

**Why the other options are incorrect:**

- **A, B, C)** While MongoDB, Redis Enterprise Cloud, and Amazon Aurora are all supported vector databases, none of them is the default. OpenSearch Serverless is automatically created when no existing vector database is specified.

---

### Question 9
**Domain:** Fundamentals of AI and ML

> A content marketing company notices that a generative AI model can only consider a certain amount of text at once before generating its response.
>
> What is this concept called that defines the maximum amount of text or characters the AI model can process at one time?

- A) Context window :white_check_mark:
- B) Character count
- C) Embeddings
- D) Tokens

**Correct Answer: A**

**Explanation:**

The context window defines how much text (measured in tokens) the AI model can process at one time to generate a coherent output. It determines the limit of input data that the model can use to understand context, maintain conversation history, or generate relevant responses.

**Why the other options are incorrect:**

- **B) Character count** -- Measures the number of characters in text, but AI models do not limit input based on characters alone. They rely on tokens.
- **C) Embeddings** -- Numerical representations that encode semantic meaning of words or phrases. They don't define the amount of text processed at once.
- **D) Tokens** -- Individual units of text that the model processes. Tokens are components *within* the context window, not the concept that describes the total capacity.

---

### Question 10
**Domain:** Fundamentals of Generative AI

> Which of the following embedding models would be most suitable for differentiating the contextual meanings of words when applied to different phrases?

- A) Singular Value Decomposition (SVD)
- B) Principal Component Analysis (PCA)
- C) Word2Vec
- D) Bidirectional Encoder Representations from Transformers (BERT) :white_check_mark:

**Correct Answer: D**

**Explanation:**

BERT is specifically designed to capture the contextual meaning of words by looking at both the words that come before and after them (bidirectional context). Unlike older models that use static embeddings, BERT creates dynamic word embeddings that change depending on the surrounding text, making it ideal for understanding nuances and subtleties of language.

**Why the other options are incorrect:**

- **A) SVD** -- A matrix decomposition method used in data compression and noise reduction. Not designed for dynamic, context-dependent word meanings.
- **B) PCA** -- A statistical method for reducing dimensions of large datasets. Does not understand or differentiate contextual meanings of words.
- **C) Word2Vec** -- Creates static vector representations where each word has a single embedding regardless of context, making it less effective at differentiating words with multiple meanings.

---

### Question 11
**Domain:** Fundamentals of AI and ML

> An e-commerce company uses a chatbot powered by Amazon Bedrock. They want the chatbot to continuously learn and improve from real-time customer interactions.
>
> Which approach would be the most suitable for enabling ongoing self-improvement?

- A) Leverage reinforcement learning (RL), where rewards are generated from positive customer feedback :white_check_mark:
- B) Leverage incremental training
- C) Leverage supervised learning using the latest datasets
- D) Leverage transfer learning

**Correct Answer: A**

**Explanation:**

Reinforcement learning is the most suitable approach for self-improvement in this context. The chatbot can learn from customer interactions in real-time, with positive customer feedback serving as a reward signal. The chatbot adapts its behavior based on rewards or penalties, refining its conversational skills through continuous feedback loops.

**Why the other options are incorrect:**

- **B) Incremental training** -- Allows updating with new data but may not be sufficient for optimizing in real-time without direct feedback signals.
- **C) Supervised learning** -- Requires extensive labeled datasets and retraining, making it less adaptive in real-time environments.
- **D) Transfer learning** -- Applies knowledge from one domain to another but does not provide a framework for continuous self-improvement based on ongoing interactions.

---

### Question 12
**Domain:** Fundamentals of Generative AI

> What is a key difference between Foundation Models (FMs) and Large Language Models (LLMs) in the context of generative AI?

- A) LLMs are pre-trained on massive datasets and can be fine-tuned, whereas FMs are not pre-trained and are built from scratch
- B) Foundation Models serve as a broad base for various AI applications, whereas LLMs are specialized for understanding and generating human language :white_check_mark:
- C) Foundation Models are specifically designed for text generation, while LLMs can generate images, videos, and audio
- D) Foundation Models are only used in academic research, while LLMs are used in commercial applications

**Correct Answer: B**

**Explanation:**

Foundation Models provide a broad base with generalized capabilities that can be applied to various tasks such as NLP, question answering, and image classification. In contrast, Large Language Models are specifically designed for tasks involving understanding and generation of human language -- making them more specialized (summarization, text generation, classification, open-ended conversation, and information extraction).

**Why the other options are incorrect:**

- **A)** Both FMs and LLMs are pre-trained on massive datasets. The distinction is about general purpose vs. specialized nature.
- **C)** FMs and LLMs can both be used for a variety of generative tasks, not limited to specific types.
- **D)** Both are used in various settings, including academic research and commercial applications.

---

### Question 13
**Domain:** Applications of Foundation Models

> A retail company needs to perform sentiment analysis for its customer service audio calls. Which AWS services would you recommend?

- A) Amazon Transcribe and Amazon Comprehend :white_check_mark:
- B) Amazon Rekognition and Amazon Transcribe
- C) Amazon Transcribe and Amazon Translate
- D) Amazon Translate and Amazon Comprehend

**Correct Answer: A**

**Explanation:**

Amazon Transcribe converts audio input into text. Amazon Comprehend is an NLP service that uses machine learning to find insights and relationships in text, including sentiment analysis. By combining them, you can convert audio calls to text and then perform sentiment analysis on the resulting text.

**Why the other options are incorrect:**

- **B)** Amazon Rekognition is for image and video analysis -- not useful for audio files.
- **C)** Amazon Translate is for language translation, not sentiment analysis.
- **D)** Amazon Translate cannot convert audio to text; it only translates text. Without Transcribe, there's no way to process the audio.

---

### Question 14
**Domain:** Applications of Foundation Models

> A tech company needs a database for RAG with Amazon Bedrock that can handle fast index lookups, similarity searches, and rank results by relevance.
>
> Which database solution would be most appropriate?

- A) Amazon DynamoDB
- B) Amazon OpenSearch Service :white_check_mark:
- C) Amazon DocumentDB (with MongoDB compatibility)
- D) Amazon Aurora

**Correct Answer: B**

**Explanation:**

Amazon OpenSearch Service is specifically built for search and analytics workloads, including fast index lookups and similarity scoring. It supports full-text search, vector search, and advanced data indexing -- essential for Retrieval-Augmented Generation (RAG). It enables the model to quickly find and rank relevant documents based on similarity to the query.

**Why the other options are incorrect:**

- **A) DynamoDB** -- Designed for fast key-value retrieval, but does not natively support advanced search capabilities or similarity scoring.
- **C) DocumentDB** -- Primarily for semi-structured JSON data, not optimized for full-text or similarity searches.
- **D) Aurora** -- Optimized for OLTP workloads and transactional integrity, not for search and retrieval tasks.

---

### Question 15
**Domain:** Fundamentals of AI and ML

> In generative AI, there is a specific concept used to represent words, sub-words, or characters that the model processes as discrete units of text. What is this concept called?

- A) Context window
- B) Embeddings
- C) Tokens :white_check_mark:
- D) Vectors

**Correct Answer: C**

**Explanation:**

Tokens are the fundamental units of text that the AI model processes. They can be whole words, parts of words (sub-words), or even single characters, depending on the model's tokenization strategy. The model breaks down text into tokens to better understand structure, meaning, and context.

**Why the other options are incorrect:**

- **A) Context window** -- The total amount of text (measured in tokens) a model can process at once, not the individual units.
- **B) Embeddings** -- Numerical vector representations of tokens used to capture semantic relationships, not the units themselves.
- **D) Vectors** -- Mathematical constructs representing relationships between words in the embedding space, not the discrete text units.

---

### Question 16
**Domain:** Security, Compliance, and Governance for AI Solutions

> A media company's AI-based image generation model consistently produces biased outputs due to imbalanced training data that underrepresents certain demographic groups.
>
> What would be the most suitable strategy to address the data imbalance?

- A) Augment the data by generating new instances of data for underrepresented groups :white_check_mark:
- B) Leverage human intervention to manually correct the imbalanced dataset
- C) Apply model regularization techniques to address the imbalance in data
- D) Use another model that can handle the imbalance in data

**Correct Answer: A**

**Explanation:**

Data augmentation creates additional examples to balance the dataset, increasing representation of underrepresented groups. This widely used technique helps the model learn to generate fair and unbiased images that reflect the diversity of the population.

**Why the other options are incorrect:**

- **B)** Manual intervention is not practical for large datasets, is prone to human error, and is not scalable.
- **C)** Regularization techniques (L1, L2) are designed to prevent overfitting, not to address data imbalance or bias.
- **D)** Switching models does not address the underlying problem of biased input data.

---

### Question 17
**Domain:** Fundamentals of AI and ML

> A developer is working on an AI application for predicting customer churn. What should the developer ask the research team to do to ensure the best model is selected?

- A) Define the target audience of the application broadly
- B) Determine the cost constraints for model training
- C) Define the use case of the application narrowly :white_check_mark:
- D) Identify potential data sources for the application

**Correct Answer: C**

**Explanation:**

A narrowly defined use case provides clear and specific requirements for the application, helping the research team understand exactly what the model needs to accomplish. This clarity is crucial for selecting the most appropriate model that fits the specific needs and constraints of the application.

**Why the other options are incorrect:**

- **A)** Defining the target audience broadly leads to ambiguity and lack of focus.
- **B)** Cost constraints affect budget management but don't directly influence the selection of the best model.
- **D)** Identifying data sources is a preliminary step for data collection, not directly for model selection.

---

### Question 18
**Domain:** Security, Compliance, and Governance for AI Solutions

> A company wants to evaluate and improve its text translation model's performance. Which metric would be most appropriate for assessing translation accuracy?

- A) Accuracy
- B) BLEU (Bilingual Evaluation Understudy) score :white_check_mark:
- C) BERT score
- D) ROUGE (Recall-Oriented Understudy for Gisting Evaluation)

**Correct Answer: B**

**Explanation:**

BLEU score is one of the most widely used metrics for evaluating machine translation quality. It compares machine-generated translations with one or more human reference translations by analyzing n-gram overlaps. A higher BLEU score indicates closer alignment with the reference translation. A BLEU score is typically between 0-1.

**Why the other options are incorrect:**

- **A) Accuracy** -- Too simplistic for translation; it's typically used for classification tasks and doesn't account for syntax and grammar complexities.
- **C) BERT score** -- More advanced but less established than BLEU for translation evaluation. BLEU remains the standard.
- **D) ROUGE** -- Primarily used for evaluating text summarization quality, not specifically tailored for translation tasks.

---

### Question 19
**Domain:** Guidelines for Responsible AI

> A streaming service wants to classify movies into 20 categories and needs a model that provides clear insights into how classification decisions are made (transparency and interpretability).
>
> Which machine learning algorithm would be the most suitable?

- A) Support Vector Machines (SVMs)
- B) Neural Networks
- C) Decision Trees :white_check_mark:
- D) Logistic Regression

**Correct Answer: C**

**Explanation:**

Decision Trees are highly interpretable models that provide a clear, tree-like structure where each branch represents a decision rule. This makes it easy to understand how different features contribute to the final classification, offering high transparency and interpretability.

**Why the other options are incorrect:**

- **A) SVMs** -- Effective for classification but do not inherently provide an interpretable way to understand the decision-making process via hyperplanes.
- **B) Neural Networks** -- Powerful but considered "black-box" models due to multiple layers and nonlinear transformations, making them difficult to interpret.
- **D) Logistic Regression** -- Primarily designed for binary classification and may not perform effectively with 20 categories. It also doesn't provide an easily interpretable structure for multiclass problems.

---

### Question 20
**Domain:** Fundamentals of AI and ML

> A manufacturing company needs to evaluate its material classification model's performance with detailed insights into accuracy and classification errors.
>
> Which option would be the most suitable?

- A) Root Mean Squared Error (RMSE)
- B) Confusion matrix :white_check_mark:
- C) Correlation matrix
- D) Mean Absolute Error (MAE)

**Correct Answer: B**

**Explanation:**

A confusion matrix is specifically designed to evaluate classification model performance by displaying true positives, true negatives, false positives, and false negatives. It provides a detailed breakdown across all classes, showing where the model performs well and where it needs adjustments.

**Why the other options are incorrect:**

- **A) RMSE** -- Used for regression models, measuring continuous outcomes, not discrete class predictions.
- **C) Correlation matrix** -- Measures statistical correlation between variables, not classification performance.
- **D) MAE** -- Used in regression tasks for continuous variable predictions, not for categorical classification.

---

### Question 21
**Domain:** Fundamentals of AI and ML

> An e-commerce company wants to analyze thousands of customer reviews daily to understand customer sentiment (positive, negative, neutral, or mixed).
>
> Which services would you recommend? (Select TWO)

- A) Amazon Personalize
- B) Amazon Textract
- C) Amazon Bedrock :white_check_mark:
- D) Amazon Rekognition
- E) Amazon Comprehend :white_check_mark:

**Correct Answer: C, E**

**Explanation:**

- **Amazon Comprehend** is an NLP service specifically designed for sentiment analysis, entity recognition, key phrase extraction, and language detection. It can directly determine the overall sentiment of text.
- **Amazon Bedrock** provides access to foundation models that can be configured for NLP tasks including sentiment analysis, offering more customizable solutions.

**Why the other options are incorrect:**

- **A) Amazon Personalize** -- Provides personalized recommendations, not NLP or sentiment analysis.
- **B) Amazon Textract** -- An OCR service for extracting text from documents, not for analyzing sentiment.
- **D) Amazon Rekognition** -- Designed for image and video analysis, not text analysis.

---

### Question 22
**Domain:** Fundamentals of AI and ML

> Which explanation BEST describes the differences between Shapley values and Partial Dependence Plots (PDP) in the context of model explainability?

- A) Both are global explainability methods; Shapley values are computationally less expensive than PDP
- B) Shapley values provide a local explanation by quantifying each feature's contribution to a specific instance; PDP provides a global explanation showing the marginal effect across the dataset :white_check_mark:
- C) Shapley values provide a global view; PDP offers a local view
- D) Shapley values provide visual interpretation; PDP provides numeric values

**Correct Answer: B**

**Explanation:**

- **Shapley values** are a local interpretability method that explains individual predictions by assigning each feature a contribution score based on its marginal effect.
- **PDP (Partial Dependence Plots)** provide a global view by illustrating how the predicted outcome changes as a single feature varies across its range, holding all others constant.

**Why the other options are incorrect:**

- **A)** Shapley values are computationally *more* intensive than PDP, and they are not purely global methods.
- **C)** This reverses the concepts -- Shapley values are local, PDP is global.
- **D)** Shapley values provide quantitative contributions, not just visual; PDP provides visual insight, not just numeric.

---

### Question 23
**Domain:** Applications of Foundation Models

> A company is deploying a generative AI model on Amazon Bedrock and needs to reduce cost while using prompt examples of up to 10 sample tasks as part of each input.
>
> Which approach would be the most effective in minimizing costs?

- A) Reduce the batch size while training the model
- B) Reduce the temperature inference parameter
- C) Reduce the top-P inference parameter
- D) Reduce the number of tokens in the input :white_check_mark:

**Correct Answer: D**

**Explanation:**

The cost of using a generative AI model on Amazon Bedrock is directly proportional to the number of tokens processed. By reducing the input length (fewer prompt examples or shorter examples), the company decreases computational power required per request, thereby lowering costs.

**Why the other options are incorrect:**

- **A)** Batch size affects training, not inference cost. You cannot train base FMs on Bedrock -- only customize them.
- **B)** Temperature affects creativity/randomness of output but has no effect on cost.
- **C)** Top-P affects output diversity but does not influence processing cost.

---

### Question 24
**Domain:** Fundamentals of AI and ML

> Which option best summarizes the differences between model inference and model evaluation in the context of generative AI?

- A) Model evaluation is evaluating and comparing model outputs to find the best model; model inference is generating an output (response) from a given input (prompt) :white_check_mark:
- B) Both refer to evaluating and comparing model outputs
- C) Model inference is evaluating; model evaluation is generating output
- D) Both refer to generating output from input

**Correct Answer: A**

**Explanation:**

- **Model inference** is the process of a model generating an output (response) from a given input (prompt).
- **Model evaluation** is the process of evaluating and comparing model outputs to determine the best model for a use case.

**Why the other options are incorrect:**

- **B, C, D)** These options either reverse the definitions or incorrectly equate the two concepts. Inference and evaluation serve fundamentally different purposes.

---

### Question 25
**Domain:** Fundamentals of AI and ML

> A retail analytics company is calculating statistical measures to summarize data and using visualizations to uncover patterns and trends before model development.
>
> Which phase of the data science process does this belong to?

- A) Model Evaluation
- B) Data Preparation
- C) Exploratory Data Analysis (EDA) :white_check_mark:
- D) Data Augmentation

**Correct Answer: C**

**Explanation:**

EDA involves examining data through statistical summaries and visualizations to identify patterns, detect anomalies, and form hypotheses. It serves as the foundation for building predictive models by providing deep understanding of the data.

**Why the other options are incorrect:**

- **A) Model Evaluation** -- Assessing model performance using metrics like accuracy, precision, recall -- happens after model training.
- **B) Data Preparation** -- Involves cleaning and preprocessing data (handling missing values, removing duplicates), not calculating statistics and visualizing data.
- **D) Data Augmentation** -- A technique to artificially increase training dataset size, not related to exploratory analysis.

---

### Question 26
**Domain:** Applications of Foundation Models

> A company wants a unified search solution connecting multiple data repositories, third-party document repositories, and FAQs.
>
> Which ML-powered AWS service offers these search features?

- A) Amazon SageMaker Data Wrangler
- B) Amazon Comprehend
- C) Amazon Kendra :white_check_mark:
- D) Amazon Textract

**Correct Answer: C**

**Explanation:**

Amazon Kendra is a highly accurate enterprise search service powered by ML. It allows developers to add search capabilities to applications, discovering information across manuals, research reports, FAQs, HR documentation, and various systems (S3, SharePoint, Salesforce, ServiceNow, RDS, OneDrive). It uses ML algorithms to understand context and return the most relevant results.

**Why the other options are incorrect:**

- **A) SageMaker Data Wrangler** -- For data preparation and feature engineering, not search.
- **B) Amazon Comprehend** -- Extracts insights from text (NLP) but is not a search service.
- **D) Amazon Textract** -- Extracts text from scanned documents (OCR), not a search service.

---

### Question 27
**Domain:** Fundamentals of Generative AI

> Which statement is correct regarding Foundation Models (FMs) in the context of generative AI?

- A) FMs use supervised learning to create labels; fine-tuning is supervised
- B) FMs use supervised learning to create labels; fine-tuning is self-supervised
- C) FMs use self-supervised learning to create labels; fine-tuning is supervised :white_check_mark:
- D) FMs use self-supervised learning to create labels; fine-tuning is self-supervised

**Correct Answer: C**

**Explanation:**

Foundation models use **self-supervised learning** to create labels from input data -- no one has instructed or trained the model with labeled training data sets. Self-supervised learning creates implicit labels from unstructured data.

**Fine-tuning** is a **supervised learning** process where you provide labeled data to train a model on specific tasks. The model learns to associate which types of outputs should be generated for certain inputs.

**Why the other options are incorrect:**

- **A)** FMs use self-supervised learning, not supervised learning, for initial training.
- **B)** FMs use self-supervised learning (not supervised), and fine-tuning is supervised (not self-supervised).
- **D)** Fine-tuning is a supervised process, not self-supervised.

---

### Question 28
**Domain:** Applications of Foundation Models

> A biotechnology company wants to enhance a Foundation Model in Amazon Bedrock to become a domain expert in genomics.
>
> Which approaches would be the most effective? (Select TWO)

- A) Supervised Learning
- B) Incremental Learning
- C) Continued Pre-Training :white_check_mark:
- D) Domain Adaptation Fine-Tuning :white_check_mark:
- E) Reinforcement Learning

**Correct Answer: C, D**

**Explanation:**

- **Continued Pre-Training** further trains the model on a large corpus of domain-specific data, enhancing its understanding of domain-specific terms, jargon, and context.
- **Domain Adaptation Fine-Tuning** adjusts the model's parameters using domain-specific data, helping it learn the nuances and terminology specific to the domain while retaining general knowledge.

**Why the other options are incorrect:**

- **A) Supervised Learning** -- Task-specific and requires large amounts of labeled domain data; doesn't generalize as well for overall domain expertise.
- **B) Incremental Learning** -- Helps adapt to new data over time but lacks the focused, intensive learning required for domain specialization.
- **E) Reinforcement Learning** -- Focuses on learning optimal behaviors through rewards/penalties in interactive scenarios, not domain knowledge acquisition.

---

### Question 29
**Domain:** Fundamentals of AI and ML

> Which of the following is the best-fit for the Amazon Forecast service?

- A) Predict product demand to accurately vary inventory and pricing at different store locations :white_check_mark:
- B) Recommendations tailored to a user's profile, behavior, preferences, and history
- C) Design conversational solutions that respond to frequently asked questions
- D) Detect and categorize toxic audio and foster a safe online environment

**Correct Answer: A**

**Explanation:**

Amazon Forecast is a fully managed service that uses statistical and ML algorithms for highly accurate time-series forecasts. Common use cases include retail demand planning, supply chain planning, resource planning, and operational planning.

**Why the other options are incorrect:**

- **B)** Amazon Personalize handles tailored recommendations.
- **C)** Amazon Lex is designed for conversational interfaces.
- **D)** Amazon Transcribe can detect and categorize toxic audio.

---

### Question 30
**Domain:** Security, Compliance, and Governance for AI Solutions

> A company needs to monitor the input data and output responses of its ML models on Amazon Bedrock for compliance and auditing.
>
> Which solution would be the most suitable?

- A) AWS Config
- B) Enable model invocation logging :white_check_mark:
- C) AWS CloudTrail
- D) Amazon EventBridge

**Correct Answer: B**

**Explanation:**

Model invocation logging allows you to collect invocation logs, model input data, and model output data for all invocations in your AWS account. You can capture the full request data, response data, and metadata. Logs can be sent to Amazon CloudWatch Logs or Amazon S3. This is disabled by default.

**Why the other options are incorrect:**

- **A) AWS Config** -- Monitors resource configurations and compliance, not model input/output data.
- **C) AWS CloudTrail** -- Tracks API calls and access, but does not capture actual input and output data of model invocations.
- **D) Amazon EventBridge** -- Reacts to events and triggers workflows, but does not provide detailed logging of input/output data.

---

### Question 31
**Domain:** Fundamentals of Generative AI

> A legal research firm wants to implement fully managed RAG workflow support in Amazon Bedrock.
>
> What solution would you recommend?

- A) Continued pretraining in Amazon Bedrock
- B) Knowledge Bases for Amazon Bedrock :white_check_mark:
- C) Watermark detection for Amazon Bedrock
- D) Guardrails for Amazon Bedrock

**Correct Answer: B**

**Explanation:**

Knowledge Bases for Amazon Bedrock provides FMs and agents with contextual information from your company's private data sources for RAG. It handles the entire ingestion workflow -- converting documents into embeddings and storing them in a specialized vector database.

**Why the other options are incorrect:**

- **A) Continued pretraining** -- Familiarizes a model with domain-specific data but does not implement RAG workflow.
- **C) Watermark detection** -- Identifies images generated by Amazon Titan Image Generator. Unrelated to RAG.
- **D) Guardrails** -- Implements safeguards by filtering harmful content and redacting PII. Not a RAG solution.

---

### Question 32
**Domain:** Fundamentals of Generative AI

> Which service is specifically designed to provide insights into model predictions by explaining how input features contribute to the final output?

- A) Amazon SageMaker Model Monitor
- B) Amazon SageMaker Feature Store
- C) Amazon SageMaker Canvas
- D) Amazon SageMaker Clarify :white_check_mark:

**Correct Answer: D**

**Explanation:**

Amazon SageMaker Clarify provides tools to explain how ML models make predictions. It uses a model-agnostic feature attribution approach (based on SHAP/Shapley values) to understand why a model made a prediction. It also produces Partial Dependence Plots (PDPs) showing the marginal effect features have on predicted outcomes.

**Why the other options are incorrect:**

- **A) Model Monitor** -- Monitors quality of ML models in production, not feature contribution analysis.
- **B) Feature Store** -- A repository for storing, sharing, and managing ML features, not explainability.
- **C) Canvas** -- A no-code interface for building ML models, not for model explainability.

---

### Question 33
**Domain:** Fundamentals of AI and ML

> The marketing department wants creative scripts for an ad campaign using Amazon Bedrock. What do you recommend?

- A) Use higher Top-P
- B) Use higher Temperature :white_check_mark:
- C) Use lower Top-P
- D) Use lower Temperature

**Correct Answer: B**

**Explanation:**

Temperature is a value between 0 and 1 that regulates the creativity of the model's responses. A **higher temperature** produces more creative or different responses for the same prompt. A **lower temperature** produces more deterministic responses.

**Why the other options are incorrect:**

- **A, C)** Top-P represents the percentage of most-likely candidates for the next token. It controls output diversity but is not the primary parameter for creativity.
- **D)** Lower temperature produces more deterministic, less creative responses -- the opposite of what's needed.

---

### Question 34
**Domain:** Applications of Foundation Models

> Which AWS service powers Amazon Q Developer?

- A) Amazon Bedrock :white_check_mark:
- B) Amazon SageMaker Jumpstart
- C) Amazon Q Apps
- D) Amazon Kendra

**Correct Answer: A**

**Explanation:**

Amazon Q Developer is a generative AI-powered conversational assistant that helps you understand, build, extend, and operate AWS applications. It is powered by Amazon Bedrock.

**Why the other options are incorrect:**

- **B) SageMaker JumpStart** -- An ML hub for Foundation Models and pre-built solutions, but doesn't power Amazon Q.
- **C) Amazon Q Apps** -- A capability within Amazon Q Business for building generative AI apps, not the underlying engine.
- **D) Amazon Kendra** -- An intelligent search service, not the engine powering Amazon Q Developer.

---

### Question 35
**Domain:** Security, Compliance, and Governance for AI Solutions

> Which of the following are correct statements regarding the AWS Global Infrastructure? (Select TWO)

- A) Each AWS Region consists of a minimum of two Availability Zones (AZ)
- B) Each AWS Region consists of two or more Edge Locations
- C) Each Availability Zone (AZ) consists of two or more discrete data centers
- D) Each AWS Region consists of a minimum of three Availability Zones (AZ) :white_check_mark:
- E) Each Availability Zone (AZ) consists of one or more discrete data centers :white_check_mark:

**Correct Answer: D, E**

**Explanation:**

- Each AWS Region consists of a **minimum of three**, isolated, and physically separate AZs within a geographic area.
- An Availability Zone is **one or more** discrete data centers with redundant power, networking, and connectivity.

**Why the other options are incorrect:**

- **A)** Minimum is three AZs per region, not two.
- **B)** Edge Locations are independent of Regions and not organized this way.
- **C)** Each AZ consists of *one or more* data centers, not necessarily two or more.

---

### Question 36
**Domain:** Security, Compliance, and Governance for AI Solutions

> Which best describes the division of responsibilities in the AWS shared responsibility model?

- A) AWS configures customer app security; customer manages underlying hardware
- B) AWS handles all security aspects; customer only manages virtual machines
- C) AWS is responsible for security "of" the cloud (infrastructure, hardware, software); customer is responsible for security "in" the cloud (data, applications, access management) :white_check_mark:
- D) Customers ensure physical security of data centers; AWS monitors network traffic

**Correct Answer: C**

**Explanation:**

In the shared responsibility model, AWS is responsible for the **security of the cloud** (physical security of data centers, networking infrastructure, hardware). The customer is responsible for **security in the cloud** (data, access/identity management, network configuration, application security).

**Why the other options are incorrect:**

- **A)** AWS manages infrastructure; customers configure their own app security.
- **B)** AWS does not handle all security -- customers must manage their own data encryption, access, and application security.
- **D)** AWS is responsible for physical security of data centers, not customers.

---

### Question 37
**Domain:** Fundamentals of Generative AI

> A manufacturing company wants to create a generative AI application on Amazon Bedrock that automates monitoring of inventory levels, sales data, supply chain information, and recommends optimal reorder points.
>
> What do you recommend?

- A) Watermark detection for Amazon Bedrock
- B) Agents for Amazon Bedrock :white_check_mark:
- C) Knowledge Bases for Amazon Bedrock
- D) Guardrails for Amazon Bedrock

**Correct Answer: B**

**Explanation:**

Agents for Amazon Bedrock are fully managed capabilities for creating generative AI-based applications that can complete complex, multi-step tasks autonomously or semi-autonomously. Amazon Bedrock manages prompt engineering, memory, monitoring, encryption, user permissions, and API invocation.

**Why the other options are incorrect:**

- **A) Watermark detection** -- For identifying images generated by Amazon Titan Image Generator. Not applicable here.
- **C) Knowledge Bases** -- Provides contextual information for RAG, but doesn't automate multi-step tasks.
- **D) Guardrails** -- Implements safeguards by filtering harmful content and PII -- not for task automation.

---

### Question 38
**Domain:** Applications of Foundation Models

> A company processes datasets of less than 1 GB (daily sales records, customer logs) and does not require immediate responses. Which inference method is most suitable?

- A) Asynchronous inference :white_check_mark:
- B) Serverless inference
- C) Real-time inference
- D) Batch inference

**Correct Answer: A**

**Explanation:**

Asynchronous inference allows processing smaller payloads without requiring real-time responses by queuing requests and handling them in the background. It is cost-effective and efficient when some delay is acceptable and payload size is less than 1 GB.

**Why the other options are incorrect:**

- **B) Serverless inference** -- Good for unpredictable/sporadic workloads but may not be as cost-effective for predictable workloads with acceptable delays.
- **C) Real-time inference** -- Optimized for low latency with immediate responses needed -- overkill and more expensive for this use case.
- **D) Batch inference** -- Typically more efficient for larger payloads (several GB+). For <1 GB payloads, batch inference may be overkill.

---

### Question 39
**Domain:** Fundamentals of AI and ML

> A company wants its models across departments to learn from each other by sharing data insights and patterns.
>
> Which approach would be the most suitable for cross-model optimization?

- A) Self-supervised learning
- B) Reinforcement learning
- C) Incremental training
- D) Transfer learning :white_check_mark:

**Correct Answer: D**

**Explanation:**

Transfer learning allows a model to utilize knowledge learned from one task or dataset to improve performance on a new, related task. It enables optimization by adapting insights from the latest data generated by other models, reducing the need for extensive data and computational resources while ensuring shared knowledge across domains.

**Why the other options are incorrect:**

- **A) Self-supervised learning** -- Learns from unlabeled data but doesn't address cross-model knowledge sharing.
- **B) Reinforcement learning** -- Learns through rewards/penalties in interactive scenarios, not cross-model data sharing.
- **C) Incremental training** -- Updates a single model with new data but doesn't facilitate learning from other models' data.

---

### Question 40
**Domain:** Security, Compliance, and Governance for AI Solutions

> A company wants to use few-shots prompting to help an Amazon Bedrock chatbot recognize user intent (refund, product info, technical support).
>
> What type of data should the few-shots examples include?

- A) User-input along with the correct user intent :white_check_mark:
- B) Model-response along with the correct user intent
- C) User-input along with the correct model-response
- D) User-input along with model-response

**Correct Answer: A**

**Explanation:**

Few-shots prompting involves providing examples that include both the user-input and the correct user intent. These examples help the model learn how to map various user queries to their appropriate intents, enabling it to generalize to new, unseen queries.

**Why the other options are incorrect:**

- **B)** Does not include the original user-input, which is essential for learning the relationship between queries and intent.
- **C)** Focuses on matching input to specific responses rather than understanding intent.
- **D)** Does not specifically teach the model how to recognize and differentiate user intents.

---

### Question 41
**Domain:** Applications of Foundation Models

> Which of the following represent the correct options about Amazon Q vs Amazon Bedrock? (Select TWO)

- A) Both are generative AI-powered assistants that create pre-packaged applications
- B) With Amazon Bedrock, you can choose the underlying Foundation Model; Amazon Q does not allow this :white_check_mark:
- C) Amazon Bedrock is a generative AI-powered assistant; Amazon Q provides an environment to build/scale
- D) With Amazon Q, you can choose the underlying Foundation Model; Amazon Bedrock does not
- E) Amazon Q is a generative AI-powered assistant; Amazon Bedrock provides an environment to build and scale generative AI applications using FMs :white_check_mark:

**Correct Answer: B, E**

**Explanation:**

- **Amazon Q** is a generative AI-powered assistant for pre-packaged generative AI applications. You cannot choose the underlying Foundation Model.
- **Amazon Bedrock** provides an environment to build and scale generative AI applications using FMs. It offers a choice of high-performing FMs from leading AI companies through a single API.

**Why the other options are incorrect:**

- **A)** Only Amazon Q is a pre-packaged assistant; Bedrock is a platform for building applications.
- **C)** Reverses the descriptions of Q and Bedrock.
- **D)** You cannot choose the FM with Amazon Q; Amazon Bedrock does allow FM selection.

---

### Question 42
**Domain:** Fundamentals of Generative AI

> Which statement is correct regarding model customization methods for Amazon Bedrock?

- A) Continued pre-training uses unlabeled data; fine-tuning also uses unlabeled data
- B) Continued pre-training uses labeled data; fine-tuning also uses labeled data
- C) Continued pre-training uses unlabeled data; fine-tuning uses labeled data :white_check_mark:
- D) Continued pre-training uses labeled data; fine-tuning uses unlabeled data

**Correct Answer: C**

**Explanation:**

- **Continued pre-training** uses **unlabeled data** to familiarize the model with certain types of inputs and improve domain knowledge.
- **Fine-tuning** uses **labeled data** where you provide examples of inputs and expected outputs to improve performance on specific tasks.

**Why the other options are incorrect:**

- **A, B, D)** Each incorrectly pairs the data type (labeled/unlabeled) with the customization method.

---

### Question 43
**Domain:** Applications of Foundation Models

> Which of the following are CORRECT statements regarding Amazon ML services? (Select TWO)

- A) Amazon Comprehend service uses machine learning to find insights and relationships in text :white_check_mark:
- B) Amazon Polly is used to deploy high-quality, natural-sounding human voices in dozens of languages :white_check_mark:
- C) Amazon Comprehend uses machine learning models to convert speech to text
- D) Amazon Rekognition can extract key phrases and organize text files by topic
- E) Amazon Transcribe is for building conversational interfaces using voice and text

**Correct Answer: A, B**

**Explanation:**

- **Amazon Comprehend** is an NLP service using ML to find insights and relationships in text.
- **Amazon Polly** is a cloud service that converts text into lifelike speech in multiple languages.

**Why the other options are incorrect:**

- **C)** Amazon **Transcribe** (not Comprehend) converts speech to text.
- **D)** Amazon Rekognition is for image and video analysis, not text extraction or key phrases.
- **E)** Amazon **Lex** (not Transcribe) is for building conversational interfaces. Transcribe converts speech to text.

---

### Question 44
**Domain:** Fundamentals of AI and ML

> A company using Amazon Bedrock wants to regulate the number of most-likely candidates considered for the next word. Which inference parameter do you recommend?

- A) Temperature
- B) Top K :white_check_mark:
- C) Top P
- D) Stop sequences

**Correct Answer: B**

**Explanation:**

**Top K** represents the **number** of most likely candidates that the model considers for the next token. A lower value limits options to more likely outputs; a higher value allows less likely outputs.

**Why the other options are incorrect:**

- **A) Temperature** -- Regulates creativity/randomness of responses (0 to 1).
- **C) Top P** -- Represents the **percentage** of most likely candidates (not the number).
- **D) Stop sequences** -- Specifies character sequences that stop the model from generating further tokens.

---

### Question 45
**Domain:** Fundamentals of AI and ML

> What are the key constituents of a good prompting technique?

- A) Instructions, Parameters, Input data, Output Indicator
- B) Hyperparameters, Context, Input data, Output Indicator
- C) Instructions, Hyperparameters, Input data, Output Indicator
- D) Instructions, Context, Input data, Output Indicator :white_check_mark:

**Correct Answer: D**

**Explanation:**

The four constituents of a good prompting technique are:
1. **Instructions** -- A task for the model to do (description, how the model should perform)
2. **Context** -- External information to guide the model
3. **Input data** -- The input for which you want a response
4. **Output Indicator** -- The output type or format

**Why the other options are incorrect:**

- **A, B, C)** Hyperparameters and parameters control the training process and model behavior but are not part of the prompting technique itself.

---

### Question 46
**Domain:** Guidelines for Responsible AI

> A Large Language Model chatbot is generating responses that appear plausible and factual but are actually incorrect. What is this phenomenon called?

- A) Underfitting
- B) Hallucination :white_check_mark:
- C) Data drift
- D) Overfitting

**Correct Answer: B**

**Explanation:**

A "hallucination" is when a language model generates responses that sound plausible and appear factual but are actually false or unsupported by any underlying data. This occurs because the model relies on patterns learned during training rather than verified knowledge.

**Why the other options are incorrect:**

- **A) Underfitting** -- When a model is too simple to learn data complexities, leading to poor performance overall -- not specifically fabricated information.
- **C) Data drift** -- When input data distribution changes over time, degrading model performance -- not about generating plausible but false responses.
- **D) Overfitting** -- When a model learns training data too well and fails to generalize -- not specifically about generating plausible but incorrect information.

---

### Question 47
**Domain:** Guidelines for Responsible AI

> A security camera AI system is disproportionately flagging individuals from a specific ethnic group. The team suspects the issue is due to overrepresentation or underrepresentation in training data.
>
> Which type of bias is most likely responsible?

- A) Sampling bias :white_check_mark:
- B) Observer bias
- C) Measurement bias
- D) Confirmation bias

**Correct Answer: A**

**Explanation:**

Sampling bias occurs when the training data does not accurately reflect the diversity of the real-world population. If certain ethnic groups are underrepresented or overrepresented, the model may learn biased patterns, causing disproportionate flagging.

**Why the other options are incorrect:**

- **B) Observer bias** -- Relates to human errors during data analysis/observation; the AI processes data autonomously.
- **C) Measurement bias** -- Involves inaccuracies in data collection (faulty equipment), not demographic composition.
- **D) Confirmation bias** -- Involves selectively interpreting information to confirm existing beliefs; not applicable to the AI system in this scenario.

---

### Question 48
**Domain:** Security, Compliance, and Governance for AI Solutions

> A company wants to optimize their AWS environment for governance, cost savings, performance, security, and fault tolerance. Which AWS tool do you recommend?

- A) AWS Audit Manager
- B) AWS Trusted Advisor :white_check_mark:
- C) AWS CloudTrail
- D) AWS Config

**Correct Answer: B**

**Explanation:**

AWS Trusted Advisor provides guidance to help you provision resources following AWS best practices. It helps optimize your AWS environment in areas such as cost savings, performance, security, and fault tolerance.

**Why the other options are incorrect:**

- **A) AWS Audit Manager** -- Helps continuously audit AWS usage for risk and compliance, but focuses on compliance reporting rather than optimization.
- **C) AWS CloudTrail** -- Records API calls for auditing purposes but doesn't offer optimization recommendations.
- **D) AWS Config** -- Assesses, audits, and evaluates resource configurations for compliance monitoring, not broad optimization guidance.

---

### Question 49
**Domain:** Fundamentals of AI and ML

> A marketing department wants to exclude competitive brand names or sensitive topics from generative AI content.
>
> What type of prompting technique does this represent?

- A) Few-shot Prompting
- B) Chain-of-thought prompting
- C) Zero-shot Prompting
- D) Negative prompting :white_check_mark:

**Correct Answer: D**

**Explanation:**

Negative prompting guides a generative AI model to avoid certain outputs or behaviors by specifying what should NOT be included in the generated content. It refines and controls output by explicitly excluding unwanted content.

**Why the other options are incorrect:**

- **A) Few-shot Prompting** -- Provides a few examples to guide output, not exclusions.
- **B) Chain-of-thought prompting** -- Breaks complex questions into logical steps to enhance reasoning.
- **C) Zero-shot Prompting** -- Asks the model to perform a task without examples, relying on general knowledge.

---

### Question 50
**Domain:** Fundamentals of AI and ML

> How does reinforcement learning work?

- A) Transforms raw data into a new feature space to reduce dimensionality
- B) Relies on unsupervised learning techniques to cluster data points
- C) Uses supervised learning algorithms to label data and make predictions
- D) An agent interacts with an environment by taking actions and receiving rewards or penalties, learning a policy to maximize cumulative rewards :white_check_mark:

**Correct Answer: D**

**Explanation:**

Reinforcement learning works by having an agent take actions in an environment, receiving rewards or penalties based on those actions, and learning a policy to maximize cumulative rewards over time. The agent continuously adjusts actions based on feedback.

**Why the other options are incorrect:**

- **A)** Describes feature engineering/dimensionality reduction, not RL.
- **B)** RL is not unsupervised learning and does not cluster data without feedback.
- **C)** RL does not use supervised learning to label data; it learns from environmental interaction.

---

### Question 51
**Domain:** Fundamentals of AI and ML

> A company's ML models for credit risk and fraud detection are not accurate enough. Which approach would enhance accuracy?

- A) Decrease the learning rate
- B) Increase the number of epochs :white_check_mark:
- C) Reduce the batch size
- D) Increase regularization

**Correct Answer: B**

**Explanation:**

Increasing the number of epochs allows the model to learn from the training data for a longer period, potentially capturing more complex patterns and relationships. Multiple epochs are run until accuracy reaches an acceptable level or error rate drops below an acceptable threshold.

**Why the other options are incorrect:**

- **A)** Decreasing the learning rate can slow convergence and cause the model to get stuck in local minima.
- **C)** Reducing batch size can make training noisier and doesn't necessarily improve accuracy.
- **D)** Increasing regularization is beneficial for overfitting but could further decrease performance if the model is already underfitting.

---

### Question 52
**Domain:** Fundamentals of AI and ML

> A model shows high accuracy on training data but drops significantly in production with new data.
>
> What would be the most effective approach to fix this overfitting problem?

- A) Swap with a state-of-the-art generative AI model
- B) Increase the amount of training data
- C) Use hyperparameters for model tuning (regularization, learning rates, dropout rates) :white_check_mark:
- D) Reduce the amount of training data

**Correct Answer: C**

**Explanation:**

Hyperparameter tuning allows you to adjust settings that control the learning process. By increasing regularization, implementing early stopping, or adjusting dropout rates, the model can avoid overfitting to training data and better generalize to new, unseen data.

**Why the other options are incorrect:**

- **A)** Switching models doesn't address the underlying overfitting issue.
- **B)** More data can help but is less direct and more resource-intensive than hyperparameter tuning.
- **D)** Reducing training data can cause underfitting, making the problem worse.

---

### Question 53
**Domain:** Applications of Foundation Models

> A healthcare company wants to fine-tune a foundation model in Amazon Bedrock using its own labeled dataset. Which approach is most suitable?

- A) Leverage Amazon Bedrock playground
- B) Use On-Demand mode
- C) Use Provisioned Throughput mode :white_check_mark:
- D) Leverage batch inference

**Correct Answer: C**

**Explanation:**

Once a fine-tuning job is complete, you receive a unique model ID. To test and deploy your customized model, you **must** purchase Provisioned Throughput. This mode is designed for predictable, continuous workloads such as the intensive compute required during fine-tuning and deployment.

> **Exam Alert:** For testing and deploying customized models on Amazon Bedrock (via fine-tuning or continued pre-training), Provisioned Throughput is mandatory.

**Why the other options are incorrect:**

- **A) Bedrock playground** -- For experimenting with prompts and inference parameters, not fine-tuning.
- **B) On-Demand mode** -- Does not support model customization via fine-tuning or continued pre-training.
- **D) Batch inference** -- For running multiple inference requests asynchronously, not for facilitating fine-tuning.

---

### Question 54
**Domain:** Applications of Foundation Models

> Which statement best defines the use of MLflow with Amazon SageMaker?

- A) Perform automatic model tuning
- B) Label data using human-in-the-loop
- C) Manage machine learning experiments :white_check_mark:
- D) Leverage no-code ML

**Correct Answer: C**

**Explanation:**

MLflow with Amazon SageMaker lets you track, organize, view, analyze, and compare iterative ML experimentation to gain comparative insights and register and deploy your best-performing models.

**Why the other options are incorrect:**

- **A)** Automatic model tuning is performed using SageMaker Automatic Model Tuning (AMT).
- **B)** Human-in-the-loop labeling is performed using SageMaker Ground Truth.
- **D)** No-code ML is offered by SageMaker Canvas.

---

### Question 55
**Domain:** Applications of Foundation Models

> Which generative AI techniques are used in the Amazon Q Business web application workflow? (Select TWO)

- A) Variational autoencoders (VAE)
- B) Diffusion Model
- C) Retrieval-Augmented Generation (RAG) :white_check_mark:
- D) Generative adversarial network (GAN)
- E) Large Language Model (LLM) :white_check_mark:

**Correct Answer: C, E**

**Explanation:**

Depending on configuration, the Amazon Q Business web application workflow can use **LLM**, **RAG**, or both:
- **LLMs** are focused on language-based tasks such as summarization, text generation, classification, and information extraction.
- **RAG** optimizes LLM output by referencing an authoritative knowledge base before generating a response, ensuring relevance and accuracy.

**Why the other options are incorrect:**

- **A) VAE** -- Uses encoder-decoder networks for latent space representation, not used in Amazon Q workflow.
- **B) Diffusion Model** -- Creates data by iteratively adding/removing noise, not used in Amazon Q.
- **D) GAN** -- Trains generator and discriminator networks in competition, not used in Amazon Q.

---

### Question 56
**Domain:** Fundamentals of Generative AI

> What is one of the primary advantages of using generative AI in the AWS cloud environment?

- A) Generative AI can automate the creation of new data based on existing patterns, enhancing productivity and innovation :white_check_mark:
- B) Generative AI can replace all human roles in software development
- C) Generative AI ensures 100% security against all cyber threats
- D) Generative AI can perform all cloud maintenance tasks without any human intervention

**Correct Answer: A**

**Explanation:**

Generative AI in the AWS cloud environment automates the creation of new data from existing patterns, significantly boosting productivity and driving innovation. It allows businesses to generate new insights, designs, and solutions more efficiently.

**Why the other options are incorrect:**

- **B)** Generative AI assists and enhances human capabilities, it does not replace all human roles.
- **C)** No technology guarantees 100% security against all cyber threats.
- **D)** Generative AI can assist in maintenance tasks but cannot perform all of them without human oversight.

---

### Question 57
**Domain:** Fundamentals of Generative AI

> Which AWS services would you recommend for developing LLM-based solutions? (Select TWO)

- A) AWS Inferentia
- B) Amazon SageMaker JumpStart :white_check_mark:
- C) Amazon Q
- D) AWS Trainium
- E) Amazon Bedrock :white_check_mark:

**Correct Answer: B, E**

**Explanation:**

AWS recommends **Amazon Bedrock** and **Amazon SageMaker JumpStart** as the best-fit services for developing LLM-based solutions:
- **Amazon Bedrock** is the easiest way to build and scale generative AI applications with foundation models through a single API.
- **Amazon SageMaker JumpStart** provides access to pre-trained models including foundation models, with full customization and easy deployment.

**Why the other options are incorrect:**

- **A) AWS Inferentia** -- An ML chip purpose-built for high-performance inference, not an LLM development service.
- **C) Amazon Q** -- A generative AI assistant for software development and internal data, not for building LLM solutions.
- **D) AWS Trainium** -- An ML chip purpose-built for deep learning training, not an LLM development service.

---

### Question 58
**Domain:** Applications of Foundation Models

> Which statement best describes the Amazon Personalize service?

- A) Derive and understand valuable insights from text within documents
- B) Automatically convert speech to text and gain insights
- C) Deploy high-quality, natural-sounding human voices in dozens of languages
- D) Elevate the customer experience with ML-powered personalization :white_check_mark:

**Correct Answer: D**

**Explanation:**

Amazon Personalize is a fully managed ML service that uses your data (user data, item catalog, interaction data) to generate personalized product and content recommendations. It improves user engagement, conversion rates, and customer satisfaction.

**Why the other options are incorrect:**

- **A)** Describes Amazon Comprehend (NLP service for text insights).
- **B)** Describes Amazon Transcribe (speech-to-text).
- **C)** Describes Amazon Polly (text-to-speech).

---

### Question 59
**Domain:** Applications of Foundation Models

> Which use case is NOT the right fit for Amazon Rekognition?

- A) Searchable media libraries
- B) Enable multilingual user experiences in your applications :white_check_mark:
- C) Celebrity recognition
- D) Face-based user identity verification

**Correct Answer: B**

**Explanation:**

Amazon Translate (not Rekognition) is the service for enabling multilingual user experiences. Amazon Rekognition is a cloud-based image and video analysis service.

**Why the other options are incorrect:**

- **A, C, D)** Searchable media libraries, celebrity recognition, and face-based user identity verification are all classic Amazon Rekognition use cases.

---

### Question 60
**Domain:** Security, Compliance, and Governance for AI Solutions

> A company with uncertain usage patterns needs a flexible pricing model for Amazon Bedrock. Which pricing model is most appropriate?

- A) Provisioned throughput
- B) Reserved instances
- C) Spot instances
- D) On-demand pricing :white_check_mark:

**Correct Answer: D**

**Explanation:**

On-demand pricing allows the company to pay based on actual usage without upfront payment or long-term contracts. It provides the flexibility and scalability needed for uncertain usage patterns.

**Why the other options are incorrect:**

- **A) Provisioned throughput** -- Designed for predictable, consistent usage; may lead to unnecessary costs if actual usage is lower.
- **B) Reserved instances** -- An EC2 pricing model (1-3 year commitment), not applicable to Amazon Bedrock.
- **C) Spot instances** -- An EC2 pricing model with interruption risk, not applicable to Amazon Bedrock.

---

### Question 61
**Domain:** Fundamentals of Generative AI

> Which of the following best describes generative AI?

- A) Models and algorithms capable of creating new content such as text, images, and audio based on patterns learned from existing data :white_check_mark:
- B) Algorithms that analyze existing data to generate new insights without creating new content
- C) AI systems limited to performing predefined tasks without adapting to new data
- D) A subset of AI that focuses exclusively on improving data retrieval efficiency

**Correct Answer: A**

**Explanation:**

Generative AI is a type of AI that can create new content and ideas, including conversations, stories, images, videos, and music. It encompasses models and algorithms capable of creating new content based on patterns learned from existing data.

**Why the other options are incorrect:**

- **B)** Generative AI creates new content, not just insights from existing data.
- **C)** Generative AI is capable of adapting and creating new content, not limited to predefined tasks.
- **D)** Generative AI focuses on content creation, not just data retrieval efficiency.

---

### Question 62
**Domain:** Applications of Foundation Models

> A retail company wants pre-trained and customizable computer vision capabilities for in-store operations. What do you suggest?

- A) Amazon SageMaker
- B) Amazon Rekognition :white_check_mark:
- C) Amazon Textract
- D) Amazon DeepRacer

**Correct Answer: B**

**Explanation:**

Amazon Rekognition is a cloud-based image and video analysis service that offers **pre-trained and customizable** computer vision (CV) capabilities. It can detect objects, text, unsafe content, analyze images/videos, and compare faces without requiring ML expertise.

**Why the other options are incorrect:**

- **A) Amazon SageMaker** -- A fully managed ML service for building, training, and deploying ML models -- not a pre-trained CV service.
- **C) Amazon Textract** -- Extracts text from scanned documents (OCR), not a general computer vision service.
- **D) Amazon DeepRacer** -- An autonomous race car for testing reinforcement learning models, not a CV service.

---

### Question 63
**Domain:** Applications of Foundation Models

> A retail company has product catalogs in PDF form and wants to provide current, relevant responses through its LLM chatbot. Which is the most cost-effective approach?

- A) Attach all product catalog PDFs to each customer query
- B) Utilize a Retrieval-Augmented Generation (RAG) system by indexing all PDFs :white_check_mark:
- C) Attach a single relevant PDF to each customer query
- D) Fine-tune the LLM with data extracted from the PDFs

**Correct Answer: B**

**Explanation:**

RAG is the most cost-effective solution. It converts all product catalog PDFs into a searchable knowledge base. When a query comes in, RAG first retrieves the most relevant information, then uses the LLM to generate a coherent response. No re-training or large data attachments needed.

**Why the other options are incorrect:**

- **A)** Attaching all PDFs to every query is highly inefficient, increasing costs, processing time, and latency.
- **C)** There's no low-cost way to automatically identify which single PDF is relevant per query without a custom solution.
- **D)** Fine-tuning is costly, resource-intensive, and requires re-fine-tuning whenever product literature updates.

---

### Question 64
**Domain:** Applications of Foundation Models

> How does the inference parameter Top P influence the model response for Amazon Bedrock?

- A) Influences the likelihood of selecting lower-probability outputs (creativity)
- B) Influences the percentage of most-likely candidates that the model considers for the next token :white_check_mark:
- C) Influences the number of most-likely candidates that the model considers for the next token
- D) Specifies the sequences of characters that stop the model from generating further tokens

**Correct Answer: B**

**Explanation:**

**Top P** represents the **percentage** of most likely candidates that the model considers for the next token. A lower value limits options to more likely outputs; a higher value allows less likely outputs.

**Why the other options are incorrect:**

- **A)** Describes the Temperature parameter, which regulates creativity.
- **C)** Describes the Top K parameter, which represents the **number** (not percentage) of candidates.
- **D)** Describes the Stop sequences parameter.

---

### Question 65
**Domain:** Applications of Foundation Models

> Which of the following represent the key features of Amazon SageMaker JumpStart? (Select TWO)

- A) Pre-trained models are fully customizable for your use case with your data :white_check_mark:
- B) SageMaker JumpStart provides only public models; proprietary models are not supported
- C) Your inference and training data will be used to train the base model
- D) You can build highly accurate ML models using a visual interface without any code
- E) You can evaluate, compare, and select Foundation Models quickly based on pre-defined quality and responsibility metrics :white_check_mark:

**Correct Answer: A, E**

**Explanation:**

- **Pre-trained models are fully customizable** for your use case with your data, and you can easily deploy them into production with the UI or SDK.
- **You can evaluate, compare, and select FMs** quickly based on pre-defined quality and responsibility metrics for tasks like article summarization and image generation.

**Why the other options are incorrect:**

- **B)** SageMaker JumpStart provides both proprietary and public models.
- **C)** Your inference and training data will NOT be used to update or train the base model.
- **D)** This describes Amazon SageMaker Canvas (no-code ML), not JumpStart.

---
