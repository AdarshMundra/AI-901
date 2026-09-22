# Section 3: Azure Language in Foundry Tools (Text Analysis / NLP)
## AI-901 Practice Exam Questions (55 Questions)

---

## Setup Reference

```python
pip install azure-ai-textanalytics

from azure.core.credentials import AzureKeyCredential
from azure.ai.textanalytics import TextAnalyticsClient

endpoint = "https://<resource>.cognitiveservices.azure.com/"
key = "<your-key>"
client = TextAnalyticsClient(endpoint=endpoint, credential=AzureKeyCredential(key))
```

**Key Methods:**
| Method | Purpose |
|--------|---------|
| `detect_language()` | Identify the language of text |
| `recognize_pii_entities()` | Find and redact personal information |
| `analyze_sentiment()` | Determine positive/negative/neutral/mixed sentiment |
| `recognize_entities()` | Named Entity Recognition (NER) |
| `extract_key_phrases()` | Pull out important phrases |

All methods accept a **list** of strings and return a **list** of results.

---

## PART A: Foundations (Questions 1-10)

**Q1. (Fill-in-the-blank)**
To install the Azure Text Analytics SDK, you run:
```
pip install _______________
```
- A) `azure-ai-language`
- B) `azure-ai-textanalytics`
- C) `azure-cognitiveservices-text`
- D) `azure-text-analytics`

---

**Q2. (Code Output)**
What does the following code print?
```python
from azure.core.credentials import AzureKeyCredential
cred = AzureKeyCredential("my-secret-key")
print(type(cred).__name__)
```
- A) `str`
- B) `AzureKeyCredential`
- C) `Credential`
- D) `KeyCredential`

---

**Q3. (Bug Finding)**
This code crashes on the last line. Why?
```python
client = TextAnalyticsClient(endpoint=endpoint, credential=key)
result = client.detect_language(["Hello"])
```
- A) `detect_language` does not accept a list
- B) The `credential` parameter requires an `AzureKeyCredential` object, not a raw string
- C) The endpoint URL is wrong
- D) You must pass a dictionary, not a string

---

**Q4. (True/False)**
The `TextAnalyticsClient` endpoint format is `https://<resource>.cognitiveservices.azure.com/`.

- A) True
- B) False

---

**Q5. (Compare & Contrast)**
Which TWO statements correctly distinguish the Azure Language SDK from the OpenAI API for text analysis?

- A) The Language SDK returns structured, consistent results; the OpenAI API returns probabilistic, flexible responses
- B) The OpenAI API is better for entity recognition because it has a dedicated `recognize_entities` method
- C) The Language SDK requires you to parse free-text responses to extract sentiment
- D) The Language SDK provides dedicated methods like `analyze_sentiment()` with typed output fields
- E) Both approaches return identical JSON schemas

---

**Q6. (Fill-in-the-blank)**
Complete the client creation line:
```python
client = TextAnalyticsClient(
    endpoint=endpoint,
    credential=_______________(key)
)
```

- A) `ApiKeyCredential`
- B) `AzureKeyCredential`
- C) `TokenCredential`
- D) `DefaultAzureCredential`

---

**Q7. (Multiple Correct)**
Which of the following are valid methods on `TextAnalyticsClient`? (Select ALL that apply)

- A) `detect_language()`
- B) `translate_text()`
- C) `recognize_pii_entities()`
- D) `analyze_sentiment()`
- E) `generate_summary()`
- F) `extract_key_phrases()`
- G) `recognize_entities()`

---

**Q8. (True/False)**
All `TextAnalyticsClient` methods accept a single string directly, like `client.detect_language("Hello")`.

- A) True
- B) False

---

**Q9. (Order the Steps)**
Arrange these steps in the correct order to use Azure Language for text analysis:

1. Call a method like `client.analyze_sentiment([text])`
2. `pip install azure-ai-textanalytics`
3. Create an `AzureKeyCredential` with your key
4. Access results via `result[0].sentiment`
5. Create a `TextAnalyticsClient` with endpoint and credential
6. Import `TextAnalyticsClient` and `AzureKeyCredential`

- A) 2, 6, 3, 5, 1, 4
- B) 6, 2, 3, 5, 1, 4
- C) 2, 6, 5, 3, 1, 4
- D) 6, 3, 5, 2, 1, 4

---

**Q10. (Scenario)**
A developer wants to quickly prototype a chatbot that sometimes summarizes text and sometimes detects sentiment, with creative and varied outputs. Which approach is more suitable?

