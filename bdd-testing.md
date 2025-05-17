TITLE: Creating a Gherkin Feature File for Playwright Site Testing
DESCRIPTION: This snippet demonstrates how to write a Gherkin feature file for testing the Playwright website. It includes a scenario with Given, When, and Then steps, as well as tags for categorization.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/index.md#2025-04-22_snippet_0

LANGUAGE: gherkin
CODE:
```
@desktop
Feature: Playwright site

    @jira:123
    Scenario: Check title
        Given I open url "https://playwright.dev"
        When I click link "Get started"
        Then I see in title "Playwright"
```

----------------------------------------

TITLE: Configuring Playwright-BDD in JavaScript
DESCRIPTION: This snippet shows how to set up the configuration file for Playwright-BDD. It defines the test directory, feature file, and step file locations.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/getting-started/write-first-test.md#2025-04-22_snippet_0

LANGUAGE: javascript
CODE:
```
import { defineConfig } from '@playwright/test';
import { defineBddConfig } from 'playwright-bdd';

const testDir = defineBddConfig({
  features: 'sample.feature',
  steps: 'steps.js',
});

export default defineConfig({
  testDir,
  reporter: 'html',
});
```

----------------------------------------

TITLE: Writing a Gherkin Feature File
DESCRIPTION: This snippet demonstrates how to write a Gherkin feature file for BDD testing. It defines a feature and a scenario with Given, When, and Then steps.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/getting-started/write-first-test.md#2025-04-22_snippet_1

LANGUAGE: gherkin
CODE:
```
Feature: Playwright site

    Scenario: Check get started link
        Given I am on home page
        When I click link "Get started"
        Then I see in title "Installation"
```

----------------------------------------

TITLE: Creating Custom Test Instance and BDD Functions in TypeScript
DESCRIPTION: This code snippet shows how to create a custom test instance with fixtures and export it along with BDD step definition functions. It extends the base test with a custom fixture and uses createBdd to generate Given, When, Then functions.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/getting-started/add-fixtures.md#2025-04-22_snippet_0

LANGUAGE: typescript
CODE:
```
// fixtures.ts
import { test as base, createBdd } from 'playwright-bdd';

export const test = base.extend({
  myFixture: async ({ page }, use) => {
    // ... define your fixture here
  }
});

export const { Given, When, Then } = createBdd(test);
```

----------------------------------------

TITLE: Running Playwright BDD Tests in Debug Mode
DESCRIPTION: This command generates BDD tests and runs them with the --debug flag, which opens the browser and allows step-by-step evaluation of the test execution.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/debugging.md#2025-04-22_snippet_0

LANGUAGE: bash
CODE:
```
npx bddgen && npx playwright test --debug
```

----------------------------------------

TITLE: Implementing Step Definition using Decorators in TypeScript
DESCRIPTION: Illustrates how to use decorators to mark POM (Page Object Model) class methods as steps. This approach is recommended for all projects.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/index.md#2025-04-22_snippet_2

LANGUAGE: typescript
CODE:
```
class TodoPage {
  @Given('I open page {string}')
  async open(url: string) {
    await this.page.goto(url);
  }
}
```

----------------------------------------

TITLE: Implementing Playwright-style Step Definition in TypeScript
DESCRIPTION: Demonstrates how to write a step definition using Playwright-style syntax. This approach is recommended for new BDD projects or existing Playwright projects.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/index.md#2025-04-22_snippet_0

LANGUAGE: typescript
CODE:
```
Given('I open page {string}', async ({ page }, url: string) => {
  await page.goto(url);
});
```

----------------------------------------

TITLE: Implementing BDD Steps in TypeScript
DESCRIPTION: This code snippet shows how to implement the steps defined in the feature file using TypeScript. It uses the createBdd function to define Given, When, and Then steps.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/getting-started/write-first-test.md#2025-04-22_snippet_2

LANGUAGE: typescript
CODE:
```
import { expect } from '@playwright/test';
import { createBdd } from 'playwright-bdd';

const { Given, When, Then } = createBdd();

Given('I am on home page', async ({ page }) => {
  await page.goto('https://playwright.dev');
});

When('I click link {string}', async ({ page }, name) => {
  await page.getByRole('link', { name }).click();
});

Then('I see in title {string}', async ({ page }, keyword) => {
  await expect(page).toHaveTitle(new RegExp(keyword));
});
```

----------------------------------------

TITLE: Running Playwright-BDD Tests Command
DESCRIPTION: Basic command to generate and run BDD tests with Playwright
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/index.md#2025-04-22_snippet_0

LANGUAGE: bash
CODE:
```
npx bddgen && npx playwright test
```

----------------------------------------

TITLE: Implementing Page Object Model with Decorators
DESCRIPTION: Demonstrates how to create a TodoPage class using decorators to define test steps and fixtures. Shows implementation of Given, When, and Then steps within a Page Object Model.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/decorators.md#2025-04-22_snippet_1

LANGUAGE: typescript
CODE:
```
// TodoPage.ts
import { Page, expect } from '@playwright/test';
import { Fixture, Given, When, Then } from 'playwright-bdd/decorators';

export @Fixture('todoPage') class TodoPage {
  constructor(public page: Page) { }

  @Given('I am on todo page')
  async open() {
    await this.page.goto('https://demo.playwright.dev/todomvc/');
  }

  @When('I add todo {string}')
  async addToDo(text: string) {
    await this.page.locator('input.new-todo').fill(text);
    await this.page.locator('input.new-todo').press('Enter');
  }

  @Then('visible todos count is {int}')
  async checkVisibleTodosCount(count: number) {
    await expect(this.page.getByTestId('todo-item')).toHaveCount(count);
  }
}
```

----------------------------------------

TITLE: Configuring Playwright-BDD Project in TypeScript
DESCRIPTION: Example of using defineBddProject to configure a Playwright-BDD project. It demonstrates how to set up a project with custom features and steps directories.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/api.md#2025-04-22_snippet_0

LANGUAGE: typescript
CODE:
```
import { defineConfig } from '@playwright/test';
import { defineBddProject } from 'playwright-bdd';

export default defineConfig({
  projects: [
    {
      ...defineBddProject({
        name: 'foo',
        features: '*.feature',
        steps: 'steps/*.ts',
      }), // -> { name: 'foo', testDir: '.features-gen/foo' }
    },
  ]
});
```

----------------------------------------

TITLE: Installing Playwright-BDD with Yarn - New Project
DESCRIPTION: Commands to install Playwright and Playwright-BDD dependencies using Yarn, followed by installing Playwright browsers.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/getting-started/installation.md#2025-04-22_snippet_5

LANGUAGE: bash
CODE:
```
yarn add -D @playwright/test playwright-bdd
```

LANGUAGE: bash
CODE:
```
yarn playwright install
```

----------------------------------------

TITLE: Defining Step Definitions for Todo App in TypeScript
DESCRIPTION: This code snippet shows how to create step definitions for a Todo app using Playwright-BDD. It includes steps for navigating to the page, adding and removing todos, and checking the todo count.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/chatgpt.md#2025-04-22_snippet_0

LANGUAGE: typescript
CODE:
```
import { createBdd } from 'playwright-bdd';

const { Given, When, Then } = createBdd(test);

Given('I am on todo page', async ({ page }) => { 
  await page.goto('https://demo.playwright.dev/todomvc/');
});

When('I add todo {string}', async ({ page }, text: string) => {
  await page.locator('input.new-todo').fill(text);
  await page.locator('input.new-todo').press('Enter');
});

When('I remove todo {string}', async ({ page }, text: string) => {
  const todo = page.getByTestId('todo-item').filter({ hasText: text });
  await todo.hover();
  await todo.getByRole('button', { name: 'Delete' }).click();
});

Then('visible todos count is {int}', async ({ page }, count: number) => { 
  await expect(page.getByTestId('todo-item')).toHaveCount(count);
});
```

----------------------------------------

TITLE: Defining a Scoped Step with Tags in JavaScript
DESCRIPTION: Shows how to scope a step definition to a particular feature using the tags option. This step will only be used for features or scenarios tagged with @foo.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/scoped.md#2025-04-22_snippet_0

LANGUAGE: javascript
CODE:
```
Given('a step', { tags: '@foo' }, async () => {
  // ...
});
```

----------------------------------------

TITLE: Initializing Playwright BDD Configuration in TypeScript
DESCRIPTION: Example configuration setup for Playwright BDD in playwright.config.ts. Shows how to use defineBddConfig() to specify feature files and step definitions locations, and integrate with Playwright's configuration.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/configuration/index.md#2025-04-22_snippet_0

LANGUAGE: typescript
CODE:
```
import { defineConfig } from '@playwright/test';
import { defineBddConfig } from 'playwright-bdd';

const testDir = defineBddConfig({
  features: 'feature/*.feature',
  steps: 'steps/**/*.ts',
  // ...other playwright-bdd options
});

export default defineConfig({
  testDir,
});
```

----------------------------------------

TITLE: Skipping Tests Conditionally with Playwright-BDD in TypeScript
DESCRIPTION: This snippet demonstrates how to use the `$test` fixture in Playwright-BDD to conditionally skip tests based on the browser name. It requires Playwright and the Playwright-BDD library as dependencies. The function checks if the browser is 'firefox' and skips the test if so.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/bdd-fixtures.md#2025-04-22_snippet_0

LANGUAGE: TypeScript
CODE:
```
Given('I do something', async ({ browserName, $test }) => { 
  if (browserName === 'firefox') $test.skip();
  // ...
});
```

----------------------------------------

TITLE: Defining TypeScript Types for Context Object in Playwright BDD
DESCRIPTION: TypeScript example showing how to define types for the context object used in BDD steps. It defines a strict type for 'ctx' with a specific property type, enhancing type safety for cross-step data sharing.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/passing-data-between-steps.md#2025-04-22_snippet_3

LANGUAGE: typescript
CODE:
```
type Ctx = {
  newTapPromise: Promise<Page> 
};

export const test = base.extend<{ ctx: Ctx }>({
  ctx: async ({}, use) => {
    const ctx = {} as Ctx;
    await use(ctx);
  },
});

export const { Given, When, Then } = createBdd(test);
```

----------------------------------------

TITLE: Playwright Configuration with Environment Variables
DESCRIPTION: Configuration setup in playwright.config.ts showing how to import environment variables using dotenv package.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/env-vars.md#2025-04-22_snippet_2

LANGUAGE: typescript
CODE:
```
// playwright.config.ts

import { defineConfig, devices } from '@playwright/test';
import { defineBddConfig, cucumberReporter } from 'playwright-bdd';

import 'dotenv/config'; // <-- populate env variables from .env

const testDir = defineBddConfig({
  // ...
});

export default defineConfig({
  // ...
});
```

----------------------------------------

TITLE: Configuring Playwright-BDD with Basic Options
DESCRIPTION: This snippet demonstrates how to configure Playwright-BDD with basic options for features and steps directories.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/configuration/options.md#2025-04-22_snippet_0

LANGUAGE: javascript
CODE:
```
const testDir = defineBddConfig({
  features: './features/**/*.feature',
  steps: './features/steps/**/*.js',
  featuresRoot: './features',
});
```

----------------------------------------

TITLE: Implementing Cucumber-style Step Definition in TypeScript
DESCRIPTION: Shows how to write a step definition using Cucumber-style syntax. This method is recommended for migrating CucumberJS projects to the Playwright runner.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/index.md#2025-04-22_snippet_1

LANGUAGE: typescript
CODE:
```
Given('I open page {string}', async function (url: string) {
  await this.page.goto(url);
});
```

----------------------------------------

TITLE: Defining World Class for Cucumber-Style Steps in TypeScript
DESCRIPTION: This snippet defines a World class for Cucumber-style step definitions in Playwright-BDD. It includes a constructor that takes a Page object and a method to open the homepage.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/cucumber-style.md#2025-04-22_snippet_0

LANGUAGE: typescript
CODE:
```
// world.ts
import { Page } from '@playwright/test';

export class World {
  constructor(public page: Page) {}

  async openHomePage() {
    await this.page.goto('https://playwright.dev');
  }
}
```

----------------------------------------

TITLE: Re-using Step Functions with Fixtures in Playwright BDD
DESCRIPTION: This example demonstrates how to re-use a step function by saving the return value of When() and invoking it in other steps. It shows creating a reusable 'createTodo' step that can be called from another step with required fixtures.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/reusing-step-fn.md#2025-04-22_snippet_0

LANGUAGE: typescript
CODE:
```
import { createBdd } from 'playwright-bdd';

const { When, Then } = createBdd();

const createTodo = When('I create todo {string}', async ({ page }, text: string) => {
  await page.getByLabel('title').fill(text);
  await page.getByRole('button').click();
});

When('I create 2 todos {string} and {string}', async ({ page }, text1: string, text2: string) => {
  await createTodo({ page }, text1);
  await createTodo({ page }, text2);
});
```

----------------------------------------

TITLE: Displaying Markdown List of Playwright-BDD Features
DESCRIPTION: This markdown snippet lists the key features and benefits of using Playwright-BDD for test file generation, including IDE integration, debugging capabilities, and UI mode support.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/faq.md#2025-04-22_snippet_0

LANGUAGE: markdown
CODE:
```
  * Run a single test with [VS Code extension](guides/ide-integration.md#vs-code)
  * Debug and set breakpoints on specific BDD steps
  * Use `--ui` mode to watch changes 
  * Do everything you can with regular Playwright tests
```

----------------------------------------

TITLE: ChatGPT-Generated Gherkin Scenarios for Todo App
DESCRIPTION: This Gherkin code snippet shows the BDD scenarios generated by ChatGPT for the Todo app. It includes multiple scenarios for adding and removing todo items, demonstrating different user interactions.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/chatgpt.md#2025-04-22_snippet_2

LANGUAGE: gherkin
CODE:
```
Feature: Adding and Removing Todo Items

  As a user
  I want to add and remove todo items in a todo list app
  So that I can manage my tasks effectively

  Background:
    Given I am on todo page

  Scenario: Add a new todo and remove it
    When I add todo "Buy groceries"
    And I remove todo "Buy groceries"
    Then visible todos count is 0

  Scenario: Add multiple todos and remove one
    When I add todo "Buy groceries"
    And I add todo "Go to the gym"
    And I add todo "Read a book"
    And I remove todo "Go to the gym"
    Then visible todos count is 2

  Scenario: Add and remove multiple todos
    When I add todo "Buy groceries"
    And I add todo "Go to the gym"
    And I add todo "Read a book"
    And I remove todo "Buy groceries"
    And I remove todo "Go to the gym"
    Then visible todos count is 1

  Scenario: Add multiple todos and remove all
    When I add todo "Buy groceries"
    And I add todo "Go to the gym"
    And I add todo "Read a book"
    And I remove todo "Buy groceries"
    And I remove todo "Go to the gym"
    And I remove todo "Read a book"
    Then visible todos count is 0
```

