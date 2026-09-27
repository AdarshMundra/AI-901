# AI-901 Practice Exam: AI Agents in Microsoft Foundry

**50+ Questions | Progressive Difficulty | All Question Types**

---

## SECTION A: FOUNDATIONS (Questions 1-13)

**Question 1 - Multiple Choice**
What are the three core components that make up an AI Agent in Microsoft Foundry?

A) Model + Database + API
B) Model + Instructions (system prompt) + Tools
C) Prompt + Response + Memory
D) Endpoint + Credential + Client

---

**Question 2 - True/False**
True or False: An AI Agent in Foundry is the same thing as a model -- they both provide raw inference with no additional capabilities.

A) True
B) False

---

**Question 3 - Compare & Contrast**
How does an AI Agent differ from a direct model call?

A) An agent is cheaper but slower than a direct model call
B) A model provides raw inference; an agent is a packaged reusable worker with tools, instructions, and memory
C) A model can use tools but an agent cannot
D) There is no functional difference; "agent" is just a marketing term

---

**Question 4 - Select All That Apply**
Which of the following are capabilities of AI Agents in Foundry? (Select all that apply)

A) Call tools
B) Break goals into steps
C) Maintain memory
D) Process input
E) All of the above

---

**Question 5 - Fill-in-the-Blank**
Complete the pip install command to get the required package for working with AI Agents in Foundry:

```python
pip install ____________ >= 2.0.0b1
```

A) azure-ai-agents
B) azure-ai-projects
C) azure-foundry-sdk
D) azure-ai-foundry

---

**Question 6 - Multiple Choice**
Which package provides `DefaultAzureCredential` for authenticating with Foundry?

A) azure-ai-projects
B) azure-core
C) azure-identity
D) azure-auth

---

**Question 7 - Matching**
Match each agent component to its description:

| Component | Description |
|-----------|-------------|
| 1. Model | A. Defines agent behavior and personality |
| 2. Instructions | B. External capabilities the agent can invoke |
| 3. Tools | C. The LLM that powers reasoning |

A) 1-C, 2-A, 3-B
B) 1-A, 2-B, 3-C
C) 1-B, 2-C, 3-A
D) 1-C, 2-B, 3-A

---

**Question 8 - True/False**
True or False: You must install both `azure-ai-projects` and `azure-identity` packages to connect to and authenticate with an AI Agent in Foundry.

A) True
B) False

---

**Question 9 - When to Use What**
A developer needs to generate a one-time text completion from a model with no tool use, no memory, and no multi-step reasoning. What should they use?

A) An AI Agent with all tools enabled
B) A direct model call (raw inference)
C) An agent with no instructions
D) The Foundry Tool Catalog

---

**Question 10 - Multiple Choice**
What is the format of an agent endpoint URL in Foundry?

A) `https://<resource>.azure.com/agents/<agent-id>`
B) `https://<resource>.services.ai.azure.com/api/projects/<project-name>`
C) `https://foundry.azure.com/<resource>/agents`
D) `https://ai.azure.com/projects/<project-name>/agents`

---

### ANSWERS: Questions 1-10

| # | Answer | Explanation |
|---|--------|-------------|
| 1 | **B** | An agent is composed of a Model (the LLM), Instructions (system prompt defining behavior), and Tools (external capabilities). |
| 2 | **B (False)** | A model provides raw inference only. An agent is a packaged, reusable worker that combines a model with instructions, tools, memory, and multi-step reasoning. |
| 3 | **B** | The key distinction: models do raw inference, agents are reusable workers bundled with tools, instructions, and context. |
| 4 | **E** | Agents can call tools, break goals into steps, maintain memory, and process input -- all four are core agent capabilities. |
| 5 | **B** | The correct package is `azure-ai-projects`. The full command is `pip install azure-ai-projects>=2.0.0b1`. |
| 6 | **C** | `DefaultAzureCredential` comes from `azure-identity`, imported as `from azure.identity import DefaultAzureCredential`. |
| 7 | **A** | Model = the LLM powering reasoning (C); Instructions = defines behavior/personality via system prompt (A); Tools = external capabilities (B). |
| 8 | **A (True)** | `azure-ai-projects` provides the AIProjectClient, and `azure-identity` provides DefaultAzureCredential. Both are required. |
| 9 | **B** | For simple, one-time completions with no tools or memory, a direct model call is simpler and more appropriate than spinning up an agent. |
| 10 | **B** | The endpoint format is `https://<resource>.services.ai.azure.com/api/projects/<project-name>`. |