- A) Azure Language SDK -- it provides structured sentiment analysis
- B) OpenAI API -- it offers flexible, prompt-based responses for varied tasks
- C) Azure Language SDK -- it handles summarization and creative generation natively
- D) Neither; you need Azure Translator for this

---

### ANSWERS: Part A (Questions 1-10)

| Q | Answer | Explanation |
|---|--------|-------------|
| 1 | **B** | The correct package is `azure-ai-textanalytics`. |
| 2 | **B** | `type(cred).__name__` returns the class name `"AzureKeyCredential"`. |
| 3 | **B** | The `credential` parameter needs an `AzureKeyCredential` object wrapping the key string, not the raw string itself. Correct: `credential=AzureKeyCredential(key)`. |
| 4 | **A (True)** | The standard endpoint format is `https://<resource>.cognitiveservices.azure.com/`. |
| 5 | **A, D** | The Language SDK returns structured/consistent data with dedicated typed methods. The OpenAI API is probabilistic and flexible but lacks dedicated NER methods. |
| 6 | **B** | `AzureKeyCredential` is the correct class from `azure.core.credentials`. |
| 7 | **A, C, D, F, G** | `translate_text()` belongs to Azure Translator. `generate_summary()` is not a standard method on this client. The five valid methods are detect_language, recognize_pii_entities, analyze_sentiment, extract_key_phrases, and recognize_entities. |
| 8 | **B (False)** | All methods require a **list** of strings, e.g., `client.detect_language(["Hello"])`. Passing a bare string will raise an error. |
| 9 | **A** | Install -> Import -> Create credential -> Create client -> Call method -> Access results. |
| 10 | **B** | For creative, flexible, varied tasks the OpenAI API is more suitable. The Language SDK excels at structured, consistent NLP tasks like sentiment analysis but is not designed for creative generation. |

---

## PART B: Language Detection (Questions 11-20)

**Q11. (Code Output)**
```python
result = client.detect_language(["Bonjour tout le monde"])[0]
print(result.primary_language.name)
```
What is printed?
- A) `"fr"`
- B) `"French"`
- C) `"Bonjour"`
- D) `"fra"`

---

**Q12. (Code Output)**
```python
result = client.detect_language(["Bonjour tout le monde"])[0]
print(result.primary_language.iso6391_name)
```
What is printed?
- A) `"French"`
- B) `"fr"`
- C) `"FR"`
- D) `"fra"`

---

**Q13. (Data Interpretation)**
A language detection call returns `confidence_score = 0.42`. What does this indicate?

- A) The text is in 42 languages
- B) The service is 42% confident in the detected language -- the text may be ambiguous or very short
- C) The text has 42 characters
- D) The detection failed

---

**Q14. (Bug Finding)**
This code does not produce the expected language name. Why?
```python
result = client.detect_language(["Guten Tag"])[0]
print(result.iso6391_name)
```
- A) `"Guten Tag"` is not recognized
- B) The attribute path is wrong; it should be `result.primary_language.iso6391_name`
- C) `detect_language` returns a string, not an object
- D) You need to pass `language="de"` as a hint

---

**Q15. (Edge Case)**
What is the most likely behavior when you call:
```python
result = client.detect_language([""])[0]
```
- A) Returns `"English"` by default
- B) Returns `"(Unknown)"` with a low confidence score
- C) Throws a `ValueError` immediately
- D) Returns `None` for `primary_language`

---

**Q16. (True/False)**
`confidence_score` for language detection ranges from 0.0 to 1.0, where 1.0 means maximum confidence.

- A) True
- B) False

---

**Q17. (Fill-in-the-blank)**
To get the ISO 639-1 code (e.g., `"fr"`) from a language detection result, you access:
```python
result.primary_language._______________
```
- A) `language_code`
- B) `iso_code`
- C) `iso6391_name`
- D) `code`

---

**Q18. (Scenario)**
A company receives customer emails in English, Spanish, French, and German. They need to automatically route emails to the correct support team based on language. Which approach is best?

- A) Use the OpenAI API to ask "What language is this?"
- B) Use `client.detect_language()` and route based on `primary_language.iso6391_name`
- C) Use `client.analyze_sentiment()` since sentiment reveals language
- D) Manually tag each email

---

**Q19. (Multiple Correct)**
Which TWO properties are available on `result.primary_language` after calling `detect_language()`?