----------------------------------------

TITLE: Configuring AI-Assisted Test Fixing in Playwright-BDD
DESCRIPTION: This snippet demonstrates how to enable AI-assisted test fixing with custom options in Playwright-BDD.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/configuration/options.md#2025-04-22_snippet_2

LANGUAGE: javascript
CODE:
```
const testDir = defineBddConfig({
  aiFix: {
    promptAttachment: true,
  },
  // ...other options
});
```

----------------------------------------

TITLE: Step Definitions Implementation
DESCRIPTION: JavaScript implementation of the BDD step definitions using Playwright APIs
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/index.md#2025-04-22_snippet_3

LANGUAGE: javascript
CODE:
```
Given('I am on Playwright home page', async ({ page }) => {
  await page.goto('https://playwright.dev');
});

When('I click link {string}', async ({ page }, name) => {
  await page.getByRole('link', { name }).click();
});

Then('I see in title {string}', async ({ page }, text) => {
  await expect(page).toHaveTitle(new RegExp(text));
});
```

----------------------------------------

TITLE: Using defineBddProject Helper for Multiple Projects
DESCRIPTION: This snippet demonstrates the use of the defineBddProject helper function to simplify configuration for multiple BDD projects. It automatically sets outputDir based on the project name.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/configuration/multiple-projects.md#2025-04-22_snippet_2

LANGUAGE: typescript
CODE:
```
import { defineConfig } from '@playwright/test';
import { defineBddProject } from 'playwright-bdd';

export default defineConfig({
  projects: [
    {
      ...defineBddProject({
        name: 'project-one',
        features: 'project-one/*.feature',
        steps: 'project-one/steps/*.ts',
      }),
    },
    {
      ...defineBddProject({
        name: 'project-two',
        features: 'project-two/*.feature',
        steps: 'project-two/steps/*.ts',
      }),
    },
  ],
});
```

----------------------------------------

TITLE: Implementing Scoped Step Definitions in Playwright-BDD v8
DESCRIPTION: Demonstrates how to scope step definitions to specific features or scenarios using tags. This allows the same step to coexist in multiple features, improving maintainability in large projects.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/blog/whats-new-in-v8.md#2025-04-22_snippet_1

LANGUAGE: typescript
CODE:
```
When('I click the PLAY button', { tags: '@game' }, async () => {
  // ...
});
```

LANGUAGE: typescript
CODE:
```
When('start playing', { tags: '@game' }, async () => { ... });
When('start playing', { tags: '@video-player' }, async () => { ... });
```

----------------------------------------

TITLE: Defining Feature with DataTable in Gherkin
DESCRIPTION: Example of a Gherkin feature file showing how to structure a login scenario using DataTable to provide test data in a tabular format.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/data-tables.md#2025-04-22_snippet_0

LANGUAGE: gherkin
CODE:
```
Feature: Some feature

    Scenario: Login
        When I fill login form with values
          | label     | value    |
          | Username  | vitalets |
          | Password  | 12345    |
```

----------------------------------------

TITLE: NPM Scripts Configuration for Playwright-BDD Watch Mode
DESCRIPTION: Package.json script configuration that sets up concurrent watching of BDD files and Playwright UI mode using npm-run-all. Includes separate commands for BDD generation and Playwright test execution.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/ui-mode.md#2025-04-22_snippet_1

LANGUAGE: json
CODE:
```
"scripts": {
  "watch:bdd": "nodemon -w ./features -w ./steps -e feature,js,ts --exec \"npx bddgen\"",
  "watch:pw": "playwright test --ui",
  "watch": "run-p watch:*"
}
```

----------------------------------------

TITLE: Simplified Configuration with featuresRoot in Playwright-BDD v8
DESCRIPTION: This snippet shows the simplified configuration introduced in Playwright-BDD v8, using featuresRoot as a common base directory for features and steps.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/configuration/options.md#2025-04-22_snippet_1

LANGUAGE: javascript
CODE:
```
const testDir = defineBddConfig({
  featuresRoot: './features',
});
```

----------------------------------------

TITLE: Using Context Object for Data Passing Between Playwright BDD Steps
DESCRIPTION: JavaScript implementation of BDD steps that demonstrates how to pass data between steps using the 'ctx' object. In the first step, a promise for a new tab is stored, and in the second step, that promise is awaited and checked.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/passing-data-between-steps.md#2025-04-22_snippet_2

LANGUAGE: javascript
CODE:
```
import { Given, When, Then } from './fixtures';

When('I click the link', async ({ page, ctx }) => {
  ctx.newTapPromise = context.waitForEvent('page');
  await page.getByRole('link').click();
});

Then('new tab is opened', async ({ ctx }) => {
  const newTab = await ctx.newTapPromise;
  await expect(newTab).toHaveTitle(/.*checkout/);
});
```

----------------------------------------

TITLE: Targeting BeforeScenario Hook with Tags
DESCRIPTION: Example of targeting a BeforeScenario hook to specific scenarios using tags in Playwright-BDD.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_11

LANGUAGE: typescript
CODE:
```
BeforeScenario({ tags: '@mobile and not @slow' }, async function () {
  // runs for scenarios with @mobile and not @slow
});

// Shortcut for passing only tags
BeforeScenario('@mobile and not @slow', async function () {
  // runs for scenarios with @mobile and not @slow
});
```

----------------------------------------

TITLE: Generated Playwright-BDD Test in JavaScript
DESCRIPTION: This snippet shows an example of a generated test file from the BDD feature. It uses the test function from playwright-bdd to describe the scenario and execute the steps.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/getting-started/write-first-test.md#2025-04-22_snippet_3

LANGUAGE: javascript
CODE:
```
// Generated from: sample.feature
import { test } from 'playwright-bdd';

test.describe('Playwright site', () => {

  test('Check get started link', async ({ Given, When, Then }) => {
    await Given('I am on home page');
    await When('I click link "Get started"');
    await Then('I see in title "Installation"');
  });

});
```

----------------------------------------

TITLE: Implementing DataTable Step Definition in TypeScript
DESCRIPTION: TypeScript implementation of a step definition that processes DataTable input. Shows how to iterate through table rows and interact with form elements using Playwright's page object.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/data-tables.md#2025-04-22_snippet_1

LANGUAGE: typescript
CODE:
```
import { createBdd, DataTable } from 'playwright-bdd';

const { Given, When, Then } = createBdd();

When('I fill login form with values', async ({ page }, data: DataTable) => {
  for (const row of data.hashes()) {
    await page.getByLabel(row.label).fill(row.value);
  }
  /*
  data.hashes() returns:
  [
    { label: 'Username', value: 'vitalets' },
    { label: 'Password', value: '12345' }
  ]
  */
});
```

----------------------------------------

TITLE: Defining and Using Custom Worker Fixture in BeforeWorker Hook
DESCRIPTION: Example of defining a custom worker fixture and using it in a BeforeWorker hook in Playwright-BDD.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_9

LANGUAGE: typescript
CODE:
```
import { test as base, createBdd } from 'playwright-bdd';

export const test = base.extend<{}, { myWorkerFixture: MyWorkerFixture }>({
  myWorkerFixture: [async ({}, use) => {
    // ... setup myWorkerFixture
  }, { scope: 'worker' }]
});

export const { BeforeWorker } = createBdd(test);

// In another file:
import { BeforeWorker } from './fixtures';

BeforeWorker(async ({ myWorkerFixture }) => {
  // ... use myWorkerFixture in hook
});
```

----------------------------------------

TITLE: Adjusting Playwright Configuration for SauceLabs
DESCRIPTION: TypeScript configuration for Playwright, including BDD setup, reporter options, and project settings for SauceLabs integration.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/usage-with-saucelabs.md#2025-04-22_snippet_3

LANGUAGE: typescript
CODE:
```
import { defineConfig, devices } from '@playwright/test';
import { defineBddConfig } from 'playwright-bdd';

const testDir = defineBddConfig({
  features: 'features/*.feature',
  steps: 'features/steps/*.ts',
});

export default defineConfig({
  testDir,
  reporter: [
    process.env.SAUCE_VM // put report into __assets__ when running on SauceLabs
      ? [ 'html', { open: 'never', outputFolder: '__assets__/html-report/', attachmentsBaseURL: './' } ]
      : [ 'html', { open: 'never' } ],
  ],
  use: {
    screenshot: 'on',
  },
  projects: [
    {
      name: 'chromium', // use project name 'chromium' as defined in '.sauce/config.yml'
      use: { ...devices['Desktop Chrome'] },
    },
  ],
});
```

----------------------------------------

TITLE: Using Custom Fixtures in Step Definitions with TypeScript
DESCRIPTION: This code snippet demonstrates how to use the custom fixtures in step definitions. It imports the Given, When, Then functions from the fixtures file and uses the custom fixture in a step definition.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/getting-started/add-fixtures.md#2025-04-22_snippet_1

LANGUAGE: typescript
CODE:
```
// steps.ts

import { Given, When, Then } from './fixtures';

Given('My step', async ({ myFixture }) => {
  // step code that uses myFixture
});
```

----------------------------------------

TITLE: Using Scenario Name as Template for Example Titles in Gherkin
DESCRIPTION: This snippet demonstrates how to use column names in the scenario name to create unique titles for each example in a Scenario Outline.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/customize-examples-title.md#2025-04-22_snippet_0

LANGUAGE: gherkin
CODE:
```
Feature: Calculator

    Scenario Outline: Multiply <value> by two
      Given value is <value>
      When multiply by two
      Then result is <result>

      Examples:
        | value | result |
        | 1     | 2      |
        | 2     | 4      |
```

----------------------------------------

TITLE: Setting Global Language in Playwright-BDD Configuration (TypeScript)
DESCRIPTION: Demonstrates how to configure the default language for all feature files using the defineBddConfig function. This example sets Spanish ('es') as the global language.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/i18n.md#2025-04-22_snippet_0

LANGUAGE: typescript
CODE:
```
import { defineBddConfig } from 'playwright-bdd';

const testDir = defineBddConfig({
  language: 'es',
  // other config
});
```

----------------------------------------

TITLE: Implementing BeforeScenario Hook in Playwright-BDD
DESCRIPTION: Example of implementing a BeforeScenario hook in Playwright-BDD with custom fixtures.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_10

LANGUAGE: typescript
CODE:
```
import { test as base, createBdd } from 'playwright-bdd';

export const test = base.extend({ /* ...your fixtures */ });

const { BeforeScenario } = createBdd(test);

BeforeScenario(async () => {
  // runs before each scenario
});
```

----------------------------------------

TITLE: Using Shared Context in Step Definitions for Playwright-BDD
DESCRIPTION: TypeScript implementation of step definitions that utilize the shared context. These steps demonstrate how to create a page in one scenario and then use it in subsequent scenarios within the same feature file.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/passing-data-between-scenarios.md#2025-04-22_snippet_2

LANGUAGE: typescript
CODE:
```
import { Given, When, Then } from "./fixtures";

Given("I am logged in as {string}", async ({ ctx, browser }, user: string) => {
  ctx.page = await browser.newPage();
  // ...perform login for user
});

When("I open profile page", async ({ ctx }) => {
  await ctx.page.getByRole("link", { name: "Profile" }).click();
});

Then("I see name {string}", async ({ ctx }, user: string) => {
  await expect(ctx.page.getByRole("header")).toContainText(user);
});
```

----------------------------------------

TITLE: Accessing Step Details Using Playwright-BDD in TypeScript
DESCRIPTION: This code snippet shows how to access and use the current step's title using the `$step` fixture. Useful for conditional logic based on the step's text, the snippet logs the received step title for further actions. Requires Playwright and Playwright-BDD.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/bdd-fixtures.md#2025-04-22_snippet_1

LANGUAGE: TypeScript
CODE:
```
Given('I open url {string}', async ({ $step }, url: string) => { 
  console.log($step.title); // I open url "https://playwright.dev"
  // ...
});
```

----------------------------------------

TITLE: Configuring Allure Reporter in Playwright Config
DESCRIPTION: Configuration setup for enabling Allure reporter in Playwright tests with BDD integration. Uses defineConfig from Playwright and defineBddConfig from playwright-bdd to set up the test directory and enable the allure-playwright reporter.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/reporters/allure.md#2025-04-22_snippet_0

LANGUAGE: javascript
CODE:
```
import { defineConfig } from '@playwright/test';
import { defineBddConfig } from 'playwright-bdd';

const testDir = defineBddConfig({ /* BDD config */ });

export default defineConfig({
  testDir,
  reporter: 'allure-playwright', // <- enable allure reporter
});
```

----------------------------------------

TITLE: Implementing BeforeWorker Hook in Playwright-BDD
DESCRIPTION: Example of implementing a BeforeWorker hook in Playwright-BDD with custom fixtures.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_4

LANGUAGE: typescript
CODE:
```
import { test as base, createBdd } from 'playwright-bdd';

export const test = base.extend({ /* ...your fixtures */ });

const { BeforeWorker } = createBdd(test);

BeforeWorker(async ({ $workerInfo, browser }) => {
  // runs when each worker starts
});
```

----------------------------------------

TITLE: Using BeforeStep Hook in Playwright-BDD - TypeScript
DESCRIPTION: This snippet demonstrates how to implement the BeforeStep method provided by Playwright-BDD, which executes pre-defined code before each test step. It includes options for tagging steps to modify behavior based on test conditions.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_13

LANGUAGE: typescript
CODE:
```
import { test as base, createBdd } from 'playwright-bdd';

export const test = base.extend({ /* ...your fixtures */ });

const { BeforeStep } = createBdd(test);

BeforeStep(async () => {
  // runs before each step
});
```

LANGUAGE: typescript
CODE:
```
import { createBdd } from 'playwright-bdd';

const { BeforeStep } = createBdd();
```

LANGUAGE: typescript
CODE:
```
BeforeStep({ tags: '@mobile and not @slow' }, async function () {
  // runs for scenarios with @mobile and not @slow
});
```

LANGUAGE: typescript
CODE:
```
BeforeStep('@mobile and not @slow', async function () {
  // runs for scenarios with @mobile and not @slow
});
```

LANGUAGE: typescript
CODE:
```
const { BeforeStep } = createBdd(test, { tags: '@mobile' });

BeforeStep(async () => {
  // runs only for scenarios with @mobile 
});
```

