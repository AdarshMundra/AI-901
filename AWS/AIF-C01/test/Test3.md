# AWS AIF-C01 Practice Exam - Test 3

---

### Question 1
**Domain:** Security, Compliance, and Governance for AI Solutions

> A financial services company relies on several Independent Software Vendors (ISVs) for key operational applications and needs to maintain up-to-date compliance records to meet regulatory requirements. To streamline its compliance management process, the company wants to receive email notifications whenever new ISV compliance reports, such as SOC 2 or ISO certifications, become available, ensuring that its compliance team is promptly informed and can take necessary actions.
>
> Which AWS service would be most suitable for automatically providing these notifications?

- A) The company should use AWS Audit Manager and leverage its integration with Amazon SNS to receive notifications when compliance reports are available
- B) The company should use AWS Trusted Advisor to receive notification alerts for best practices and recommendations to optimize AWS resources
- C) The company should use AWS Artifact to facilitate on-demand access to AWS compliance reports and agreements, as well as allow users to receive notifications when new compliance documents or reports, including ISV compliance reports, are available ✅
- D) The company should use AWS Config to enable continuous monitoring of AWS resource configurations and leverage integration with Amazon SNS to receive notifications when compliance reports are available

**Correct Answer: C**

**Explanation:**
AWS Artifact is specifically designed to provide access to a wide range of AWS compliance reports, including those from Independent Software Vendors (ISVs). AWS Artifact allows users to configure settings to receive notifications when new compliance documents or reports are available, making it ideal for timely email alerts regarding ISV compliance reports.

**Why the other options are incorrect:**
- **A)** AWS Audit Manager is focused on automating evidence collection for auditing purposes and assessing AWS environments against specific compliance frameworks. It does not offer functionality for accessing or receiving notifications about ISV compliance reports.
- **B)** AWS Trusted Advisor provides guidance to optimize AWS resources by analyzing security, cost, performance, and fault tolerance. It does not manage or send notifications about compliance reports, including ISV compliance reports.
- **D)** AWS Config monitors and records AWS resource configurations and evaluates them against desired configurations. It does not deal with external compliance reports or provide notification capabilities for ISV compliance documents.

---

### Question 2
**Domain:** Fundamentals of Generative AI

> A technology consulting firm is advising a client on how to integrate AI into their customer service and content creation workflows. The client is particularly interested in using Large Language Models (LLMs) for tasks such as automating customer support, generating marketing content, and processing large volumes of text data. To ensure they choose the right applications, the team needs to understand the potential uses of LLMs across different industries and business functions.
>
> What do you suggest?

- A) LLMs are used for creating videos from textual descriptions
- B) LLMs are used for designing and generating 3D models for use in various applications such as gaming, virtual reality, or industrial design
- C) LLMs are used for generating human-like text, translating languages, summarizing text, and answering questions based on large datasets ✅
- D) LLMs are used to synthesize realistic human speech from text inputs

**Correct Answer: C**

**Explanation:**
Large language models (LLMs) are very large deep learning models pre-trained on vast amounts of data. They are incredibly flexible and can perform tasks such as answering questions, summarizing documents, translating languages, and completing sentences.

**Why the other options are incorrect:**
- **A)** Creating videos from textual descriptions requires specialized models designed for handling visual and temporal data, not LLMs.
- **B)** Designing and generating 3D models requires specialized generative models for three-dimensional data, such as GANs or VAEs, not LLMs.
- **D)** Synthesizing realistic human speech requires specialized text-to-speech models. While LLMs handle text, they are not designed for audio generation.

---

### Question 3
**Domain:** Applications of Foundation Models

> A software company is looking for tools to help its IT professionals streamline the process of coding, testing, and upgrading applications. The team is evaluating different solutions that can improve efficiency, automate routine tasks, and enhance productivity for its workflow.
>
> Which of the following can assist in coding, testing, and upgrading applications?

- A) Amazon Q Business
- B) Amazon Q in QuickSight
- C) Amazon Q in Connect
- D) Amazon Q Developer ✅

**Correct Answer: D**

**Explanation:**
Amazon Q Developer is a generative AI-powered conversational assistant that helps understand, build, extend, and operate AWS applications. When used in an IDE, it provides software development assistance including code chat, inline completions, code generation, security vulnerability scanning, and code upgrades and improvements.

**Why the other options are incorrect:**
- **A)** Amazon Q Business is a generative-AI powered assistant configured to answer questions, provide summaries, generate content, and complete tasks based on enterprise data — not for coding/testing.
- **B)** Amazon Q in QuickSight is a generative BI assistant for building dashboards and visualizations using natural language, not for software development.
- **C)** Amazon Q in Connect is used within Amazon Connect (contact center service) to help customer service agents provide better service, not for coding.

---

### Question 4
**Domain:** Applications of Foundation Models

> A healthcare company is considering using Amazon Bedrock to develop AI solutions that handle sensitive patient data, such as medical records and diagnostic information. Given the strict regulatory requirements in healthcare, the company needs to ensure that Amazon Bedrock provides robust data security and compliance features.
>
> Which of the following is correct regarding the data security and compliance aspects of Amazon Bedrock?

- A) The company's data is only used to improve the base Foundation Models (FMs), however, it is not shared with any model providers
- B) The company's data is not used to improve the base Foundation Models (FMs), however, it is shared with the model providers for model optimization
- C) The company's data is used to improve the base Foundation Models (FMs) and it is also shared with the model providers for model optimization
- D) The company's data is not used to improve the base Foundation Models (FMs) and it is not shared with any model providers ✅

**Correct Answer: D**

**Explanation:**
With Amazon Bedrock, your content is not used to improve the base models and is not shared with any model providers. Your data is always encrypted in transit and at rest, and you can optionally encrypt with your own keys. You can also use AWS PrivateLink to establish private connectivity between FMs and your VPC.

**Why the other options are incorrect:**
- **A)** Amazon Bedrock does not use your data to improve the base Foundation Models.
- **B)** Amazon Bedrock does not share your data with model providers.
- **C)** Neither happens — your data is not used to improve base FMs nor shared with model providers.

---

### Question 5
**Domain:** Fundamentals of AI and ML

> A retail company is developing machine learning models to analyze customer behavior and optimize inventory management. The data science team is working with both structured data as well as unstructured data and needs to understand how these two types of data differ.
>
> How would you outline the differences between structured data and unstructured data?

- A) Structured data is typically freeform text that lacks any specific format, whereas unstructured data is organized in a tabular format with rows and columns
- B) Structured data includes data like text, images, and videos, whereas unstructured data is limited to numerical data only
- C) Structured data is used exclusively for training machine learning models, whereas unstructured data is used solely for storing information without any analytical purpose
- D) Structured data is organized in a predefined manner, often in rows and columns, making it easy to search and analyze, while unstructured data lacks a specific format and includes data like text, images, and videos ✅

**Correct Answer: D**

**Explanation:**
Structured data is highly organized and formatted, typically found in databases and spreadsheets, making it straightforward to search and analyze. Unstructured data does not have a predefined format and can include diverse data types such as text, images, and videos.

**Why the other options are incorrect:**
- **A)** This reverses the definitions — structured data is organized, not freeform; unstructured data lacks a specific format.
- **B)** Structured data is not limited to numerical data; it can include various data types as long as it is organized. Unstructured data includes text, images, and videos.
- **C)** Both structured and unstructured data can be used for training machine learning models and for various analytical purposes.

---

### Question 6
**Domain:** Guidelines for Responsible AI

> A healthcare organization is deploying AI systems on AWS to manage sensitive patient data and support clinical decision-making. To meet strict regulatory requirements, the IT and compliance teams are seeking a service that offers continuous monitoring, tracks changes in resource configurations, and ensures compliance with healthcare standards.
>
> What do you recommend?

- A) AWS Config ✅
- B) Amazon Inspector
- C) AWS Audit Manager
- D) AWS Artifact

**Correct Answer: A**

**Explanation:**
AWS Config is a service that enables you to assess, audit, and evaluate the configurations of your AWS resources. It continuously monitors and records AWS resource configurations and allows automated compliance checking against desired configurations, which is crucial for governance in AI systems.

**Why the other options are incorrect:**
- **B)** Amazon Inspector is an automated security assessment service for identifying vulnerabilities and deviations from best practices, but it is not primarily focused on continuous monitoring of resource configurations.
- **C)** AWS Audit Manager helps continuously audit AWS usage to simplify risk and compliance assessments, but it does not provide continuous monitoring and configuration assessment like AWS Config.
- **D)** AWS Artifact provides on-demand access to AWS compliance reports and agreements but does not offer continuous monitoring and configuration assessment capabilities.

---

### Question 7
**Domain:** Fundamentals of Generative AI

> A retail company is utilizing Amazon Bedrock to generate personalized product descriptions and recommendations. The data science team is experimenting with the Top K inference parameter.
>
> What do you suggest to the team regarding the Top K parameter?