- A) `name` (e.g., `"French"`)
- B) `sentiment` (e.g., `"positive"`)
- C) `iso6391_name` (e.g., `"fr"`)
- D) `key_phrases` (e.g., `["hello"]`)

---

**Q20. (Code Output)**
```python
docs = ["Hello world", "Hola mundo", "Bonjour"]
results = client.detect_language(docs)
print(len(results))
```
What is printed?
- A) `1`
- B) `2`
- C) `3`
- D) An error -- you can only pass one document

---

### ANSWERS: Part B (Questions 11-20)

| Q | Answer | Explanation |
|---|--------|-------------|
| 11 | **B** | `.name` returns the human-readable name `"French"`. |
| 12 | **B** | `.iso6391_name` returns the two-letter ISO code `"fr"`. |
| 13 | **B** | Confidence scores range 0-1. A score of 0.42 means the service is not very confident, likely due to short or ambiguous text. |
| 14 | **B** | The correct path is `result.primary_language.iso6391_name`, not `result.iso6391_name`. The `primary_language` level is required. |
| 15 | **B** | Empty strings typically return `"(Unknown)"` with a very low confidence score since there is no text to analyze. |
| 16 | **A (True)** | Confidence scores are always between 0.0 and 1.0 inclusive. |
| 17 | **C** | The property is `iso6391_name`, returning codes like `"fr"`, `"en"`, `"de"`. |
| 18 | **B** | `detect_language()` provides consistent, structured language codes perfect for automated routing. The OpenAI API would work but is overkill and less consistent for this specific task. |
| 19 | **A, C** | `primary_language` has `name`, `iso6391_name`, and `confidence_score`. Sentiment and key_phrases come from different methods. |
| 20 | **C** | The SDK processes lists and returns one result per input document. Three inputs produce three results. |

---

## PART C: PII Detection & Named Entity Recognition (Questions 21-32)

**Q21. (Code Output)**
```python
result = client.recognize_pii_entities(["Maria called from 020 7946 0958"])[0]
print(result.redacted_text)
```
What is the approximate output?
- A) `"Maria called from 020 7946 0958"`
- B) `"***** called from ************"`
- C) `"[REDACTED] called from [REDACTED]"`
- D) `""`

---

**Q22. (Code Output)**
```python
result = client.recognize_pii_entities(["Maria called from 020 7946 0958"])[0]
print(result.entities[0].category)
```
What is the most likely output?
- A) `"Name"`
- B) `"PersonName"`
- C) `"Person"`
- D) `"Individual"`

---

**Q23. (Data Interpretation)**
Given this PII result:
```
Entity: "Maria", Category: "PersonName", Confidence: 0.95
Entity: "020 7946 0958", Category: "PhoneNumber", Confidence: 0.88
```
Which entity was the service MORE confident about?
- A) The phone number
- B) The person name
- C) Both have equal confidence
- D) Cannot be determined

---

**Q24. (Bug Finding)**
A developer writes this code to redact PII but gets an `AttributeError`:
```python
result = client.recognize_pii_entities(["Call John at john@email.com"])[0]
print(result.redacted)
```
What is wrong?
- A) The method name is wrong
- B) The attribute is `redacted_text`, not `redacted`
- C) PII detection does not support email addresses
- D) You must pass `redact=True` as a parameter

---

**Q25. (Matching)**
Match each PII entity to its correct category:

| Entity | Category |
|--------|----------|
| 1. `"Sarah"` | a. `PhoneNumber` |
| 2. `"sarah@company.com"` | b. `Address` |
| 3. `"555-0123"` | c. `PersonName` |
| 4. `"123 Main St, Seattle"` | d. `Email` |

- A) 1-c, 2-d, 3-a, 4-b
- B) 1-c, 2-a, 3-d, 4-b
- C) 1-d, 2-c, 3-a, 4-b
- D) 1-c, 2-d, 3-b, 4-a

---

**Q26. (Compare & Contrast)**
What is the key difference between `recognize_pii_entities()` and `recognize_entities()`?

- A) They are identical methods with different names
- B) `recognize_pii_entities()` focuses on personal/sensitive data and provides `redacted_text`; `recognize_entities()` identifies general named entities like organizations and locations
- C) `recognize_entities()` only works with English text
- D) `recognize_pii_entities()` only detects phone numbers

---