LANGUAGE: typescript
CODE:
```
const { BeforeStep } = createBdd(test, { tags: '@mobile' });

BeforeStep({ tags: '@slow' }, async function () {
  // runs for scenarios with @mobile and @slow
});
```

LANGUAGE: typescript
CODE:
```
BeforeStep({ name: 'my hook', timeout: 5000 }, async function () {
  // ...
});
```

----------------------------------------

TITLE: Checking Element Visibility with Conditional Logic in TypeScript
DESCRIPTION: This code snippet expands on the `$step` fixture to conditionally check if an element should or should not be visible based on the step title. It requires Playwright for navigating and managing page elements.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/bdd-fixtures.md#2025-04-22_snippet_2

LANGUAGE: TypeScript
CODE:
```
Then('element with text {string} should( not) be displayed', async ({ page, $step }, text: string) => {
  const negate = /should not/.test($step.title);
  if (negate) {
    await expect(page.getByText(text)).toBeHidden();
  } else {
    await expect(page.getByText(text)).toBeVisible();
  }
});
```

----------------------------------------

TITLE: Configuring Multiple Projects with HTML Reporter in Playwright-BDD
DESCRIPTION: Example configuration showing how to set up multiple browser projects with HTML reporting in Playwright-BDD. Includes project configuration for Chrome and Firefox browsers.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/reporters/cucumber.md#2025-04-22_snippet_0

LANGUAGE: typescript
CODE:
```
import { defineConfig, devices } from '@playwright/test';
import { defineBddConfig, cucumberReporter } from 'playwright-bdd';

const testDir = defineBddConfig({
  features: 'features/*.feature',
  steps: 'features/steps/*.ts',
});

export default defineConfig({
  testDir,
  reporter: [ 
    cucumberReporter('html', { outputFile: 'cucumber-report/index.html' })
  ],
  projects: [
    {
      name: 'chromium',
      use: { ...devices['Desktop Chrome'] },
    },
    {
      name: 'firefox',
      use: { ...devices['Desktop Firefox'] },
    },
  ],
});
```

----------------------------------------

TITLE: Enabling Fix with AI in Playwright-BDD Configuration
DESCRIPTION: This snippet shows how to enable the Fix with AI feature in the Playwright-BDD configuration. It adds the aiFix section to the BDD config object.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/fix-with-ai.md#2025-04-22_snippet_0

LANGUAGE: javascript
CODE:
```
const testDir = defineBddConfig({
  aiFix: {
    promptAttachment: true,
  },
  // ...other options
});
```

----------------------------------------

TITLE: Using AfterStep Hook in Playwright-BDD - TypeScript
DESCRIPTION: This snippet shows how to implement the AfterStep method from Playwright-BDD, which runs after each test step. It includes an example of capturing screenshots post-execution of each step.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_14

LANGUAGE: typescript
CODE:
```
import { test as base, createBdd } from 'playwright-bdd';

export const test = base.extend({ /* ...your fixtures */ });

const { AfterStep } = createBdd(test);

AfterStep(async () => {
  // runs after each scenario
});
```

LANGUAGE: typescript
CODE:
```
export const { AfterStep } = createBdd(test);
```

LANGUAGE: typescript
CODE:
```
import { AfterStep } from './fixtures';

AfterStep(async ({ page, $testInfo, $step }) => {
  await $testInfo.attach(`screenshot after ${$step.title}`, {
    contentType: 'image/png',
    body: await page.screenshot()
  });
});
```

----------------------------------------

TITLE: Implementing Before and After Hooks in Cucumber
DESCRIPTION: Example of implementing Before and After hooks in Cucumber for handling authentication.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_1

LANGUAGE: typescript
CODE:
```
Before({ tags: '@auth' }, async function () {
  // do sign-in
});

After({ tags: '@auth' }, async function () {
  // do sign-out
});
```

----------------------------------------

TITLE: Using Non-Default Page for ARIA Snapshot in Playwright-BDD Tests
DESCRIPTION: This snippet illustrates how to manually set the page instance for capturing ARIA snapshots in multi-page scenarios. It uses the $prompt BDD fixture to switch the page for the AI prompt.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/fix-with-ai.md#2025-04-22_snippet_2

LANGUAGE: javascript
CODE:
```
When('I open a new tab', async ({ page, context, $prompt }) => { // <-- add $prompt fixture
  const [newPage] = await Promise.all([
    context.waitForEvent('page'),
    page.getByRole('link').click(),
  ]);
  $prompt.setPage(newPage); // <-- call $prompt.setPage() to switch the page
  await expect(newPage.getByRole('heading')).toContainText('Another page');
});
```

----------------------------------------

TITLE: Setting Locale for Tests Using Playwright-BDD in TypeScript
DESCRIPTION: Illustrates how to use a custom fixture to set a specific locale (`fi`) if a `@LocaleFi` tag is present in the test tags. Dependencies include Playwright-BDD, and additional setup may be needed for locale settings.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/bdd-fixtures.md#2025-04-22_snippet_5

LANGUAGE: TypeScript
CODE:
```
import { test as base } from 'playwright-bdd';

export const test = base.extend({
  locale: async ({ $tags, locale }, use) => {
    if ($tags.includes('@LocaleFi')) {
      locale = 'fi';
    }
    await use(locale);
  },
});
```

----------------------------------------

TITLE: Creating a Context Fixture for Cross-Step Data Sharing in Playwright BDD
DESCRIPTION: JavaScript code that extends Playwright test with a custom 'ctx' fixture that acts as a container for cross-step data. This creates a context that persists between steps in a scenario, similar to Cucumber's 'world' concept.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/passing-data-between-steps.md#2025-04-22_snippet_1

LANGUAGE: javascript
CODE:
```
import { test as base, createBdd } from 'playwright-bdd';

export const test = base.extend({
  ctx: async ({}, use) => {
    const ctx = {};
    await use(ctx);
  },
});

export const { Given, When, Then } = createBdd(test);
```

----------------------------------------

TITLE: Configuring Tagged BeforeAll and AfterAll Hooks in Playwright-BDD v8
DESCRIPTION: Shows how to use the new 'name' and 'tags' options for BeforeAll and AfterAll hooks. These tagged hooks will only execute if the corresponding feature is executed, running in each worker similar to Playwright worker hooks.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/blog/whats-new-in-v8.md#2025-04-22_snippet_2

LANGUAGE: typescript
CODE:
```
BeforeAll({ name: 'populate db', tags: '@game' }, async () => {
  // worker setup for game
});

AfterAll({ name: 'cleanup db', tags: '@game' }, async () => {
  // worker teardown for game
});
```

----------------------------------------

TITLE: Binding POM Class with Fixture using TypeScript Decorator
DESCRIPTION: Example showing how to use the @Fixture decorator to bind a Page Object Model class with a fixture name. The example includes type safety by using generic parameter to restrict fixture names to available ones.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/api.md#2025-04-22_snippet_2

LANGUAGE: typescript
CODE:
```
import { Fixture } from 'playwright-bdd/decorators';
import type { test } from './fixtures';

export
@Fixture<typeof test>('todoPage')
class TodoPage { ... };
```

----------------------------------------

TITLE: AI Prompt Template for Playwright-BDD Test Fixing
DESCRIPTION: This markdown code block contains the default AI prompt template used by Playwright-BDD for generating fix suggestions. It includes instructions for the AI and placeholders for test-specific information.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/fix-with-ai.md#2025-04-22_snippet_3

LANGUAGE: markdown
CODE:
```
You are an expert in Playwright BDD testing.
Fix the error in the BDD scenario.

- Provide response as a diff highlighted code snippet.
- First, try to fix the test by adjusting Gherkin steps parameters.
- If the test is not fixable by Gherkin, try to modify the code snippet.
- Strictly rely on the ARIA snapshot of the page.
- Avoid adding any new code.
- Avoid adding comments to the code.
- Avoid changing the test logic.
- Use only role-based locators: getByRole, getByLabel, etc.
- Add a concise note about applied changes.
- If the test may be correct and there is a bug in the page, note it.

Failing gherkin scenario: 

Scenario: {scenarioName}
{steps}

Error details:
{error}

{snippet}

ARIA snapshot of the page:

{ariaSnapshot}
```

----------------------------------------

TITLE: Implementing Context Sharing Between Scenarios with Playwright Fixtures
DESCRIPTION: TypeScript implementation that creates test fixtures to enable context sharing. It defines a file-scoped ctx fixture and a worker-scoped ctxMap fixture that maintains context across scenarios within the same feature file.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/passing-data-between-scenarios.md#2025-04-22_snippet_1

LANGUAGE: typescript
CODE:
```
import { test as base, createBdd } from 'playwright-bdd';

// context shared between scenarios in a file
type Ctx = { page: Page };

export const test = base.extend<{ ctx: Ctx }, { ctxMap: Record<string, Ctx> }>({
  ctx: async ({ ctxMap }, use, testInfo) => {
    // get or init a context for the current file
    ctxMap[testInfo.file] = ctxMap[testInfo.file] || {};
    // pass context to scenarios as a `ctx` fixture
    await use(ctxMap[testInfo.file]);
  },
  ctxMap: [async ({}, use) => {
    const ctxMap: Record<string, Ctx> = {};
    await use(ctxMap);
    // cleanup all contexts on worker teardown
    for (const ctx of Object.values(ctxMap)) await ctx.page?.close();
  }, { scope: 'worker' }],
});

export const { Given, When, Then } = createBdd(test);
```

----------------------------------------

TITLE: Cucumber-Style Data Passing Using 'this' Context in Playwright BDD
DESCRIPTION: JavaScript implementation of steps using the Cucumber-style approach, where 'this' is used to store and retrieve data between steps. This approach is an alternative to the fixture-based 'ctx' method.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/passing-data-between-steps.md#2025-04-22_snippet_4

LANGUAGE: javascript
CODE:
```
import { Given, When, Then } from './fixtures';

When('I click the link', async function () {
  this.newTapPromise = this.context.waitForEvent('page');
  await this.page.getByRole('link').click();
});

Then('new tab is opened', async function () {
  const newTab = await this.newTapPromise;
  await expect(newTab).toHaveTitle(/.*checkout/);
});
```

----------------------------------------

TITLE: Using @skip/@fixme Tags in Playwright BDD Tests
DESCRIPTION: Shows how to use @skip or @fixme tags to exclude specific features or scenarios from test execution. These tags are useful when tests are temporarily broken or under development.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/special-tags.md#2025-04-22_snippet_1

LANGUAGE: gherkin
CODE:
```
@skip
Feature: Playwright site

    @skip
    Scenario: Check title
        Given I open url "https://playwright.dev"
```

----------------------------------------

TITLE: Writing Gherkin Feature Files in Playwright-BDD
DESCRIPTION: A sample Gherkin feature file that defines a test scenario for checking the Playwright website title. The scenario includes three steps: opening a URL, clicking a link, and verifying text in the page title.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/snippets.md#2025-04-22_snippet_0

LANGUAGE: gherkin
CODE:
```
Feature: Playwright site

    Scenario: Check title
        Given I open url "https://playwright.dev"
        When I click link "Get started"
        Then I see in title "Playwright"
```

----------------------------------------

TITLE: Using Feature-Level @timeout Tag in Playwright BDD Tests
DESCRIPTION: Shows how to set timeouts at the feature level, which applies to all scenarios within the feature. Each scenario gets the specified timeout value.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/special-tags.md#2025-04-22_snippet_5

LANGUAGE: gherkin
CODE:
```
@timeout:5000
Feature: Playwright site
    
    Scenario: Check title
        Given I open url "https://playwright.dev"

    Scenario: Check navigation
        Given I open url "https://playwright.dev"
```

----------------------------------------

TITLE: Re-using Cucumber-style Step Functions with World Context
DESCRIPTION: This example shows how to re-use step functions in Cucumber-style steps by invoking the step function via .call() to pass the actual World context. This preserves the 'this' context when calling the reusable step.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/reusing-step-fn.md#2025-04-22_snippet_1

LANGUAGE: javascript
CODE:
```
const createTodo = When('I create todo {string}', async function (text: string) {
  await this.page.getByLabel('title').fill(text);
  await this.page.getByRole('button').click();
});

When('I create 2 todos {string} and {string}', async function (text1: string, text2: string) {
  await createTodo.call(this, text1);
  await createTodo.call(this, text2);
});
```

----------------------------------------

TITLE: Using @timeout Tag in Playwright BDD Tests
DESCRIPTION: Demonstrates setting custom timeouts for scenarios using the @timeout:N tag. When applied to a feature, it sets the timeout for each scenario within that feature.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/special-tags.md#2025-04-22_snippet_4

LANGUAGE: gherkin
CODE:
```
Feature: Playwright site
    
    @timeout:5000
    Scenario: Check title
        Given I open url "https://playwright.dev"
```

----------------------------------------

TITLE: Configuring Playwright-BDD with Shared Feature Files
DESCRIPTION: This snippet demonstrates how to set up Playwright-BDD configuration for multiple projects that use the same set of feature files. It defines a single testDir at the root level of the config.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/configuration/multiple-projects.md#2025-04-22_snippet_0

LANGUAGE: typescript
CODE:
```
import { defineConfig, devices } from '@playwright/test';
import { defineBddConfig } from 'playwright-bdd';

const testDir = defineBddConfig({
  features: 'feature/*.feature',
  steps: 'steps/**/*.ts',
});

export default defineConfig({
  testDir,
  projects: [
    {
      name: 'chromium',
      use: { ...devices['Desktop Chrome'] },
    },
    {
      name: 'firefox',
      use: { ...devices['Desktop Firefox'] },
    },
  ],
});
```

----------------------------------------

TITLE: Package.json Script Update for Environment Variables
DESCRIPTION: Example showing how to update package.json scripts to properly handle environment variables.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/env-vars.md#2025-04-22_snippet_4

LANGUAGE: javascript
CODE:
```
"scripts": {
   "test": "npx bddgen && npx playwright test",
},
```

----------------------------------------

TITLE: Defining and Using Custom Fixture in BeforeScenario Hook
DESCRIPTION: Example of defining a custom fixture and using it in a BeforeScenario hook in Playwright-BDD.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_12

LANGUAGE: typescript
CODE:
```
import { test as base, createBdd } from 'playwright-bdd';

export const test = base.extend<{ myFixture: MyFixture }>({
  myFixture: async ({ page }, use) => {
    // ... setup myFixture
  }
});

export const { BeforeScenario } = createBdd(test);

// In another file:
import { BeforeScenario } from './fixtures';

BeforeScenario(async ({ myFixture }) => {
  // ... use myFixture in the hook
});
```

----------------------------------------

TITLE: Using Special Comment Syntax for Example Titles in Gherkin
DESCRIPTION: This snippet shows how to use a special comment syntax to provide a custom title format for examples in a Scenario Outline.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/customize-examples-title.md#2025-04-22_snippet_2

