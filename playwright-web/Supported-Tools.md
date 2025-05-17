*   Console log monitoring
*   Code Generation
*   Web Scraping
*   Screenshot capabilities
*   JavaScript execution
*   Basic web interaction (navigation, clicking, form filling, drop down select and hover)
*   Content retrieval (visible text and HTML)

* * *

Note

Playwright UI automation is supported for very limited feature sets, more features will be added in upcoming days. Please feel free to fork the repo and add the feature and raise PR, will can build the library together!

Code Generation Tools[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#code-generation-tools "Direct link to Code Generation Tools")
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

These tools allow you to record and generate reusable Playwright test scripts.

### start_codegen_session[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#start_codegen_session "Direct link to start_codegen_session")

Start a new code generation session to record Playwright actions.

*   **Inputs:**

    *   **`options`**_(object, required)_:

Code generation options:
        *   **`outputPath`**_(string, required)_:

Directory path where generated tests will be saved (use absolute path).
        *   **`testNamePrefix`**_(string, optional)_:

Prefix to use for generated test names (default: 'GeneratedTest').
        *   **`includeComments`**_(boolean, optional)_:

Whether to include descriptive comments in generated tests.

*   **Response:**

    *   Session ID for the newly created code generation session.

* * *

### end_codegen_session[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#end_codegen_session "Direct link to end_codegen_session")

End a code generation session and generate the test file.

*   **Inputs:**

    *   **`sessionId`**_(string, required)_:

ID of the session to end.

*   **Response:**

    *   Information about the generated test file.

* * *

### get_codegen_session[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#get_codegen_session "Direct link to get_codegen_session")

Get information about a code generation session.

*   **Inputs:**

    *   **`sessionId`**_(string, required)_:

ID of the session to retrieve.

*   **Response:**

    *   Session information including recorded actions and status.

* * *

### clear_codegen_session[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#clear_codegen_session "Direct link to clear_codegen_session")

Clear a code generation session without generating a test.

*   **Inputs:**

    *   **`sessionId`**_(string, required)_:

ID of the session to clear.

*   **Response:**

    *   Confirmation that the session was cleared.

* * *

Browser Automation Tools[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#browser-automation-tools "Direct link to Browser Automation Tools")
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Playwright_navigate[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_navigate "Direct link to Playwright_navigate")

Navigate to a URL in the browser with configurable viewport and browser settings

*   **`url`**_(string, required)_:

URL of the application under test.

*   **`browserType`**_(string, optional, default: "chromium")_:

Browser engine to use. Supported values: "chromium", "firefox", "webkit".

*   **`width`**_(number, optional, default: 1280)_:

Viewport width in pixels.

*   **`height`**_(number, optional, default: 720)_:

Viewport height in pixels.

*   **`timeout`**_(number, optional)_:

Navigation timeout in milliseconds.

*   **`waitUntil`**_(string, optional)_:

Navigation wait condition.

*   **`headless`**_(boolean, optional, default: false)_:

Run browser in headless mode.

* * *

### Playwright_screenshot[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_screenshot "Direct link to Playwright_screenshot")

Capture screenshots of the entire page or specific elements

*   **`name`**_(string, required)_:

Name for the screenshot.

*   **`selector`**_(string, optional)_:

CSS selector for the element to screenshot.

*   **`width`**_(number, optional, default: 800)_:

Screenshot width.

*   **`height`**_(number, optional, default: 600)_:

Screenshot height.

*   **`storeBase64`**_(boolean, optional, default: false)_:

Store the screenshot as a base64 string.

*   **`fullPage`**_(boolean, optional, default: false)_: Capture a screenshot of the full page.

*   **`savePng`**_(boolean, optional, default: false)_: Save the screenshot as a PNG file.

*   **`downloadsDir`**_(string, optional)_: Directory to save the screenshot.

* * *

### Playwright_click[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_click "Direct link to Playwright_click")

Click elements on the page.

*   **`selector`**_(string)_:

CSS selector for the element to click.

* * *

### playwright_click_and_switch_tab[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_click_and_switch_tab "Direct link to playwright_click_and_switch_tab")

Clicks a link on the page and switches to the newly opened tab.

*   **Inputs:**
    *   **`selector`**_(string)_:

CSS selector for the link to click.

*   **Response:**
    *   Success message with the URL of the newly opened tab.

* * *

### Playwright_iframe_click[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_iframe_click "Direct link to Playwright_iframe_click")

Click elements in an iframe on the page.

*   **`iframeSelector`**_(string)_:

CSS selector for the iframe containing the element to click.

*   **`selector`**_(string)_:

CSS selector for the element to click.

* * *

### Playwright_iframe_fill[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_iframe_fill "Direct link to Playwright_iframe_fill")

Fill elements in an iframe on the page.

*   **`iframeSelector`**_(string)_:

CSS selector for the iframe containing the element to fill.

*   **`selector`**_(string)_:

CSS selector for the element to fill.

* * *

### Playwright_hover[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_hover "Direct link to Playwright_hover")

Hover over elements on the page.

*   **`selector`**_(string)_:

CSS selector for the element to hover.

* * *

### Playwright_fill[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_fill "Direct link to Playwright_fill")

Fill out input fields.

*   **`selector`**_(string)_:

CSS selector for the input field.
*   **`value`**_(string)_:

Value to fill.

* * *

### Playwright_select[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_select "Direct link to Playwright_select")

Select an element with the `SELECT` tag.

*   **`selector`**_(string)_:

CSS selector for the element to select.
*   **`value`**_(string)_:

Value to select.

* * *

### Playwright_evaluate[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_evaluate "Direct link to Playwright_evaluate")

Execute JavaScript in the browser console.

*   **`script`**_(string)_:

JavaScript code to execute.

* * *

### Playwright_console_logs[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_console_logs "Direct link to Playwright_console_logs")

Retrieve console logs from the browser with filtering options Supports Retrieval of logs like - all, error, warning, log, info, debug, exception

*   **`search`**_(string)_:

Text to search for in logs (handles text with square brackets).

*   **`limit`**_(number)_: Maximum number of logs to retrieve.

*   **`type`**_(string)_: Type of logs to retrieve (all, error, warning, log, info, debug, exception).

*   **`clear`**_(boolean)_: Whether to clear logs after retrieval (default: false).

* * *

### Playwright_close[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_close "Direct link to Playwright_close")

Close the browser and release all resources. Useful while working with Cline, Cursor to release the resources.

* * *

### Playwright_expect_response[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_expect_response "Direct link to Playwright_expect_response")

Ask Playwright to start waiting for a HTTP response. This tool initiates the wait operation but does not wait for its completion.

*   **Inputs:**
    *   **`id`**_(string)_:

Unique & arbitrary identifier to be used for retrieving this response later with `Playwright_assert_response`.
    *   **`url`**_(string)_:

URL pattern to match in the response.

* * *

### Playwright_assert_response[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_assert_response "Direct link to Playwright_assert_response")

Wait for and validate a previously initiated HTTP response wait operation.

*   **Inputs:**

    *   **`id`**_(string)_:

Identifier of the HTTP response initially expected using `Playwright_expect_response`.
    *   **`value`**_(string, optional)_:

Data to expect in the body of the HTTP response. If provided, the assertion will fail if this value is not found in the response body.

*   **Response:**

    *   **`statusCode`**_(string)_:

Status code of the response.
    *   **`responseUrl`**_(string)_:

Full URL of the captured response.
    *   **`responseBody`**_(string)_:

Full response body in JSON format.

* * *

### playwright_custom_user_agent[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_custom_user_agent "Direct link to playwright_custom_user_agent")

Set a custom User Agent for the browser.

*   **Inputs:**
    *   **`userAgent`**_(string)_:

Custom User Agent for the Playwright browser instance

* * *

### playwright_get_visible_text[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_get_visible_text "Direct link to playwright_get_visible_text")

Get the visible text content of the current page.

*   **Response:**
    *   **`content`**_(string)_:

The visible text content of the current page, extracted from visible DOM elements. Hidden elements (with display:none or visibility:hidden) are excluded.

* * *

### playwright_get_visible_html[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_get_visible_html "Direct link to playwright_get_visible_html")

Get the HTML content of the current page.

*   **Response:**
    *   **`content`**_(string)_:

The complete HTML content of the current page.

* * *

### playwright_go_back[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_go_back "Direct link to playwright_go_back")

Navigate back in browser history.

*   **Response:**
    *   Confirmation message that the browser has navigated back in its history.

* * *

### playwright_go_forward[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_go_forward "Direct link to playwright_go_forward")

Navigate forward in browser history.

*   **Response:**
    *   Confirmation message that the browser has navigated forward in its history.

* * *

### playwright_drag[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_drag "Direct link to playwright_drag")

Drag an element to a target location.

*   **Inputs:**

    *   **`sourceSelector`**_(string)_:

CSS selector for the element to drag.
    *   **`targetSelector`**_(string)_:

CSS selector for the target location.

*   **Response:**

    *   Confirmation message that the drag operation has been performed.

* * *

### playwright_press_key[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_press_key "Direct link to playwright_press_key")

Press a keyboard key.

*   **Inputs:**

    *   **`key`**_(string)_:

Key to press (e.g. 'Enter', 'ArrowDown', 'a').
    *   **`selector`**_(string, optional)_:

CSS selector for an element to focus before pressing the key.

*   **Response:**

    *   Confirmation message indicating which key was pressed.

* * *

### playwright_save_as_pdf[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Supported-Tools#playwright_save_as_pdf "Direct link to playwright_save_as_pdf")

Save the current page as a PDF file.

*   **Inputs:**

    *   **`outputPath`**_(string)_:

Directory path where the PDF will be saved.
    *   **`filename`**_(string, optional, default: "page.pdf")_:

Name of the PDF file.
    *   **`format`**_(string, optional, default: "A4")_:

Page format (e.g. 'A4', 'Letter').
    *   **`printBackground`**_(boolean, optional, default: true)_:

Whether to print background graphics.
    *   **`margin`**_(object, optional)_:

Page margins with the following properties:
        *   **`top`**_(string)_: Top margin (e.g. '1cm').
        *   **`right`**_(string)_: Right margin (e.g. '1cm').
        *   **`bottom`**_(string)_: Bottom margin (e.g. '1cm').
        *   **`left`**_(string)_: Left margin (e.g. '1cm').

*   **Response:**

    *   Path to the saved PDF file.
