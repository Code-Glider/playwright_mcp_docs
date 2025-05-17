Title: Playwright MCP Server | Playwright MCP Server

URL Source: https://executeautomation.github.io/mcp-playwright/docs/intro

Markdown Content:
The **Playwright Model Context Protocol (MCP) server** is a powerful solution for automating Browser and API testing using Playwright.

With the Playwright MCP server, you can:

*   Enable LLMs to interact with web pages in a real browser environment.
*   Perform tasks such as executing JavaScript, taking screenshots, and navigating web elements.
*   Seamlessly handle API testing to validate endpoints and ensure reliability.
*   Test across multiple browser engines including Chromium, Firefox, and WebKit.

![Image 1: Playwright MCP Server](https://executeautomation.github.io/mcp-playwright/assets/images/mcp-server-54da42a78ffe41b6f4054dab83f28e1a.png)

Installation[​](https://executeautomation.github.io/mcp-playwright/docs/intro#installation "Direct link to Installation")
-------------------------------------------------------------------------------------------------------------------------

You can install Playwright MCP Server package using either **npm**, **mcp-get**, or **Smithery**:

Playwright MCP Tips

To get started more quickly on Playwright MCP Server, watch the videos mentioned in the footer of this page under `Docs`

### Installing via NPM[​](https://executeautomation.github.io/mcp-playwright/docs/intro#installing-via-npm "Direct link to Installing via NPM")

To install Playwright MCP for Claude Desktop automatically via Smithery:

`npm install -g @executeautomation/playwright-mcp-server`

### Installing via Smithery[​](https://executeautomation.github.io/mcp-playwright/docs/intro#installing-via-smithery "Direct link to Installing via Smithery")

To install Playwright MCP for Claude Desktop automatically via Smithery:

`npx @smithery/cli install @executeautomation/playwright-mcp-server --client claude`

You can type this command into Command Prompt, Powershell, Terminal, or any other integrated terminal of your code editor.

### Installing via MCP-GET[​](https://executeautomation.github.io/mcp-playwright/docs/intro#installing-via-mcp-get "Direct link to Installing via MCP-GET")

To install Playwright MCP for Claude Desktop automatically via Smithery:

`npx @michaellatman/mcp-get@latest install @executeautomation/playwright-mcp-server`

### Configuring Playwright MCP in Claude Desktop[​](https://executeautomation.github.io/mcp-playwright/docs/intro#configuring-playwright-mcp-in-claude-desktop "Direct link to Configuring Playwright MCP in Claude Desktop")

Here's the Claude Desktop configuration to use the Playwright MCP server.

Modify your `claude-desktop-config.json` file as shown below

`{  "mcpServers": {    "playwright": {      "command": "npx",      "args": ["-y", "@executeautomation/playwright-mcp-server"]    }  }}`

### What is Model Context Protocol[​](https://executeautomation.github.io/mcp-playwright/docs/intro#what-is-model-context-protocol "Direct link to What is Model Context Protocol")

This video should give you an high level overview of what Claude's MCP is and how helpful it will soon become for AI agents
