<!---
Copyright 2026 Sahíl Sharma. All rights reserved.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

# Contribute to CoffeeShop Manager Assistant

Everyone is welcome to contribute, and we value every contribution. Code contributions are not the only way to support the project. Improving AI agent behavior, data analysis, user experience, performance, architecture, security, testing, Google Cloud integration, or documentation are all valuable ways to contribute to **CoffeeShop Manager Assistant**.

If you find this project helpful, consider sharing it with others, referencing it in your blogs or projects, discussing it on social platforms, or simply giving the repository a ⭐️ to support the project and the community.

**However you choose to contribute, please be mindful and respect our [Code of Conduct](https://github.com/sahil-me/CoffeeShop-ManagerAssistant/blob/main/CODE_OF_CONDUCT.md).**

## Ways to contribute

There are several ways you can contribute to **CoffeeShop Manager Assistant**.

* **AI Agent Improvements:** Improve the agent's ability to understand business questions, analyze historical POS data, connect sales patterns with graduation schedules, and provide useful staffing and inventory recommendations.
* **Data Analysis Improvements:** Improve analysis of sales volume, wait times, beverage complexity, cashier availability, staffing requirements, and inventory requirements.
* **Google Sheets Improvements:** Improve spreadsheet reading, spreadsheet updates, data handling, or the human-in-the-loop workflow used before writing approved tasks.
* **Cloud Run Improvements:** Improve deployment, configuration, reliability, startup behavior, resource usage, or Cloud Run integration.
* **Cloud Run Sandbox Improvements:** Improve sandbox-based analysis, command execution, error handling, timeout handling, or local-versus-production behavior.
* **Google ADK / Gemini Improvements:** Improve agent instructions, tool usage, model integration, response quality, and error handling.
* **UI/UX Improvements:** Improve the application's usability, accessibility, responsive design, visual consistency, chat experience, loading states, or error messages.
* **Performance Optimization:** Improve AI response handling, spreadsheet operations, data-analysis performance, startup time, resource usage, or overall application efficiency.
* **Security Improvements:** Help identify and address security issues related to API handling, Google Cloud configuration, IAM, service accounts, secrets, or data access.
* **Documentation:** Improve the README, setup instructions, deployment instructions, architecture documentation, troubleshooting documentation, or other project documentation.
* **Testing:** Add or improve tests for agent behavior, data analysis, spreadsheet operations, sandbox execution, WebSocket communication, or other application components.

> All contributions are equally valuable to the project and community. 🥰

## Submitting a bug-related issue or feature request

At any moment, feel free to open an issue, including relevant error logs, screenshots, browser information, Python version, dependency versions, Google Cloud service information, or other useful information when it is related to a bug.

Please check the existing issues before creating a new one. This helps avoid duplicate reports and makes it easier to track existing problems.

### Did you find a bug?

**CoffeeShop Manager Assistant** becomes more reliable through community feedback, issue reporting, and meaningful contributions.

Before reporting an issue, please make sure the bug has not already been reported under the repository's **Issues** section.

When submitting a bug report, please include the following information:

* Your **operating system** and version.
* Your **browser** and version, if the issue is related to the web interface.
* Steps to reproduce the issue.
* A short description of the expected behavior and what actually happened.
* Relevant error messages or application logs.
* Python version and relevant dependency versions.
* Google Cloud service involved, if applicable.
* Screenshots or screen recordings, if applicable.
* Any other information that may help reproduce or understand the issue.

Please **do not include API keys, passwords, authentication tokens, service-account credentials, spreadsheet credentials, or other sensitive information** in an issue.

### Do you want a new feature?

If there is a new feature you'd like to see in **CoffeeShop Manager Assistant**, please open an issue and describe:

1. **Motivation**  
   Explain the problem, limitation, or use case that the feature would address.

2. **Feature Description**  
   Describe the proposed feature and how you would expect it to work.

3. **AI Agent Behavior**  
   If the feature affects the AI agent, explain how it should influence analysis, recommendations, tool usage, or responses.

4. **Data / Spreadsheet Behavior**
   If the feature affects POS data, graduation schedules, or Google Sheets, explain how the data should be handled.

6. **User Experience**  
   Explain how the feature would improve the experience for the coffee shop manager assistant.

7. **Implementation Details**  
   If you have an implementation idea, architecture suggestion, or code example, feel free to include it.

8. **Additional References**  
   If the feature is inspired by an external project, article, design, or technical reference, please include the relevant link.

A clear and well-written feature request makes it much easier to evaluate and discuss the proposal.

## Do you want to improve the data analysis?

The historical POS data and graduation schedule are important parts of the agent's decision-making workflow.

You can contribute by:

* Improving sales-data analysis.
* Improving identification of popular coffee items.
* Improving wait-time analysis.
* Improving analysis of beverage complexity.
* Improving cashier and staffing analysis.
* Improving inventory recommendations.
* Improving the connection between historical POS data and graduation schedules.
* Improving the accuracy and clarity of generated operational recommendations.

When modifying data-analysis logic, avoid introducing assumptions that are not supported by the available data.

## Do you want to improve AI agent behavior?

Contributions that improve the agent's behavior are especially welcome.

Examples include:

* Improving agent instructions.
* Improving business-question understanding.
* Improving tool selection and tool usage.
* Improving POS-data analysis.
* Improving staffing recommendations.
* Improving inventory recommendations.
* Improving conversational responses.
* Reducing hallucinations.
* Improving error handling.
* Improving follow-up questions.
* Improving the human-in-the-loop approval workflow.
* Improving the agent's ability to clearly explain how recommendations were derived.

Changes to AI behavior should be tested against representative business questions to ensure that existing functionality is not unintentionally affected.

## Do you want to improve Google Sheets integration?

Google Sheets is used as part of the coffee shop manager workflow.

You can contribute by:

* Improving spreadsheet data access.
* Improving spreadsheet reading and analysis.
* Improving spreadsheet update handling.
* Improving creation or handling of the TODO-2026 sheet.
* Improving task formatting.
* Improving error handling for spreadsheet operations.
* Improving the approval workflow before spreadsheet updates.

Changes should preserve the principle that recommended tasks are not written to the spreadsheet without the appropriate user approval.

## Do you want to improve Cloud Run or Sandbox integration?

The application uses Google Cloud services to run the agent and support analysis workflows.

You can contribute by:

* Improving Cloud Run deployment.
* Improving container configuration.
* Improving startup reliability.
* Improving Cloud Run configuration.
* Improving Cloud Run Sandbox execution.
* Improving sandbox error handling.
* Improving command execution and timeouts.
* Improving local development behavior.
* Improving production reliability.
* Improving troubleshooting documentation.

Any infrastructure changes should be tested carefully before being submitted.

## Do you want to add documentation?

We're always looking for improvements to the documentation that make CoffeeShop-ManagerAssistant clearer and easier to understand.

You can contribute by:

* Fixing typos or grammatical errors.
* Improving setup instructions.
* Adding missing documentation.
* Clarifying Google Cloud configuration steps.
* Improving deployment instructions.
* Documenting the agent architecture.
* Documenting the data-analysis workflow.
* Adding examples.
* Improving troubleshooting documentation.
* Documenting Google Sheets integration.
* Documenting Cloud Run and Cloud Run Sandbox usage.
* Documenting AI agent behavior and tools.

Documentation contributions are highly appreciated, especially when they make it easier for new contributors to get started.

## Fixing outstanding issue

If you notice an existing issue and have a fix in mind, feel free to **[start contributing](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)** and open a Pull Request.

### Making code changes

<details>

1. **Fork the Repository**

   Go to the CoffeeShop Manager Assistant repository on GitHub and click the **Fork** button.

2. **Clone your forked repository**

   ```bash
   git clone https://github.com/<username>/CoffeeShop-ManagerAssistant.git
   ```
   Navigate into the project directory:

    ```bash
   cd CoffeeShop-ManagerAssistant
   ```

3. **Create a New Branch**

   ```bash
   git checkout -b feature/your-feature-name
   ```

4. **Set Up the Python Environment**

    Make sure Python is installed and create a virtual environment:

    ```bash
    python -m venv .venv
    ```

    Activate the virtual environment.

    **Windows PowerShell:**
    
    ```bash
    .\.venv\Scripts\Activate.ps1
    ```
  
    **macOS / Linux:**
  
    ```bash
    source .venv/bin/activate
    ```

5. **Install Dependencies**

     Install the required Python packages:
  
     ```bash
     pip install -r requirements.txt
     ```

     If the project contains multiple components with their own **requirements.txt** files, install the dependencies required for the component you are working on.

6. **Configure Google Cloud**

     Configure your Google Cloud project, region, required APIs, authentication, service account, and other services according to the project's README and deployment instructions.

   > Never commit API keys, service-account credentials, access tokens, or other secrets to the repository.

7. **Configure Environment Variables**

     Use environment variables for project-specific configuration such as Google Cloud project, region, location, and spreadsheet ID.

   > Do not commit **.env** files containing sensitive information.

8. **Run the Application Locally**

    Follow the project's README instructions to start the relevant application or agent locally.

    Make sure the application starts successfully before making or testing changes.

9. **Make Your Changes**

    - Develop the feature or fix the issue.
    - Follow the existing project structure and coding conventions.
    - Keep changes focused and maintainable.
    - Avoid unrelated modifications.
    - Test your changes locally before submitting a Pull Request.

10. **Run and Test Agent Behavior**

      If your changes affect the AI agent or business-analysis workflow, test representative scenarios such as:
      - Questions about historical POS data.
      - Questions about popular coffee items.
      - Graduation schedule analysis.
      - Staffing recommendations.
      - Inventory recommendations.
      - Follow-up questions.
      - Spreadsheet update requests.
      - User approval before writing tasks to the spreadsheet.
      - Error and unavailable-data scenarios.

      Verify that the agent remains grounded in the available business data and does not invent unsupported information.

11. **Commit Your Changes**

      ```bash
      git add .
      ```

      ```bash
      git commit -m "Add feature/bugfix description"
      ```

12. **Push to Your Fork**

       ```bash
       git push origin feature/your-feature-name
       ```

13. **Create a Pull Request**

      Go to the original **CoffeeShop Manager Assistant** repository and open a **New Pull Request**.

      In your Pull Request description:
      - Explain what you changed.
      - Explain why the change was needed.
      - Mention any relevant issue.
      - Include screenshots for UI changes when appropriate.
      - Describe any changes to AI-agent behavior.
      - Mention any changes to data analysis or Google Sheets behavior.
      - Mention any Google Cloud or deployment changes.
      - Mention any testing you performed.

14. **Address Feedback**

      If maintainers leave comments or request changes, address the feedback and push the required updates to your branch.

</details>

## Contribution Guidelines

  To keep the project maintainable and welcoming:
  - Keep Pull Requests focused on a single feature, fix, or improvement whenever possible.
  - Avoid unnecessary changes to unrelated files.
  - Follow the existing coding style and project structure.
  - Test changes before submitting a Pull Request.
  - Test AI-agent behavior when modifying agent logic.
  - Test data-analysis behavior when modifying business-analysis logic.
  - Preserve the human-in-the-loop approval workflow.
  - Do not commit secrets, API keys, credentials, .env files, or service-account files.
  - Do not intentionally introduce unsupported or misleading business information.
  - Keep data handling accurate and consistent.
  - Provide clear commit messages and Pull Request descriptions.
  - Include relevant screenshots or test results when appropriate.
  - Be respectful and constructive when reviewing or discussing contributions.

## I want to become a maintainer of the project. How do I get there?

**CoffeeShop Manager Assistant** is an AI-powered coffee shop management assistant designed to analyze historical POS data and graduation schedules and provide operational recommendations for staffing and inventory.

Contributors interested in improving AI agent behavior, Google ADK, Gemini, Vertex AI, Google Sheets integration, Cloud Run, Cloud Run Sandbox, data analysis, WebSocket communication, UI/UX, performance, testing, security, documentation, and Google Cloud deployment are always welcome.

We are happy to welcome motivated contributors who want to take a deeper role in the project and help **CoffeeShop Manager Assistant** evolve into a reliable, helpful, and maintainable AI application.

If you are interested in contributing at a deeper level, consistently submitting meaningful improvements, reviewing Pull Requests, improving documentation, or helping maintain the project, feel free to get involved and collaborate with the community.

Thank you for contributing to **CoffeeShop Manager Assistant**! ☕
  