**Q27. (Code Output)**
```python
result = client.recognize_entities(["Microsoft was founded in Redmond"])[0]
for entity in result.entities:
    print(f"{entity.text}: {entity.category}")
```
What is the approximate output?
- A) `Microsoft: Company` and `Redmond: City`
- B) `Microsoft: Organization` and `Redmond: Location`
- C) `Microsoft: PersonName` and `Redmond: Address`
- D) `Microsoft: Brand` and `Redmond: Place`

---

**Q28. (Scenario)**
A hospital needs to process patient notes and remove all personal information before sharing with researchers. Which method should they use?

- A) `client.analyze_sentiment()` -- to understand the tone of the notes
- B) `client.recognize_entities()` -- to find all named entities
- C) `client.recognize_pii_entities()` -- to detect and redact personal data
- D) `client.extract_key_phrases()` -- to summarize the notes

---

**Q29. (True/False)**
The `recognize_pii_entities()` method returns a `redacted_text` field where PII is replaced with asterisks (`*`).

- A) True
- B) False

---

**Q30. (Error Diagnosis)**
```python
result = client.recognize_pii_entities("My SSN is 123-45-6789")[0]
```
This code raises an error. What is wrong?

- A) Social Security Numbers are not supported
- B) The input must be a list: `["My SSN is 123-45-6789"]`
- C) You need to specify `categories=["SSN"]`
- D) `recognize_pii_entities` is not a valid method

---

**Q31. (Multiple Correct)**
Which of the following are valid PII categories returned by `recognize_pii_entities()`? (Select ALL that apply)

- A) `PersonName`
- B) `PhoneNumber`
- C) `CreditCardNumber`
- D) `Email`
- E) `Address`
- F) `FavoriteColor`

---

**Q32. (Edge Case)**
What happens when you call `recognize_pii_entities()` on text that contains no personal information?
```python
result = client.recognize_pii_entities(["The sky is blue"])[0]
```
- A) The method throws an exception
- B) `result.entities` is an empty list and `result.redacted_text` equals the original text
- C) `result.entities` contains `"sky"` as a Location entity
- D) The method returns `None`

---

### ANSWERS: Part C (Questions 21-32)

| Q | Answer | Explanation |
|---|--------|-------------|
| 21 | **B** | PII entities are replaced with asterisks. `"Maria"` becomes `"*****"` and the phone number becomes `"************"`. |
| 22 | **B** | The PII category for a person's name is `"PersonName"`, not `"Name"` or `"Person"`. |
| 23 | **B** | `"Maria"` has confidence 0.95 which is higher than the phone number's 0.88. |
| 24 | **B** | The correct attribute is `redacted_text`, not `redacted`. |
| 25 | **A** | Sarah = PersonName, sarah@company.com = Email, 555-0123 = PhoneNumber, 123 Main St = Address. |
| 26 | **B** | PII focuses on sensitive personal data and provides redaction. NER identifies general entities like organizations, locations, dates, etc. |
| 27 | **B** | NER uses categories like `Organization` and `Location`, not informal labels like "Company" or "City". |
| 28 | **C** | `recognize_pii_entities()` is designed exactly for this -- detecting and redacting personal information from text. |
| 29 | **A (True)** | `redacted_text` replaces each PII entity with asterisks matching the character length. |
| 30 | **B** | All SDK methods require a list of strings. Passing a bare string instead of `["..."]` causes a type error. |
| 31 | **A, B, C, D, E** | All are valid PII categories. `FavoriteColor` is not personal identifiable information tracked by the service. |
| 32 | **B** | When no PII is found, `entities` is empty and `redacted_text` is identical to the original input since nothing needs redaction. |

---

## PART D: Sentiment Analysis & Key Phrase Extraction (Questions 33-42)

**Q33. (Code Output)**
```python
result = client.analyze_sentiment(["Great product! Highly recommend."])[0]
print(result.sentiment)
```
What is printed?
- A) `"happy"`
- B) `"positive"`
- C) `"good"`
- D) `1.0`

---

**Q34. (Code Output)**
```python
result = client.analyze_sentiment(["Great product!"])[0]
print(result.confidence_scores.positive)
```
What type of value is returned?
- A) A boolean (`True`/`False`)
- B) A string (`"high"`)
- C) A float between 0 and 1 (e.g., `0.98`)
- D) An integer (e.g., `98`)

---

**Q35. (Multiple Correct)**
Which of the following are valid sentiment values returned by `analyze_sentiment()`? (Select ALL that apply)