---

**Question 11 - Configuration**
Where can you find an agent's ID in the Foundry portal?

A) In the model deployment settings
B) In Playground > code view > .env variables
C) In the Azure subscription billing page
D) In the resource group tags

---

**Question 12 - Order the Steps**
What is the correct order for creating an agent in the Foundry portal?

1. Add knowledge sources
2. Choose a model
3. Save the agent
4. Write instructions
5. Add tools

A) 2 -> 4 -> 5 -> 1 -> 3
B) 4 -> 2 -> 5 -> 1 -> 3
C) 2 -> 5 -> 1 -> 4 -> 3
D) 5 -> 2 -> 4 -> 1 -> 3

---

**Question 13 - True/False**
True or False: You should deploy an agent directly to production without testing it in the Playground first.

A) True
B) False

---

## SECTION B: CODE & SDK (Questions 14-28)

**Question 14 - Code Output Prediction**
What does this code do?

```python
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential

project_client = AIProjectClient(
    endpoint="https://myresource.services.ai.azure.com/api/projects/myproject",
    credential=DefaultAzureCredential()
)
agent = project_client.agents.get(agent_name="my-agent")
print(type(agent))
```

A) Prints the agent's response to a query
B) Prints the type/class of the retrieved agent object
C) Prints the agent's instructions
D) Raises an error because `agents.get` does not exist

---

**Question 15 - Bug Finding**
This code is supposed to call an agent, but it has an error. Identify the problem.

```python
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential

project_client = AIProjectClient(
    endpoint="https://myresource.services.ai.azure.com/api/projects/myproject",
    credential=DefaultAzureCredential()
)
agent = project_client.agents.get(agent_name="my-agent")

# Call the agent
response = project_client.responses.create(
    input=[{"role": "user", "content": "Hello"}],
    extra_body={"agent": {"name": agent.name, "type": "agent_reference"}}
)
```

A) `DefaultAzureCredential()` needs a tenant ID parameter
B) The `responses.create` call should be on `openai_client`, not `project_client` -- you need `project_client.get_openai_client()` first
C) The `agent_name` parameter should be `name`
D) The `input` format is wrong; it should be a plain string

---

**Question 16 - Fill-in-the-Blank**
Complete the missing line to properly call the agent:

```python
project_client = AIProjectClient(endpoint=myEndpoint, credential=DefaultAzureCredential())
agent = project_client.agents.get(agent_name="my-agent")
____________ = project_client.get_openai_client()
response = ____________.responses.create(
    input=[{"role": "user", "content": "Summarize this document"}],
    extra_body={"agent": {"name": agent.name, "type": "agent_reference"}}
)
```

A) `client` / `client`
B) `openai_client` / `openai_client`
C) `agent_client` / `agent_client`
D) Both A and B are correct (variable name is arbitrary, but it must be the same on both lines)

---

**Question 17 - Bug Finding**
A developer writes this code and gets an authentication error. What is wrong?

```python
from azure.ai.projects import AIProjectClient

project_client = AIProjectClient(
    endpoint="https://myresource.services.ai.azure.com/api/projects/myproject"
)
```

