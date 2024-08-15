TODO: 
- [ ] Add images for: 
	- [ ] Document writing / checking
	- [ ] Coding assistant / review / auto-complete
- [ ] Context length restrictions
- [ ] Elaborate on commercial restrictions for llama3.1, codellama
- [ ] Data security when scaling ollama client-server setup
	- [ ] Does Ollama cache prompts? 
- [ ] 


## 1. Introduction

Language Models (LLMs) have emerged as powerful tools in the field of artificial intelligence, capable of understanding and generating human-like text. These models, trained on vast amounts of textual data, have found applications across a wide spectrum of tasks, from natural language processing to code generation and analysis. As the capabilities of LLMs continue to expand, their potential to revolutionise various aspects of software engineering becomes increasingly apparent.

The primary objective of this technical document is to demonstrate the feasibility and practicality of running open-source LLMs in offline environments. This approach addresses several key concerns that organisations may have when considering the adoption of LLM technology, including data privacy, network restrictions, and the desire for complete control over the AI infrastructure.

Throughout this document, we will explore the process of setting up LLMs for local use on individual machines, as well as implementing a client-server approach within an offline network. We will delve into the potential applications of these models in software engineering contexts, providing insights into how they can enhance productivity and quality across various development tasks.

Additionally, we will address the critical aspects of data security when working with these models in an offline setting. This includes an examination of how pre-trained models can be utilised without the need for fine-tuning, thereby mitigating risks associated with data leakage or unintended model behaviour modifications.

Finally, we will provide a comprehensive overview of the legal and licensing requirements associated with the commercial use of open-source LLMs. This information is crucial for organisations looking to integrate these technologies into their workflows while ensuring compliance with intellectual property laws and open-source licensing agreements.

By the conclusion of this document, readers will have a good understanding of how to leverage LLMs without relying on cloud-based services. This knowledge will enable organisations to harness the power of AI-driven language processing while maintaining strict control over their data and computing environments.

## 2. Setup and Infrastructure

### 2.1 Local Setup with Ollama

The process of setting up and running LLMs locally has been significantly simplified with the introduction of tools like Ollama. This open-source project provides a streamlined interface for managing and operating various language models on local hardware. Ollama's architecture is designed to optimise resource utilisation, making it possible to run sophisticated models even on machines with limited computational capacity.

The installation process for Ollama is straightforward and well-documented. Once installed, users can easily pull pre-trained models from Ollama's repository. For instance, to acquire and run the Llama 3.1 7B model, one would simply execute the commands "ollama pull llama3.1" followed by "ollama run llama3.1". This simplicity belies the complex operations occurring behind the scenes, where Ollama manages model loading, memory allocation, and inference processes.

Ollama's efficiency stems from its intelligent handling of model quantisation and caching mechanisms. These features allow for rapid switching between different models and optimise the use of available system resources. Furthermore, Ollama's support for multiple model architectures provides flexibility in choosing the most appropriate model for specific tasks or hardware configurations.

### 2.2 Available Open-Source Models for Commercial Use

The landscape of open-source language models suitable for commercial use is rapidly evolving. Several notable models have been released under licenses that permit commercial applications, each with its own strengths and characteristics. 

| Model             | Parameter Sizes (Billion) | Context Window (tokens) | Targeted Use Case                                               | Licensing                                          |
| ----------------- | ------------------------- | ----------------------- | --------------------------------------------------------------- | -------------------------------------------------- |
| Llama 3.1         | 8, 70, 405                | 128k                    | Multilingual tasks, long documents, safety features             | Permissive license for research and commercial use |
| Gemma 2           | 2, 7, 13                  | 8k                      | General NLP tasks, code understanding and generation            | CC BY 4.0                                          |
| DeepSeek-Coder-V2 | 16, 236                   | 128k                    | Code-specific tasks, mathematical reasoning                     | MIT license                                        |
| CodeGemma         | 2, 7                      | 8k                      | Code completion, code infilling, open-ended generation          | CC BY 4.0                                          |
| CodeLlama         | 7, 13, 34, 70             | 16k                     | Code-related tasks, programming languages, software development | Permissive license for research and commercial use |

### 2.3 Scaling to Client-Server Approach

While local setups are suitable for individual use or small teams, larger organisations operating in offline networks may benefit from a centralised client-server architecture. In this configuration, a central server hosts the LLM and provides inference capabilities to multiple clients across the network.

The server component in this setup typically consists of a high-performance machine or cluster capable of running larger, more sophisticated models. This central node manages the model loading, inference processing, and result distribution. Client machines, which may have more limited resources, send requests to the server and receive responses, effectively leveraging the power of the central model without the need for local model storage or intensive computation.

Implementing such a system requires careful consideration of network architecture, load balancing, and failover mechanisms. It's crucial to design the system with scalability in mind, allowing for the addition of more server resources or the distribution of load across multiple nodes as demand increases.

### 2.4 Model Size and Performance Considerations

