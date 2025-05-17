

Markdown Content:
⚙️Examples of API automation | Playwright MCP Server
===============

[Skip to main content](https://executeautomation.github.io/mcp-playwright/docs/playwright-api/Examples#__docusaurus_skipToContent_fallback)

[![Image 1: Playwright MCP Server](https://executeautomation.github.io/mcp-playwright/img/EA-Icon.svg) **Playwright MCP Server**](https://executeautomation.github.io/mcp-playwright/)[Tutorial](https://executeautomation.github.io/mcp-playwright/docs/intro)

[GitHub](https://github.com/executeautomation/mcp-playwright)

*   [Playwright MCP Server](https://executeautomation.github.io/mcp-playwright/docs/intro)
*   [Release Notes](https://executeautomation.github.io/mcp-playwright/docs/release)
*   [Local Development](https://executeautomation.github.io/mcp-playwright/docs/category/local-development) 
    *   [Installation](https://executeautomation.github.io/mcp-playwright/docs/local-setup/Installation)
    *   [Debugging](https://executeautomation.github.io/mcp-playwright/docs/local-setup/Debugging)

*   [Playwright Web Features](https://executeautomation.github.io/mcp-playwright/docs/category/playwright-web-features) 
    *   [��️ Supported Tools](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools)
    *   [📁 Support of Console Logs](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Console-Logging)
    *   [💻 Support of Cline and Cursor](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Support-of-Cline-Cursor)
    *   [🌐 Examples of browser automation](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Examples)
    *   [🎥 Recording Actions](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Recording-Actions)

*   [Playwright API Features](https://executeautomation.github.io/mcp-playwright/docs/category/playwright-api-features) 
    *   [🛠️ Supported Tools](https://executeautomation.github.io/mcp-playwright/docs/playwright-api/Supported-Tools)
    *   [⚙️Examples of API automation](https://executeautomation.github.io/mcp-playwright/docs/playwright-api/Examples)

*   [AI Courses to Learn](https://executeautomation.github.io/mcp-playwright/docs/category/ai-courses-to-learn) 
    *   [🤖 Using Generative AI in Software Automation Testing](https://executeautomation.github.io/mcp-playwright/docs/ai-courses/GenAICourse)
    *   [🧠 Understand, Test, and Fine-tune AI Models with Hugging Face](https://executeautomation.github.io/mcp-playwright/docs/ai-courses/MachineLearning)
    *   [🧠🤖 Build & Test AI Agents, ChatBots, and RAG with Ollama & Local LLM](https://executeautomation.github.io/mcp-playwright/docs/ai-courses/AIAgents)

*   [MCP Testing Videos](https://executeautomation.github.io/mcp-playwright/docs/category/mcp-testing-videos) 
    *   [🎭 UI + Database Testing 💽](https://executeautomation.github.io/mcp-playwright/docs/testing-videos/AIAgents)
    *   [🎭 BDD Testing with Playwright MCP Server 🥒](https://executeautomation.github.io/mcp-playwright/docs/testing-videos/Bdd)

*   [](https://executeautomation.github.io/mcp-playwright/)
*   [Playwright API Features](https://executeautomation.github.io/mcp-playwright/docs/category/playwright-api-features)
*   ⚙️Examples of API automation

On this page

⚙️Examples of API automation
============================

Lets see how we can use the power of Playwright MCP Server to automate API of our application

### Scenario[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-api/Examples#scenario "Direct link to Scenario")

`// Basic POST requestPerform POST operation for the URL https://api.restful-api.dev/objects with body{   "name": "Apple MacBook Pro 16",   "data": {      "year": 2024,      "price": 2499,      "CPU model": "M4",      "Hard disk size": "5 TB"   }}And verify if the response has createdAt and id property and store the ID in a variable for future reference say variable productID// POST request with Bearer token authorizationPerform POST operation for the URL https://api.restful-api.dev/objects with Bearer token "your-token-here" set in the headers{        'Content-Type': 'application/json',        'Authorization': 'Bearer your-token-here'      },and body{   "name": "Secure MacBook Pro",   "data": {      "year": 2024,      "price": 2999,      "CPU model": "M4 Pro",      "Hard disk size": "8 TB",      "security": "enhanced"   }}Perform GET operation for the created ProductID using URL https://api.restful-api.dev/objects/productID and verify the response has properties like Id, name, dataPerform PUT operation for the created ProductID using URL https://api.restful-api.dev/objects/productID with body {   "name": "Apple MacBook Pro 16",   "data": {      "year": 2025,      "price": 4099,      "CPU model": "M5",      "Hard disk size": "10 TB",      "color": "Titanium"   }}And verify if the response has createdAt and id propertyPerform PATCH operation for the created ProductID using URL https://api.restful-api.dev/objects/productID with body{   "name": "Apple MacBook Pro 19 (Limited Edition)"}And verify if the response has updatedAt property with value Apple MacBook Pro 19 (Limited Edition)`

And once the entire test operation completes, we will be presented with the entire details of how the automation did happened.

![Image 2: Playwright MCP Server](https://executeautomation.github.io/mcp-playwright/assets/images/playwright-api-046cf2650b0fc907a8a083e0b0f43a02.png)

tip

You can also see the `Request/Response/StatusCode` from the execution of Playwright MCP Server

![Image 3: Playwright MCP Server](https://executeautomation.github.io/mcp-playwright/assets/images/api-response-211162266965e627fc51a2527446175c.png)

[Edit this page](https://github.com/facebook/docusaurus/tree/main/packages/create-docusaurus/templates/shared/docs/playwright-api/Examples.md)

[Previous 🛠️ Supported Tools](https://executeautomation.github.io/mcp-playwright/docs/playwright-api/Supported-Tools)[Next AI Courses to Learn](https://executeautomation.github.io/mcp-playwright/docs/category/ai-courses-to-learn)

*   [Scenario](https://executeautomation.github.io/mcp-playwright/docs/playwright-api/Examples#scenario)

Docs

*   [Tutorial](https://executeautomation.github.io/mcp-playwright/docs/intro)
*   [Playwright MCP for UI](https://youtu.be/8CcgFUE16HM)
*   [Playwright MCP for API](https://youtu.be/BYYyoRxCcFE)

Community

*   [Youtube](https://youtube.com/executeautomation)
*   [Udemy](https://www.udemy.com/user/karthik-kk)
*   [X](http://x.com/ExecuteAuto)

Copyright © 2025 ExecuteAutomation Pvt Ltd.