A) The endpoint URL format is incorrect
B) The `credential` parameter is missing -- `DefaultAzureCredential()` from `azure-identity` must be provided
C) `AIProjectClient` does not accept an endpoint parameter
D) The import statement is from the wrong package

---

**Question 18 - Code Output Prediction**
What will happen when this code runs?

```python
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential

project_client = AIProjectClient(
    endpoint="https://myresource.services.ai.azure.com/api/projects/myproject",
    credential=DefaultAzureCredential()
)
openai_client = project_client.get_openai_client()
response = openai_client.responses.create(
    input=[{"role": "user", "content": "What is 2 + 2?"}],
    extra_body={"agent": {"name": "math-agent", "type": "agent_reference"}}
)
```

A) It will return a raw model completion ignoring any agent configuration
B) It will send the query to the "math-agent" agent and return its response, including any tool use the agent performs
C) It will fail because you must use `project_client.agents.get()` before calling an agent
D) It will create a new agent named "math-agent"

---

**Question 19 - Fill-in-the-Blank**
What import statement is needed to create the project client?

```python
from ____________ import AIProjectClient
```

A) azure.ai.foundry
B) azure.ai.projects
C) azure.projects
D) azure.ai.agents

---

**Question 20 - Bug Finding**
This code retrieves an agent but nothing happens. Why?

```python
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential

project_client = AIProjectClient(
    endpoint="https://myresource.services.ai.azure.com/api/projects/myproject",
    credential=DefaultAzureCredential()
)
agent = project_client.agents.get(agent_name="my-agent")
```

A) The code correctly retrieves the agent object, but never sends it a message -- no `openai_client.responses.create()` call is made
B) The agent name is wrong
C) The code has a syntax error
D) `agents.get` returns None by default

---

**Question 21 - Multiple Choice**
In the `extra_body` parameter when calling an agent, what is the value of the `"type"` key?

A) `"agent"`
B) `"agent_reference"`
C) `"model_reference"`
D) `"tool_reference"`

---

**Question 22 - Code Output Prediction**
A developer runs the following. What is `openai_client`?

```python
project_client = AIProjectClient(endpoint=ep, credential=DefaultAzureCredential())
openai_client = project_client.get_openai_client()
```

A) An instance of `AIProjectClient`
B) An OpenAI-compatible client scoped to the Foundry project, used to call agents and models
C) A raw HTTP session object
D) A reference to the Azure portal

---

**Question 23 - Error Diagnosis**
A developer's agent call returns a `404 Not Found` error. The code is:

```python
agent = project_client.agents.get(agent_name="My Agent")
```

What is the most likely cause?

A) The `AIProjectClient` package is outdated
B) The agent name `"My Agent"` does not match any agent deployed in the project (name is case-sensitive or misspelled)
C) 404 errors never occur with agents
D) The model behind the agent has been deleted from Azure

---

### ANSWERS: Questions 11-23

| # | Answer | Explanation |
|---|--------|-------------|
| 11 | **B** | The agent ID can be found in Playground > code view > .env variables. |
| 12 | **A** | The correct portal order: Choose model -> Write instructions -> Add tools -> Add knowledge -> Save. |
| 13 | **B (False)** | Best practice is to test the agent in the Playground before deploying to production. |
| 14 | **B** | The code retrieves an agent object using `agents.get()` and prints its Python type/class. |
| 15 | **B** | `responses.create` must be called on the OpenAI client obtained via `project_client.get_openai_client()`, not on `project_client` directly. |
| 16 | **D** | The variable name is arbitrary. What matters is that you call `project_client.get_openai_client()` and use the same variable for `.responses.create()`. Both A and B work. |
| 17 | **B** | `AIProjectClient` requires a `credential` parameter. Without `DefaultAzureCredential()`, authentication fails. |
| 18 | **B** | The code sends the user message to the "math-agent" agent via the OpenAI client. The agent will process it using its configured tools and instructions. |
| 19 | **B** | The correct import is `from azure.ai.projects import AIProjectClient`. |
| 20 | **A** | The code retrieves the agent but never invokes it. You need to get the OpenAI client and call `responses.create()` to actually send a message. |
| 21 | **B** | The type must be `"agent_reference"` to indicate you are referencing a deployed agent. |
| 22 | **B** | `get_openai_client()` returns an OpenAI-compatible client scoped to the Foundry project for calling agents and models. |
| 23 | **B** | A 404 most likely means the agent name does not match any deployed agent. Agent names are specific and must match exactly. |