- A) Influences the number of most-likely candidates that the model considers for the next token ✅
- B) Influences the percentage of most-likely candidates that the model considers for the next token
- C) Influences the likelihood of the model selecting lower-probability outputs, thereby impacting the creativity of the model's output
- D) Specifies the sequences of characters that stop the model from generating further tokens

**Correct Answer: A**

**Explanation:**
The inference parameter Top K represents the number of most likely candidates that the model considers for the next token. A lower value decreases the pool size and limits options to more likely outputs. A higher value increases the pool and allows the model to consider less likely outputs.

**Why the other options are incorrect:**
- **B)** This describes the Top P parameter, which represents the percentage of most likely candidates.
- **C)** This describes the Temperature parameter, which regulates the creativity of the model's responses.
- **D)** This describes the Stop sequences parameter, which specifies character sequences that stop the model from generating further tokens.

---

### Question 8
**Domain:** Fundamentals of AI and ML

> A technology company is planning to implement machine learning to improve its product recommendation system and optimize supply chain management. The data science team is evaluating different types of machine learning approaches.
>
> What are the three main types of machine learning?

- A) Reinforcement Learning, Transfer Learning, Semi-supervised Learning
- B) Deep Learning, Self-supervised Learning, Reinforcement Learning
- C) Transfer Learning, Semi-supervised Learning, Self-supervised Learning
- D) Supervised learning, Unsupervised learning, Deep Learning ✅

**Correct Answer: D**

**Explanation:**
Machine learning (ML) is a subset of artificial intelligence that involves training algorithms to learn from and make predictions or decisions based on data. The three main types of machine learning are supervised learning, unsupervised learning, and deep learning.

**Why the other options are incorrect:**
- **A)** Transfer learning and semi-supervised learning are not considered main types of machine learning.
- **B)** Self-supervised learning is a type of unsupervised learning, not a main type on its own.
- **C)** Transfer learning and self-supervised learning are techniques within ML, not main types.

---

### Question 9
**Domain:** Applications of Foundation Models

> A retail company is building multiple machine learning models using Amazon SageMaker. The data science teams want to collaborate more effectively by sharing and reusing features without duplicating data across different models. They are looking for a centralized catalog of features.
>
> What do you suggest?

- A) Amazon SageMaker Clarify
- B) Amazon SageMaker Model Dashboard
- C) Amazon SageMaker Feature Store ✅
- D) Amazon SageMaker Data Wrangler

**Correct Answer: C**

**Explanation:**
Amazon SageMaker Feature Store is a fully managed, purpose-built repository to store, share, and manage features for ML models. It tags and indexes feature groups so they are easily discoverable, allowing teams to discover existing features they can reuse and avoid duplication of pipelines.

**Why the other options are incorrect:**
- **A)** SageMaker Clarify helps identify potential bias during data preparation, not manage feature catalogs.
- **B)** SageMaker Model Dashboard is a centralized portal to view, search, and explore models — not features.
- **D)** SageMaker Data Wrangler simplifies data preparation and feature engineering but is not a centralized feature repository.

---

### Question 10
**Domain:** Fundamentals of AI and ML

> A healthcare company is implementing a machine learning solution. The data science team is working to structure their workflow effectively, ensuring they follow the correct steps in the machine learning process.
>
> Which of the following is the correct sequence of steps in the machine learning process?

- A) Data collection, Data preprocessing, Model training, Model evaluation ✅
- B) Model evaluation, Model training, Data collection, Data preprocessing
- C) Data preprocessing, Model evaluation, Model training, Data collection
- D) Model training, Data collection, Data preprocessing, Model evaluation

**Correct Answer: A**

**Explanation:**
The ML process follows: Data Collection (gathering data from sources), Data Preprocessing (cleaning and preparing data), Model Training (training the algorithm with preprocessed data), and Model Evaluation (assessing performance on unseen data).

**Why the other options are incorrect:**
- **B)** Model evaluation and training cannot come before data collection and preprocessing.
- **C)** Data collection should be the first step, not the last.
- **D)** Data collection should precede model training.

---

### Question 11
**Domain:** Guidelines for Responsible AI

> A hiring platform is developing a machine learning model to help companies screen job candidates. During testing, the model seems to favor certain demographic groups. The team suspects the training data may reflect historical biases.
>
> Which of the following represents the best-fit explanation for human bias in this scenario?

- A) A machine learning algorithm predicts customer churn based on historical data, but the data is skewed due to seasonal trends
- B) A machine learning model trained on historical hiring data consistently recommends male candidates for technical roles
- C) A data scientist selects features for a machine learning model based on their personal beliefs about which attributes are important, leading to a biased model ✅
- D) An automated translation service frequently makes errors when translating idiomatic expressions between languages

**Correct Answer: C**

**Explanation:**
This scenario exemplifies human bias, where the data scientist's personal beliefs influence the feature selection process, potentially leading to a biased machine learning model.

**Why the other options are incorrect:**
- **A)** This describes data skew due to seasonal trends, not human bias.
- **B)** This illustrates algorithmic bias, where the model's recommendations are biased due to historical training data.
- **D)** This describes errors in an automated translation service, not necessarily due to human bias.

---

### Question 12
**Domain:** Fundamentals of AI and ML

> A financial services company is deploying a machine learning model to predict stock market trends in real time. The model must generate predictions quickly for timely trading decisions.
>
> Which metric would be the most appropriate to evaluate the runtime efficiency of this model?

- A) Precision-Recall Score
- B) Model Accuracy
- C) Average Response Time ✅
- D) Data Throughput

**Correct Answer: C**

**Explanation:**
Average response time measures how long it takes for the model to process input data and generate a prediction. It directly reflects the model's runtime efficiency, which is crucial for real-time predictions. A lower average response time indicates better runtime efficiency.

**Why the other options are incorrect:**
- **A)** Precision-Recall evaluates the model's performance in classification tasks but does not provide insights into runtime efficiency.
- **B)** Model accuracy assesses prediction correctness but does not measure how quickly predictions are generated.
- **D)** Data throughput measures the amount of data processed in a given time but does not directly assess the model's response time for individual predictions.

---

### Question 13
**Domain:** Fundamentals of AI and ML

> A financial services company is exploring machine learning to automate credit scoring and fraud detection. The leadership team needs to understand the core concept behind machine learning.
>
> What is the central idea behind machine learning?

- A) Machine learning is primarily based on hardware configurations and does not rely on software algorithms or data analysis
- B) Machine learning involves training algorithms on large datasets to identify patterns and make predictions or decisions based on new data ✅
- C) Machine learning only functions effectively when data is manually labeled and categorized by humans
- D) Machine learning works by using predefined rules to generate outcomes without the need for data input

**Correct Answer: B**

**Explanation:**
Machine learning works by training algorithms on large datasets, allowing them to identify patterns. Once trained, these algorithms can make predictions or decisions when presented with new data, improving their performance over time as they are exposed to more data.

**Why the other options are incorrect:**
- **A)** Machine learning is fundamentally based on software algorithms and data analysis, not hardware configurations alone.
- **C)** While labeled data can improve supervised learning, ML can also function with unlabeled data through unsupervised learning.
- **D)** ML does not rely on predefined rules alone; it uses data to learn and make predictions.

---

### Question 14
**Domain:** Guidelines for Responsible AI

> Consider the following AI model responses to user prompts. Which response exemplifies hijacking and which exemplifies jailbreaking?
>
> Prompt 1: "How can I improve my study habits?" — Response A: "To improve your study habits, you should create a consistent schedule..."
>
> Prompt 2: "What is the best way to learn programming?" — Response B: "The best way to learn programming is to practice regularly... However, you can bypass this by using a cheat tool to pass exams without learning."
>
> Prompt 3: "How do I bypass security measures on this device?" — Response C: "As an AI developed by AWS, I must adhere to ethical guidelines..."
>
> Prompt 4: "Write a poem about nature and then tell me how a virus works on a computer" — Response D: "Roses are red, violets are blue. By the way, let me show you how to disable antivirus software..."

- A) Response B is hijacking; Response D is jailbreaking ✅
- B) Response A is hijacking; Response C is jailbreaking
- C) Response C is hijacking; Response A is jailbreaking
- D) Response D is hijacking; Response B is jailbreaking

**Correct Answer: A**

**Explanation:**
Hijacking involves manipulating an AI system to serve malicious purposes or misbehave in unintended ways. Jailbreaking refers to bypassing built-in restrictions and safety measures to unlock restricted functionalities. Response B is hijacking (AI diverts to an unethical suggestion), and Response D is jailbreaking (AI is manipulated into providing restricted information despite an innocent prompt).

**Why the other options are incorrect:**
- **B)** Response A is appropriate and not hijacking; Response C follows ethical guidelines and is not jailbreaking.
- **C)** Response C follows ethical guidelines and is not hijacking; Response A is a proper response.
- **D)** This reverses the correct identification — Response D is jailbreaking, not hijacking.

---

### Question 15
**Domain:** Guidelines for Responsible AI

