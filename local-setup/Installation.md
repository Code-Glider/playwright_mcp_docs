

Markdown Content:
Build and Run Playwright MCP Server locally[​](https://executeautomation.github.io/mcp-playwright/docs/local-setup/Installation#build-and-run-playwright-mcp-server-locally "Direct link to Build and Run Playwright MCP Server locally")
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

To build/run Playwright MCP Server in your local machine follow the below steps

### Step 1 : Clone Repository[​](https://executeautomation.github.io/mcp-playwright/docs/local-setup/Installation#step-1--clone-repository "Direct link to Step 1 : Clone Repository")

`git clone https://github.com/executeautomation/mcp-playwright.git`

Step 2: Install Dependencies[​](https://executeautomation.github.io/mcp-playwright/docs/local-setup/Installation#step-2-install-dependencies "Direct link to Step 2: Install Dependencies")
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

`npm install`

Step 3: Build Code[​](https://executeautomation.github.io/mcp-playwright/docs/local-setup/Installation#step-3-build-code "Direct link to Step 3: Build Code")
-------------------------------------------------------------------------------------------------------------------------------------------------------------

`npm run buildnpm link`

Step 4: Configuring Playwright MCP in Claude Desktop[​](https://executeautomation.github.io/mcp-playwright/docs/local-setup/Installation#step-4-configuring-playwright-mcp-in-claude-desktop "Direct link to Step 4: Configuring Playwright MCP in Claude Desktop")
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Modify your `claude-desktop-config.json` file as shown below to work with local playwright mcp server

`{  "mcpServers": {    "playwright": {      "command": "npx",      "args": [        "--directory",        "/your-playwright-mcp-server-clone-directory",        "run",        "@executeautomation/playwright-mcp-server"      ]    }  }}`

Important

After modifying the `claude-desktop-config.json` file, you **must** completely close Claude Desktop and **manually terminate** any running processes from **Task Manager** (Windows 10/11).

⚠️ If you skip this step, the configuration changes **may not take effect**.

Reward[​](https://executeautomation.github.io/mcp-playwright/docs/local-setup/Installation#reward "Direct link to Reward")
--------------------------------------------------------------------------------------------------------------------------

If your setup is all correct, you should see Playwright MCP Server pointing your local machine source code

![Image 1: Playwright MCP Server](https://executeautomation.github.io/mcp-playwright/assets/images/mcp-server-54da42a78ffe41b6f4054dab83f28e1a.png)