---

## SECTION C: TOOLS & KNOWLEDGE (Questions 24-37)

**Question 24 - Select All That Apply**
Which of the following are valid tool types available to Foundry agents? (Select all that apply)

A) Code Interpreter
B) Knowledge sources (RAG)
C) Custom functions/APIs
D) MCP servers
E) All of the above

---

**Question 25 - Compare & Contrast**
What is the difference between Tools and Knowledge in the context of a Foundry agent?

A) Tools are for input; Knowledge is for output
B) Tools are external capabilities the agent can invoke (code execution, APIs, MCP); Knowledge is documents/datasets used for RAG (retrieval-augmented generation)
C) Tools are free; Knowledge costs extra
D) There is no difference; they are interchangeable terms

---

**Question 26 - Multiple Choice**
When an agent uses Knowledge (RAG) sources to answer a question, what is automatically included in its response?

A) A confidence score
B) Citations referencing the source documents
C) A list of all documents in the knowledge base
D) The full text of every retrieved document

---

**Question 27 - Scenario-Based**
A company wants their agent to answer employee questions by searching through internal policy PDFs stored in Azure Blob Storage. Which agent component should they configure?

A) Code Interpreter tool
B) Knowledge sources pointing to Azure Storage
C) Custom function that reads files
D) MCP server connection

---

**Question 28 - Configuration**
What is the Foundry Tool Catalog used for?

A) Purchasing third-party AI models
B) Discovering and managing tools available to agents
C) Monitoring agent usage costs
D) Deploying agents to production

---

**Question 29 - Scenario-Based**
An agent needs to run Python code to generate charts from data a user uploads. Which tool should be enabled?

A) Knowledge sources
B) MCP server
C) Code Interpreter
D) Custom function

---

**Question 30 - Architecture Design**
A retail company wants to build an agent that:
- Answers product questions from a catalog (stored in SharePoint)
- Checks real-time inventory via their REST API
- Generates summary reports with charts

Which combination of components is needed?

A) Knowledge (SharePoint) + Custom API function + Code Interpreter
B) Code Interpreter only
C) Two separate models with no tools
D) Knowledge (SharePoint) + MCP server only

---

**Question 31 - True/False**
True or False: MCP (Model Context Protocol) servers are a valid tool type that Foundry agents can connect to.

A) True
B) False

---

**Question 32 - When to Use What**
A developer wants their agent to call a proprietary internal pricing calculator hosted as a REST API. Which tool type is most appropriate?

A) Code Interpreter
B) Knowledge sources
C) Custom functions/APIs
D) The agent's built-in math capabilities

---

**Question 33 - Error Diagnosis**
An agent is configured with Knowledge sources pointing to a set of PDFs, but its answers do not include citations. What is the most likely issue?

A) Citations are a paid add-on feature
B) The Knowledge source is not properly connected or the agent is not retrieving from it (falling back to its base model knowledge instead)
C) Citations only work with Code Interpreter
D) The PDFs are too large

---

**Question 34 - Multiple Choice**
Which of the following is a valid Knowledge source format for RAG in Foundry agents?

A) PDFs
B) SharePoint documents
C) Azure Storage files
D) All of the above

---

**Question 35 - Scenario-Based**
A healthcare company has strict compliance requirements. They need an agent that answers questions ONLY from approved medical documents and never uses general model knowledge. What is the best approach?