LANGUAGE: gherkin
CODE:
```
Feature: Calculator

    Scenario Outline: Multiply by two
      Given value is <value>
      When multiply by two
      Then result is <result>

      # title-format: check <value>
      Examples:
        | value | result |
        | 1     | 2      |
        | 2     | 4      |
```

----------------------------------------

TITLE: Using @mode Tag for Parallel Execution in Playwright BDD Tests
DESCRIPTION: Demonstrates using @mode:parallel tag to configure parallel execution of scenarios within a feature. This allows multiple scenarios to run simultaneously in separate workers.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/special-tags.md#2025-04-22_snippet_8

LANGUAGE: gherkin
CODE:
```
@mode:parallel
Feature: Playwright site
    
    Scenario: Scenario 1
        Given I open url "https://playwright.dev"

    Scenario: Scenario 2
        Given I open url "https://playwright.dev"
```

----------------------------------------

TITLE: Configuring Playwright-BDD with Different Feature Files
DESCRIPTION: This snippet shows how to configure Playwright-BDD for projects using different feature files. It defines a separate testDir for each project and sets unique outputDir to avoid conflicts.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/configuration/multiple-projects.md#2025-04-22_snippet_1

LANGUAGE: typescript
CODE:
```
import { defineConfig } from '@playwright/test';
import { defineBddConfig } from 'playwright-bdd';

export default defineConfig({
  projects: [
    {
      name: 'project-one',
      testDir: defineBddConfig({
        outputDir: '.features-gen/one',
        features: 'project-one/*.feature',
        steps: 'project-one/steps/*.ts',
      }),
    },
    {
      name: 'project-two',
      testDir: defineBddConfig({
        outputDir: '.features-gen/two',
        features: 'project-two/*.feature',
        steps: 'project-two/steps/*.ts',
      }),
    },
  ],
});
```

----------------------------------------

TITLE: Configuring Cucumber Reporter in Playwright Config
DESCRIPTION: Example of using cucumberReporter to set up HTML reporting for Playwright-BDD tests in the Playwright configuration file.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/api.md#2025-04-22_snippet_1

LANGUAGE: typescript
CODE:
```
import { cucumberReporter } from 'playwright-bdd';

export default defineConfig({
  reporter: [
    cucumberReporter('html', { outputFile: `reports/report.html` }),
  ],
  // ...other options
});
```

----------------------------------------

TITLE: Creating BDD with Default Tags for Video Player in TypeScript
DESCRIPTION: Shows how to create BDD functions with default tags for all step definitions in a file, scoping them to @video-player.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/scoped.md#2025-04-22_snippet_10

LANGUAGE: typescript
CODE:
```
// video-player.steps.ts
const { Given, When, Then } = createBdd(test, { tags: '@video-player' });

When('I click the PLAY button', async () => {
  // actions for video-player.feature
});
```

----------------------------------------

TITLE: Setting missingSteps Option in Playwright-BDD v8
DESCRIPTION: Demonstrates how to use the new missingSteps option to control behavior when step definitions are missing. Options include failing on generation, failing on run, or skipping the scenario.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/blog/whats-new-in-v8.md#2025-04-22_snippet_5

LANGUAGE: typescript
CODE:
```
const testDir = defineBddConfig({
  missingSteps: 'skip-scenario',
  // ...
});
```

----------------------------------------

TITLE: Configuring Playwright HTML Reporter with BDD
DESCRIPTION: Example configuration for enabling Playwright's HTML reporter in a BDD-oriented test setup. This code shows how to use defineBddConfig from playwright-bdd alongside standard Playwright configuration.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/reporters/playwright.md#2025-04-22_snippet_0

LANGUAGE: javascript
CODE:
```
import { defineConfig } from '@playwright/test';
import { defineBddConfig } from 'playwright-bdd';

const testDir = defineBddConfig({ /* BDD config */ });

export default defineConfig({
  testDir,
  reporter: 'html', // <- define reporter as usual
});
```

----------------------------------------

TITLE: Using cross-env for Environment Variables
DESCRIPTION: Alternative approach using cross-env package to set environment variables for the entire command.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/env-vars.md#2025-04-22_snippet_6

LANGUAGE: shell
CODE:
```
npx cross-env-shell USERNAME=foo "npx bddgen && npx playwright test"
```

----------------------------------------

TITLE: Extending Playwright Test with World Fixture in TypeScript
DESCRIPTION: This code extends the Playwright test with a World fixture and creates Given/When/Then functions for step definitions. It uses the previously defined World class.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/cucumber-style.md#2025-04-22_snippet_1

LANGUAGE: typescript
CODE:
```
// fixtures.ts
import { test as base } from 'playwright-bdd';
import { World } from './world';

export const test = base.extend<{ world: World }>({
  world: async ({ page }, use) => {
    const world = new World(page);
    await use(world);
  },
});

export const { Given, When, Then, Before, After } = createBdd(test, { 
  worldFixture: 'world' 
});
```

----------------------------------------

TITLE: Using Feature-Level @retries Tag in Playwright BDD Tests
DESCRIPTION: Demonstrates setting retry attempts for all scenarios in a feature using the @retries:N tag. This helps handle flaky tests at the feature level.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/special-tags.md#2025-04-22_snippet_6

LANGUAGE: gherkin
CODE:
```
@retries:2
Feature: Playwright site
    
    Scenario: Check title
        Given I open url "https://playwright.dev"
```

----------------------------------------

TITLE: Customizing AI Prompt Template in Playwright-BDD Configuration
DESCRIPTION: This code demonstrates how to customize the AI prompt template in the Playwright-BDD configuration. It allows users to define their own prompt template for better results specific to their project.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/fix-with-ai.md#2025-04-22_snippet_1

LANGUAGE: javascript
CODE:
```
const testDir = defineBddConfig({
  aiFix: {
    promptAttachment: true,
    promptTemplate: 'my custom prompt'
  },
  // ...other options
});
```

----------------------------------------

TITLE: Configuring Playwright for Sharded Test Execution
DESCRIPTION: This TypeScript snippet demonstrates how to configure Playwright-BDD in `playwright.config.ts` for running and merging reports from test shards. Dependencies include `playwright/test`, `playwright-bdd`, and their supporting functions like `defineConfig`, `defineBddConfig`, and `cucumberReporter`. Key parameters include `testDir`, indicating where feature and step files are located, and `reporter` for distinguishing report types based on run context. No other limitations are noted.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/reporters/cucumber.md#2025-04-22_snippet_8

LANGUAGE: TypeScript
CODE:
```
import { defineConfig } from '@playwright/test';
import { defineBddConfig, cucumberReporter } from 'playwright-bdd';

const testDir = defineBddConfig({
  features: 'features/*.feature',
  steps: 'features/*.ts',
});

// Distinguish shard runs from regular local runs and merge-reports run
const isShardRun = process.argv.some((a) => a.startsWith('--shard'));

export default defineConfig({
  testDir,
  reporter: isShardRun
    ? 'blob' // on shard output Blob report
    : [ cucumberReporter('html', { outputFile: 'report.html' }) ],
});
```

----------------------------------------

TITLE: Implementing Custom Fixtures in Cucumber-Style World
DESCRIPTION: This code shows how to implement custom fixtures in a Cucumber-style World object. It extends the test with a custom fixture and includes it in the World object.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/cucumber-style.md#2025-04-22_snippet_3

LANGUAGE: typescript
CODE:
```
// fixtures.ts
import { test as base } from 'playwright-bdd';

type World = {
  page: Page;
  myFixture: MyFixture; // <- custom fixture property
};

export const test = base.extend<{ world: World }>({
  myFixture: async ({}, use) => {
    // setup myFixture...
  },
  world: async ({ page, myFixture }, use) => {
    const world: World = { page, myFixture };
    await use(world);
  },
});

export const { Given, When, Then, Before, After } = createBdd(test, { 
  worldFixture: 'world' 
});
```

----------------------------------------

TITLE: Using Scenario-Level @retries Tag in Playwright BDD Tests
DESCRIPTION: Shows how to set retry attempts for individual scenarios using the @retries:N tag. This allows fine-grained control over retry behavior.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/special-tags.md#2025-04-22_snippet_7

LANGUAGE: gherkin
CODE:
```
Feature: Playwright site
    
    @retries:2
    Scenario: Check title
        Given I open url "https://playwright.dev"
```

----------------------------------------

TITLE: Setting Language for Individual Feature File (Gherkin)
DESCRIPTION: Shows how to specify the language for a specific feature file using the language directive. The example demonstrates writing a feature file in Spanish with basic test scenarios.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/i18n.md#2025-04-22_snippet_1

LANGUAGE: gherkin
CODE:
```
# language: es
Característica: Sitio de Playwright

    Escenario: Verificar título
        Dado que abro la url "https://playwright.dev"
        Cuando hago clic en el enlace "Get started"
        Entonces veo en el título "Playwright"
```

----------------------------------------

TITLE: Switching to Mobile Viewport Based on Test Tags in TypeScript
DESCRIPTION: This snippet details how to modify the viewport dimensions if a test includes the `@mobile` tag, switching to a mobile-sized viewport. It's implemented with Playwright-BDD, requiring knowledge of viewport configuration.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/bdd-fixtures.md#2025-04-22_snippet_6

LANGUAGE: TypeScript
CODE:
```
import { test as base } from 'playwright-bdd';

export const test = base.extend({
  viewport: async ({ $tags, viewport }, use) => {
    if ($tags.includes('@mobile')) {
      viewport = { width: 375, height: 667 };
    }
    await use(viewport);
  }
});
```

----------------------------------------

TITLE: Custom Reporter Configuration in Playwright-BDD
DESCRIPTION: Configuration for using a custom reporter implementation in Playwright-BDD.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/reporters/cucumber.md#2025-04-22_snippet_7

LANGUAGE: javascript
CODE:
```
import { defineConfig } from '@playwright/test';
import { defineBddConfig, cucumberReporter } from 'playwright-bdd';

const testDir = defineBddConfig({
  features: 'features/*.feature',
  steps: 'steps/*.ts',
});

export default defineConfig({
  testDir,
  reporter: [
    cucumberReporter('./my-reporter.ts', { someKey: 'someValue' }), 
  ],
});
```

----------------------------------------

TITLE: Configuring VS Code settings for Cucumber (Gherkin) Full Support extension
DESCRIPTION: This JSON configuration enables autocompletion of steps and go-to-definition functionality in feature files when using the Cucumber (Gherkin) Full Support extension in VS Code.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/ide-integration.md#2025-04-22_snippet_0

LANGUAGE: json
CODE:
```
{
  "cucumberautocomplete.steps": ["features/steps/*.{ts,js}"],
  "cucumberautocomplete.strictGherkinCompletion": false,
  "cucumberautocomplete.strictGherkinValidation": false,
  "cucumberautocomplete.smartSnippets": true,
  "cucumberautocomplete.onTypeFormat": true,
  "editor.quickSuggestions": {
    "comments": false,
    "strings": true,
    "other": true
  },
}
```

----------------------------------------

TITLE: Tagged Video Player Feature in Gherkin
DESCRIPTION: A Gherkin feature file for a video player that is tagged with @video-player to match the scope of the corresponding step definition.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/scoped.md#2025-04-22_snippet_8

LANGUAGE: gherkin
CODE:
```
@video-player
Feature: Video player

  Scenario: Start playing
    ... 
    When I click the PLAY button
```

----------------------------------------

TITLE: Defining Step Definition with Given Keyword in JavaScript
DESCRIPTION: A JavaScript example of a step definition using the Given keyword. By default, this definition matches steps with any keyword (Given, When, or Then).
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/keywords-matching.md#2025-04-22_snippet_0

LANGUAGE: js
CODE:
```
Given('a step', () => { ... });
```

----------------------------------------

TITLE: Targeting BeforeWorker Hook with Tags
DESCRIPTION: Example of targeting a BeforeWorker hook to specific features using tags in Playwright-BDD.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_6

LANGUAGE: typescript
CODE:
```
BeforeWorker({ tags: '@auth' }, async () => { ... });
```

----------------------------------------

TITLE: JUnit Reporter Configuration in Playwright-BDD
DESCRIPTION: Configuration for JUnit XML reporting format with suite name specification.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/reporters/cucumber.md#2025-04-22_snippet_4

LANGUAGE: javascript
CODE:
```
import { defineConfig } from '@playwright/test';
import { defineBddConfig, cucumberReporter } from 'playwright-bdd';

const testDir = defineBddConfig({
  features: ['features/*.feature'],
  steps: ['steps/*.ts'],
});

export default defineConfig({
  testDir,
  reporter: [
    cucumberReporter('junit', { 
      outputFile: 'cucumber-report/report.xml',
      suiteName: 'my suite'
    }), 
  ],
});
```

----------------------------------------

TITLE: Logging Test Tags with Playwright-BDD in TypeScript
DESCRIPTION: This snippet involves using the `$tags` fixture to log test tags during execution. This can be utilized to alter test behavior based on specified tags. Requires Playwright-BDD and no additional dependencies.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/bdd-fixtures.md#2025-04-22_snippet_3

LANGUAGE: TypeScript
CODE:
```
Given('I do something', async ({ $tags }) => {
  console.log($tags); // outputs ["@slow", "@jira:123"]
});
```

----------------------------------------

TITLE: Feature Definition for Video Player in Gherkin
DESCRIPTION: A sample Gherkin feature file for a video player that includes a step for clicking the PLAY button, similar to the game feature.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/scoped.md#2025-04-22_snippet_2

LANGUAGE: gherkin
CODE:
```
Feature: Video player

  Scenario: Start playing
    ... 
    When I click the PLAY button
```

----------------------------------------

TITLE: Defining Feature and Scenario in Gherkin for BDD Testing
DESCRIPTION: A Gherkin feature file example that defines a scenario for checking a link that opens a new tab. The scenario includes a 'When' step for clicking a link and a 'Then' step for verifying a new tab opens.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/passing-data-between-steps.md#2025-04-22_snippet_0

LANGUAGE: gherkin
CODE:
```
Feature: home page

  Scenario: check link
    When I click the link
    Then new tab is opened
```

----------------------------------------

TITLE: Create Test Fixtures Configuration
DESCRIPTION: Setup of test fixtures by merging Playwright component test and BDD test configurations
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/component-tests.md#2025-04-22_snippet_2

LANGUAGE: typescript
CODE:
```
import { mergeTests } from '@playwright/test';
import { test as ctBase } from '@playwright/experimental-ct-react';
import { test as base } from 'playwright-bdd';

export const test = mergeTests(base, ctBase);
```