- A) `"positive"`
- B) `"negative"`
- C) `"neutral"`
- D) `"mixed"`
- E) `"uncertain"`
- F) `"angry"`

---

**Q36. (Data Interpretation)**
A sentiment analysis result returns:
```
sentiment: "mixed"
confidence_scores.positive: 0.45
confidence_scores.negative: 0.40
confidence_scores.neutral: 0.15
```
What does this tell you about the text?

- A) The text is mostly positive
- B) The text contains both positive and negative opinions with no clear dominant sentiment
- C) The analysis failed
- D) The text is neutral

---

**Q37. (Scenario)**
An e-commerce company wants to automatically flag negative product reviews for urgent follow-up. Which code pattern is correct?

- A)
```python
result = client.analyze_sentiment([review_text])[0]
if result.sentiment == "negative":
    flag_for_followup(review_text)
```
- B)
```python
result = client.detect_language([review_text])[0]
if result.primary_language.name == "negative":
    flag_for_followup(review_text)
```
- C)
```python
result = client.extract_key_phrases([review_text])[0]
if "bad" in result.key_phrases:
    flag_for_followup(review_text)
```
- D)
```python
result = client.recognize_entities([review_text])[0]
if result.entities[0].category == "Negative":
    flag_for_followup(review_text)
```

---

**Q38. (Code Output)**
```python
result = client.extract_key_phrases(["Azure AI services are powerful and easy to use"])[0]
print(type(result.key_phrases))
```
What is printed?
- A) `<class 'str'>`
- B) `<class 'dict'>`
- C) `<class 'list'>`
- D) `<class 'tuple'>`

---

**Q39. (Bug Finding)**
This code is supposed to extract key phrases but crashes:
```python
result = client.extract_key_phrases("Azure AI is powerful")[0]
```
What is the bug?

- A) `extract_key_phrases` does not exist
- B) The input must be a list: `["Azure AI is powerful"]`
- C) Key phrase extraction requires at least 10 words
- D) You must specify `language="en"`

---

**Q40. (True/False)**
`extract_key_phrases()` returns a list of strings representing the most important phrases in the text.

- A) True
- B) False

---

**Q41. (Compare & Contrast)**
A developer needs to understand what topics customers are discussing. Which method is most appropriate?

- A) `analyze_sentiment()` -- tells you how customers feel
- B) `extract_key_phrases()` -- tells you what topics are being discussed
- C) `detect_language()` -- tells you what language they use
- D) `recognize_pii_entities()` -- tells you who the customers are

---

**Q42. (Edge Case)**
```python
result = client.analyze_sentiment([""])[0]
```
What is the most likely value of `result.sentiment`?

- A) `"positive"`
- B) `"negative"`
- C) `"neutral"`
- D) An exception is thrown

---

### ANSWERS: Part D (Questions 33-42)

| Q | Answer | Explanation |
|---|--------|-------------|
| 33 | **B** | Sentiment values are `"positive"`, `"negative"`, `"neutral"`, or `"mixed"`. Not informal labels like "happy" or "good". |
| 34 | **C** | Confidence scores are floats between 0 and 1, e.g., `0.98`. |
| 35 | **A, B, C, D** | The four valid sentiments are positive, negative, neutral, and mixed. "Uncertain" and "angry" are not valid values. |
| 36 | **B** | `"mixed"` sentiment with close positive (0.45) and negative (0.40) scores means the text expresses both positive and negative opinions. |
| 37 | **A** | `analyze_sentiment()` returns a structured `sentiment` field that can be compared to `"negative"` for routing. The other options use wrong methods for sentiment detection. |
| 38 | **C** | `key_phrases` is a list of strings. |
| 39 | **B** | All SDK methods require a list input. The fix is `client.extract_key_phrases(["Azure AI is powerful"])`. |
| 40 | **A (True)** | `key_phrases` returns a list of strings like `["Azure AI", "powerful"]`. |
| 41 | **B** | Key phrase extraction identifies the main topics and subjects in text. Sentiment tells you tone, not topics. |
| 42 | **C** | Empty or near-empty text typically returns `"neutral"` since there is no positive or negative content to detect. |

---

## PART E: Integrated Scenarios & Multi-Step (Questions 43-50)

**Q43. (Multi-Step Scenario)**
A company wants to process incoming support tickets: first detect the language, then analyze sentiment, then extract key phrases. Which code is correct?

