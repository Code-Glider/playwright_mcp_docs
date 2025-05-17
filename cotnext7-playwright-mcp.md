TITLE: Running Playwright MCP with Configuration File (Bash)
DESCRIPTION: Shows how to start the Playwright MCP server using the `npx` command and specify a custom configuration file path using the `--config` flag, allowing for detailed server and browser settings to be loaded from a JSON file.
SOURCE: https://github.com/microsoft/playwright-mcp/blob/main/README.md#_snippet_3

LANGUAGE: bash
CODE:
```
npx @playwright/mcp@latest --config path/to/config.json
```

----------------------------------------

TITLE: Defining Playwright MCP Configuration Format (TypeScript)
DESCRIPTION: Describes the structure of the JSON configuration file for the Playwright MCP server, detailing options for browser settings, server port/host, enabled capabilities, vision mode, output directory, network origin filtering, and tool-specific configurations.
SOURCE: https://github.com/microsoft/playwright-mcp/blob/main/README.md#_snippet_2

LANGUAGE: typescript
CODE:
```
{
  // Browser configuration
  browser?: {
    // Browser type to use (chromium, firefox, or webkit)
    browserName?: 'chromium' | 'firefox' | 'webkit';

    // Path to user data directory for browser profile persistence
    userDataDir?: string;

    // Browser launch options (see Playwright docs)
    // @see https://playwright.dev/docs/api/class-browsertype#browser-type-launch
    launchOptions?: {
      channel?: string;        // Browser channel (e.g. 'chrome')
      headless?: boolean;      // Run in headless mode
      executablePath?: string; // Path to browser executable
      // ... other Playwright launch options
    };

    // Browser context options
    // @see https://playwright.dev/docs/api/class-browser#browser-new-context
    contextOptions?: {
      viewport?: { width: number, height: number };
      // ... other Playwright context options
    };

    // CDP endpoint for connecting to existing browser
    cdpEndpoint?: string;

    // Remote Playwright server endpoint
    remoteEndpoint?: string;
  },

  // Server configuration
  server?: {
    port?: number;  // Port to listen on
    host?: string;  // Host to bind to (default: localhost)
  },

  // List of enabled capabilities
  capabilities?: Array<
    'core' |    // Core browser automation
    'tabs' |    // Tab management
    'pdf' |     // PDF generation
    'history' | // Browser history
    'wait' |    // Wait utilities
    'files' |   // File handling
    'install' | // Browser installation
    'testing'   // Testing
  >;

  // Enable vision mode (screenshots instead of accessibility snapshots)
  vision?: boolean;

  // Directory for output files
  outputDir?: string;

  // Network configuration
  network?: {
    // List of origins to allow the browser to request. Default is to allow all. Origins matching both `allowedOrigins` and `blockedOrigins` will be blocked.
    allowedOrigins?: string[];

    // List of origins to block the browser to request. Origins matching both `allowedOrigins` and `blockedOrigins` will be blocked.
    blockedOrigins?: string[];
  };

  // Tool-specific configurations
  tools?: {
    browser_take_screenshot?: {
      // Disable base64-encoded image responses
      omitBase64?: boolean;
    }
  }
}
```

----------------------------------------

TITLE: Creating Playwright MCP Server Programmatically (JavaScript)
DESCRIPTION: Presents a JavaScript example demonstrating how to programmatically create and connect to a headless Playwright MCP server instance using the `@playwright/mcp` and `@modelcontextprotocol/sdk` libraries, setting up an SSE transport over an HTTP response.
SOURCE: https://github.com/microsoft/playwright-mcp/blob/main/README.md#_snippet_8

LANGUAGE: javascript
CODE:
```
import http from 'http';

import { createServer } from '@playwright/mcp';
import { SSEServerTransport } from '@modelcontextprotocol/sdk/server/sse.js';

http.createServer(async (req, res) => {
  // ...

  // Creates a headless Playwright MCP server with SSE transport
  const mcpServer = await createServer({ headless: true });
  const transport = new SSEServerTransport('/messages', res);
  await mcpServer.connect(transport);

  // ...
});
```

----------------------------------------

TITLE: Configuring Playwright MCP Client for Docker (JavaScript)
DESCRIPTION: Illustrates configuring a Playwright MCP client to launch the server via a Docker command, specifying the `command` as "docker" and providing the necessary `args` array to run the `mcp/playwright` image interactively, removing the container after exit, and initializing it.
SOURCE: https://github.com/microsoft/playwright-mcp/blob/main/README.md#_snippet_6

LANGUAGE: javascript
CODE:
```
{
  "mcpServers": {
    "playwright": {
      "command": "docker",
      "args": ["run", "-i", "--rm", "--init", "mcp/playwright"]
    }
  }
}
```

----------------------------------------

TITLE: Configuring Playwright MCP Client for Vision Mode (JavaScript)
DESCRIPTION: Shows how to configure a Playwright MCP client to start the server in Vision Mode by including the `--vision` flag in the `args` array for the `npx` command, enabling screenshot-based interactions.
SOURCE: https://github.com/microsoft/playwright-mcp/blob/main/README.md#_snippet_9

LANGUAGE: javascript
CODE:
```
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": [
        "@playwright/mcp@latest",
        "--vision"
      ]
    }
  }
}
```

----------------------------------------

TITLE: Running Playwright MCP Server with SSE Transport (Bash)
DESCRIPTION: Demonstrates running the Playwright MCP server with the `--port` flag to enable Server-Sent Events (SSE) transport, which is useful for environments without a display or when running from IDE worker processes.
SOURCE: https://github.com/microsoft/playwright-mcp/blob/main/README.md#_snippet_4

LANGUAGE: bash
CODE:
```
npx @playwright/mcp@latest --port 8931
```

----------------------------------------

TITLE: Configuring Playwright MCP Client for SSE (JavaScript)
DESCRIPTION: Provides an example of how to configure a Playwright MCP client to connect to a server running with SSE transport, specifying the `url` property within the `mcpServers` object to point to the SSE endpoint.
SOURCE: https://github.com/microsoft/playwright-mcp/blob/main/README.md#_snippet_5

LANGUAGE: javascript
CODE:
```
{
  "mcpServers": {
    "playwright": {
      "url": "http://localhost:8931/sse"
    }
  }
}
```

----------------------------------------

TITLE: Example Playwright MCP Server Configuration (JS)
DESCRIPTION: Provides an example configuration object for integrating the Playwright MCP server into a system, specifying the command and arguments needed to launch it using npx.
SOURCE: https://github.com/microsoft/playwright-mcp/blob/main/README.md#_snippet_0

LANGUAGE: js
CODE:
```
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": [
        "@playwright/mcp@latest"
      ]
    }
  }
}
```

----------------------------------------

TITLE: Installing Playwright MCP Server in VS Code (Bash)
DESCRIPTION: Demonstrates how to install the Playwright MCP server using the VS Code command-line interface, adding it as an MCP server with its name, command, and arguments.
SOURCE: https://github.com/microsoft/playwright-mcp/blob/main/README.md#_snippet_1

LANGUAGE: bash
CODE:
```
# For VS Code
code --add-mcp '{"name":"playwright","command":"npx","args":["@playwright/mcp@latest"]}'
```

----------------------------------------

TITLE: Building Playwright MCP Docker Image (Bash)
DESCRIPTION: Shows the command line instruction to build the Docker image for Playwright MCP using the local Dockerfile, tagging the resulting image as `mcp/playwright`.
SOURCE: https://github.com/microsoft/playwright-mcp/blob/main/README.md#_snippet_7

LANGUAGE: bash
CODE:
```
docker build -t mcp/playwright .
```