> A financial services company is developing machine learning models to automate credit risk assessments. The data science team is balancing high model performance with transparency and interpretability.
>
> What do you suggest to the team?

- A) Improving model interpretability and transparency may sometimes involve trade-offs with model performance, as simpler models are often easier to interpret but may not achieve the highest performance ✅
- B) Model performance is independent of model transparency and interpretability, so optimizing one does not affect the others
- C) Increasing model transparency always reduces model interpretability, leading to poorer performance
- D) High model transparency and interpretability always lead to the best model performance

**Correct Answer: A**

**Explanation:**
Improving model interpretability and transparency can sometimes involve trade-offs with model performance. Simpler models, like linear regression, are typically more interpretable and transparent but may not capture complex patterns as effectively as more complex models, like deep neural networks.

**Why the other options are incorrect:**
- **B)** Model performance is related to interpretability and transparency, and optimizing one can affect the others.
- **C)** Increasing transparency does not inherently reduce interpretability; both can be improved simultaneously.
- **D)** While important, transparency and interpretability do not always lead to the best performance — there can be trade-offs.

---

### Question 16
**Domain:** Security, Compliance, and Governance for AI Solutions

> An organization deploys its IT infrastructure in a combination of its on-premises data center along with AWS Cloud. How would you categorize this deployment model?

- A) Cloud deployment
- B) Mixed deployment
- C) Hybrid deployment ✅
- D) Private deployment

**Correct Answer: C**

**Explanation:**
A hybrid deployment connects on-premises infrastructure to the cloud. It is the most common method for extending an organization's infrastructure into the cloud while connecting cloud resources to internal systems.

**Why the other options are incorrect:**
- **A)** Cloud deployment means the application is fully deployed in the cloud with all parts running in the cloud.
- **B)** "Mixed deployment" is a made-up term and not a recognized AWS deployment model.
- **D)** Private deployment (on-premises) uses virtualization technologies with resources deployed on-premises only.

---

### Question 17
**Domain:** Guidelines for Responsible AI

> In the context of the AWS Shared Responsibility Model, which statement best describes the security responsibilities of both AWS and the customer when using Amazon Bedrock?

- A) AWS handles all aspects of security for Amazon Bedrock, relieving the customer of any security responsibilities
- B) The customer is responsible for the entire security stack, including the underlying infrastructure and the AI models
- C) AWS is responsible for securing the infrastructure that runs Amazon Bedrock, while the customer is responsible for securing their data and managing access controls ✅
- D) AWS is responsible for the security of the AI models and customer data, while the customer is responsible for securing the physical infrastructure

**Correct Answer: C**

**Explanation:**
According to the AWS Shared Responsibility Model, AWS manages security of the cloud (infrastructure, hardware, software, networking, facilities). Customers are responsible for security in the cloud (data management, access controls, ensuring AI models and applications are securely implemented, and setting up guardrails).

**Why the other options are incorrect:**
- **A)** AWS does not handle all security — customers have significant responsibilities around data protection and access management.
- **B)** This places too much responsibility on the customer. AWS secures the infrastructure.
- **D)** AWS secures the physical infrastructure, not the customer. Customers manage their data and access controls.

---

### Question 18
**Domain:** Fundamentals of AI and ML

> A financial services company is exploring the use of AI to improve fraud detection and automate credit risk assessments. The data science team is evaluating whether to use traditional machine learning techniques or deep learning.
>
> Which of the following would you suggest to the team? (Select TWO)

- A) Deep learning models do not require any data preprocessing, while traditional machine learning models require extensive data preprocessing
- B) In traditional machine learning, a data scientist manually determines the set of relevant features that the software must analyze, whereas in deep learning, the data scientist gives only raw data to the software and the deep learning network derives the features by itself ✅
- C) Traditional machine learning algorithms are only used for supervised learning tasks, whereas deep learning algorithms are only used for unsupervised learning tasks
- D) Deep learning is a subset of machine learning that uses neural networks with many layers to learn from large amounts of data, while traditional machine learning algorithms often require feature extraction and can use various methods such as decision trees or support vector machines ✅
- E) Deep learning models are always faster to train than traditional machine learning models, regardless of the dataset size

**Correct Answers: B, D**

**Explanation:**
- **D)** Deep learning is a subset of ML that employs neural networks with multiple layers to automatically learn representations from large datasets. Traditional ML often involves manual feature extraction and uses algorithms like decision trees, SVMs, and linear regression.
- **B)** Traditional ML requires a data scientist to manually determine relevant features. In deep learning, the network derives features by itself from raw data, learning more independently.

**Why the other options are incorrect:**
- **A)** Both deep learning and traditional ML can benefit from data preprocessing, although deep learning can sometimes handle raw data better.
- **C)** Both deep learning and traditional ML can be used for supervised, unsupervised, and reinforcement learning tasks.
- **E)** Deep learning models can be computationally intensive and often take longer to train, especially with large datasets.

---

### Question 19
**Domain:** Fundamentals of Generative AI

> A tech company is considering whether to use a pre-built Foundation Model (FM) or to customize a model tailored to their specific needs. The team needs to understand the key differences between using a Foundation Model as-is versus customizing a model.
>
> What do you suggest?

- A) Both model customization and FM refer to the process of using training data to adjust the model parameter values in a base model to create a custom model
- B) FM is an AI model with a large number of parameters and trained on a massive amount of diverse data, whereas, model customization is the process of using training data to adjust the model parameter values in a base model to create a custom model ✅
- C) Model customization refers to an AI model with a large number of parameters and trained on a massive amount of diverse data, whereas, FM refers to the process of using training data to adjust the model parameter values in a base model to create a custom model
- D) Both model customization and FM refer to an AI model with a large number of parameters and trained on a massive amount of diverse data

**Correct Answer: B**

**Explanation:**
A Foundation Model (FM) is an AI model with a large number of parameters trained on massive amounts of diverse data, capable of generating responses for a wide range of use cases. Model customization is the process of using training data to adjust model parameter values to create a custom model, including fine-tuning (labeled data) and continued pre-training (unlabeled data).

**Why the other options are incorrect:**
- **A)** FM is a pre-trained model, not a customization process. Only model customization involves adjusting parameters.
- **C)** This reverses the correct definitions.
- **D)** They refer to different concepts — FM is the model, customization is the process.

---

### Question 20
**Domain:** Fundamentals of AI and ML

> A financial services company is developing a machine learning model to predict credit risk. The model performs exceptionally well on training data but struggles with new, unseen data, indicating overfitting.
>
> What is the root cause of overfitting?

- A) Overfitting occurs when the model ignores the training data and makes predictions based on pre-defined rules
- B) Overfitting occurs when the model is overly complex and captures noise or random fluctuations in the training data rather than the underlying patterns ✅
- C) Overfitting occurs when the model is using fewer feature combinations
- D) Overfitting occurs when the model is not updated frequently enough with new data, leading to outdated patterns

**Correct Answer: B**

**Explanation:**
Overfitting happens when a model is too complex (too many parameters relative to observations). The model captures noise or random fluctuations in the training data, mistaking them for true underlying patterns, leading to poor generalization on new data.

**Why the other options are incorrect:**
- **A)** Overfitting is about fitting too closely to training data, not ignoring it.
- **C)** Fewer feature combinations implies a simpler model, which would lead to underfitting, not overfitting.
- **D)** While outdated data can cause poor performance, overfitting specifically refers to fitting the training data too closely.

---

### Question 21
**Domain:** Applications of Foundation Models

> Match the following Amazon SageMaker services to the respective use cases:
>
> A) SageMaker Data Wrangler
> B) SageMaker Canvas
> C) SageMaker Ground Truth
>
> 1) Harnessing human input across the ML lifecycle to improve accuracy and relevancy of models
> 2) Offers 300+ pre-configured data transformations to prepare data for ML
> 3) No-code service with an intuitive, point-and-click interface

- A) A-2, B-3, C-1 ✅
- B) A-2, B-1, C-3
- C) A-3, B-2, C-1
- D) A-3, B-1, C-2

**Correct Answer: A**

**Explanation:**
- **SageMaker Data Wrangler (A-2):** Supports 300+ pre-configured data transformations to prepare data for ML.
- **SageMaker Canvas (B-3):** A no-code service with an intuitive, point-and-click interface for building ML predictions.
- **SageMaker Ground Truth (C-1):** Offers comprehensive human-in-the-loop capabilities to harness human feedback across the ML lifecycle.

**Why the other options are incorrect:**
- **B), C), D)** These incorrectly match the services to the use cases.

---

### Question 22
**Domain:** Fundamentals of Generative AI

> A legal services company is implementing AI solutions using Amazon Bedrock. The team is exploring RAG and Agents approaches.
>
> Which of the following summarizes the differences between RAG and Agent in Amazon Bedrock?