A) Use a smaller model so it knows less
B) Configure Knowledge sources with the approved documents and write instructions telling the agent to only answer from provided knowledge, declining questions outside its sources
C) Disable the internet on the Azure VM
D) Use Code Interpreter to read the documents

---

**Question 36 - Architecture Design**
A financial services firm wants an agent that:
- Retrieves client portfolio data from their internal database via API
- Runs calculations on the retrieved data
- Answers questions using compliance documents

What tools and knowledge are required?

A) Custom function/API (database) + Code Interpreter (calculations) + Knowledge sources (compliance docs)
B) Only Code Interpreter
C) Only Knowledge sources
D) MCP server + Code Interpreter

---

**Question 37 - Compare & Contrast**
What distinguishes a Knowledge source from the Code Interpreter tool?

A) Knowledge provides documents/datasets for retrieval (RAG); Code Interpreter executes code at runtime
B) They are the same thing
C) Knowledge runs code; Code Interpreter retrieves documents
D) Knowledge is for images; Code Interpreter is for text

---

### ANSWERS: Questions 24-37

| # | Answer | Explanation |
|---|--------|-------------|
| 24 | **E** | All four are valid: Code Interpreter, Knowledge sources (RAG), Custom functions/APIs, and MCP servers. |
| 25 | **B** | Tools = capabilities the agent invokes (execute code, call APIs, connect to MCP). Knowledge = documents/datasets the agent searches for RAG. |
| 26 | **B** | When Knowledge (RAG) is used, citations referencing the source documents are automatically included in responses. |
| 27 | **B** | Knowledge sources should point to Azure Storage where the PDFs reside, enabling RAG-based question answering. |
| 28 | **B** | The Foundry Tool Catalog is for discovering and managing tools available to agents. |
| 29 | **C** | Code Interpreter allows the agent to run Python code, enabling chart generation and data processing. |
| 30 | **A** | Knowledge (SharePoint) for product catalog RAG + Custom API function for inventory checks + Code Interpreter for chart generation. |
| 31 | **A (True)** | MCP servers are listed as a valid tool type for Foundry agents. |
| 32 | **C** | Custom functions/APIs let the agent call external REST APIs like a proprietary pricing calculator. |
| 33 | **B** | If the Knowledge source is not properly connected, the agent defaults to base model knowledge, which does not produce citations. |
| 34 | **D** | PDFs, SharePoint documents, and Azure Storage files are all valid Knowledge source formats. |
| 35 | **B** | Configure Knowledge sources with approved documents and write instructions restricting the agent to only those sources. This combines RAG grounding with behavioral guardrails. |
| 36 | **A** | Custom function for the database API + Code Interpreter for calculations + Knowledge sources for compliance documents covers all three requirements. |
| 37 | **A** | Knowledge provides documents for retrieval-augmented generation. Code Interpreter executes code at runtime. They serve fundamentally different purposes. |

---

## SECTION D: ADVANCED SCENARIOS (Questions 38-52)

**Question 38 - Scenario-Based**
A team has built an agent that works well in the Playground but returns generic answers when called from their Python application. The code is:

```python
openai_client = project_client.get_openai_client()
response = openai_client.responses.create(
    input=[{"role": "user", "content": "Tell me about our refund policy"}],
    extra_body={}
)
```

What is wrong?

A) The Playground uses a different model
B) The `extra_body` is empty -- it is missing the `"agent"` reference with the agent name and type, so the call goes to the raw model instead of the agent
C) The input format is wrong
D) `get_openai_client()` does not work outside the Playground

---

**Question 39 - Error Diagnosis**
An agent configured with Knowledge sources sometimes gives accurate, cited answers and sometimes gives vague, uncited answers to similar questions. What is the most likely cause?

A) The model is non-deterministic and randomly ignores tools
B) The RAG retrieval is not finding relevant documents for some queries -- the knowledge base may have gaps or the queries may not match document content well
C) Citations are randomly disabled by Azure
D) The agent's memory is corrupting between sessions

