# Demoblaze BDD Automation Framework

A test automation framework for [Demoblaze](https://www.demoblaze.com) (a demo e-commerce site), built with **Cucumber BDD + Selenium + TestNG**, and developed using **GitHub Copilot** as an AI pair-programmer.

This project was built as hands-on practice in **AI-assisted test automation** — using Copilot to generate the framework, then applying testing judgment to review, debug, and harden it.

---

## What it tests

**Positive flow (end-to-end purchase):**
Login → navigate to store → select a product → add to cart → view cart → place order → fill the order form → purchase → verify the order confirmation.

**Negative flow (invalid login):**
Attempt login with a valid username and a wrong password → verify the correct error message ("Wrong password.") is shown.

---

## Tech stack

| Layer            | Tool                     |
|------------------|--------------------------|
| Language         | Java 17                  |
| Build            | Maven                    |
| BDD              | Cucumber 7               |
| UI automation    | Selenium 4               |
| Test runner      | TestNG                   |

---

## Project structure

```
src/
├── main/resources/files/
│   └── Demoblaze.feature          # Gherkin scenarios (positive + negative)
└── test/java/
    ├── stepsDef/
    │   └── BlazeSteps.java         # Step definitions + @Before/@After hooks + reusable helpers
    └── runners/
        └── TestRunner.java         # Cucumber + TestNG entry point
```

---

## How to run

**Prerequisites:** Java 17+, Maven, Google Chrome.

```bash
mvn test
```

Or run `TestRunner.java` directly in the IDE. An HTML report is generated at `target/cucumber-report.html`.

---

## Highlights

- **Reusable helpers** — a `jsClick()` method (wait → scroll → JavaScript click) and an `acceptAlert()` method with retry logic, so flaky clicks are handled in one place instead of being repeated.
- **Test lifecycle management** — `@Before` launches a clean browser (incognito, to avoid browser popups) and `@After` closes it, keeping each scenario independent.
- **Explicit waits throughout** — to handle the site's dynamic loading, animated modals, and AJAX re-rendering.
- **Real assertions** — each scenario verifies an outcome (confirmation message, error alert), not just that steps ran.
- **Step reuse** — a shared `Given` step for opening the application, used across scenarios.

---

## Built with GitHub Copilot

Copilot was used to generate the initial step definitions, feature scenarios, and locators. Every suggestion was then **reviewed and corrected** — fixing guessed locators, adding the right waits, choosing JavaScript clicks where normal clicks failed, and deciding what to assert. The AI accelerated the boilerplate; the testing judgment stayed human.
