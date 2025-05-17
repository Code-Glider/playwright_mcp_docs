# Using Generative AI in Software Automation/Manual Testing

This document summarizes the introductory video for a course on leveraging Generative AI in software testing, covering both manual and automation testing.

**What is Generative AI?**

Generative AI (Gen AI) refers to AI models designed to create new, original content or data based on input. It can generate text, images, music, and code.

**Models under the Generative AI Umbrella:**

1.  **Large Language Models (LLMs):** Used for text generation, code generation, and chatbots (e.g., GPT-4, Llama, Gemini, Claude 3.5 Sonnet, Mistral).
2.  **Generative Adversarial Networks (GANs):** Used for image generation, deepfake verification, art creation, and video creation (e.g., DALL-E).
3.  **Variational Autoencoders (VAEs):** Used for generating new data and data compression.

The course will primarily focus on Large Language Models (LLMs) due to their relevance in code generation and text-based tasks.

**Applications of Generative AI in Software Testing:**

Gen AI offers several applications to make software testing more efficient:

*   **Manual Testing:**
    *   Automatic generation of manual test cases.
    *   Data mapping to verify if data aligns with application attributes.
*   **Automated Testing:**
    *   Automated code suggestion and generation for test scripts (e.g., using tools like GitHub Copilot or Tabnine with project source code as context).
    *   AI-powered code correction.
    *   Assisting with code coverage analysis based on application context.
    *   Generating realistic test data for complex objects, reducing manual data entry and duplication.
    *   Automated bug tracking, including identifying duplicate bugs (e.g., using tools like Busura).
*   **API Testing:**
    *   Generating API tests (e.g., for Postman or Rest Assured) from documentation like Swagger, requiring only review and inspection of the generated code.
*   **UI Testing:**
    *   Ensuring locators in UI test code match the current page structure by providing the page source to the AI, helping to identify if failures are due to UI changes or logic changes. This often requires using Gen AI APIs.

**Actionable Takeaways:**

*   Explore and integrate Generative AI tools and techniques into your testing workflows for increased efficiency.
*   Focus on leveraging LLMs for tasks like test case generation, test code writing assistance, code correction, and test data generation.
*   Investigate how Gen AI can assist with API test generation from documentation and UI locator validation.
*   Stay updated on new Gen AI applications and tools emerging in the software testing field.

**Conclusion:**

Generative AI has the potential to significantly enhance software testing by automating repetitive tasks and providing intelligent assistance across various testing phases, allowing testers to focus on more complex problem-solving.