- A)
```python
text = ["My order arrived broken and late"]
lang = client.detect_language(text)[0].primary_language.iso6391_name
sent = client.analyze_sentiment(text)[0].sentiment
phrases = client.extract_key_phrases(text)[0].key_phrases
```
- B)
```python
text = "My order arrived broken and late"
lang = client.detect_language(text).primary_language.iso6391_name
sent = client.analyze_sentiment(text).sentiment
phrases = client.extract_key_phrases(text).key_phrases
```
- C)
```python
text = ["My order arrived broken and late"]
result = client.analyze_all(text)
lang = result.language
sent = result.sentiment
phrases = result.key_phrases
```
- D)
```python
text = ["My order arrived broken and late"]
lang = client.detect_language(text)[0].iso6391_name
sent = client.analyze_sentiment(text)[0].confidence_scores
phrases = client.extract_key_phrases(text)[0]
```

---

**Q44. (Scenario)**
A law firm processes documents containing client names, phone numbers, and case details. They need to:
1. Redact all personal information before archiving
2. Understand the overall tone of the document
3. Identify key topics discussed

Which combination of methods do they need?

- A) `recognize_pii_entities()`, `analyze_sentiment()`, `extract_key_phrases()`
- B) `recognize_entities()`, `detect_language()`, `extract_key_phrases()`
- C) `recognize_pii_entities()`, `detect_language()`, `recognize_entities()`
- D) `analyze_sentiment()`, `extract_key_phrases()`, `detect_language()`

---

**Q45. (Error Diagnosis)**
```python
texts = ["I love this!", "Terrible service.", "It was okay."]
results = client.analyze_sentiment(texts)
print(results.sentiment)
```
This code crashes. Why?

- A) You cannot pass multiple texts at once
- B) `results` is a list, not a single object; you need `results[0].sentiment`, `results[1].sentiment`, etc.
- C) `analyze_sentiment` does not have a `.sentiment` attribute
- D) The texts are too short

---

**Q46. (Code Output)**
```python
texts = ["I love this!", "Terrible experience.", "It was fine."]
results = client.analyze_sentiment(texts)
sentiments = [r.sentiment for r in results]
print(sentiments)
```
What is the approximate output?

- A) `["positive", "negative", "neutral"]`
- B) `["love", "terrible", "fine"]`
- C) `[0.98, 0.02, 0.50]`
- D) `["happy", "angry", "indifferent"]`

---

**Q47. (Scenario)**
A multinational bank receives a message: `"Please transfer $5000 to John Smith at john.smith@bank.com, account 12345678."`

They run `recognize_pii_entities()` on this text. Which entities are MOST LIKELY to be detected? (Select ALL that apply)

- A) `"John Smith"` -- PersonName
- B) `"john.smith@bank.com"` -- Email
- C) `"$5000"` -- Currency (not a PII category)
- D) `"12345678"` -- could be flagged as a numeric identifier
- E) `"Please transfer"` -- Action verb (not a PII category)

---

**Q48. (Compare & Contrast)**
A startup is deciding between using the OpenAI API and the Azure Language SDK for a customer feedback analysis pipeline. They need consistent, repeatable results that can be programmatically compared week over week. Which is the better choice and why?

- A) OpenAI API -- its creative responses make analysis more interesting
- B) Azure Language SDK -- it returns structured, consistent output (e.g., always `"positive"`, `"negative"`, `"neutral"`, `"mixed"`) that is ideal for repeatable, automated pipelines
- C) OpenAI API -- it has a dedicated sentiment analysis endpoint
- D) Either works equally well for consistent pipelines

---

**Q49. (Multi-Step)**
Given this code:
```python
text = ["Maria from London called about a broken laptop. Terrible support!"]

pii = client.recognize_pii_entities(text)[0]
ner = client.recognize_entities(text)[0]
sent = client.analyze_sentiment(text)[0]
kp = client.extract_key_phrases(text)[0]
```
Match each variable to what it provides:

| Variable | Provides |
|----------|----------|
| 1. `pii.redacted_text` | a. `"negative"` |
| 2. `ner.entities` | b. `["broken laptop", "Terrible support"]` (approx.) |
| 3. `sent.sentiment` | c. `"***** from ****** called about a broken laptop..."` |
| 4. `kp.key_phrases` | d. Organization/Location/Person entities |

