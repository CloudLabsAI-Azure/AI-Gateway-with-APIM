# Exercise 4: Semantic Caching for Performance Optimization 

### Task 1: Understand semantic caching principles. 


### Introduction

Semantic caching is an advanced caching technique that improves the performance and efficiency of large language model (LLM) applications, such as those using Azure OpenAI.
Unlike traditional caching, which matches requests based on exact text or URLs, semantic caching uses meaning (semantics) to identify whether two queries are similar enough to reuse a previous response.

This approach enables faster responses, lower latency, and reduced token consumption by avoiding redundant calls to the backend Azure OpenAI service.


### How Semantic Caching Works

- When a user submits a prompt to an AI service, the system:

   - Generates a vector embedding of the input text using an embedding model (for example, text-embedding-ada-002).

   - Compares this embedding with vectors from previously cached requests.

      1. If the new prompt is semantically similar (based on a similarity score threshold) to a cached one, the cached response is returned.

      2. If not, the request is sent to the OpenAI model, and the new response is stored in the cache for future use.

- This technique ensures that responses for similar or repeated questions can be served instantly from the cache without reprocessing the entire request.

### Key Concepts

   | **Concept**                         | **Description**                               |
   | ----------------------------------- | --------------------------------------- |
   | Semantic Similarity                 | Measures how close two pieces of text are in meaning using vector embeddings.                  |
   | Embedding                           | A numerical vector representation of text that captures its semantic meaning.                  |
   | Similarity Threshold                | A configurable value (e.g., 0.9) determining how similar two inputs must be for a cache hit.   |
   | Cache Lookup                        | The process of searching for semantically similar previous prompts before calling the AI model.|
   | Cache Store                         | Saving the new prompt and its response to the cache for future reuse. |


### Benefits of Semantic Caching

- Reduces latency: Cached responses are returned almost instantly.

- Lowers token costs: Avoids unnecessary calls to Azure OpenAI models.

- Improves scalability: Decreases backend workload and bandwidth usage.

- Enhances user experience: Provides consistent and faster AI responses.


### Example Scenario

1. If one user asks:

   ```
   What is Azure Cognitive Search?
   ```

2. And another later asks:

   ```
   Can you explain what Azure Cognitive Search does?
   ```
   
Although the two prompts are worded differently, semantic caching identifies them as semantically similar and retrieves the earlier cached response — saving time and tokens.






https://github.com/Azure-Samples/AI-Gateway/tree/main/labs/semantic-caching