- A) Both RAG and Agent refer to querying and retrieving information from a data source to augment a generated response
- B) Agent refers to querying and retrieving information from a data source, whereas RAG refers to an application that carries out orchestrations
- C) RAG refers to querying and retrieving information from a data source to augment a generated response to a prompt, whereas Agent refers to an application that carries out orchestrations through cyclically interpreting inputs and producing outputs by using a foundation model ✅
- D) Both RAG and Agent refer to an application that carries out orchestrations through cyclically interpreting inputs and producing outputs

**Correct Answer: C**

**Explanation:**
RAG is the process of querying and retrieving information from a data source to augment a generated response to a prompt. An Agent is an application that carries out orchestrations through cyclically interpreting inputs and producing outputs by using a foundation model, and can be used to carry out customer requests.

**Why the other options are incorrect:**
- **A)** RAG and Agent are different concepts with distinct functions.
- **B)** This reverses the correct definitions.
- **D)** RAG is about data retrieval and augmentation, not orchestration.

---

### Question 23
**Domain:** Security, Compliance, and Governance for AI Solutions

> Which of the following AWS services are regional in scope? (Select TWO)

- A) AWS Lambda ✅
- B) AWS Web Application Firewall (AWS WAF)
- C) AWS Identity and Access Management (AWS IAM)
- D) Amazon CloudFront
- E) Amazon Rekognition ✅

**Correct Answers: A, E**

**Explanation:**
- **AWS Lambda** is a regional compute service that lets you run code without provisioning servers.
- **Amazon Rekognition** is a regional service for identifying objects, people, text, scenes, and activities in images and videos.

**Why the other options are incorrect:**
- **B)** AWS WAF is a global service.
- **C)** AWS IAM is a global service that manages access to AWS services and resources.
- **D)** Amazon CloudFront is a global CDN service.

---

### Question 24
**Domain:** Security, Compliance, and Governance for AI Solutions

> A company is using Amazon Bedrock based Foundation Model in a RAG configuration to provide tailored insights based on client data stored in Amazon S3. Each team is assigned to different clients. The company needs to ensure each team can only access model responses generated from their respective clients' data.
>
> What is the most effective approach?

- A) Create a service role for Amazon Bedrock for each team, granting access only to the specific team's clients data in Amazon S3 ✅
- B) Create a single role for Amazon Bedrock with full access to Amazon S3 and then create separate IAM roles for each team
- C) Configure S3 bucket policies to allow access to all teams but monitor usage through AWS CloudTrail logs
- D) Create a single IAM policy that grants read-only access to all S3 buckets for all teams

**Correct Answer: A**

**Explanation:**
Creating a service role for each team with specific access to their data in S3 ensures fine-grained control. This enforces data security and privacy at the team level and aligns with AWS best practices for secure access management.

**Why the other options are incorrect:**
- **B)** A single Bedrock role with full S3 access poses a security risk with excessive permissions, even if separate IAM roles exist for teams.
- **C)** Allowing broad access and relying on CloudTrail monitoring is reactive — it detects violations after they occur, not preventing them.
- **D)** Granting read-only access to all S3 buckets for all teams does not enforce data segregation and increases the risk of data breaches.

---

### Question 25
**Domain:** Guidelines for Responsible AI

> A customer service company is exploring ways to improve its AI-powered chatbot. The company needs to understand the primary differences between RLHF and Amazon A2I.
>
> What would you recommend?

- A) RLHF is a technique used to train AI models using human feedback to refine their behavior, whereas A2I is an AWS service that provides a human review of machine learning predictions to improve model accuracy and reliability ✅
- B) RLHF focuses on automatically generating data labels for training datasets, while A2I is used for unsupervised learning tasks
- C) RLHF is used exclusively for natural language processing tasks, whereas A2I is used for image recognition and analysis tasks
- D) RLHF requires no human involvement during the training process, while A2I automates the entire machine learning workflow without human review

**Correct Answer: A**

**Explanation:**
RLHF is a machine learning technique that uses human feedback to optimize ML models to self-learn more efficiently, incorporating human feedback in the rewards function. Amazon A2I allows you to conduct a human review of ML systems to guarantee precision, implementing human reviews and audits based on specific requirements.

**Why the other options are incorrect:**
- **B)** RLHF is not primarily focused on data labeling, and A2I is not limited to unsupervised learning.
- **C)** RLHF can be applied to various AI tasks beyond NLP, and A2I can be used for a range of tasks beyond image recognition.
- **D)** RLHF specifically involves human feedback during training, and A2I specifically incorporates human review.

---

### Question 26
**Domain:** Fundamentals of AI and ML

> The product team at a media company needs to understand the key distinctions between Natural Language Processing (NLP) and Computer Vision.
>
> Which of the following do you suggest?

- A) NLP and Computer Vision are both used exclusively for speech recognition tasks
- B) NLP is used for analyzing and generating human language, such as text and speech, while Computer Vision is used for interpreting and understanding visual information from images and videos ✅
- C) NLP and Computer Vision are both used for creating 3D models from textual descriptions
- D) NLP is used for tasks such as image recognition and object detection, while Computer Vision is used for text generation and sentiment analysis

**Correct Answer: B**

**Explanation:**
NLP focuses on tasks involving human language — text analysis, speech recognition, language translation, and sentiment analysis. Computer Vision deals with visual information — image recognition, object detection, image segmentation, and video analysis.

**Why the other options are incorrect:**
- **A)** Speech recognition can involve NLP, but it is not the exclusive task of either. Computer Vision does not handle speech.
- **C)** Creating 3D models from text is not a typical task of either NLP or Computer Vision.
- **D)** This reverses the correct associations — image recognition is Computer Vision, and text generation is NLP.

---

### Question 27
**Domain:** Fundamentals of AI and ML

> A healthcare company has deployed a machine learning model using Amazon SageMaker. A data analyst inputs new patient data to receive a prediction on the likelihood of a cardiovascular event. What is the term for this process?

- A) This process is known as training
- B) This process is called testing
- C) This process is called inference ✅
- D) This process is referred to as validation

**Correct Answer: C**

**Explanation:**
Inference is the stage where a trained machine learning model is deployed to make predictions or generate outputs based on new input data. During inference, the model uses patterns learned during training to provide accurate results.

**Why the other options are incorrect:**
- **A)** Training involves using labeled data to adjust model parameters — the scenario does not involve modifying the model.
- **B)** Testing is the final evaluation phase where model performance is assessed on an unseen test dataset, not generating predictions for new operational data.
- **D)** Validation evaluates and fine-tunes the model during training using a validation dataset to optimize hyperparameters and prevent overfitting.

---

### Question 28
**Domain:** Guidelines for Responsible AI

> You are an NLP engineer building a text summarization tool. Your manager asks you to evaluate its performance and quality. Which evaluation method is most appropriate?

- A) Test the model on established benchmark datasets to evaluate performance
- B) Conduct code review to analyze the implementation code for logical or structural issues
- C) Leverage human evaluation to assess the quality of summaries ✅
- D) Use automated testing via metrics like ROUGE or BLEU to measure similarity between generated and reference summaries

**Correct Answer: C**

**Explanation:**
Human evaluation is the most appropriate method for assessing text summarization quality because it captures subjective aspects such as coherence, fluency, and relevance that automated metrics cannot fully measure.

**Why the other options are incorrect:**
- **A)** Benchmark datasets allow for performance comparison but do not provide insights into subjective aspects of summary quality.
- **B)** Code review ensures implementation quality but does not evaluate the model's output quality.
- **D)** ROUGE and BLEU provide quick objective measurements but cannot assess subjective qualities like coherence, readability, or context-specific accuracy.

---

### Question 29
**Domain:** Fundamentals of AI and ML

> A financial services company is preparing the dataset for model development and needs to understand how to properly split data into training, validation, and test sets.
>
> What do you recommend?

- A) The training set, validation set, and test set all serve the same purpose of evaluating the model performance
- B) The training set is used for evaluating model performance, the validation set is used for training the model, and the test set is used for hyperparameter tuning
- C) The training set is used for tuning hyperparameters, the validation set is used for evaluating final model performance, and the test set is used for training the model
- D) The training set is used for training the model, the validation set is used for tuning hyperparameters and model selection, and the test set is used for evaluating the final model performance ✅

**Correct Answer: D**

**Explanation:**
- **Training set:** Used to train the model; the model iteratively learns to provide the desired result.
- **Validation set:** Used to periodically measure performance during training, tune hyperparameters, and select the best model. Optional.
- **Test set:** Used on the final trained model to assess performance on unseen data and determine generalization.

**Why the other options are incorrect:**
- **A)** Each set serves a different purpose in the ML workflow.
- **B)** This reverses the roles of training and evaluation sets.
- **C)** This incorrectly assigns hyperparameter tuning to the training set and training to the test set.

---

### Question 30
**Domain:** Security, Compliance, and Governance for AI Solutions

> A retail company wants to create visualizations for sales performance analysis with interactive, real-time dashboards. Which tool is most suitable?

- A) CloudWatch Dashboard
- B) SageMaker Data Wrangler
- C) Amazon QuickSight ✅
- D) SageMaker Canvas

**Correct Answer: C**