- A) 1-c, 2-d, 3-a, 4-b
- B) 1-d, 2-c, 3-b, 4-a
- C) 1-c, 2-a, 3-d, 4-b
- D) 1-a, 2-b, 3-c, 4-d

---

**Q50. (Scenario)**
A government agency processes citizen feedback in multiple languages. They want to:
1. Detect the language of each message
2. Only process English messages through sentiment analysis
3. Redact any personal information from all messages

Which code structure is correct?

- A)
```python
for msg in messages:
    lang = client.detect_language([msg])[0]
    pii = client.recognize_pii_entities([msg])[0]
    redacted = pii.redacted_text
    if lang.primary_language.iso6391_name == "en":
        sentiment = client.analyze_sentiment([msg])[0].sentiment
```
- B)
```python
for msg in messages:
    sentiment = client.analyze_sentiment([msg])[0]
    if sentiment.sentiment == "en":
        lang = client.detect_language([msg])[0]
```
- C)
```python
for msg in messages:
    lang = client.detect_language(msg)
    if lang == "English":
        sentiment = client.analyze_sentiment(msg)
```
- D)
```python
sentiment = client.analyze_sentiment(messages)
lang = client.detect_language(messages)
```

---

### ANSWERS: Part E (Questions 43-50)

| Q | Answer | Explanation |
|---|--------|-------------|
| 43 | **A** | All methods need list input and `[0]` to get the first result. Option A correctly uses lists and accesses `primary_language.iso6391_name`. Option B passes bare strings. Option C uses a non-existent `analyze_all` method. Option D accesses wrong attribute paths. |
| 44 | **A** | Redact PII = `recognize_pii_entities()`. Understand tone = `analyze_sentiment()`. Identify topics = `extract_key_phrases()`. |
| 45 | **B** | `client.analyze_sentiment(texts)` returns a **list** of results. You must index into it (e.g., `results[0].sentiment`). Calling `.sentiment` on the list itself causes an `AttributeError`. |
| 46 | **A** | The list comprehension extracts the sentiment string from each result. "I love this!" is positive, "Terrible experience." is negative, "It was fine." is neutral. |
| 47 | **A, B, D** | "John Smith" (PersonName) and "john.smith@bank.com" (Email) are clear PII. The account number may be flagged. "$5000" and "Please transfer" are not PII categories. |
| 48 | **B** | The Language SDK returns deterministic, structured results. Every call to `analyze_sentiment()` returns the same format with the same four possible values, making it ideal for automated pipelines that need week-over-week comparisons. |
| 49 | **A** | `pii.redacted_text` gives asterisk-redacted text (c). `ner.entities` gives named entities with categories (d). `sent.sentiment` gives the sentiment label (a). `kp.key_phrases` gives key phrases (b). |
| 50 | **A** | Option A correctly: uses list input for all methods, checks `iso6391_name == "en"` for language filtering, redacts all messages via PII detection, and only runs sentiment on English messages. |

---

## PART F: Advanced & Tricky Questions (Questions 51-55)

**Q51. (Tricky - Edge Case)**
```python
result = client.detect_language(["Je suis happy today, esto es loco"])[0]
print(result.primary_language.confidence_score > 0.9)
```
What is the most likely output?

- A) `True` -- the service always returns high confidence
- B) `False` -- the text mixes French, English, and Spanish, so confidence will likely be low
- C) An error -- mixed languages are not supported
- D) `True` -- it defaults to English with high confidence

---

**Q52. (Tricky - Code Analysis)**
```python
texts = ["Great!", "Awful!", "Meh."]
results = client.analyze_sentiment(texts)
avg_positive = sum(r.confidence_scores.positive for r in results) / len(results)
print(f"Average positive confidence: {avg_positive:.2f}")
```
Is this code valid and what does it compute?

- A) Invalid -- `confidence_scores.positive` is not a number
- B) Valid -- it computes the average positive confidence score across all three texts
- C) Invalid -- you cannot iterate over `results`
- D) Valid -- but it always returns exactly `0.33`

---

**Q53. (Tricky - Ordering)**
A developer runs all five methods on the same text. Which statement is TRUE?

- A) The methods must be called in a specific order or they will fail
- B) Each method is independent; they can be called in any order on the same text
- C) `detect_language()` must always be called first
- D) `analyze_sentiment()` must be called before `extract_key_phrases()`

---

**Q54. (Tricky - Multiple Correct)**
Which of the following are TRUE about the Azure Language SDK? (Select ALL that apply)

