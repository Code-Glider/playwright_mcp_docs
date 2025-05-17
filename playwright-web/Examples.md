

Markdown Content:
Lets see how we can use the power of Playwright MCP Server to automate our browser and do webscrapping

### Using Different Browser Types[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Examples#using-different-browser-types "Direct link to Using Different Browser Types")

Playwright MCP now supports multiple browser engines. You can choose between Chromium (default), Firefox, and WebKit:

`Given I navigate to website "https://example.com" using the "firefox" browserAnd I take a screenshot named "firefox-example"Then I navigate to website "https://example.com" using the "webkit" browser And I take a screenshot named "webkit-example"`

When you send these commands to Claude, it will open the website in Firefox first, take a screenshot, then switch to WebKit and take another screenshot, allowing you to compare how different browsers render the same website.

### Scenario in BDD Format[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Examples#scenario-in-bdd-format "Direct link to Scenario in BDD Format")

`Given I navigate to website http://eaapp.somee.com and click login linkAnd I enter username and password as "admin" and "password" respectively and perform loginThen click the Employee List page And click "Create New" button and enter realistic employee details to create for Name, Salary, DurationWorked,Select dropdown for Grade as CLevel and Email.`

Once I enter the above text in _**Claude Desktop Client**_ I should see Claude desktop giving me prompt to perform operation by opening real browser like this

![Image 1: Playwright MCP Server](https://executeautomation.github.io/mcp-playwright/assets/images/mcp-execution-bc744c681006e1ff2f756812e32a6d1d.png)

And once the entire test operation completes, we will be presented with the entire details of how the automation did happened.

![Image 2: Playwright MCP Server](https://executeautomation.github.io/mcp-playwright/assets/images/mcp-result-30c8e9297f34cc8d1ea840cddea499ad.png)

### Using Browser History Navigation[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Examples#using-browser-history-navigation "Direct link to Using Browser History Navigation")

You can navigate through the browser's history using the new navigation controls:

`Given I navigate to website "https://example.com"When I navigate to website "https://example.com/about"And I navigate back in browser historyThen the current page should be "https://example.com"When I navigate forward in browser historyThen the current page should be "https://example.com/about"`

### Using Drag and Drop Functionality[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Examples#using-drag-and-drop-functionality "Direct link to Using Drag and Drop Functionality")

You can drag and drop elements using the new drag tool:

`Given I navigate to website "https://example.com/drag-drop-demo"When I drag element with id "draggable" to element with id "droppable"Then I should see confirmation message "Dropped!"`

### Using Keyboard Interactions[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Examples#using-keyboard-interactions "Direct link to Using Keyboard Interactions")

You can simulate keyboard presses with the new keyboard tool:

`Given I navigate to website "https://example.com/form"When I focus on the input field with id "search-box"And I press the "Enter" keyThen the search results should appear`

### Saving Page as PDF[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Examples#saving-page-as-pdf "Direct link to Saving Page as PDF")

You can save the current page as a PDF file:

`Given I navigate to website "https://example.com/report"When I save the current page as a PDF in "/downloads" folder with name "report.pdf"Then I should see confirmation that the PDF was saved`

Advanced example with custom options:

`Given I navigate to website "https://example.com/invoice"When I save the page as PDF with the following settings:  | Setting          | Value     |  | ----------------- | --------- |  | Output Path      | /downloads |  | Filename         | invoice.pdf |  | Format           | Letter    |  | Print Background | true      |  | Top Margin       | 2cm       |  | Right Margin     | 1cm       |  | Bottom Margin    | 2cm       |  | Left Margin      | 1cm       |Then I should see confirmation that the PDF was saved`

### Extracting Page Content[​](https://executeautomation.github.io/mcp-playwright/docs/playwright-web/Examples#extracting-page-content "Direct link to Extracting Page Content")

You can extract visible text content from the page:

`Given I navigate to website "https://example.com/article"When I extract all visible text from the pageThen I should see the article content in plain text without hidden elements`

You can also get the complete HTML of the page:

`Given I navigate to website "https://example.com/products"When I extract the HTML content of the pageThen I should receive the complete HTML structure of the page`

Example use case for content analysis:

`Given I navigate to website "https://example.com/pricing"When I extract all visible text from the pageThen I should be able to analyze the text to find pricing informationAnd I can determine if the "Enterprise" plan mentions "custom pricing"`