The choice of model size is a critical factor in both local and client-server deployments, involving a balance between performance, accuracy, and resource utilisation. Smaller models, while generally faster in terms of inference speed, may not achieve the same level of accuracy or versatility as their larger counterparts.

For local deployments, hardware limitations often necessitate the use of smaller, more efficient models. These models can provide reasonable performance for many tasks while operating within the constraints of individual machines. However, they may struggle with more complex queries or specialised domains that benefit from the deeper knowledge embedded in larger models.

In a client-server setup, the centralised nature of the system allows for the deployment of larger, more sophisticated models. These models can offer enhanced accuracy and broader capabilities but come at the cost of increased computational requirements and potentially longer inference times.

The relationship between model size and performance is not strictly linear. Advances in model architecture and training techniques have led to the development of models that achieve impressive results despite relatively modest parameter counts. Therefore, the selection of an appropriate model should involve careful benchmarking and evaluation within the specific use case and hardware environment.

Additionally, context length, which refers to the amount of text a model can consider at once, significantly impacts a model’s effectiveness in various applications. For instance, longer context lengths are crucial for tasks like document summarization, multi-turn conversations, and code generation, where understanding extended sequences is essential.

## 3. Applications in Software Engineering

The integration of LLMs into software engineering workflows opens up a wide array of possibilities for enhancing productivity, code quality, and documentation processes. This section explores several key areas where LLMs can provide significant value to development teams.

### 3.1 Document Writing and Checking

LLMs excel in tasks related to natural language processing and generation, making them valuable tools for creating and refining technical documentation. When it comes to drafting technical specifications, these models can assist in structuring documents, suggesting appropriate terminology, and ensuring consistency across different sections.

For user documentation, LLMs can help generate clear, concise explanations of software features and functionalities. They can adapt their language based on the intended audience, whether it's for end-users, system administrators, or other developers.

In the proofreading and improvement phase, LLMs can identify grammatical errors, suggest more precise phrasing, and help maintain a consistent tone throughout the document. They can also flag potential ambiguities or areas that may require further clarification.

Tools like the Continue VS Code extension integrate these capabilities directly into the development environment, allowing for seamless document creation and editing alongside code development. Similarly, web-based interfaces like the Ollama Web UI provide accessible platforms for document-related tasks.

### 3.2 Coding Assistant

As coding assistants, LLMs offer a range of functionalities that can significantly enhance developer productivity. One of the primary use cases is in code completion and suggestion. By analysing the context of the current code and the programmer's intent, these models can offer relevant completions that go beyond simple syntax-based suggestions.

LLMs are particularly adept at explaining complex code snippets. When a developer encounters unfamiliar or intricate code, they can prompt the model for an explanation, receiving a detailed breakdown of the code's functionality, potential edge cases, and underlying principles.

Another valuable application is in providing examples of design patterns and best practices. Developers can query the model for implementations of specific patterns or ask for guidance on structuring their code to adhere to established principles of software design.

Tools like the Continue VS Code extension bring these capabilities directly into the integrated development environment (IDE), offering context-aware assistance throughout the coding process.

### 3.3 Autocomplete Functionality

LLMs have the potential to significantly enhance code autocomplete features beyond traditional static analysis-based systems. The context-aware nature of these models allows for more intelligent and relevant suggestions that take into account the broader scope of the code being written.

One of the most powerful aspects of LLM-based autocomplete is the ability to generate full function and class implementations. By understanding the function signature and surrounding context, these models can propose complete implementations, saving developers significant time and reducing the likelihood of boilerplate errors.

Docstring generation is another area where LLMs excel. By analysing the function or class definition, these models can automatically generate comprehensive documentation, including parameter descriptions, return value explanations, and usage examples.

Tools like Continue VS Code extension integrate these advanced autocomplete features directly into the IDE, providing a seamless experience for developers.

### 3.4 Code Review

The code review process can be significantly enhanced through the application of LLMs. These models can analyse code submissions to identify potential bugs, inefficiencies, or deviations from best practices.

In terms of code readability, LLMs can suggest improvements to variable naming, function structuring, and overall code organisation. This can help maintain consistency across a codebase and improve long-term maintainability.

LLMs can also assist in checking adherence to coding standards. By training on or being provided with the specific standards of an organisation, these models can flag deviations and suggest corrections, ensuring that all code meets the required quality benchmarks.

While tools like DeepCode offer specialised offline code review capabilities, custom integrations with Ollama can also be developed to tailor the review process to an organisation's specific needs and standards.

### 3.5 Requirements Analysis

In the realm of requirements analysis, LLMs can serve as valuable aids to software engineers and product managers. These models can assist in generating probing questions to clarify ambiguous or incomplete requirements, helping to ensure that all aspects of a feature or system are thoroughly considered.

LLMs are particularly useful in identifying potential edge cases or scenarios that human analysts might overlook. By processing the given requirements and drawing on their vast knowledge base, these models can highlight areas that may require additional consideration or specification.

Another valuable application is in the generation of user stories based on high-level descriptions. Given a general outline of a feature or system, an LLM can propose detailed user stories that capture various aspects of functionality and user interaction.

