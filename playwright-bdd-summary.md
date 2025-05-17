# Playwright-BDD Summary

This document summarizes the key aspects of Playwright-BDD based on the provided snippets, covering its purpose, core features, configuration, and usage patterns for implementing Behavior-Driven Development (BDD) with Playwright.

**Purpose:**

Playwright-BDD allows developers and testers to write and execute end-to-end tests using the Gherkin syntax (Given, When, Then) with Playwright as the test runner. It bridges the gap between human-readable specifications and automated test code.

**Key Features and Concepts:**

1.  **Gherkin Feature Files:** Write test scenarios in `.feature` files using Gherkin syntax, making tests understandable by non-technical stakeholders. Examples include scenarios for checking page titles, clicking links, and managing todo items.
2.  **Step Definitions:** Implement the Gherkin steps using JavaScript or TypeScript. Playwright-BDD provides functions (`Given`, `When`, `Then`) to define the actions corresponding to each step.
3.  **`bddgen` CLI Tool:** A command-line tool (`npx bddgen`) that generates executable test files (typically JavaScript or TypeScript) from the Gherkin feature files. This generated code uses the Playwright test runner.
4.  **Configuration:** Configure Playwright-BDD using `defineBddConfig` within the Playwright configuration file (`playwright.config.ts` or `.js`). This includes specifying the location of feature files and step definitions.
5.  **Fixtures:** Leverage Playwright's fixture system to share state and resources between steps and scenarios. Custom fixtures can be created to handle tasks like authentication, data sharing (`ctx` object), and browser context management.
6.  **Hooks:** Implement `BeforeAll`, `AfterAll`, `BeforeWorker`, `AfterWorker`, `BeforeScenario`, `AfterScenario`, `BeforeStep`, and `AfterStep` hooks to perform setup and teardown actions at different stages of the test lifecycle. Hooks can be scoped using tags.
7.  **Tags:** Use tags (`@tagname`) in feature files to categorize scenarios, filter test execution (`bddgen --tags`), and scope step definitions or hooks. Special tags like `@only`, `@skip`, `@fail`, `@slow`, `@retries:N`, and `@mode:serial/@mode:parallel` control test execution behavior.
8.  **Data Tables:** Use Data Tables within Gherkin scenarios to provide structured test data, which can be accessed and processed within step definitions.
9.  **Page Object Model (POM):** Supports implementing step definitions within POM classes using decorators (`@Given`, `@When`, `@Then`) for better organization and maintainability.
10. **Reporters:** Integrate with various reporters (HTML, JUnit, JSON, Allure, Currents) to generate detailed test execution reports.
11. **AI-Assisted Test Fixing:** Configuration options (`aiFix`) are available to enable AI assistance for fixing failing tests, potentially using page snapshots (like ARIA snapshots) as context.
12. **Environment Variables:** Access environment variables within step definitions for flexible test configurations.

**Workflow:**

The typical workflow involves:
1. Writing `.feature` files in Gherkin.
2. Implementing corresponding step definitions.
3. Running `npx bddgen` to generate Playwright test files.
4. Running `npx playwright test` to execute the generated tests.

Playwright-BDD provides a structured approach to writing automated tests, combining the readability of BDD with the power of the Playwright automation library.