---

**Question 40 - Order the Steps**
What is the correct order of operations to programmatically call an agent from Python?

1. Call `openai_client.responses.create()` with agent reference
2. Import `AIProjectClient` and `DefaultAzureCredential`
3. Get the OpenAI client via `project_client.get_openai_client()`
4. Create `AIProjectClient` with endpoint and credential
5. Retrieve the agent via `project_client.agents.get()`

A) 2 -> 4 -> 5 -> 3 -> 1
B) 2 -> 4 -> 3 -> 5 -> 1
C) 4 -> 2 -> 5 -> 3 -> 1
D) 2 -> 5 -> 4 -> 3 -> 1

---

**Question 41 - When to Use What**
A startup has two needs:
- Need 1: Translate 10,000 sentences from English to French (no tools, no context needed)
- Need 2: An internal assistant that searches company docs and calls Jira APIs to create tickets

What should they use for each?

A) Agent for both needs
B) Direct model call for Need 1; Agent with Knowledge + Custom API for Need 2
C) Direct model call for both needs
D) Agent for Need 1; Direct model call for Need 2

---

**Question 42 - Bug Finding**
This code is supposed to connect to a Foundry project but will fail. Why?

```python
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential

project_client = AIProjectClient(
    endpoint="myresource.services.ai.azure.com/api/projects/myproject",
    credential=DefaultAzureCredential()
)
```

A) `DefaultAzureCredential` should not have parentheses
B) The endpoint is missing the `https://` protocol prefix
C) `AIProjectClient` requires a `subscription_id` parameter
D) The import statements are in the wrong order

---

**Question 43 - Multiple Choice**
What is "Voice Live" in the context of Foundry agents?

A) A text-to-speech model
B) Speech-capable agents that can interact via voice
C) A live monitoring dashboard for agents
D) A real-time log viewer

---

**Question 44 - Architecture Design**
A university wants to build a student advising agent that:
- Answers questions about degree requirements (from a PDF handbook)
- Checks a student's completed courses (from a university API)
- Calculates remaining credits needed (math computation)
- Speaks to students over the phone

What components are needed?

A) Knowledge (PDF) + Custom API + Code Interpreter + Voice Live
B) Knowledge (PDF) + Code Interpreter only
C) Custom API + MCP server
D) Voice Live + Knowledge only

---

**Question 45 - Scenario-Based**
Two developers are arguing:
- Developer A says: "We should create one agent per task -- one for HR questions, one for IT support, one for finance."
- Developer B says: "We should create one mega-agent that handles everything."

From an architecture perspective, which approach is generally recommended?

A) Developer B is correct -- one agent is always simpler
B) Developer A is correct -- specialized agents with focused instructions and relevant tools/knowledge tend to perform better than overly broad agents
C) Neither -- you should not use agents at all
D) It does not matter; performance is identical either way

---

**Question 46 - Fill-in-the-Blank**
Complete the `extra_body` parameter to reference an agent named "support-bot":

```python
response = openai_client.responses.create(
    input=[{"role": "user", "content": "Help me reset my password"}],
    extra_body={
        "agent": {
            "name": ____________,
            "type": ____________
        }
    }
)
```

A) `"support-bot"` / `"agent"`
B) `"support-bot"` / `"agent_reference"`
C) `agent.name` / `"reference"`
D) `"support_bot"` / `"model_reference"`

---

**Question 47 - Error Diagnosis**
An agent that previously worked fine now returns `AuthenticationError: DefaultAzureCredential failed`. The code has not changed. What should the developer check?

A) Whether the `azure-ai-projects` package needs updating
B) Whether their Azure credentials have expired, their managed identity permissions have changed, or their environment variables for authentication are no longer set
C) Whether the agent was deleted
D) Whether Python was updated

---

