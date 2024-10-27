# Azure OpenAI Glossary

### Deployment
Setting up a model or application on Azure for use, allowing it to be accessed by specific applications or users.

### Embedding
A way of representing data (like text) as dense, information-rich vectors (arrays of numbers) that capture the meaning of the data. In this format, similar texts have similar vectors, making it easy for AI models to understand relationships and similarities between different pieces of text.

### Epoch
One full cycle through the entire training dataset during model training. In each epoch, the model learns patterns from all data points.

### Fine-Tuning
The process of further training a pre-existing Large Language Model (LLM) using custom data to create a more specialized version that performs better on specific tasks.

### Model
The core AI system that generates responses, processes data, or performs specific tasks. In Azure OpenAI, models can include language models like GPT-3 or Codex.

### Prompt
A piece of text or input given to the model to instruct it on what kind of response to generate.

### Prompt Engineering
The process of designing effective prompts to get accurate and relevant responses from a model. This technique optimizes model performance for specific tasks.

### Reinforcement Learning through Human Feedback (RLHF)
A training method where human preferences are used to guide the model, making its responses more aligned with what people want or expect.

### Retrieval-Augmented Generation (RAG)
A technique where the model retrieves relevant external information to improve response quality. This keeps responses accurate and cost-effective, especially when specialized knowledge is required.

### Temperature
A setting that controls how random or creative the model’s responses are. Lower temperatures make responses more predictable, while higher temperatures increase randomness and creativity.

### Top Probabilities (Top P)
A setting to control randomness by narrowing token selection to the most likely options. Lowering Top P makes the model focus on higher-probability words, making responses more predictable.

---

### Additional Terms

### API (Application Programming Interface)
A set of rules and tools for software to communicate with other software. In Azure OpenAI, APIs allow applications to interact with language models.

### Token
A unit of text, often a word or part of a word, that the model processes individually. Tokens help in understanding the input length and cost of model usage.

### Latency
The time delay between sending a request and receiving a response from the model. Lower latency means faster response times.

### Endpoint
A specific URL on Azure where requests are sent to access an AI model. Endpoints make it easy to connect applications to Azure OpenAI.

### Transformer
A machine learning architecture that powers many language models, like GPT, enabling them to understand and generate human-like text.

### Zero-shot, One-shot, and Few-shot Learning
Methods for providing examples in prompts:
- **Zero-shot**: The model has no example of the task and must infer it.
- **One-shot**: The model is given one example to understand the task.
- **Few-shot**: The model is given a few examples to clarify the task.

### Azure Cognitive Services
A suite of tools on Azure for adding AI capabilities to applications, including language, vision, and decision-making models.