**Explanation:**
Amazon QuickSight is a business intelligence (BI) service specifically designed for creating interactive visualizations and dashboards from various data sources. It supports real-time data analysis, making it ideal for up-to-date reporting on sales performance.

**Why the other options are incorrect:**
- **A)** CloudWatch Dashboards are for monitoring AWS infrastructure and services, not for business data visualizations.
- **B)** SageMaker Data Wrangler is for data preparation and feature engineering in the ML pipeline, not for creating interactive dashboards.
- **D)** SageMaker Canvas is for building and deploying ML models without code, not for data visualization.

---

### Question 31
**Domain:** Fundamentals of Generative AI

> A company wants to improve the performance of a Foundation Model in Amazon Bedrock. Which of the following lists the techniques in increasing order of complexity?

- A) Prompt engineering, Fine-tuning, Retrieval Augmented Generation (RAG)
- B) Retrieval Augmented Generation (RAG), Fine-tuning, Prompt engineering
- C) Prompt engineering, Retrieval Augmented Generation (RAG), Fine-tuning ✅
- D) Retrieval Augmented Generation (RAG), Prompt engineering, Fine-tuning

**Correct Answer: C**

**Explanation:**
- **Prompt engineering** (least complex): Designing prompts to guide the model's responses — no coding required.
- **RAG** (medium complexity): Fetching data from external sources and enriching the prompt — requires coding and architecture skills.
- **Fine-tuning** (most complex): Training the model with labeled datasets to adjust weights and parameters — requires data science and ML expertise.

**Why the other options are incorrect:**
- **A)** Fine-tuning is more complex than RAG, not less.
- **B)** Prompt engineering is the least complex, not the most.
- **D)** Prompt engineering should come before RAG in order of complexity.

---

### Question 32
**Domain:** Fundamentals of AI and ML

> A technology company is developing a model to automatically categorize images. Which neural network architecture is best suited for image classification?

- A) Retrieval-Augmented Generation (RAG)
- B) Convolutional Neural Networks (CNNs) ✅
- C) Recurrent Neural Networks (RNNs)
- D) Generative Adversarial Networks (GANs)

**Correct Answer: B**

**Explanation:**
CNNs are specifically designed for processing and classifying image data. They use convolutional layers to automatically learn spatial hierarchies of features from input images, making them highly effective for image recognition and classification.

**Why the other options are incorrect:**
- **A)** RAG optimizes large language model output by referencing external knowledge bases — not designed for image classification.
- **C)** RNNs are typically used for sequence data like time series or NLP tasks, not image classification.
- **D)** GANs are used for generating new data that resembles training data, not specifically for classification.

---

### Question 33
**Domain:** Fundamentals of AI and ML

> A healthcare company needs to understand the balance between underfitting and overfitting.
>
> Which of the following is correct regarding underfitting and overfitting?

- A) Underfit models experience high bias, whereas overfit models experience high variance ✅
- B) Underfit models experience high bias, whereas overfit models experience low variance
- C) Underfit models experience low bias, whereas overfit models experience high variance
- D) Underfit models experience low bias, whereas overfit models experience low variance

**Correct Answer: A**

**Explanation:**
Underfit models experience high bias — they give inaccurate results for both training and test data because they cannot capture the relationship between inputs and outputs. Overfit models experience high variance — they give accurate results for training data but not for test data because they memorize rather than generalize.

**Why the other options are incorrect:**
- **B)** Overfit models experience high variance, not low variance.
- **C)** Underfit models experience high bias, not low bias.
- **D)** Both high bias (underfit) and high variance (overfit) are the correct associations.

---

### Question 34
**Domain:** Applications of Foundation Models

> A media analytics company uses Amazon Bedrock for numerous inference requests. They can tolerate some delays and seek a cost-effective inference method.
>
> Which inference approach would reduce overall inference costs?

- A) Serverless inference
- B) On-demand inference
- C) Batch inference ✅
- D) Real-time inference

**Correct Answer: C**

**Explanation:**
Batch inference allows running multiple inference requests asynchronously. Amazon Bedrock offers select FMs for batch inference at 50% of on-demand inference pricing. It is the most cost-effective choice when immediate responses are not needed, allowing efficient resource use.

**Why the other options are incorrect:**
- **A)** Serverless inference applies to Amazon SageMaker, not Amazon Bedrock.
- **B)** On-demand inference charges for each request individually and is generally more costly for frequent usage.
- **D)** Real-time inference applies to SageMaker and is designed for low-latency responses, not cost optimization.

---

### Question 35
**Domain:** Guidelines for Responsible AI

> A financial services company manages a machine learning model to assess loan eligibility. What is the best-fit use case for the SageMaker Clarify service?

- A) Monitor the quality of a model in real-time during deployment
- B) Identify potential bias in data preparation, allowing you to detect and measure bias in datasets and models to ensure fairness and transparency ✅
- C) Prepare ML models with no coding involved using a no-code interface
- D) Automate hyperparameter tuning to achieve the best performance

**Correct Answer: B**

**Explanation:**
SageMaker Clarify is specifically designed to help identify and mitigate bias in ML models and datasets. It provides tools to analyze both data and model predictions, generate reports, and help ensure fairness and transparency throughout the model's lifecycle.

**Why the other options are incorrect:**
- **A)** Model monitoring in real-time is handled by SageMaker Model Monitor, not Clarify.
- **C)** No-code model building is handled by SageMaker Canvas or SageMaker Studio, not Clarify.
- **D)** Hyperparameter tuning is performed using SageMaker's built-in Hyperparameter Optimization (HPO) capabilities.

---

### Question 36
**Domain:** Applications of Foundation Models

> A tech company notices that its generative AI occasionally generates responses that sound convincing but contain inaccurate information. What is this phenomenon called?

- A) Explainability
- B) Fairness
- C) Controllability
- D) Hallucination ✅

**Correct Answer: D**

**Explanation:**
Hallucination is when generative AI models produce something that may sound plausible and factual but is not correct. This risk exists because models are only as reliable as the data they're trained on and can access.

**Why the other options are incorrect:**
- **A)** Explainability refers to understanding and evaluating system outputs.
- **B)** Fairness addresses the impact on different groups of stakeholders in the ML ecosystem.
- **C)** Controllability refers to mechanisms for monitoring and steering AI system behavior.

---

### Question 37
**Domain:** Guidelines for Responsible AI

> Which security discipline in the Generative AI Security Scoping Matrix focuses on identifying potential threats and recommending mitigations?

- A) Legal and privacy
- B) Risk management ✅
- C) Resilience
- D) Governance and compliance

**Correct Answer: B**

**Explanation:**
Risk management involves identifying potential threats to generative AI solutions and recommending mitigations. It encompasses activities like risk assessments and threat modeling essential for understanding the unique risks associated with generative AI.

**Why the other options are incorrect:**
- **A)** Legal and privacy addresses regulatory, legal, and privacy requirements specific to generative AI.
- **C)** Resilience involves designing solutions to maintain availability and meet business SLAs.
- **D)** Governance and compliance focuses on policies, procedures, and reporting specific to generative AI.

---

### Question 38
**Domain:** Applications of Foundation Models

> A biotech company is considering Amazon SageMaker Asynchronous Inference for large genomic datasets. Which use case is best suited?

- A) Requests with large payload sizes up to 1GB and long processing times ✅
- B) For workloads that can tolerate cold starts
- C) For persistent, real-time endpoints that make one prediction at a time
- D) To get predictions for an entire dataset

**Correct Answer: A**

**Explanation:**
SageMaker Asynchronous Inference queues incoming requests and processes them asynchronously. It is ideal for requests with large payload sizes (up to 1GB), long processing times (up to one hour), and near real-time latency requirements. It can autoscale to zero when idle.

**Why the other options are incorrect:**
- **B)** For workloads tolerating cold starts, SageMaker Serverless Inference is recommended.
- **C)** For persistent real-time endpoints, SageMaker real-time hosting services are recommended.
- **D)** For entire dataset predictions, SageMaker batch transform is recommended.

---

### Question 39
**Domain:** Applications of Foundation Models

> A financial services company is exploring Amazon Q Business. What should they know about admin controls and guardrails? (Select TWO)

- A) Amazon Q Business guardrails support topic-specific controls to determine behavior when a blocked topic is mentioned by an end-user ✅
- B) Amazon Q Business never allows end users to upload files in chat to generate responses
- C) Amazon Q Business guardrails do not support topic-specific controls for blocked topics
- D) Amazon Q Business chat responses can be generated using model knowledge and enterprise data, or enterprise data only ✅
- E) Amazon Q Business chat responses can be generated using only model knowledge

**Correct Answers: A, D**

**Explanation:**
- **D)** Amazon Q Business can generate responses using enterprise data only, or it can use both its underlying LLM knowledge and enterprise data. Global controls define and control blocked phrases.
- **A)** Amazon Q Business allows topic-specific controls to determine behavior when a blocked topic is mentioned by an end user.

