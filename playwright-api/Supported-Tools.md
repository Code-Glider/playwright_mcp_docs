

Markdown Content:
Playwright MCP for API automation has following key features

*   Support of GET Request
*   Support of POST Request
*   Support of PATCH Request
*   Support of PUT Request
*   Support of DELETE Request

* * *

Note

Still the library is not matured enough to support Oauth, Multi-form, Binary input or complex API requests. Please feel free to fork the repo and add the feature with a PR, will can build the library together!

### Playwright_get[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-api/Supported-Tools#playwright_get "Direct link to Playwright_get")

Perform a GET operation on any given API request.

*   **Inputs:**

    *   **`url`**_(string)_:

URL to perform the GET operation.

*   **Response:**

    *   **`statusCode`**_(string)_:

Status code of the API.

* * *

### Playwright_post[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-api/Supported-Tools#playwright_post "Direct link to Playwright_post")

Perform a POST operation on any given API request.

*   **Inputs:**

    *   **`url`**_(string)_:

URL to perform the POST operation.
    *   **`value`**_(string)_:

Data to include in the body of the POST request.
    *   **`token`**_(string, optional)_:

Bearer token for authorization. When provided, it will be sent as `Authorization: Bearer <token>` header.
    *   **`headers`**_(object, optional)_:

Additional headers to include in the request. Note: Content-Type: application/json is set by default.

*   **Response:**

    *   **`statusCode`**_(string)_:

Status code of the API.
    *   **`responseData`**_(string)_:

Response data in JSON format.

* * *

### Playwright_put[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-api/Supported-Tools#playwright_put "Direct link to Playwright_put")

Perform a PUT operation on any given API request.

*   **Inputs:**

    *   **`url`**_(string)_:

URL to perform the PUT operation.
    *   **`value`**_(string)_:

Data to include in the body of the PUT request.

*   **Response:**

    *   **`statusCode`**_(string)_:

Status code of the API.
    *   **`responseData`**_(string)_:

Response data in JSON format.

* * *

### Playwright_patch[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-api/Supported-Tools#playwright_patch "Direct link to Playwright_patch")

Perform a PATCH operation on any given API request.

*   **Inputs:**

    *   **`url`**_(string)_:

URL to perform the PATCH operation.
    *   **`value`**_(string)_:

Data to include in the body of the PATCH request.

*   **Response:**

    *   **`statusCode`**_(string)_:

Status code of the API.
    *   **`responseData`**_(string)_:

Response data in JSON format.

* * *

### Playwright_delete[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-api/Supported-Tools#playwright_delete "Direct link to Playwright_delete")

Perform a DELETE operation on any given API request.

*   **Inputs:**

    *   **`url`**_(string)_:

URL to perform the DELETE operation.

*   **Response:**

    *   **`statusCode`**_(string)_:

Status code of the API.

### Upon running the test Claude Desktop will run MCP Server to use above tools[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-api/Supported-Tools#upon-running-the-test-claude-desktop-will-run-mcp-server-to-use-above-tools "Direct link to Upon running the test Claude Desktop will run MCP Server to use above tools")

![Image 1: Playwright MCP Server](https://executeautomation.github.io/mcp-playwright/assets/images/playwright-api-046cf2650b0fc907a8a083e0b0f43a02.png)