While specialised requirements management tools exist, custom integrations with Ollama can provide tailored solutions for requirements analysis that align closely with an organisation's specific methodologies and needs.

## 4. Data Security Considerations

When using open-source LLMs in offline environments with Ollama, understanding the model's behavior and potential risks of data leakage between user sessions is crucial. This section explores these aspects and provides strategies for maintaining data security.

### 4.1 Ollama's Operational Behaviour

Ollama's design and operation have important implications for data security:

- Stateless Execution: By default, Ollama processes each query independently, without retaining information from previous queries.
- In-Memory Processing: All data processing occurs in RAM, which is volatile and cleared when the container is stopped or restarted.
- No Persistent Storage: Ollama does not automatically store user prompts or responses on disk.

### 4.2 Multi-User Scenarios and Data Isolation

In a centralised setup with multiple clients accessing a shared Ollama instance:

- No Direct Cross-Session Data Storage: Ollama doesn't inherently store or cache user inputs or outputs in a way that allows direct access to another user's data.
- Potential for Residual Information: The language model may temporarily hold information in its active memory (RAM), which could theoretically influence subsequent responses.
- Lack of Built-in Session Management: Ollama doesn't have native mechanisms for managing separate user sessions or isolating user data.

### 4.3 Security Strategies for Ollama Deployments

To mitigate the risk of data leakage between sessions:

1. **Session Management:**
    - Implement a custom session management layer that resets the model state between user interactions.
    - For highly sensitive applications, consider using separate model instances for each user session.
2. **Container Isolation:**
    - Use separate Ollama containers for different users or security levels.
    - Regularly restart Ollama containers to clear any residual information in memory.
3. **Access Control:**
    - Utilise Ollama's API key feature to segregate user access.
    - Implement robust user authentication and authorisation mechanisms.
4. **Monitoring and Auditing:**
    - Develop logging systems to track model usage and detect potential data leakage.
    - Regularly review logs and conduct security audits.
5. **Data Handling Policies:**
    - Establish clear guidelines for data handling and model usage.
    - Train users on security practices when interacting with the model.

### 4.4 Considerations for Local vs. Centralised Deployments

**Local Deployments:**
- Provide natural session isolation as each user typically has their own Ollama installation.
- Implement strict user access controls on the host system.
- Regularly clear Ollama's cache and temporary files between uses.

**Centralised Deployments:**
- Implement robust load balancing to distribute requests across multiple Ollama instances.
- Use containerisation for stronger isolation between user groups or departments.
- Consider implementing a queuing system to manage and isolate requests from different users.

## 5. Licensing and Legal Considerations

The use of open-source LLMs in commercial settings necessitates a thorough understanding of the associated licensing terms and legal obligations. This section provides an overview of the licensing considerations for several popular open-source models, as well as general legal considerations for their commercial use.

### 5.1 Llama 2 (Meta AI)

Llama 2 is released under the Meta AI License, which allows for commercial use but comes with certain restrictions. The license requires attribution to Meta AI and prohibits the use of the model for certain specific purposes, such as the development of surveillance technologies or weapons. Organisations intending to use Llama 2 should carefully review the full license terms to ensure compliance.

### 5.2 GPT-J (EleutherAI)

GPT-J is released under the Apache 2.0 license, which is known for its permissive terms. This license allows for free commercial use of the model. The main requirements are to include the license and copyright notice with any distribution of the model or derivative works. The Apache 2.0 license also provides an express grant of patent rights from contributors to users.

### 5.3 BLOOM (BigScience)

The BLOOM model is made available under the BigScience RAIL (Responsible AI License) License. This license permits commercial use but emphasises ethical considerations in AI deployment. Users of BLOOM are required to respect ethical guidelines outlined in the license, which include prohibitions on uses that could cause harm or discriminate against individuals or groups. Attribution to the BigScience project is also required.

### 5.4 CodeLlama (Meta AI)

CodeLlama follows a licensing model similar to Llama 2, using the Meta AI License. It allows for commercial use with restrictions similar to those applied to Llama 2. Given its specialisation in code-related tasks, organisations should pay particular attention to how they integrate CodeLlama into their development workflows to ensure compliance with the license terms.

### 5.5 Mistral AI Models

Models released by Mistral AI are typically made available under the Apache 2.0 license. This permissive license allows for free commercial use, with the primary requirement being the inclusion of the license and copyright notice. The use of Mistral AI models in commercial settings is relatively straightforward from a licensing perspective, but organisations should still review the specific terms for the particular model version they intend to use.

### 5.6 General Legal Considerations

Beyond the specific licensing terms of each model, organisations must consider broader legal implications when deploying LLMs in commercial environments. Compliance with data protection regulations such as the General Data Protection Regulation (GDPR) in the European Union or the California Consumer Privacy Act (CCPA) in the United States is crucial, especially when processing personal data through these models.

Organisations should clearly define the ownership of LLM-generated content in their terms of service. This is particularly important when the model is used to generate content for clients or end-users. The legal status of AI-generated content is an evolving area, and clear policies can help prevent future disputes.