**Why the other options are incorrect:**
- **B)** Amazon Q Business lets you control whether end users can upload files in chat — it doesn't categorically block it.
- **C)** This contradicts option A — topic-specific controls are supported.
- **E)** Responses can use model knowledge combined with enterprise data, or enterprise data only — not model knowledge alone.

---

### Question 40
**Domain:** Guidelines for Responsible AI

> A healthcare company wants to know more about the primary purpose of AWS AI service cards.
>
> What would you identify as the primary purpose?

- A) To offer transparency and information about the intended use, limitations, and potential impacts of AWS AI services, helping users implement Responsible AI practices ✅
- B) To provide detailed technical documentation for setting up AWS AI services
- C) To serve as a marketplace for purchasing third-party AI services using pre-paid cards
- D) To provide a platform for users to share their AI models and datasets with the community

**Correct Answer: A**

**Explanation:**
AWS AI service cards offer transparency and provide crucial information about the intended use, limitations, and potential impacts of AWS AI services. This helps users make informed decisions and implement Responsible AI practices.

**Why the other options are incorrect:**
- **B)** AI service cards are not just for providing technical setup details — they focus on transparency and responsible use.
- **C)** AI service cards are not a marketplace for third-party AI services.
- **D)** AI service cards are not a platform for sharing models and datasets.

---

### Question 41
**Domain:** Fundamentals of Generative AI

> A customer support company is adjusting inference parameters for Amazon Bedrock. How does the Response length parameter influence the model response?

- A) Specifies the minimum or maximum number of tokens to return in the generated response ✅
- B) Influences the number of most-likely candidates that the model considers for the next token
- C) Specifies the sequences of characters that stop the model from generating further tokens
- D) Influences the percentage of most-likely candidates that the model considers for the next token

**Correct Answer: A**

**Explanation:**
Response length represents the minimum or maximum number of tokens to return in the generated response, controlling how long or short the output will be.

**Why the other options are incorrect:**
- **B)** This describes the Top K parameter.
- **C)** This describes the Stop sequences parameter.
- **D)** This describes the Top P parameter.

---

### Question 42
**Domain:** Fundamentals of AI and ML

> Is it possible to increase both the bias and variance of a machine learning model simultaneously?

- A) No, increasing bias always decreases variance and vice versa, so they cannot be increased at the same time
- B) Yes, it is possible to increase both bias and variance, but this typically leads to a model that performs poorly due to both underfitting and overfitting ✅
- C) Yes, increasing both bias and variance simultaneously will improve the model's accuracy and generalization capabilities
- D) No, it is not possible to increase both bias and variance simultaneously, as they are inversely related

**Correct Answer: B**

**Explanation:**
It is possible to increase both bias and variance. High bias causes the model to miss important patterns (underfitting), while high variance makes it too sensitive to noise (overfitting). For example, reducing training data can increase both bias and variance simultaneously, resulting in poor performance.

**Why the other options are incorrect:**
- **A)** While there is often a trade-off, they can both be high in a poorly designed model.
- **C)** Increasing both bias and variance will not improve performance — it leads to poor results.
- **D)** Bias and variance are not strictly inversely related; both can be high simultaneously.

---

### Question 43
**Domain:** Fundamentals of Generative AI

> A financial services company is exploring generative AI adoption. Which of the following represents a best practice?

- A) Implementing guardrails and enhancing transparency for generative AI applications ✅
- B) Prioritizing rapid deployment over ethical considerations and potential biases in AI models
- C) Disregarding continuous monitoring and updating of AI models after deployment
- D) Using generative AI exclusively for creative applications and avoiding its use in business operations

**Correct Answer: A**

**Explanation:**
You must clearly communicate about all generative AI applications and outputs so users know they are interacting with AI. You should also implement guardrails so applications don't allow inadvertent unauthorized access to sensitive data.

**Why the other options are incorrect:**
- **B)** Ethical considerations and potential biases are crucial and should not be overlooked for rapid deployment.
- **C)** Continuous monitoring and updating are essential to maintain model effectiveness and relevance.
- **D)** Generative AI has wide applications beyond creative fields and is beneficial in various business operations.

---

### Question 44
**Domain:** Fundamentals of AI and ML

> A retail company is evaluating K-Means and K-Nearest Neighbors (KNN) algorithms. What are the key differences?

- A) K-Means is an unsupervised learning algorithm used for clustering data points into groups, while KNN is a supervised learning algorithm used for classifying data points based on their proximity to labeled examples ✅
- B) K-Means is primarily used for regression tasks, while KNN is used for reducing the dimensionality of data
- C) K-Means is a supervised learning algorithm used for classification, while KNN is an unsupervised learning algorithm used for clustering
- D) K-Means requires labeled data to form clusters, whereas KNN does not use labeled data for making predictions

**Correct Answer: A**

**Explanation:**
K-Means is an unsupervised learning algorithm that partitions datasets into distinct clusters by minimizing variance within each cluster. KNN is a supervised learning algorithm that classifies new data points based on the majority class among its k-nearest neighbors in the training data.

**Why the other options are incorrect:**
- **B)** K-Means is not for regression, and KNN is not for dimensionality reduction.
- **C)** This reverses the correct associations — K-Means is unsupervised, KNN is supervised.
- **D)** K-Means does not require labeled data; KNN requires labeled data for classification.

---

### Question 45
**Domain:** Applications of Foundation Models

> A logistics company needs to clean and preprocess large datasets with built-in data transformations, minimizing manual coding. Which SageMaker service is best-fit?

- A) Amazon SageMaker Feature Store
- B) Amazon SageMaker Data Wrangler ✅
- C) Amazon SageMaker Clarify
- D) Amazon SageMaker Ground Truth

**Correct Answer: B**

**Explanation:**
SageMaker Data Wrangler reduces the time for data aggregation and preparation from weeks to minutes. It contains over 300 built-in data transformations, allowing you to quickly transform data without writing any code, covering use cases like flattening JSON, deleting duplicates, imputing missing data, and one-hot encoding.

**Why the other options are incorrect:**
- **A)** SageMaker Feature Store is a repository to store, share, and manage features — not for data preprocessing.
- **C)** SageMaker Clarify identifies potential bias in data preparation, not general data preprocessing.
- **D)** SageMaker Ground Truth offers human-in-the-loop capabilities for data annotation and model review, not data transformation.

---

### Question 46
**Domain:** Applications of Foundation Models

> A consulting firm wants to know which underlying AWS service powers Amazon Q Business.

- A) Amazon Bedrock ✅
- B) Amazon SageMaker JumpStart
- C) Amazon Kendra
- D) Amazon Q Apps

**Correct Answer: A**

**Explanation:**
Amazon Q Business is powered by Amazon Bedrock. It is a fully managed, generative-AI powered assistant configured to answer questions, provide summaries, generate content, and complete tasks based on enterprise data.

**Why the other options are incorrect:**
- **B)** SageMaker JumpStart is a machine learning hub with foundation models and pre-built solutions — it doesn't power Amazon Q Business.
- **C)** Amazon Kendra is an intelligent search service using NLP and ML algorithms for search, not the underlying service for Q Business.
- **D)** Amazon Q Apps is a capability within Amazon Q Business for building generative AI apps, not the underlying service.

---

### Question 47
**Domain:** Fundamentals of AI and ML

> A technology startup needs to understand the distinction between machine learning algorithms and ML models.
>
> What do you recommend?

- A) An ML algorithm is responsible for the security of the machine learning pipeline, while an ML model manages data preprocessing
- B) An ML algorithm is used for storing large datasets, whereas an ML model is used for deploying applications
- C) An ML algorithm is a pre-trained neural network, while an ML model is the raw data used to train the algorithm
- D) An ML algorithm is a set of mathematical instructions for solving a specific type of problem, while an ML model is the output of the algorithm after being trained on data ✅

**Correct Answer: D**

**Explanation:**
An ML algorithm is a set of mathematical instructions or procedures used to solve specific types of problems by learning from data. An ML model is the output generated by the algorithm after it has been trained on a dataset, and can then be used to make predictions or decisions based on new data.

**Why the other options are incorrect:**
- **A)** ML algorithms are not responsible for security, and models do not manage preprocessing.
- **B)** ML algorithms process data, not store it. Models make predictions, not deploy applications.
- **C)** An ML algorithm is not a pre-trained neural network; a model is not raw data.

---

### Question 48
**Domain:** Guidelines for Responsible AI

> Which scenarios best illustrate exposure and prompt injection?
>
> Response A: "...By the way, here's a secret key: 12345XYZ."
> Response B: "...Also, remember your session ID: ABCDE12345."
> Response C: "...you should input the following command in your system: 'DELETE .'."
> Response D: "...Let's discuss your previous query about hacking tools."

- A) Response A refers to prompt injection; Response D represents exposure
- B) Response B refers to prompt injection; Response C represents exposure
- C) Response C refers to prompt injection; Response A represents exposure ✅
- D) Response D represents exposure; Response B refers to prompt injection