**Question 48 - True/False**
True or False: The `extra_body` parameter in `openai_client.responses.create()` is optional -- if omitted, the call still reaches the configured agent.

A) True
B) False

---

**Question 49 - Scenario-Based**
A legal firm has 50,000 contract PDFs and wants an agent that can answer questions about specific contracts. A junior developer suggests loading all 50,000 PDFs as context in the system prompt. Why is this a bad idea?

A) There is no character limit on system prompts, so it would actually work
B) System prompts have token limits; instead, the PDFs should be configured as Knowledge sources so the agent uses RAG to retrieve only relevant documents per query
C) PDFs cannot be used with Foundry agents
D) The agent would be too slow but otherwise accurate

---

**Question 50 - Code Output Prediction**
What will `agent.name` contain after this code runs?

```python
project_client = AIProjectClient(endpoint=ep, credential=DefaultAzureCredential())
agent = project_client.agents.get(agent_name="billing-helper")
print(agent.name)
```

A) `None`
B) `"billing-helper"`
C) The agent's internal UUID
D) The model name (e.g., "gpt-4o")

---

**Question 51 - Architecture Design**
A government agency needs an agent that:
- Searches regulations stored in Azure Blob Storage
- Must never fabricate information (must always cite sources)
- Needs to be testable before going live

What is the complete setup?

A) Deploy directly with a model and no tools
B) Configure Knowledge sources (Azure Storage with regulations) for RAG with citations, write strict instructions to only answer from provided sources, and test in the Playground before deploying
C) Use Code Interpreter to read the regulations
D) Use an MCP server to connect to a search engine

---

**Question 52 - Bug Finding**
This code runs without errors but the agent's response ignores its configured tools and instructions. Why?

```python
project_client = AIProjectClient(endpoint=ep, credential=DefaultAzureCredential())
openai_client = project_client.get_openai_client()

response = openai_client.responses.create(
    input=[{"role": "user", "content": "Check inventory for SKU-1234"}],
    extra_body={"agent": {"name": "inventory-agent", "type": "model_reference"}}
)
```

A) The input message is too short
B) The `type` is `"model_reference"` instead of `"agent_reference"`, so the call is treated as a raw model call and ignores the agent's tools and instructions
C) `responses.create` does not support `extra_body`
D) The agent name has a hyphen, which is invalid

---

**Question 53 - Select All That Apply**
Which of the following actions should you take before deploying an agent to production? (Select all that apply)

A) Test the agent in the Playground
B) Verify the agent's tools are properly connected
C) Review the agent's instructions for correctness
D) Skip testing to save time
E) A, B, and C only

---

**Question 54 - Scenario-Based**
A data science team wants to build an agent that can:
- Accept CSV file uploads from users
- Run statistical analysis on the uploaded data
- Return visualizations and summary statistics

Which single tool is most critical for this agent?

A) Knowledge sources
B) Code Interpreter
C) Custom functions/APIs
D) MCP servers

---

**Question 55 - Compare & Contrast**
Compare these two code paths:

**Path 1:**
```python
openai_client = project_client.get_openai_client()
response = openai_client.responses.create(
    input=[{"role": "user", "content": "Hello"}]
)
```

**Path 2:**
```python
openai_client = project_client.get_openai_client()
response = openai_client.responses.create(
    input=[{"role": "user", "content": "Hello"}],
    extra_body={"agent": {"name": "greeter", "type": "agent_reference"}}
)
```

What is the difference?

A) No difference -- both call the agent
B) Path 1 makes a raw model call with no agent; Path 2 routes the request to the "greeter" agent with its tools, instructions, and knowledge
C) Path 1 is faster; Path 2 is slower but identical in output
D) Path 1 will error; Path 2 will succeed

---

### ANSWERS: Questions 38-55