----------------------------------------

TITLE: Message Reporter Configuration in Playwright-BDD
DESCRIPTION: Setup for Cucumber Message format reporting with NDJSON output.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/reporters/cucumber.md#2025-04-22_snippet_5

LANGUAGE: javascript
CODE:
```
import { defineConfig } from '@playwright/test';
import { defineBddConfig, cucumberReporter } from 'playwright-bdd';

const testDir = defineBddConfig({
  features: ['features/*.feature'],
  steps: ['steps/*.ts'],
});

export default defineConfig({
  testDir,
  reporter: [
    cucumberReporter('message', { outputFile: 'cucumber-report/report.ndjson' }), 
  ],
});
```

----------------------------------------

TITLE: Setting Environment Variables with cross-env-shell
DESCRIPTION: Command demonstrating how to set environment variables and run Playwright tests using cross-env-shell. Sets GREETING variable and executes bddgen and playwright test commands
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/env-variables.md#2025-04-22_snippet_1

LANGUAGE: shell
CODE:
```
npx cross-env-shell GREETING=hello "npx bddgen && npx playwright test"
```

----------------------------------------

TITLE: Configuring matchKeywords Option in Playwright Config
DESCRIPTION: Configuration example for enabling strict keyword matching in Playwright-BDD. This sets the matchKeywords option to true, which makes step definitions match only steps with the corresponding keyword.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/keywords-matching.md#2025-04-22_snippet_2

LANGUAGE: js
CODE:
```
// playwright.config.js
import { defineConfig } from '@playwright/test';
import { defineBddConfig } from 'playwright-bdd';

const testDir = defineBddConfig({
  matchKeywords: true,
  // ...
});

export default defineConfig({
  testDir,
});
```

----------------------------------------

TITLE: Defining Serial Mode Feature with Related Scenarios in Gherkin
DESCRIPTION: A Gherkin feature file example that demonstrates how to use the @mode:serial tag to share context between scenarios. The first scenario handles authentication while the second uses the same context to perform checks.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/passing-data-between-scenarios.md#2025-04-22_snippet_0

LANGUAGE: gherkin
CODE:
```
@mode:serial
Feature: My feature

  Scenario: Authenticate
    Given I am logged in as "user1"

  Scenario: Check profile
    # still in the same page with the same context!
    When I open profile page
    Then I see name "user1"
```

----------------------------------------

TITLE: Define BDD Test Steps
DESCRIPTION: Implementation of Given/When/Then step definitions for component testing using React and Playwright
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/component-tests.md#2025-04-22_snippet_3

LANGUAGE: typescript
CODE:
```
import React from 'react';
import { expect } from '@playwright/test';
import { createBdd } from 'playwright-bdd';
import { test } from './fixtures';

const { Given, When, Then } = createBdd(test);

Given('Mounted input component', async ({ mount }) => {
  await mount(<textarea data-testid="textField" />);
});

When('I type {string}', async ({ page }, arg: string) => {
  await page.getByTestId('textField').fill(arg);
});

Then('input field has {string}', async ({ page }, arg: string) => {
  await expect(page.getByTestId('textField')).toHaveValue(arg);
});
```

----------------------------------------

TITLE: Auto-generated Step Definition Snippets in Playwright-BDD
DESCRIPTION: Output showing auto-generated JavaScript step definition snippets for missing steps. Each snippet includes the step pattern, function signature, and comments showing the original step and its location in the feature file.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/snippets.md#2025-04-22_snippet_2

LANGUAGE: javascript
CODE:
```
Missing step definitions: 3

Given('I open url {string}', async ({}, arg) => {
  // Step: Given I open url "https://playwright.dev"
  // From: features/homepage.feature:4:5
});

When('I click link {string}', async ({}, arg) => {
  // Step: When I click link "Get started"
  // From: features/homepage.feature:5:5
});

Then('I see in title {string}', async ({}, arg) => {
  // Step: Then I see in title "Playwright"
  // From: features/homepage.feature:6:5
});

Use the snippets above to create missing steps.
```

----------------------------------------

TITLE: Sample BDD Feature File
DESCRIPTION: Example of a Gherkin feature file defining a test scenario for the Playwright homepage
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/index.md#2025-04-22_snippet_1

LANGUAGE: gherkin
CODE:
```
Feature: Playwright Home Page

    Scenario: Check title
        Given I am on Playwright home page
        When I click link "Get started"
        Then I see in title "Installation"
```

----------------------------------------

TITLE: Defining a Gherkin Scenario with Authentication Tag
DESCRIPTION: Example of a Gherkin scenario with an @auth tag for user authorization.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_0

LANGUAGE: gherkin
CODE:
```
Feature: Some feature

    @auth
    Scenario: Some scenario
        Given I am an authorized user
```

----------------------------------------

TITLE: Creating an Auth Fixture in Playwright
DESCRIPTION: Example of creating an auth fixture in Playwright for handling user authentication.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_2

LANGUAGE: typescript
CODE:
```
export const test = base.extend({
  auth: async ({}, use) => {
    // do sign-in
    await use({ username: 'some user' });
    // do sign-out
  }
});
```

----------------------------------------

TITLE: Report Viewing Script Configuration in package.json
DESCRIPTION: Package.json script configuration for viewing Cucumber HTML reports via HTTP server.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/reporters/cucumber.md#2025-04-22_snippet_2

LANGUAGE: json
CODE:
```
{
  "scripts": {
    "report": "npx http-server ./cucumber-report -c-1 -a localhost -o index.html"
  }
}
```

----------------------------------------

TITLE: Using @slow Tag in Playwright BDD Tests
DESCRIPTION: Shows how to use the @slow tag to mark tests that need extended timeout (3x normal timeout). This is useful for scenarios that take longer to execute.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/special-tags.md#2025-04-22_snippet_3

LANGUAGE: gherkin
CODE:
```
Feature: Playwright site
    
    @slow
    Scenario: Check title
        Given I open url "https://playwright.dev"
```

----------------------------------------

TITLE: Generated Playwright Test File
DESCRIPTION: JavaScript test file automatically generated from the BDD feature file using bddgen
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/index.md#2025-04-22_snippet_2

LANGUAGE: javascript
CODE:
```
import { test } from 'playwright-bdd';

test.describe('Playwright Home Page', () => {

  test('Check title', async ({ Given, When, Then }) => {
    await Given('I am on Playwright home page');
    await When('I click link "Get started"');
    await Then('I see in title "Installation"');
  });

});
```

----------------------------------------

TITLE: Feature Definition for Game in Gherkin
DESCRIPTION: A sample Gherkin feature file for a game that includes a step for clicking the PLAY button.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/scoped.md#2025-04-22_snippet_1

LANGUAGE: gherkin
CODE:
```
Feature: Game

  Scenario: Start playing
    ... 
    When I click the PLAY button
```

----------------------------------------

TITLE: Custom Fixture for Browser-Specific Test Execution in TypeScript
DESCRIPTION: This example demonstrates defining a custom fixture to skip tests based on the `$tags` available. It checks for a specific tag (`@firefox`) and skips the test if the current browser is not Firefox. Integrates with Playwright-BDD, and custom configurations might be needed for various browser settings.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/bdd-fixtures.md#2025-04-22_snippet_4

LANGUAGE: TypeScript
CODE:
```
import { test as base } from 'playwright-bdd';

export const test = base.extend<{ firefoxOnly: void }>({
  firefoxOnly: [
    async ({ $tags, defaultBrowserType }, use, testInfo) => {
      if ($tags.includes('@firefox') && defaultBrowserType !== 'firefox') {
        testInfo.skip();
      }
      await use();
    },
    { auto: true },
  ],
});
```

----------------------------------------

TITLE: Using @fail Tag in Playwright BDD Tests
DESCRIPTION: Demonstrates using the @fail tag to mark tests that are expected to fail. This is useful for tracking known issues while keeping them in the test suite.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/special-tags.md#2025-04-22_snippet_2

LANGUAGE: gherkin
CODE:
```
Feature: Playwright site
    
    @fail
    Scenario: Check title
        Given I open url "https://playwright.dev"
```

----------------------------------------

TITLE: Applying Tag Expressions for Scenario Filtering in Playwright-BDD
DESCRIPTION: This snippet shows how to use tag expressions to filter scenarios for test generation in Playwright-BDD.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/configuration/options.md#2025-04-22_snippet_3

LANGUAGE: typescript
CODE:
```
const testDir = defineBddConfig({
  tags: '@desktop and not @slow',
  // ...
});
```

----------------------------------------

TITLE: Step Definition for Video Player in JavaScript
DESCRIPTION: A step definition file for the video player feature, implementing the 'I click the PLAY button' step.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/scoped.md#2025-04-22_snippet_4

LANGUAGE: javascript
CODE:
```
// video-player.steps.js
When('I click the PLAY button', async () => {
  // actions for video-player.feature
});
```

----------------------------------------

TITLE: Directory Structure for Basic Tag Assignment
DESCRIPTION: Example showing how to organize feature files and step definitions in @-prefixed directories to automatically assign tags to all contained files.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/tags-from-path.md#2025-04-22_snippet_0

LANGUAGE: plaintext
CODE:
```
features
├── @game                     <- sets @game tag to all files inside
│   ├── game.feature
│   └── steps.ts
└── @video-player             <- sets @video-player tag to all files inside
    ├── video-player.feature
    └── steps.ts
```

----------------------------------------

TITLE: Configuring Playwright with Currents Reporter
DESCRIPTION: This TypeScript code configures Playwright to use the Currents reporter. It imports necessary modules, sets up Currents configuration, defines BDD config, and exports the Playwright configuration.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/usage-with-currents.md#2025-04-22_snippet_3

LANGUAGE: typescript
CODE:
```
import 'dotenv/config';
import { defineConfig, devices } from '@playwright/test';
import { defineBddConfig } from 'playwright-bdd';
import { CurrentsConfig, currentsReporter } from '@currents/playwright';

const currentsConfig: CurrentsConfig = {
  recordKey: process.env.CURRENTS_RECORD_KEY || '',
  projectId: process.env.CURRENTS_PROJECT_ID || '',
};

const testDir = defineBddConfig({
  features: 'features/*.feature',
  steps: 'features/steps/*.ts',
});

export default defineConfig({
  testDir,
  reporter: [currentsReporter(currentsConfig)],
  use: {
    screenshot: 'on',
    trace: 'on',
  },
});
```

----------------------------------------

TITLE: Running Playwright Tests with Tag Expressions
DESCRIPTION: This command shows how to run Playwright tests using tag expressions. It generates BDD tests with specific tags and then executes the Playwright test runner.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/index.md#2025-04-22_snippet_1

LANGUAGE: shell
CODE:
```
npx bddgen --tags "@desktop and not @slow" && npx playwright test
```

----------------------------------------

TITLE: Scoped Step Definition for Video Player in JavaScript
DESCRIPTION: A step definition for the video player feature that uses the tags option to scope it to features tagged with @video-player.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/scoped.md#2025-04-22_snippet_6

LANGUAGE: javascript
CODE:
```
// video-player.steps.js
When('I click the PLAY button', { tags: '@video-player' }, async () => {
  // actions for video-player.feature
});
```

----------------------------------------

TITLE: Demonstrating Directory Structure for Tags from Path in Playwright-BDD v8
DESCRIPTION: Shows the directory structure for automatically assigning tags to features and steps using @-prefixed directory names. This eliminates the need for manual tagging and helps bind features with steps.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/blog/whats-new-in-v8.md#2025-04-22_snippet_0

LANGUAGE: plaintext
CODE:
```
features
├── @game                     <- sets @game tag to all files inside
│   ├── game.feature
│   └── steps.ts
└── @video-player             <- sets @video-player tag to all files inside
    ├── video-player.feature
    └── steps.ts
```

----------------------------------------

TITLE: Sample Gherkin Feature File for Playwright Testing
DESCRIPTION: Example Gherkin feature file demonstrating BDD test scenarios for the Playwright home page. Tests navigation and title verification using Given-When-Then syntax.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/reporters/allure.md#2025-04-22_snippet_1

LANGUAGE: gherkin
CODE:
```
Feature: Playwright Home Page

    Scenario: Check title
        Given I am on Playwright home page
        When I click link "Get started"
        Then I see in title "Installation"
```

----------------------------------------

TITLE: Running Playwright BDD Tests in UI Mode
DESCRIPTION: This command generates BDD tests and runs them in Playwright's UI mode, which provides a graphical interface for monitoring and debugging test execution.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/debugging.md#2025-04-22_snippet_1

LANGUAGE: bash
CODE:
```
npx bddgen && npx playwright test --ui
```

----------------------------------------

TITLE: Example Gherkin Feature File Structure
DESCRIPTION: Sample Gherkin feature file showing a feature with Background, basic Scenario, and Scenario Outline with Examples.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/pickles.md#2025-04-22_snippet_0

LANGUAGE: gherkin
CODE:
```
Feature: feature 1

  Background:
    A

  Scenario: scenario 1
    B

  Scenario Outline: scenario 2
    C
    
  Examples:
    C1
    C2
```

----------------------------------------

TITLE: Defining Dynamic Authentication Step in Gherkin
DESCRIPTION: This snippet shows a Gherkin step definition for dynamic authentication. It allows specifying the user email directly in the step, enabling flexible authentication scenarios.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/examples/auth-in-steps/README.md#2025-04-22_snippet_0

LANGUAGE: gherkin
CODE:
```
Given I am logged in as "xxx@example.com"
```

----------------------------------------

TITLE: Configuring SauceLabs Credentials
DESCRIPTION: Command to set up SauceLabs credentials using the saucectl configure command.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/usage-with-saucelabs.md#2025-04-22_snippet_1

LANGUAGE: bash
CODE:
```
saucectl configure
```

----------------------------------------

TITLE: Sample BDD Feature File for Playwright Tests
DESCRIPTION: A Gherkin-syntax feature file example that tests the Playwright website. This demonstrates how BDD scenarios appear in Playwright reports.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/reporters/playwright.md#2025-04-22_snippet_1

LANGUAGE: gherkin
CODE:
```
Feature: Playwright Home Page

    Scenario: Check title
        Given I am on Playwright home page
        When I click link "Get started"
        Then I see in title "Installation"
```

----------------------------------------

TITLE: Running Playwright-BDD Watch Mode
DESCRIPTION: Command to start the concurrent watch mode for both BDD generation and Playwright UI mode testing.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/ui-mode.md#2025-04-22_snippet_2

LANGUAGE: shell
CODE:
```
npm run watch
```

----------------------------------------