- A) All methods accept a list of strings as input
- B) All methods return a list of results, one per input document
- C) Confidence scores are always integers from 0 to 100
- D) `recognize_pii_entities()` provides both entity details and a redacted version of the text
- E) The SDK can process multiple documents in a single method call (batching)
- F) Sentiment analysis can only return `"positive"` or `"negative"`

---

**Q55. (Comprehensive Scenario)**
A healthcare company builds a patient feedback pipeline:

```python
feedback = [
    "Dr. Smith was wonderful. My recovery at 123 Oak St clinic was smooth.",
    "Terrible wait times. Nurse Jane was rude. Call me at 555-0199.",
    "The facilities were clean and modern."
]

# Step 1: Redact PII
pii_results = client.recognize_pii_entities(feedback)

# Step 2: Analyze sentiment
sentiment_results = client.analyze_sentiment(feedback)

# Step 3: Extract key phrases
kp_results = client.extract_key_phrases(feedback)
```

Which of the following are TRUE about the output? (Select ALL that apply)

- A) `pii_results[0].redacted_text` will have "Dr. Smith" and "123 Oak St" redacted
- B) `sentiment_results[1].sentiment` will likely be `"negative"`
- C) `kp_results[2].key_phrases` will likely include something like `"clean facilities"` or `"modern facilities"`
- D) `pii_results[1].entities` will include entities for "Nurse Jane" and "555-0199"
- E) `len(sentiment_results)` equals `3`
- F) `sentiment_results[0].confidence_scores.positive` will likely be close to `0.0`

---

### ANSWERS: Part F (Questions 51-55)

| Q | Answer | Explanation |
|---|--------|-------------|
| 51 | **B** | Text mixing French ("Je suis"), English ("happy today"), and Spanish ("esto es loco") creates ambiguity. The service returns a primary language but with low confidence because no single language dominates. |
| 52 | **B** | The code is valid. `confidence_scores.positive` is a float, so arithmetic works. It sums the positive scores across all three texts and divides by 3 to get the average. |
| 53 | **B** | Each method operates independently. There is no required ordering or dependency between `detect_language`, `analyze_sentiment`, `recognize_entities`, etc. |
| 54 | **A, B, D, E** | All methods take lists and return lists (A, B). PII detection returns both entities and redacted text (D). Batching multiple documents is supported (E). Confidence scores are floats 0-1, not integers (C is false). Sentiment has four values including neutral and mixed (F is false). |
| 55 | **A, B, C, D, E** | A: "Dr. Smith" (PersonName) and "123 Oak St" (Address) are PII. B: "Terrible" and "rude" make it negative. C: Key phrases will capture the main topics. D: "Nurse Jane" (PersonName) and "555-0199" (PhoneNumber) are PII. E: Three inputs produce three results. F is false: the first feedback is positive ("wonderful", "smooth"), so positive confidence will be high, not near 0.0. |

---

## Scoring Guide

| Score | Level | Recommendation |
|-------|-------|----------------|
| **50-55** | Expert | You have mastered Azure Language text analysis. Focus on hands-on projects. |
| **40-49** | Proficient | Strong understanding. Review the questions you missed and revisit edge cases. |
| **30-39** | Intermediate | Good foundation. Spend more time on code patterns, attribute paths, and method differences. |
| **20-29** | Developing | Review the SDK setup, method signatures, and the difference between each method's output. |
| **Below 20** | Beginning | Start with the fundamentals: install the package, create the client, and practice each method one at a time. |

---

## Quick Reference Cheat Sheet

```
METHOD                      -> KEY OUTPUT
detect_language()           -> .primary_language.name / .iso6391_name / .confidence_score
recognize_pii_entities()    -> .redacted_text / .entities[].text / .category / .confidence_score
analyze_sentiment()         -> .sentiment / .confidence_scores.positive/.negative/.neutral
recognize_entities()        -> .entities[].text / .category / .confidence_score
extract_key_phrases()       -> .key_phrases (list of strings)
```

**Golden Rules:**
1. Always pass a **list** of strings: `client.method(["text"])`
2. Always index the result: `result = client.method(["text"])[0]`
3. Confidence scores are **floats from 0 to 1**
4. Sentiment has **four** values: positive, negative, neutral, mixed
5. PII categories: PersonName, PhoneNumber, Address, Email (and more)
6. Azure Language SDK = structured, consistent; OpenAI API = flexible, probabilistic