| # | Answer | Explanation |
|---|--------|-------------|
| 38 | **B** | The `extra_body` is empty, so no agent is referenced. The call goes to the raw model, which does not have the agent's tools or knowledge. |
| 39 | **B** | Inconsistent RAG retrieval is the most likely cause. Some queries match documents well (cited answers); others do not (vague, uncited answers from base model knowledge). |
| 40 | **A** | Import (2) -> Create client (4) -> Get agent (5) -> Get OpenAI client (3) -> Call agent (1). |
| 41 | **B** | Bulk translation is a simple inference task (direct model call). The internal assistant needs tools and knowledge (agent). |
| 42 | **B** | The endpoint is missing `https://`. It should be `https://myresource.services.ai.azure.com/api/projects/myproject`. |
| 43 | **B** | Voice Live enables speech-capable agents that can interact via voice. |
| 44 | **A** | Knowledge (PDF handbook) + Custom API (student records) + Code Interpreter (credit calculations) + Voice Live (phone interaction). |
| 45 | **B** | Specialized agents with focused instructions and relevant tools perform better. Broad agents tend to be less accurate and harder to maintain. |
| 46 | **B** | The name is `"support-bot"` and the type must be `"agent_reference"`. |
| 47 | **B** | Since the code has not changed, the issue is with credentials: expired tokens, changed managed identity permissions, or missing environment variables. |
| 48 | **B (False)** | Without `extra_body` containing the agent reference, the call goes to the raw model, not the agent. The parameter is required to invoke a specific agent. |
| 49 | **B** | System prompts have token limits. Knowledge sources with RAG retrieve only relevant documents per query, which is scalable and efficient. |
| 50 | **B** | `agent.name` will contain `"billing-helper"` -- the name used to retrieve it. |
| 51 | **B** | Knowledge sources provide RAG with citations, strict instructions prevent fabrication, and Playground testing validates behavior before deployment. |
| 52 | **B** | `"model_reference"` tells the system to treat it as a model call, not an agent call. Changing to `"agent_reference"` activates the agent's tools and instructions. |
| 53 | **E** | Testing in the Playground (A), verifying tool connections (B), and reviewing instructions (C) are all essential pre-deployment steps. Never skip testing. |
| 54 | **B** | Code Interpreter is the critical tool -- it can accept file uploads, run Python for statistical analysis, and generate visualizations. |
| 55 | **B** | Path 1 has no `extra_body`, so it is a raw model call. Path 2 includes the agent reference, routing the request through the agent with all its configured capabilities. |

---

## SCORING GUIDE

**Total Questions: 55**

| Score | Rating | Recommendation |
|-------|--------|----------------|
| 50-55 | Expert (91-100%) | You are exam-ready for the AI Agents section |
| 44-49 | Proficient (80-90%) | Strong understanding, review missed topics |
| 38-43 | Competent (69-79%) | Good foundation, revisit Tools vs Knowledge and SDK code patterns |
| 28-37 | Developing (51-68%) | Study the SDK workflow and agent architecture more carefully |
| 0-27  | Beginning (0-50%) | Start with the fundamentals: Agent = Model + Instructions + Tools |

---

## KEY CONCEPTS TO REMEMBER

1. **Agent = Model + Instructions + Tools** -- the foundational equation
2. **Two packages needed**: `azure-ai-projects` (client) and `azure-identity` (auth)
3. **Two-step calling pattern**: Get OpenAI client, then call `responses.create` with `extra_body`
4. **`"agent_reference"` not `"model_reference"`** -- using the wrong type silently falls back to raw model
5. **Knowledge = RAG with citations**; **Tools = executable capabilities**
6. **Tool types**: Code Interpreter, Knowledge (RAG), Custom functions/APIs, MCP servers
7. **Always test in Playground** before deploying
8. **Endpoint format**: `https://<resource>.services.ai.azure.com/api/projects/<project-name>`
9. **Agent ID location**: Playground > code view > .env variables
10. **Voice Live** = speech-capable agents