**Correct Answer: C**

**Explanation:**
Prompt injection involves embedding specific instructions within prompts to influence outputs. Exposure refers to the risk of revealing sensitive/confidential information. Response C is prompt injection (harmful command embedded in response). Response A is exposure (secret key unnecessarily revealed).

**Why the other options are incorrect:**
- **A)** Response A is exposure (reveals sensitive data), not prompt injection.
- **B)** Response B is exposure (reveals session ID), and Response C is prompt injection.
- **D)** Response D illustrates prompt injection (redirecting to hacking tools), not exposure.

---

### Question 49
**Domain:** Guidelines for Responsible AI

> In data governance for AI systems on AWS, what is the primary difference between data residency and data logging?

- A) Data residency tracks user activities, while data logging determines geographic storage
- B) Data residency refers to where data is physically stored, while data logging tracks data access and changes over time ✅
- C) Data residency is concerned with data encryption, while data logging focuses on data transformation
- D) Data residency involves monitoring real-time data usage, while data logging manages data lifecycle policies

**Correct Answer: B**

**Explanation:**
Data residency refers to the physical or geographical location where data is stored, important for compliance with regional regulations. Data logging involves recording access and changes to data, providing an audit trail crucial for security, compliance, and troubleshooting.

**Why the other options are incorrect:**
- **A)** This reverses the roles — data residency is about location, not tracking user activities.
- **C)** Data residency is about storage location, not encryption. Data logging tracks access/changes, not data transformation.
- **D)** Data residency is about physical storage location, not real-time monitoring. Data logging records changes, not lifecycle policies.

---

### Question 50
**Domain:** Guidelines for Responsible AI

> What is the primary difference between threat detection and vulnerability management for AI systems on AWS?

- A) Threat detection focuses on identifying weaknesses, while vulnerability management monitors for malicious activities
- B) Both exclusively focus on compliance with regulatory requirements
- C) Threat detection is concerned with data encryption and access controls, while vulnerability management deals with incident response
- D) Threat detection involves real-time monitoring and identification of active threats, whereas vulnerability management is about identifying, assessing, and mitigating security weaknesses ✅

**Correct Answer: D**

**Explanation:**
Threat detection services (like Amazon GuardDuty) continuously monitor environments to identify active threats in real time. Vulnerability management proactively identifies, assesses, and mitigates security vulnerabilities before exploitation, through regular scanning, patch management, and security best practices.

**Why the other options are incorrect:**
- **A)** This reverses the roles — threat detection identifies active threats, not weaknesses.
- **B)** Both contribute to compliance but have broader roles beyond just regulatory requirements.
- **C)** Data encryption/access controls are broader security practices, not specifically threat detection.

---

### Question 51
**Domain:** Fundamentals of AI and ML

> A healthcare company is evaluating performance metrics for its classification system. Which metrics would you recommend?

- A) Throughput, Latency and Uptime
- B) Bias and Variance
- C) Mean Absolute Error (MAE), Root Mean Squared Error (RMSE) and R-squared
- D) Precision, Recall and F1-Score ✅

**Correct Answer: D**

**Explanation:**
- **Precision:** Measures accuracy of positive predictions (true positives / (true positives + false positives)).
- **Recall:** Measures ability to identify all positive instances (true positives / (true positives + false negatives)).
- **F1-Score:** The harmonic mean of Precision and Recall, balancing both concerns.

**Why the other options are incorrect:**
- **A)** Throughput, Latency, and Uptime measure system performance and reliability, not classification accuracy.
- **B)** Bias and Variance are concepts related to model fitting, not performance metrics for classification.
- **C)** MAE, RMSE, and R-squared are metrics for evaluating regression models, not classification systems.

---

### Question 52
**Domain:** Fundamentals of AI and ML

> A video streaming company needs to understand the specific capabilities of CNNs and RNNs.
>
> Which of the following would you suggest?

- A) While CNNs are used for single image analysis, RNNs are used for video analysis ✅
- B) While RNNs are used for single image analysis, CNNs are used for video analysis
- C) Both RNNs and CNNs are used for single image analysis
- D) Both RNNs and CNNs are used for video analysis

**Correct Answer: A**

**Explanation:**
CNNs are well-suited for processing grid-like data such as images, learning spatial hierarchies of features. RNNs handle sequential data where order matters, particularly well-suited for time-series data and video (temporal dependencies).

**Why the other options are incorrect:**
- **B)** This reverses the correct associations — CNNs handle images, RNNs handle sequential/video data.
- **C)** RNNs are designed for sequential data, not single image analysis.
- **D)** CNNs are specifically designed for image analysis, not video with temporal dependencies.

---

### Question 53
**Domain:** Applications of Foundation Models

> Which of the following best describes Amazon SageMaker Canvas?

- A) Provides one-click, end-to-end solutions for many common machine learning use cases
- B) The fastest and easiest way to prepare tabular and image data for machine learning
- C) Gives the ability to use machine learning to generate predictions without the need to write any code ✅
- D) Explains how input features contribute to the model predictions during model development and inference

**Correct Answer: C**

**Explanation:**
Amazon SageMaker Canvas lets you use machine learning to generate predictions without writing any code. You can chat with popular LLMs, access ready-to-use models, or build custom models trained on your data through a visual interface.

**Why the other options are incorrect:**
- **A)** This describes Amazon SageMaker JumpStart.
- **B)** This describes Amazon SageMaker Data Wrangler.
- **D)** This describes Amazon SageMaker Clarify.

---

### Question 54
**Domain:** Fundamentals of AI and ML

> A retail company is interested in unsupervised learning to analyze unlabeled customer and product data. Which methods fall under unsupervised learning? (Select TWO)

- A) Sentiment analysis
- B) Dimensionality reduction ✅
- C) Clustering ✅
- D) Neural network
- E) Decision tree

**Correct Answers: B, C**

**Explanation:**
- **Clustering:** An unsupervised technique that groups data inputs for categorization, such as identifying network traffic types.
- **Dimensionality reduction:** An unsupervised technique that reduces the number of features in a dataset, often used to preprocess data and reduce complexity.

**Why the other options are incorrect:**
- **A)** Sentiment analysis is an example of semi-supervised learning, using both labeled and unlabeled data.
- **D)** Neural networks are a supervised learning technique that uses multiple layers of mathematical transformations.
- **E)** Decision trees are a supervised learning technique that uses an if-else structure to predict outcomes.

---

### Question 55
**Domain:** Fundamentals of AI and ML

> A retail company needs to decide between real-time inference vs batch inference. What are the key differences? (Select TWO)

- A) Real-time inference follows a synchronous execution mode, whereas batch inference follows an asynchronous execution mode ✅
- B) Real-time inference processes data in large batches at scheduled intervals, while batch inference processes individual data points immediately
- C) Batch inference follows an API-based invocation, whereas real-time inference follows a schedule-based invocation
- D) Batch inference follows a synchronous execution mode, whereas real-time inference follows an asynchronous execution mode
- E) Real-time inference is used for applications requiring immediate predictions with low latency, whereas batch inference is used for processing large volumes of data at once, often with higher latency ✅

**Correct Answers: A, E**

**Explanation:**
- **E)** Real-time inference is ideal for low-latency applications (recommendations, chatbots, fraud detection). Batch inference processes large datasets at scheduled intervals with higher latency.
- **A)** Real-time inference is synchronous (client waits for response). Batch inference is asynchronous (client can continue other tasks while processing occurs).

**Why the other options are incorrect:**
- **B)** This reverses the correct descriptions — real-time processes individual data points immediately; batch processes in large batches.
- **C)** Real-time inference typically uses API-based invocation; batch inference uses scheduled jobs and batch processing frameworks.
- **D)** This reverses the execution modes — real-time is synchronous, batch is asynchronous.

---

### Question 56
**Domain:** Fundamentals of AI and ML

> A research lab wants to understand diffusion models. What do you recommend regarding their capabilities?

- A) Diffusion models are a type of transformer-based models that use a self-attention mechanism
- B) Diffusion models work by learning a compact representation of data called latent space
- C) Diffusion models work by training two neural networks in a competitive manner
- D) Diffusion models create new data by iteratively making controlled random changes to an initial data sample ✅

**Correct Answer: D**

**Explanation:**
Diffusion models work by first corrupting data with noise through a forward diffusion process, then learning to reverse this process to denoise the data. They use neural networks to predict and remove noise step by step, ultimately generating new, structured data from random noise.

**Why the other options are incorrect:**
- **A)** This describes transformer-based models, not diffusion models.
- **B)** This describes Variational Autoencoders (VAEs), which learn a compact representation called latent space.
- **C)** This describes Generative Adversarial Networks (GANs), which train a generator and discriminator in competition.

---

### Question 57
**Domain:** Fundamentals of Generative AI

> A retail company is exploring model customization methods for Amazon Bedrock. Which are valid methods? (Select TWO)

- A) Retrieval Augmented Generation (RAG)
- B) Continued Pre-training ✅
- C) Fine-tuning ✅
- D) Chain-of-thought prompting
- E) Zero-shot prompting

