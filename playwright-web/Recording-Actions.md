

Markdown Content:
🎥 Recording Actions | Playwright MCP Server
===============

[Skip to main content](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Recording-Actions#__docusaurus_skipToContent_fallback)

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
*   [Playwright Web Features](https://executeautomation.github.io/mcp-playwright/docs/category/playwright-web-features)
*   🎥 Recording Actions

On this page

🎥 Recording Actions
====================

Playwright MCP allows you to record your browser interactions and automatically generate test specifications. This feature helps you create automated tests without writing code manually.

Getting Started[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Recording-Actions#getting-started "Direct link to Getting Started")
-------------------------------------------------------------------------------------------------------------------------------------------------------------

To start recording your actions and generate test files, you'll need to:

1.   Start a recording session
2.   Perform your actions using MCP tools
3.   End the session to generate the test file

### Example[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Recording-Actions#example "Direct link to Example")

Here's a complete example of recording actions and generating a test spec:

1.   First, start a new recording session by specifying:

    *   Where to save the generated tests (`tests/generated` directory)
    *   What to name your tests (using 'LoginTest' as a prefix)
    *   Whether to include helpful comments in the generated code

2.   Then perform the test actions:

    *   Navigate to the Sauce Demo website ([https://www.saucedemo.com](https://www.saucedemo.com/))
    *   Enter "standard_user" in the username field
    *   Enter "secret_sauce" in the password field
    *   Click the login button

3.   Finally, end the recording session to generate your test file

The generated test file will look something like this:

`import { test, expect } from '@playwright/test';test('LoginTest_2024-03-23', async ({ page }) => {  // Navigate to the login page  await page.goto('https://www.saucedemo.com');  // Fill in username  await page.fill('#user-name', 'standard_user');  // Fill in password  await page.fill('#password', 'secret_sauce');  // Click login button  await page.click('#login-button');  // Verify successful login  await expect(page).toHaveURL(/.*inventory.html/);});`

Configuration Options[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Recording-Actions#configuration-options "Direct link to Configuration Options")
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

When starting a recording session, you can configure several options:

*   **outputPath**: Directory where the generated test files will be saved
*   **testNamePrefix**: Prefix for the generated test names
*   **includeComments**: Whether to include descriptive comments in the generated tests

For example, you might configure your session to:

*   Save tests in a 'tests/generated' folder
*   Name tests with a 'MyTest' prefix
*   Include helpful comments in the generated code

Session Management[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Recording-Actions#session-management "Direct link to Session Management")
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

You can manage your recording sessions using these tools:

*   **get_codegen_session**: Retrieve information about a recording session
*   **clear_codegen_session**: Clean up a recording session without generating a test

These tools help you check the status of your recording or clean up if you want to start over without generating a test file.

Best Practices[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Recording-Actions#best-practices "Direct link to Best Practices")
----------------------------------------------------------------------------------------------------------------------------------------------------------

1.   **Organize Tests**: Use meaningful test name prefixes to organize your generated tests
2.   **Clean Up**: Always end or clear your sessions after recording
3.   **Verify Actions**: Include verification steps in your recordings
4.   **Maintain Context**: Keep related actions in the same recording session
5.   **Documentation**: Add comments during recording for better test maintainability

Running Generated Tests[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Recording-Actions#running-generated-tests "Direct link to Running Generated Tests")
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

To run your generated tests, use the Playwright test runner:

`npx playwright test tests/generated/logintest_*.spec.ts`

tip

You can modify the generated test files to add additional assertions, setup, or teardown code as needed.

[Edit this page](https://github.com/facebook/docusaurus/tree/main/packages/create-docusaurus/templates/shared/docs/playwright-web/Recording-Actions.mdx)

[Previous 🌐 Examples of browser automation](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Examples)[Next Playwright API Features](https://executeautomation.github.io/mcp-playwright/docs/category/playwright-api-features)

*   [Getting Started](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Recording-Actions#getting-started)
    *   [Example](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Recording-Actions#example)

*   [Configuration Options](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Recording-Actions#configuration-options)
*   [Session Management](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Recording-Actions#session-management)
*   [Best Practices](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Recording-Actions#best-practices)
*   [Running Generated Tests](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Recording-Actions#running-generated-tests)

Docs

*   [Tutorial](https://executeautomation.github.io/mcp-playwright/docs/intro)
*   [Playwright MCP for UI](https://youtu.be/8CcgFUE16HM)
*   [Playwright MCP for API](https://youtu.be/BYYyoRxCcFE)

Community

*   [Youtube](https://youtube.com/executeautomation)
*   [Udemy](https://www.udemy.com/user/karthik-kk)
*   [X](http://x.com/ExecuteAuto)

Copyright © 2025 ExecuteAutomation Pvt Ltd.