TITLE: Pickle Structure Generation
DESCRIPTION: Demonstrates how the Gherkin scenarios are converted into Cucumber pickles, showing the mapping of steps and examples.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/pickles.md#2025-04-22_snippet_1

LANGUAGE: text
CODE:
```
pickle 1 (scenario 1)
  pickleStep 1.1 (A)
  pickleStep 1.2 (B)

pickle 2 (scenario 2, example row 1)
  pickleStep 2.1 (A)
  pickleStep 2.2 (C)

pickle 3 (scenario 2, example row 2)
  pickleStep 3.1 (A)
  pickleStep 3.2 (C)
```

----------------------------------------

TITLE: Creating BeforeWorker Hook without Custom Fixtures
DESCRIPTION: Example of creating a BeforeWorker hook in Playwright-BDD without custom fixtures.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_5

LANGUAGE: typescript
CODE:
```
import { createBdd } from 'playwright-bdd';

const { BeforeWorker } = createBdd();
```

----------------------------------------

TITLE: BrowserStack Credentials Configuration
DESCRIPTION: This YAML configuration file stores the BrowserStack username and access key, which are necessary for authenticating with the BrowserStack platform. These credentials should be replaced with the user's actual username and access key.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/usage-with-browserstack.md#2025-04-22_snippet_1

LANGUAGE: yaml
CODE:
```
"userName: YOUR_USERNAME\naccessKey: YOUR_ACCESS_KEY"
```

----------------------------------------

TITLE: Matching Gherkin Steps Regardless of Keyword
DESCRIPTION: Examples of Gherkin steps that would match the same step definition regardless of the keyword used (Given, When, or Then) when using default settings.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/keywords-matching.md#2025-04-22_snippet_1

LANGUAGE: gherkin
CODE:
```
Given a step
When a step
Then a step
```

----------------------------------------

TITLE: Configuring Playwright-BDD with Authentication Setup
DESCRIPTION: This snippet shows how to configure Playwright-BDD with a separate non-BDD project for authentication. It explicitly sets testDir for the setup project and configures dependencies for the main project.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/configuration/multiple-projects.md#2025-04-22_snippet_3

LANGUAGE: typescript
CODE:
```
import { defineConfig } from '@playwright/test';
import { defineBddConfig } from 'playwright-bdd';

const testDir = defineBddConfig({
  features: 'features/*.feature',
  steps: 'steps/*.ts',
});

export default defineConfig({
  testDir,
  projects: [
    {
      name: 'setup',
      testDir: './setup-steps', // <-- set testDir for setup project
      testMatch: /setup\.ts/,
    },
    {
      name: 'chromium',
      dependencies: ['setup'],
      use: {
        storageState: 'playwright/.auth/user.json',
      },      
    },
  ],
});
```

----------------------------------------

TITLE: Generated JavaScript Test File Using Special Comment Syntax
DESCRIPTION: This snippet demonstrates the JavaScript test file generated when using the special comment syntax for custom example titles.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/customize-examples-title.md#2025-04-22_snippet_3

LANGUAGE: javascript
CODE:
```
test.describe(`Calculator`, () => {

  test.describe(`Multiply by two`, () => {

    test(`check 1`, async ({ Given, When, Then }) => {
      await Given(`value is 1`);
      await When(`multiply by two`);
      await Then(`result is 2`);
    });

    test(`check 2`, async ({ Given, When, Then }) => {
      await Given(`value is 2`);
      await When(`multiply by two`);
      await Then(`result is 4`);
    });

  });
});
```

----------------------------------------

TITLE: Setting Default Tags for Hooks
DESCRIPTION: Example of setting default tags for hooks using createBdd in Playwright-BDD.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_7

LANGUAGE: typescript
CODE:
```
const { BeforeWorker } = createBdd(test, { tags: '@mobile' });

BeforeWorker(async () => {
  // runs only for features with @mobile 
});
```

----------------------------------------

TITLE: Setting Up Currents Credentials in .env File
DESCRIPTION: This snippet shows the content of the .env file with variables for Currents record key and project ID.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/usage-with-currents.md#2025-04-22_snippet_2

LANGUAGE: plaintext
CODE:
```
CURRENTS_RECORD_KEY=YOUR_RECORD_KEY # the record key from https://app.currents.dev
CURRENTS_PROJECT_ID=YOUR_PROJECT_ID # the projectId from https://app.currents.dev
```

----------------------------------------

TITLE: Using Custom Fixture in Cucumber-Style Step Definition
DESCRIPTION: This snippet demonstrates how to use a custom fixture (myFixture) in a Cucumber-style step definition. The fixture is accessed via 'this'.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/cucumber-style.md#2025-04-22_snippet_4

LANGUAGE: typescript
CODE:
```
import { Given, When, Then } from './fixtures';

Given('I am on home page', async function () {
  console.log(this.myFixture);
});
```

----------------------------------------

TITLE: Defining Cucumber-Style Step in TypeScript
DESCRIPTION: This snippet demonstrates how to define a Cucumber-style step using the Given function. It uses the World instance via 'this' to call the openHomePage method.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/cucumber-style.md#2025-04-22_snippet_2

LANGUAGE: typescript
CODE:
```
// steps.ts
import { Given, When, Then } from './fixtures';

Given('I am on home page', async function () {
  await this.openHomePage();
});
```

----------------------------------------

TITLE: Using @only Tag in Playwright BDD Tests
DESCRIPTION: Demonstrates how to use @only tag to run a single feature or scenario in isolation. This is useful during development or debugging when you want to focus on specific tests.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/special-tags.md#2025-04-22_snippet_0

LANGUAGE: gherkin
CODE:
```
@only
Feature: Playwright site
    
    @only
    Scenario: Check title
        Given I open url "https://playwright.dev"
```

----------------------------------------

TITLE: Step Definition for Game in JavaScript
DESCRIPTION: A step definition file for the game feature, implementing the 'I click the PLAY button' step.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/scoped.md#2025-04-22_snippet_3

LANGUAGE: javascript
CODE:
```
// game.steps.js
When('I click the PLAY button', async () => {
  // actions for game.feature
});
```

----------------------------------------

TITLE: Markdown Documentation for Playwright BDD Authentication
DESCRIPTION: Documentation explaining the setup of authentication in Playwright BDD tests, including project structure and handling of authenticated/non-authenticated scenarios using tags.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/examples/auth/README.md#2025-04-22_snippet_0

LANGUAGE: markdown
CODE:
```
# auth playwright-bdd example

Example of [single authentication account](https://playwright.dev/docs/auth#basic-shared-account-in-all-tests) in BDD tests. There are two Playwright projects:

* `auth` - non-BDD project for authentication
* `chromium` - BDD project that depends on `auth`

Features that don't need authentication are marked with `@noauth` tag and handled in `storageState` fixture.

If you need several accounts (that do not interact with each other), you can create several authentication states and select appropriate one by tag/feature in `storageState` fixture.

Authentication in this example is *static* - there are no steps like 
`Given I am logged in as "xxx@example.com"`. If you need dynamic authentication in steps, please check out [auth-in-steps]() example.
```

----------------------------------------

TITLE: Configure Test Command in package.json
DESCRIPTION: Script configuration for running component tests with BDD generator and Playwright
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/component-tests.md#2025-04-22_snippet_5

LANGUAGE: json
CODE:
```
"scripts": {
  "test-ct": "npx bddgen -c playwright-ct.config.ts && playwright test -c playwright-ct.config.ts"
}
```

----------------------------------------

TITLE: Setting Default Tags in Playwright-BDD v8
DESCRIPTION: Demonstrates how to provide default tags via the createBdd() option, allowing multiple step definitions and hooks to have the same tags without repetitive specification.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/blog/whats-new-in-v8.md#2025-04-22_snippet_3

LANGUAGE: typescript
CODE:
```
const { BeforeAll, Before, Given } = createBdd(test, { 
  tags: '@game' // <- default tag
});

// all functions below are tagged with `@game`
BeforeAll(async () => { ... });
Before(async () => { ... });
Given('a step', async () => { ... });
```

----------------------------------------

TITLE: Tagged Game Feature in Gherkin
DESCRIPTION: A Gherkin feature file for a game that is tagged with @game to match the scope of the corresponding step definition.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/scoped.md#2025-04-22_snippet_7

LANGUAGE: gherkin
CODE:
```
@game
Feature: Game

  Scenario: Start playing
    ... 
    When I click the PLAY button
```

----------------------------------------

TITLE: Using Environment Variables in Step Definitions
DESCRIPTION: Example showing how to access environment variables within Playwright-BDD step definitions for login automation.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/env-vars.md#2025-04-22_snippet_0

LANGUAGE: javascript
CODE:
```
When('I log in', async ({ page }) => {
  await page.getByRole('textbox', { name: 'Username' }).fill(process.env.USERNAME);
  await page.getByRole('textbox', { name: 'Password' }).fill(process.env.PASSWORD);
  await page.getByRole('button', { name: 'Log in' }).click();
});
```

----------------------------------------

TITLE: Configuring Custom Snapshot Paths in Playwright
DESCRIPTION: This TypeScript snippet demonstrates how to set a custom snapshotPathTemplate in Playwright's configuration. It moves snapshots to a separate __snapshots__ directory, organizing them by test file and project.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/ignore-generated-files.md#2025-04-22_snippet_1

LANGUAGE: typescript
CODE:
```
export default defineConfig({
  snapshotPathTemplate:
    '__snapshots__/{testFileDir}/{testFileName}-snapshots/{arg}{-projectName}{-snapshotSuffix}{ext}',
  // ...  
});
```

----------------------------------------

TITLE: Filename-based Tag Assignment Structure
DESCRIPTION: Example showing how to use @-prefixed filenames to assign tags to individual feature files.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/tags-from-path.md#2025-04-22_snippet_2

LANGUAGE: plaintext
CODE:
```
features
├── @game.feature
├── @video-player.feature
└── ...
```

----------------------------------------

TITLE: Creating BDD with Default Tags for Game in TypeScript
DESCRIPTION: Shows how to create BDD functions with default tags for all step definitions in a file, scoping them to @game.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/scoped.md#2025-04-22_snippet_9

LANGUAGE: typescript
CODE:
```
// game.steps.ts
const { Given, When, Then } = createBdd(test, { tags: '@game' });

When('I click the PLAY button', async () => {
  // actions for game.feature
});
```

----------------------------------------

TITLE: Example Output of Step Definition Export
DESCRIPTION: Sample output from the bddgen export command, showing the configured steps found in the project. The output includes the step type (Given/When/Then) and the step definition pattern.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/cli.md#2025-04-22_snippet_5

LANGUAGE: bash
CODE:
```
Using config: playwright.config.ts
List of all steps (4):

* Given I am on todo page
* When I add todo {string}
* When I remove todo {string}
* Then visible todos count is {int}
```

----------------------------------------

TITLE: Browser Configuration for Playwright on BrowserStack
DESCRIPTION: This YAML configuration defines the browsers on which the Playwright tests will run on BrowserStack, including OS, browser name, version, and Playwright configuration options. The `buildName` and `buildIdentifier` properties help organize the test results within the BrowserStack dashboard.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/usage-with-browserstack.md#2025-04-22_snippet_2

LANGUAGE: yaml
CODE:
```
"userName: YOUR_USERNAME\naccessKey: YOUR_ACCESS_KEY\n\nprojectName: playwright-bdd sample\nbuildName: my-build-name\nbuildIdentifier: '#${BUILD_NUMBER}'\nplatforms:\n  - os: Windows\n    osVersion: 11\n    browserName: chrome\n    browserVersion: latest\n    playwrightConfigOptions:\n      name: chromium\n  - os: OS X\n    osVersion: Ventura\n    browserName: playwright-webkit\n    browserVersion: latest\n    playwrightConfigOptions:\n      name: osx\n\n  # more browsers    "
```

----------------------------------------

TITLE: Creating Simple World Object with Page in JavaScript
DESCRIPTION: This code shows how to create a simple World object with just a page property in JavaScript. It extends the test and creates Given/When/Then functions.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/cucumber-style.md#2025-04-22_snippet_5

LANGUAGE: javascript
CODE:
```
import { test as base } from 'playwright-bdd';

export const test = base.extend({
  world: async ({ page }, use) => {
    const world = { page };
    await use(world);
  },
});

export const { Given, When, Then, Before, After } = createBdd(test, { worldFixture: 'world' });
```

----------------------------------------

TITLE: Installing Playwright-BDD with npm - New Project
DESCRIPTION: Commands to install Playwright and Playwright-BDD dependencies using npm, followed by installing Playwright browsers.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/getting-started/installation.md#2025-04-22_snippet_0

LANGUAGE: bash
CODE:
```
npm i -D @playwright/test playwright-bdd
```

LANGUAGE: bash
CODE:
```
npx playwright install
```

----------------------------------------

TITLE: Yarn Plug'n'Play Configuration for Playwright-BDD
DESCRIPTION: Required configuration in .yarnrc.yml file for using Playwright-BDD with Yarn Plug'n'Play feature.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/getting-started/installation.md#2025-04-22_snippet_4

LANGUAGE: yaml
CODE:
```
packageExtensions: 
  playwright-bdd@*: 
    dependencies: 
      playwright: "*"
      playwright-core: "*"
```

----------------------------------------

TITLE: Basic HTML Reporter Configuration in Playwright-BDD
DESCRIPTION: Basic setup for HTML reporting in Playwright-BDD with feature and steps path configuration.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/reporters/cucumber.md#2025-04-22_snippet_1

LANGUAGE: javascript
CODE:
```
import { defineConfig } from '@playwright/test';
import { defineBddConfig, cucumberReporter } from 'playwright-bdd';

const testDir = defineBddConfig({
  features: 'features/*.feature',
  steps: 'steps/*.ts',
});

export default defineConfig({
  testDir,
  reporter: [
    cucumberReporter('html', { outputFile: 'cucumber-report/index.html' }),  
  ],
});
```

----------------------------------------

TITLE: JSON Reporter Configuration in Playwright-BDD
DESCRIPTION: Setup for JSON reporting format in Playwright-BDD with output file configuration.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/reporters/cucumber.md#2025-04-22_snippet_3

LANGUAGE: javascript
CODE:
```
import { defineConfig } from '@playwright/test';
import { defineBddConfig, cucumberReporter } from 'playwright-bdd';

const testDir = defineBddConfig({
  features: ['features/*.feature'],
  steps: ['steps/*.ts'],
});

export default defineConfig({
  testDir,
  reporter: [
    cucumberReporter('json', { outputFile: 'cucumber-report/report.json' }), 
  ],
});
```

----------------------------------------