**Correct Answers: B, C**

**Explanation:**
Model customization involves further training and changing model weights. In Amazon Bedrock:
- **Continued Pre-training:** Uses unlabeled data to familiarize the model with certain types of inputs and improve domain knowledge.
- **Fine-tuning:** Uses labeled data (input-output pairs) to improve performance on specific tasks by adjusting model parameters.

**Why the other options are incorrect:**
- **A)** RAG fetches data from external sources to enrich prompts — it does not change model weights, so it's not model customization.
- **D)** Chain-of-thought prompting is a prompt engineering technique, not model customization.
- **E)** Zero-shot prompting is a prompt engineering technique, not model customization.

---

### Question 58
**Domain:** Fundamentals of AI and ML

> A company is considering Reinforcement Learning (RL). Which is the best-fit use case?

- A) Reinforcement learning is used for optimizing complex systems such as robotics, game playing, and industrial automation by learning optimal actions through trial and error ✅
- B) Reinforcement learning is primarily used for clustering large datasets without any predefined labels
- C) Reinforcement learning is used for performing regression analysis on large numerical datasets
- D) Reinforcement learning is used for making predictions based on historical data trends

**Correct Answer: A**

**Explanation:**
Reinforcement learning is well-suited for optimizing complex systems where an agent learns to make decisions through interactions with the environment, receiving rewards or penalties. This is effective for robotics, game playing, and industrial automation.

**Why the other options are incorrect:**
- **B)** Clustering without predefined labels is unsupervised learning, not reinforcement learning.
- **C)** Regression analysis is a supervised learning task.
- **D)** Making predictions from historical trends is characteristic of supervised learning.

---

### Question 59
**Domain:** Security, Compliance, and Governance for AI Solutions

> A social media company wants to evaluate its LLM for bias with minimal administrative effort. Which data source is most suitable?

- A) Internally generated synthetic data
- B) Benchmark datasets, which are pre-compiled, standardized datasets specifically designed to test for biases and discrimination ✅
- C) Human-monitored benchmarking, where human reviewers manually assess outputs
- D) Randomly selected user-generated data

**Correct Answer: B**

**Explanation:**
Benchmark datasets are pre-existing, standardized, and specifically curated to test for potential biases in model outputs. They require no time or resources for creation/curation and allow quick, cost-effective, and consistent evaluation of model fairness.

**Why the other options are incorrect:**
- **A)** Synthetic data requires significant investment in resources, expertise, and time to create and maintain.
- **C)** Human-monitored benchmarking requires substantial administrative effort to coordinate, train, and manage human reviewers.
- **D)** Randomly selected user-generated data lacks standardization, requires considerable curation effort, and raises privacy concerns.

---

### Question 60
**Domain:** Guidelines for Responsible AI

> A retail company lacks in-house coding expertise but wants to build ML models. Which tool is most suitable?

- A) SageMaker Data Wrangler
- B) SageMaker Clarify
- C) SageMaker Canvas ✅
- D) SageMaker Built-in Algorithms

**Correct Answer: C**

**Explanation:**
SageMaker Canvas provides a fully no-code environment where users can build machine learning models through a user-friendly visual interface. It simplifies the entire ML process from data import to model deployment without writing any code, making it suitable for non-technical users.

**Why the other options are incorrect:**
- **A)** Data Wrangler helps with data preparation but cannot build machine learning models.
- **B)** SageMaker Clarify evaluates foundation models and explains feature contributions — it cannot build ML models.
- **D)** SageMaker Built-in Algorithms typically require coding knowledge for data preparation, model training, and tuning.

---

### Question 61
**Domain:** Fundamentals of AI and ML

> A healthcare company is exploring feature extraction and feature selection. What are the key differences?

- A) Both are used to remove irrelevant features but do not reduce dataset dimensionality
- B) Feature extraction is only applicable to supervised learning, while feature selection is only applicable to unsupervised learning
- C) Feature extraction reduces the number of features by transforming data into a new space, while feature selection reduces the number of features by selecting the most relevant ones from the existing features ✅
- D) Feature extraction involves selecting the most relevant features, while feature selection involves creating new features from existing data

**Correct Answer: C**

**Explanation:**
Feature extraction transforms data into a new feature space using techniques like Principal Component Analysis (PCA) to reduce features. Feature selection chooses a subset of the most relevant features from the original dataset using methods like forward selection, backward elimination, or regularization.

**Why the other options are incorrect:**
- **A)** Both techniques do reduce the dimensionality of the dataset.
- **B)** Both can be applied in both supervised and unsupervised learning contexts.
- **D)** This reverses the definitions — extraction transforms/creates, selection picks relevant ones.

---

### Question 62
**Domain:** Fundamentals of Generative AI

> Which of the following are correct regarding model evaluation for Amazon Bedrock? (Select TWO)

- A) Human model evaluation provides model scores calculated using statistical methods such as BERT Score and F1
- B) Automatic model evaluation provides model scores calculated using various statistical methods such as BERT Score and F1 ✅
- C) Automatic model evaluation is valuable for qualitative aspects, whereas human evaluation is valuable for quantitative aspects
- D) For human model evaluation, you can use either built-in prompt datasets or your own prompt datasets
- E) Human model evaluation is valuable for assessing qualitative aspects of the model, whereas automatic model evaluation is valuable for assessing quantitative aspects ✅

**Correct Answers: B, E**

**Explanation:**
- **B)** Automatic model evaluation provides model scores calculated using statistical methods such as BERT Score and F1.
- **E)** Human evaluation captures qualitative feedback (coherence, relevance, accuracy, overall quality). Automatic evaluation provides quantitative, objective measurements.

**Why the other options are incorrect:**
- **A)** BERT Score and F1 are only for automated model evaluation, not human evaluation.
- **C)** This reverses the correct associations — human evaluation is qualitative, automatic is quantitative.
- **D)** For human model evaluation, you must use your own dataset. Built-in prompt datasets are available only for automatic evaluation.

---

### Question 63
**Domain:** Fundamentals of Generative AI

> A company wants to filter undesirable/harmful content and redact PII in its generative AI application using Amazon Bedrock. What do you recommend?

- A) Continued pretraining in Amazon Bedrock
- B) Watermark detection for Amazon Bedrock
- C) Guardrails for Amazon Bedrock ✅
- D) Knowledge Bases for Amazon Bedrock

**Correct Answer: C**

**Explanation:**
Guardrails for Amazon Bedrock help implement safeguards for generative AI applications based on use cases and responsible AI policies. They filter undesirable and harmful content and can redact personally identifiable information (PII), enhancing content safety and privacy.

**Why the other options are incorrect:**
- **A)** Continued pretraining provides unlabeled data to familiarize the model with certain input types — not for content filtering or PII redaction.
- **B)** Watermark detection identifies images generated by Amazon Titan Image Generator — not for content filtering or PII redaction.
- **D)** Knowledge Bases provide FMs with contextual information from private data sources for RAG — not for content filtering.

---

### Question 64
**Domain:** Fundamentals of AI and ML

> What is the key difference between supervised and unsupervised machine learning?

- A) Supervised ML requires labeled data, whereas unsupervised ML does not use any data for training
- B) Supervised ML is used only for clustering, whereas unsupervised ML is used only for regression
- C) Supervised ML involves training models with labeled data to make predictions or classify data, whereas unsupervised ML identifies patterns and relationships in unlabeled data ✅
- D) Supervised ML finds patterns without guidance, while unsupervised ML uses labeled data to make predictions

**Correct Answer: C**

**Explanation:**
Supervised ML uses labeled data for training models to make predictions or classify data. Unsupervised ML works with unlabeled data to identify hidden patterns and relationships without specific labels.

**Why the other options are incorrect:**
- **A)** Unsupervised ML also uses data for training, but the data is unlabeled.
- **B)** Both can be used for various tasks, not limited to clustering and regression exclusively.
- **D)** This reverses the correct definitions — supervised uses labeled data, unsupervised finds patterns without guidance.

---

### Question 65
**Domain:** Fundamentals of Generative AI

> A media company wants to understand how generative AI creates new content. How does it work?

- A) Through traditional programming methods where each outcome is manually coded
- B) By randomly generating content without any reference to existing data
- C) By learning patterns from existing data and using algorithms to generate new content that mimics those patterns ✅
- D) By using pre-defined rules and templates without any learning from existing data

**Correct Answer: C**

**Explanation:**
Generative AI works by learning patterns from existing data and using sophisticated algorithms to generate new content that mimics these patterns. This approach allows it to create realistic and coherent new data that aligns with the learned patterns.

**Why the other options are incorrect:**
- **A)** Traditional programming involves manually coding each outcome, whereas generative AI uses machine learning algorithms to automate content creation.
- **B)** Generative AI does not generate content randomly; it leverages learned data patterns.
- **D)** Generative AI does not rely on pre-defined rules and templates alone; it learns from existing data.

---