TITLE: Installing Playwright-BDD with pnpm - New Project
DESCRIPTION: Commands to install Playwright and Playwright-BDD dependencies using pnpm, followed by installing Playwright browsers.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/getting-started/installation.md#2025-04-22_snippet_2

LANGUAGE: bash
CODE:
```
pnpm i -D @playwright/test playwright-bdd
```

LANGUAGE: bash
CODE:
```
pnpm playwright install
```

----------------------------------------

TITLE: Importing Playwright-BDD Decorators
DESCRIPTION: Shows how to import the necessary decorators from playwright-bdd/decorators package.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/decorators.md#2025-04-22_snippet_0

LANGUAGE: typescript
CODE:
```
import { Fixture, Given, When, Then } from 'playwright-bdd/decorators';
```

----------------------------------------

TITLE: Running and Merging Test Shards
DESCRIPTION: The Shell scripts orchestrate running tests in sharded mode and merging their reports. No specific dependencies are noted beyond npx, Playwright, and the relevant config setup. Key parameters such as `--shard` and `--config` specify shard indexing and configurations for merging, respectively. Output involves combined reports generated in shard runs.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/reporters/cucumber.md#2025-04-22_snippet_9

LANGUAGE: Shell
CODE:
```
npx bddgen && npx playwright test --shard 1/2
npx bddgen && npx playwright test --shard 2/2
```

LANGUAGE: Shell
CODE:
```
npx playwright merge-reports --config playwright.config.ts ./blob-report
```

----------------------------------------

TITLE: Configuring Playwright BDD Settings
DESCRIPTION: Demonstrates how to configure Playwright BDD settings in the configuration file.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/decorators.md#2025-04-22_snippet_3

LANGUAGE: typescript
CODE:
```
const testDir = defineBddConfig({
  features: 'features/todo.feature',
  steps: 'fixtures.ts',
  // ...
});
```

----------------------------------------

TITLE: Installing Playwright-BDD with Yarn - Existing Project
DESCRIPTION: Command to install only Playwright-BDD in a project that already has Playwright installed using Yarn.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/getting-started/installation.md#2025-04-22_snippet_6

LANGUAGE: bash
CODE:
```
yarn add -D playwright-bdd
```

----------------------------------------

TITLE: Special Tags Directory Structure
DESCRIPTION: Example showing how to organize features using special tags as directory names for controlling test execution behavior.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/tags-from-path.md#2025-04-22_snippet_3

LANGUAGE: plaintext
CODE:
```
features
└── @game
    ├── @slow                <- for features that need more time
    │   └── feature1.feature
    ├── @skip                <- for features that are not ready
    │   └── feature2.feature 
    ├── @mode:serial         <- for features to run in serial mode
    │   └── feature3.feature
    ├── game.feature
    └── steps.ts
```

----------------------------------------

TITLE: Configuring featuresRoot as Default Directory in Playwright-BDD v8
DESCRIPTION: Shows the simplified configuration for featuresRoot as a default directory for both features and steps, unless explicitly defined. This reduces the need for separate feature and step configurations.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/blog/whats-new-in-v8.md#2025-04-22_snippet_4

LANGUAGE: typescript
CODE:
```
// before
const testDir = defineBddConfig({
  features: './features/**/*.feature',
  steps: './features/steps/**/*.js',
  featuresRoot: './features',
});

// after
const testDir = defineBddConfig({
  featuresRoot: './features',
});
```

----------------------------------------

TITLE: Running Playwright-BDD Tests with Currents
DESCRIPTION: This command generates BDD tests and runs them using Playwright, which will now report results to the Currents dashboard.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/usage-with-currents.md#2025-04-22_snippet_4

LANGUAGE: sh
CODE:
```
npx bddgen && npx playwright test
```

----------------------------------------

TITLE: Initialize Playwright Component Testing
DESCRIPTION: Command to set up initial component testing configuration with Playwright
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/component-tests.md#2025-04-22_snippet_0

LANGUAGE: bash
CODE:
```
npm init playwright@latest -- --ct
```

----------------------------------------

TITLE: Using Auth Fixture in a Given Step
DESCRIPTION: Example of using the auth fixture in a Given step definition in Playwright-BDD.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_3

LANGUAGE: typescript
CODE:
```
Given('I am an authorized user', async ({ auth }) => {
  console.log('step for authorized user', auth.username);
});
```

----------------------------------------

TITLE: Configuring Test Fixtures
DESCRIPTION: Shows how to extend the base test configuration with custom Page Object Model fixtures.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/decorators.md#2025-04-22_snippet_2

LANGUAGE: typescript
CODE:
```
// fixtures.ts
import { test as base } from 'playwright-bdd';
import { TodoPage } from './TodoPage';

export const test = base.extend<{ todoPage: TodoPage }>({
  todoPage: ({ page }, use) => use(new TodoPage(page)),
});
```

----------------------------------------

TITLE: Running Playwright Tests with BrowserStack
DESCRIPTION: This command executes the Playwright tests using the BrowserStack Node SDK after first generating the BDD scenarios. `bddgen` generates the test files and `browserstack-node-sdk playwright test` command utilizes BrowserStack for test execution.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/usage-with-browserstack.md#2025-04-22_snippet_3

LANGUAGE: bash
CODE:
```
"npx bddgen && npx browserstack-node-sdk playwright test"
```

----------------------------------------

TITLE: Configure Playwright-BDD Component Testing
DESCRIPTION: Configuration setup for Playwright component testing with BDD integration, defining feature and step file locations
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/component-tests.md#2025-04-22_snippet_1

LANGUAGE: typescript
CODE:
```
import { defineConfig, devices } from '@playwright/experimental-ct-react';
import { defineBddConfig } from 'playwright-bdd';

const testDir = defineBddConfig({
  features: ['features/*.feature'],
  steps: ['fixtures.ts', 'steps.tsx'],
});

export default defineConfig({
  testDir,
  // ...
});
```

----------------------------------------

TITLE: Implementing Page Object Inheritance
DESCRIPTION: Shows how to implement inheritance between Page Object Models while maintaining decorator functionality.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/decorators.md#2025-04-22_snippet_5

LANGUAGE: typescript
CODE:
```
// TodoPage
export @Fixture('todoPage') class TodoPage {
  @Given('I am on todo page')
  async open() { ... }
}

// AdminTodoPage inherited from TodoPage
export @Fixture('adminTodoPage') class AdminTodoPage extends TodoPage {
  @When('I add todo {string}')
  async addToDo(text: string) { ... }
}
```

----------------------------------------

TITLE: Writing Gherkin Feature File
DESCRIPTION: Example of a Gherkin feature file using the defined test steps.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/decorators.md#2025-04-22_snippet_4

LANGUAGE: gherkin
CODE:
```
# features/todo.feature
Feature: Todo Page

    Scenario: Adding todos
      Given I am on todo page
      When I add todo "foo"
      And I add todo "bar"
      Then visible todos count is 2
```

----------------------------------------

TITLE: Generating Playwright-BDD Test Report
DESCRIPTION: Command to generate test execution report for Playwright-BDD tests
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/examples/basic-esm/README.md#2025-04-22_snippet_1

LANGUAGE: shell
CODE:
```
npm run report
```

----------------------------------------

TITLE: Execute Component Tests
DESCRIPTION: Command to run the configured component tests
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/component-tests.md#2025-04-22_snippet_6

LANGUAGE: bash
CODE:
```
npm run test-ct
```

----------------------------------------

TITLE: Create Gherkin Feature File
DESCRIPTION: BDD feature file defining test scenarios for input component testing
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/component-tests.md#2025-04-22_snippet_4

LANGUAGE: gherkin
CODE:
```
Feature: input component

    Scenario: Mount component and interact with it
        Given Mounted input component
        When I type "ABC"
        Then input field has "ABC"
```

----------------------------------------

TITLE: Configuring Hook Name and Timeout
DESCRIPTION: Example of setting a name and timeout for a BeforeWorker hook in Playwright-BDD.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/hooks.md#2025-04-22_snippet_8

LANGUAGE: typescript
CODE:
```
BeforeWorker({ name: 'setup database', timeout: 1000 }, async () => {
  // runs with timeout 1000 ms
});
```

----------------------------------------

TITLE: Running Playwright-BDD Tests in TypeScript
DESCRIPTION: Command to execute Playwright-BDD tests in a TypeScript project. This command runs the tests and displays the test execution results.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/examples/basic-cjs/README.md#2025-04-22_snippet_0

LANGUAGE: shell
CODE:
```
npm t
```

----------------------------------------

TITLE: Running bddgen to Generate and Execute Playwright Tests
DESCRIPTION: Command to generate Playwright test files from Gherkin documents using the default configuration, followed by executing the tests. This is the standard workflow for running BDD tests with Playwright.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/cli.md#2025-04-22_snippet_0

LANGUAGE: bash
CODE:
```
npx bddgen && npx playwright test
```

----------------------------------------

TITLE: Scoped Step Definition for Game in JavaScript
DESCRIPTION: A step definition for the game feature that uses the tags option to scope it to features tagged with @game.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/scoped.md#2025-04-22_snippet_5

LANGUAGE: javascript
CODE:
```
// game.steps.js
When('I click the PLAY button', { tags: '@game' }, async () => {
  // actions for game.feature
});
```

----------------------------------------

TITLE: Running Playwright-BDD Tests
DESCRIPTION: Command to execute the test suite that intentionally contains failing tests to demonstrate the AI fix feature
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/examples/ai/README.md#2025-04-22_snippet_0

LANGUAGE: shell
CODE:
```
npm t
```

----------------------------------------

TITLE: Configuring Nodemon Watch Command for BDD Test Generation
DESCRIPTION: Command to watch feature and step definition files for changes and automatically regenerate test files using nodemon. Monitors files with .feature, .js, and .ts extensions.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/ui-mode.md#2025-04-22_snippet_0

LANGUAGE: shell
CODE:
```
npx nodemon -w ./features -w ./steps -e feature,js,ts --exec "npx bddgen"
```

----------------------------------------

TITLE: Using Custom Configuration Path with bddgen
DESCRIPTION: Command to specify a custom configuration file path for both bddgen and playwright test commands. This is useful when the configuration is not in the default location or when multiple configurations exist.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/cli.md#2025-04-22_snippet_2

LANGUAGE: bash
CODE:
```
npx bddgen -c path/to/playwright.config.ts && npx playwright test -c path/to/playwright.config.ts
```

----------------------------------------

TITLE: Exporting Step Definitions Using bddgen CLI
DESCRIPTION: This shell command demonstrates how to use the 'bddgen export' command to list all available step patterns defined in the Playwright configuration.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/chatgpt.md#2025-04-22_snippet_1

LANGUAGE: shellscript
CODE:
```
$ bddgen export

List of all steps found by config: playwright.config.ts

* Given I am on todo page
* When I add todo {string}
* When I remove todo {string}
* Then visible todos count is {int}
```

----------------------------------------

TITLE: Filtering Tests by Tags with bddgen
DESCRIPTION: Command to generate tests with tag filtering. This uses Cucumber's tag expression syntax to include or exclude scenarios based on their tags, allowing for selective test execution.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/cli.md#2025-04-22_snippet_1

LANGUAGE: bash
CODE:
```
npx bddgen --tags "@foo and not @bar" && npx playwright test
```

----------------------------------------

TITLE: Running Playwright-BDD Tests with Undefined Steps
DESCRIPTION: Command to generate BDD test files and run Playwright tests. This demonstrates how to execute tests even when step definitions are not yet implemented.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/snippets.md#2025-04-22_snippet_1

LANGUAGE: bash
CODE:
```
npx bddgen && npx playwright test
```

----------------------------------------

TITLE: Displaying Help for bddgen Commands
DESCRIPTION: Commands to display help information for the bddgen tool, showing available options and usage instructions for specific commands or for the tool as a whole.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/cli.md#2025-04-22_snippet_3

LANGUAGE: bash
CODE:
```
npx bddgen test -h
# or to show global help
npx bddgen -h
```

----------------------------------------

TITLE: Configuring SauceLabs for Playwright-BDD
DESCRIPTION: YAML configuration for SauceLabs, specifying Playwright settings, npm packages, test suites, and reporters.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/usage-with-saucelabs.md#2025-04-22_snippet_2

LANGUAGE: yaml
CODE:
```
apiVersion: v1alpha
kind: playwright
sauce:
  region: us-west-1
  concurrency: 10
  metadata:
    tags: [e2e, bdd]
playwright:
  version: package.json
npm:
  packages:
    playwright-bdd: latest
rootDir: ./
suites:
  - name: 'Chromium Mac'
    platformName: 'macOS 12'
    screenResolution: '1440x900'
    testMatch: ['.*.js']
    params:
      browserName: 'chromium'
      project: 'chromium' # Runs the project that's defined in `playwright.config.js`
reporters:
  spotlight:
    enabled: true
```

----------------------------------------

TITLE: Installing Playwright-BDD with npm - Existing Project
DESCRIPTION: Command to install only Playwright-BDD in a project that already has Playwright installed.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/getting-started/installation.md#2025-04-22_snippet_1

LANGUAGE: bash
CODE:
```
npm i -D playwright-bdd
```

----------------------------------------

TITLE: Running Playwright-BDD Tests
DESCRIPTION: This shell command shows how to generate and run Playwright-BDD tests using the generated feature file.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/chatgpt.md#2025-04-22_snippet_3

LANGUAGE: shellscript
CODE:
```
npx bddgen && npx playwright test
```

----------------------------------------

TITLE: Exporting Step Definitions with bddgen
DESCRIPTION: Command to list all step definitions found in the project. This is particularly useful for integrating with ChatGPT for generating BDD scenarios based on available steps.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/cli.md#2025-04-22_snippet_4

LANGUAGE: bash
CODE:
```
npx bddgen export
```

----------------------------------------

TITLE: Running Playwright-BDD Tests on SauceLabs
DESCRIPTION: Command to generate BDD tests and run them on SauceLabs using saucectl.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/usage-with-saucelabs.md#2025-04-22_snippet_4

LANGUAGE: bash
CODE:
```
npx bddgen && saucectl run
```

----------------------------------------

TITLE: Installing Playwright-BDD with pnpm - Existing Project
DESCRIPTION: Command to install only Playwright-BDD in a project that already has Playwright installed using pnpm.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/getting-started/installation.md#2025-04-22_snippet_3

LANGUAGE: bash
CODE:
```
pnpm i -D playwright-bdd
```

----------------------------------------

TITLE: Installing Currents and Playwright Reporter Dependencies
DESCRIPTION: This command installs the Currents Playwright reporter package as a dev dependency.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/usage-with-currents.md#2025-04-22_snippet_0

LANGUAGE: sh
CODE:
```
npm i -D @currents/playwright
```

----------------------------------------

TITLE: Displaying Environment Information with bddgen
DESCRIPTION: Command to show information about the current environment, including platform, Node.js version, and versions of Playwright-BDD and its dependencies.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/cli.md#2025-04-22_snippet_6

LANGUAGE: bash
CODE:
```
npx bddgen env
```

----------------------------------------

TITLE: Custom Formatter Implementation in Playwright-BDD
DESCRIPTION: Example of creating a custom Cucumber formatter that logs envelopes as JSON strings.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/reporters/cucumber.md#2025-04-22_snippet_6

LANGUAGE: typescript
CODE:
```
import * as messages from '@cucumber/messages';
import { Formatter, IFormatterOptions } from '@cucumber/cucumber';

export default class CustomFormatter extends Formatter {
  constructor(options: IFormatterOptions) {
    super(options);
    options.eventBroadcaster.on('envelope', (envelope: messages.Envelope) => {
      console.log(JSON.stringify(envelope));
    });
  }
}
```

----------------------------------------

TITLE: Running Tests with Environment Variables via npm
DESCRIPTION: Correct way to run tests with environment variables using npm script.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/env-vars.md#2025-04-22_snippet_5

LANGUAGE: shell
CODE:
```
USERNAME=foo npm test
```

----------------------------------------

TITLE: Environment Variables Definition in .env File
DESCRIPTION: Example .env file showing environment variable declarations for username and password.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/env-vars.md#2025-04-22_snippet_1

LANGUAGE: plaintext
CODE:
```
# .env
USERNAME=foo
PASSWARD=bar
```

----------------------------------------

TITLE: Example Output of Environment Information
DESCRIPTION: Sample output from the bddgen env command, displaying platform details and version information for Node.js, Playwright-BDD, Playwright Test, and Cucumber.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/cli.md#2025-04-22_snippet_7

LANGUAGE: bash
CODE:
```
Playwright-BDD environment info:

platform: darwin
node: v18.16.0
playwright-bdd: v5.1.1
@playwright/test: v1.36.2
@cucumber/cucumber: v9.2.0
```

----------------------------------------

TITLE: Ignoring Generated Playwright Test Files in Git
DESCRIPTION: This snippet shows how to ignore generated Playwright test files in .gitignore while preserving snapshots. It targets specifically the .spec.js files within the .features-gen directory.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/ignore-generated-files.md#2025-04-22_snippet_0

LANGUAGE: gitignore
CODE:
```
**/.features-gen/**/*.spec.js
```

----------------------------------------

TITLE: Running Playwright-BDD Tests
DESCRIPTION: Command to execute Playwright-BDD test suite with output showing successful test completion
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/examples/basic-esm/README.md#2025-04-22_snippet_0

LANGUAGE: shell
CODE:
```
npm t
```

LANGUAGE: plaintext
CODE:
```
Running 2 tests using 1 worker
  2 passed (2.9s)
```

----------------------------------------

TITLE: Incorrect Environment Variable Usage in CLI
DESCRIPTION: Example showing incorrect way of passing environment variables in CLI command.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/env-vars.md#2025-04-22_snippet_3

LANGUAGE: shell
CODE:
```
USERNAME=foo npx bddgen && npx playwright test
```

----------------------------------------

TITLE: Running Playwright-BDD Tests in ESM Mode
DESCRIPTION: Command to generate BDD tests and run Playwright tests in ESM projects. Compatible with Playwright-BDD v7 and Playwright v1.41+, no longer requiring the ts-node/esm loader.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/configuration/esm.md#2025-04-22_snippet_0

LANGUAGE: shell
CODE:
```
npx bddgen && npx playwright test
```

----------------------------------------

TITLE: Using Fixture Tags in Gherkin
DESCRIPTION: Demonstrates how to specify particular fixtures using Gherkin tags.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/decorators.md#2025-04-22_snippet_6

LANGUAGE: gherkin
CODE:
```
@fixture:adminTodoPage
Feature: Some feature

    Background: 
      Given I am on todo page # <- will use AdminTodoPage

    Scenario: Adding todos
      When I add todo "foo"   # <- will use AdminTodoPage
```

----------------------------------------

TITLE: Generating Playwright-BDD Test Report
DESCRIPTION: Command to generate a visual report for Playwright-BDD test results. This report provides a detailed overview of test execution outcomes.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/examples/basic-cjs/README.md#2025-04-22_snippet_1

LANGUAGE: shell
CODE:
```
npm run report
```

----------------------------------------

TITLE: Markdown Changelog Entry for Version 8.2.0
DESCRIPTION: Details improvements to Cucumber HTML reporter and introduction of step hooks
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/CHANGELOG.md#2025-04-22_snippet_1

LANGUAGE: markdown
CODE:
```
## 8.2.0
* improve Cucumber HTML reporter to show trace without explicit `attachmentsBaseURL`.
* introduce `BeforeStep` / `AfterStep` hooks (#280, thanks to @the3dsandwich).
```

----------------------------------------

TITLE: Configuring Prettier with Gherkin Plugin
DESCRIPTION: JavaScript configuration file that sets up Prettier with the Gherkin plugin for auto-formatting feature files. The configuration is exported as an ES module and enables formatting support for Gherkin syntax.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/auto-formatting.md#2025-04-22_snippet_0

LANGUAGE: javascript
CODE:
```
export default {
  plugins: ['prettier-plugin-gherkin'],
  // ...other prettier options
};
```

----------------------------------------

TITLE: Feature File with Reference Mapping
DESCRIPTION: Shows how pickle steps map back to the original feature file elements, with references indicated in comments.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/pickles.md#2025-04-22_snippet_2

LANGUAGE: gherkin
CODE:
```
Feature: feature 1

  Background: # referenced from: none
    A # referenced from: pickleStep 1.1, pickleStep 2.1, pickleStep 3.1

  Scenario: scenario 1 # referenced from: pickle 1
    B # referenced from: pickleStep 1.2

  Scenario Outline: scenario 2 # referenced from: pickle 2, pickle 3
    C # referenced from: pickleStep 2.2, pickleStep 3.2
    
  Examples:
    C1 # referenced from: pickle 2
    C2 # referenced from: pickle 3
```

----------------------------------------

TITLE: Installing dotenv for Managing Currents Credentials
DESCRIPTION: This command installs the dotenv package as a dev dependency for managing Currents credentials.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/usage-with-currents.md#2025-04-22_snippet_1

LANGUAGE: sh
CODE:
```
npm i -D dotenv
```

----------------------------------------

TITLE: Markdown Changelog Entry for Version 8.1.0
DESCRIPTION: Lists addition of AI features and attachment support updates
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/CHANGELOG.md#2025-04-22_snippet_2

LANGUAGE: markdown
CODE:
```
## 8.1.0
* add "Fix with AI" feature
* support attachments via `testInfo.attachments.push()`
* update all dependencies
```

----------------------------------------

TITLE: Generated JavaScript Test File from Gherkin Scenario Outline
DESCRIPTION: This snippet shows the JavaScript test file generated from the Gherkin Scenario Outline, with unique test titles for each example.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/customize-examples-title.md#2025-04-22_snippet_1

LANGUAGE: javascript
CODE:
```
test.describe(`Calculator`, () => {

  test.describe(`Multiply <value> by two`, () => {

    test(`Multiply 1 by two`, async ({ Given, When, Then }) => {
      await Given(`value is 1`);
      await When(`multiply by two`);
      await Then(`result is 2`);
    });

    test(`Multiply 2 by two`, async ({ Given, When, Then }) => {
      await Given(`value is 2`);
      await When(`multiply by two`);
      await Then(`result is 4`);
    });

  });
});    
```

----------------------------------------

TITLE: Tagged Feature File Example
DESCRIPTION: Shows the equivalent Gherkin syntax when a feature file is placed in an @-prefixed directory.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-features/tags-from-path.md#2025-04-22_snippet_1

LANGUAGE: gherkin
CODE:
```
@game
Feature: Game

  ...
```

----------------------------------------

TITLE: Configuring quotes Option in Playwright-BDD v8
DESCRIPTION: Shows how to set the quotes option to 'double' to revert to the previous behavior of using double quotes in generated test files. The default is now set to 'single'.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/blog/whats-new-in-v8.md#2025-04-22_snippet_6

LANGUAGE: typescript
CODE:
```
const testDir = defineBddConfig({
  quotes: 'double',
  // ...
});
```

----------------------------------------

TITLE: Installing cross-env Package
DESCRIPTION: Command to install the cross-env package as a development dependency for handling environment variables across platforms
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/env-variables.md#2025-04-22_snippet_0

LANGUAGE: shell
CODE:
```
npm install -D cross-env
```

----------------------------------------

TITLE: Installing SauceLabs CLI (saucectl)
DESCRIPTION: Command to install the SauceLabs command-line interface (saucectl) globally using npm.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/usage-with-saucelabs.md#2025-04-22_snippet_0

LANGUAGE: bash
CODE:
```
npm install -g saucectl
```

----------------------------------------

TITLE: Initializing Playwright BDD Test Scenario with Hooks
DESCRIPTION: Demonstrates a complete test scenario with before and after hooks, background steps, and multiple test steps using Playwright and BDD framework
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/test/reporter-data/expected-reports/report-less-1.46.txt#2025-04-22_snippet_0

LANGUAGE: typescript
CODE:
```
[hook] Before Hooks
    [hook] BeforeAll Hooks
    [hook] BeforeEach Hooks
    [hook] Background
[test.step] Multiple test steps
[hook] After Hooks
    [hook] AfterEach Hooks
    [hook] AfterAll Hooks
```

----------------------------------------

TITLE: Installing BrowserStack Node SDK
DESCRIPTION: This command installs the BrowserStack Node SDK as a development dependency using npm. The `-D` flag ensures it's saved as a dev dependency in package.json.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/guides/usage-with-browserstack.md#2025-04-22_snippet_0

LANGUAGE: bash
CODE:
```
"npm i -D browserstack-node-sdk"
```

----------------------------------------

TITLE: Named Before Hook Implementation
DESCRIPTION: These snippets are implementations of before and after hooks using Typescript within Playwright BDD. They are defined to execute before and after each scenario or example, providing setup and teardown functionality.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/test/reporter-data/expected-reports/report-current.txt#2025-04-22_snippet_1

LANGUAGE: text
CODE:
```
[test.step] named Before hook features/steps.ts:12:1
```

LANGUAGE: text
CODE:
```
[test.step] BeforeEach hook features/steps.ts:13:1
```

LANGUAGE: text
CODE:
```
[test.step] AfterEach hook features/steps.ts:19:1
```

LANGUAGE: text
CODE:
```
[test.step] named After hook features/steps.ts:18:1
```

----------------------------------------

TITLE: Playwright Test Scenario with Hooks and Fixtures
DESCRIPTION: Shows test scenario lifecycle with fixtures, including named hooks, background steps, and test attachments
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/test/reporter-data/expected-reports/report-less-1.46.txt#2025-04-22_snippet_1

LANGUAGE: typescript
CODE:
```
[fixture] $beforeEach
[fixture] $afterEach
[test.step] Action steps
[attach] screenshot
[attach] trace
```

----------------------------------------

TITLE: Markdown Documentation Navigation Structure
DESCRIPTION: A hierarchical markdown structure defining the navigation and organization of the Playwright BDD documentation, including sections for getting started, configuration, writing features and steps, reporters, and various implementation guides.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/_sidebar.md#2025-04-22_snippet_0

LANGUAGE: markdown
CODE:
```
* [**Getting started**](getting-started/index.md)
  - [Installation](getting-started/installation.md)
  - [Write first BDD test](getting-started/write-first-test.md)
  - [Add fixtures](getting-started/add-fixtures.md)

* [**Configuration**](configuration/index.md)
  - [Options](configuration/options.md)
  - [Multiple projects](configuration/multiple-projects.md)
  - [ESM](configuration/esm.md)

* [**Writing features**](writing-features/index.md)
  - [Special tags](writing-features/special-tags.md)
  - [Tags from path](writing-features/tags-from-path.md)
  - [Localization](writing-features/i18n.md)
  - [Auto-formatting](writing-features/auto-formatting.md)
  - [Customize examples title](writing-features/customize-examples-title.md)
  - [Use ChatGPT](writing-features/chatgpt.md)
```

----------------------------------------

TITLE: Defining Blog Index in Markdown
DESCRIPTION: A markdown list structure defining the blog index with a link to an article about Playwright-BDD version 8 updates.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/blog/index.md#2025-04-22_snippet_0

LANGUAGE: markdown
CODE:
```
# Playwright-BDD Blog

- [What's new in Playwright-BDD v8](blog/whats-new-in-v8.md)
```

----------------------------------------

TITLE: Markdown Changelog Entry for Version 8.2.1
DESCRIPTION: Documents latest version changes including Playwright 1.51 adoption and attachment handling updates
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/CHANGELOG.md#2025-04-22_snippet_0

LANGUAGE: markdown
CODE:
```
## 8.2.1
* adopt to Playwright 1.51, improve stack trace parsing.
* hide "_" prefixed attachments.
```

----------------------------------------

TITLE: Missing Step Definition Error with matchKeywords Enabled
DESCRIPTION: Example error message shown when matchKeywords is enabled and a step with 'When' keyword tries to match a definition with 'Given' keyword. The error provides a snippet to create the missing step definition.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/docs/writing-steps/keywords-matching.md#2025-04-22_snippet_3

LANGUAGE: plaintext
CODE:
```
Missing step definitions: 1

When('a step', async ({}) => {
  // Step: When a step
  // From: features/homepage.feature:4:5
});

Use snippets above to create missing steps.
```

----------------------------------------

TITLE: Playwright BeforeAll Hooks
DESCRIPTION: These snippets indicate the execution of before all hooks, typically used for setup tasks that need to be performed once before all tests in a suite. The `BeforeAll` hook is being executed.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/test/reporter-data/expected-reports/report-current.txt#2025-04-22_snippet_2

LANGUAGE: text
CODE:
```
[test.step] BeforeAll hook features/steps.ts:14:1
```

LANGUAGE: text
CODE:
```
[test.step] named BeforeAll hook features/steps.ts:15:1
```

----------------------------------------

TITLE: Playwright Page Navigation
DESCRIPTION: This snippet shows the usage of Playwright's `page.goto()` method to navigate to a specific URL. This function is typically used within a step definition in the BDD test to simulate user navigation.
SOURCE: https://github.com/vitalets/playwright-bdd/blob/main/test/reporter-data/expected-reports/report-current.txt#2025-04-22_snippet_0

LANGUAGE: text
CODE:
```
[pw:api] page.goto(about:blank) features/pom.ts:11:21
```