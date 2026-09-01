# 🤖 CoffeeShop Manager Assistant ☕

https://github.com/user-attachments/assets/09fda755-6e0b-48ce-b0dd-1f90b72942e7

> 🎥  Watch **CoffeeShop Manager Assistant** in action!

> [!CAUTION]
> The Cloud Run deployment is currently unavailable because the Google Cloud project has exhausted its available credits. The project was previously deployed and tested successfully on Google Cloud Run.

---

## Table of Contents

- [Introduction](#introduction)
- [Architecture Diagram](#architecture-diagram)
- [Project Structure](#project-structure)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Application Workflow](#application-workflow)
- [Coffee Shop Operations Data](#coffee-shop-operations-data)
- [Screenshots](#screenshots)
- [Agent Behavior and Safety](#agent-behavior-and-safety)
- [AI-Assisted Development](#ai-assisted-development)
- [Google Codelab Reference](#google-codelab-reference)
- [Future Enhancements](#future-enhancements)
- [Resources](#resources)
- [Disclaimer](#disclaimer)
- [Contributing](#contributing)
- [License](#license)
- [Author](#author)

---

## Introduction

**CoffeeShop Manager Assistant** is an AI-powered business analysis assistant designed to help coffee shop managers make operational decisions using historical sales data, event schedules, and AI-assisted analysis.

The application combines the **Google Agent Development Kit (ADK)**, a **Gemini-powered LLM agent**, **Cloud Run sandboxes**, and the **Google Sheets API** to analyze coffee shop operational data and generate actionable recommendations for staffing and inventory planning.

The assistant is designed around a graduation-weekend scenario. It analyzes historical POS data from a `POS-2025` spreadsheet tab, correlates product demand with ceremony schedules, identifies potential wait-time bottlenecks, and recommends operational actions for upcoming high-volume periods.

A key part of the workflow is **human-in-the-loop approval**. The assistant presents its findings and suggested staffing or inventory tasks to the manager before making any spreadsheet changes. Only after explicit approval can the agent create or update the `TODO-2026` spreadsheet tab.

The application is deployed as a containerized service on **Google Cloud Run**, providing a cloud-hosted runtime for the AI agent and chat interface.

---

## Architecture Diagram

The following diagram illustrates the high-level architecture of **CoffeeShop Manager Assistant**, including the user's browser, Google Cloud Run, FastAPI application, Google Agent Development Kit (ADK), Gemini-powered `LlmAgent`, Cloud Run sandbox, and Google Sheets integration.

The architecture is based on the approach demonstrated in Google's official CoffeeShop Manager Assistant codelab and adapted for this project.

<img width="752" height="361" alt="Architecture Diagram" src="https://github.com/user-attachments/assets/9ba532d9-09ed-45c4-b45d-082589c8d9b5" />

### Architecture Overview

1. **User Browser**
   - Provides the chat interface for the coffee shop manager.
   - Sends business-analysis questions and approval responses to the application.
   - Displays analysis results, bottleneck findings, and recommended tasks.

2. **Google Cloud Run**
   - Hosts the containerized CoffeeShop Manager Assistant.
   - Provides the cloud runtime for the FastAPI application and ADK agent.
   - Provides access to the Cloud Run sandbox environment when deployed.

3. **FastAPI Application**
   - Provides the application backend and HTTP endpoints.
   - Provides a WebSocket endpoint for interactive agent conversations.
   - Serves the coffee-themed web interface.

4. **Google Agent Development Kit (ADK)**
   - Provides the agent development and execution framework.
   - Connects the application with the Gemini-powered agent and available tools.
   - Manages the agent runner and in-memory session service.

5. **Gemini-Powered `LlmAgent`**
   - Acts as the coffee shop business analyst.
   - Interprets the manager's request.
   - Determines how historical data, schedules, and operational information should be analyzed.
   - Produces actionable staffing and inventory recommendations.

6. **Cloud Run Sandbox**
   - Provides an isolated execution environment for agent-generated shell and Python commands when running on Cloud Run.
   - Allows the agent to dynamically create and execute analysis scripts.
   - The application detects the production sandbox environment and uses local execution when the sandbox binary is not available.

7. **Google Sheets API**
   - Reads historical POS data from the configured spreadsheet.
   - Supports creation of the `TODO-2026` sheet tab when required.
   - Writes approved staffing and inventory tasks after manager confirmation.

8. **Gemini Model**
   - Provides model inference for understanding manager requests, analyzing available information, and generating recommendations.

---

## Project Structure

  ```text
 CoffeeShop-ManagerAssistant/
│
├── coffee-mgr-agent/
│   ├── Dockerfile
│   ├── main.py
│   └── requirements.txt
│
├── .gitignore
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── LICENSE
├── README.md
└── SECURITY.md
  ```

> [!NOTE]
> The `coffee-mgr-agent/` directory contains the main **CoffeeShop Manager Assistant** implementation, including the ADK agent, FastAPI application, Google Sheets tools, Cloud Run sandbox integration, WebSocket routing, and web interface.

---

## Features

- **AI-Powered Business Analysis:** Analyze coffee shop operational data and generate actionable business recommendations.
- **Historical POS Analysis:** Reads historical data from the `POS-2025` Google Sheets tab for comparative analysis.
- **Graduation Schedule Analysis:** Uses the current graduation schedule provided by the manager to predict future demand periods.
- **Demand Spike Detection:** Correlates historical beverage demand with ceremony timing to identify expected high-volume periods.
- **Bottleneck Diagnostics:** Evaluates wait times, cashier availability, and complex beverage demand to identify potential operational bottlenecks.
- **Staffing Recommendations:** Recommends additional cashier or support-barista coverage when operational conditions indicate a likely bottleneck.
- **Inventory Recommendations:** Identifies inventory-preparation opportunities for high-demand beverage periods.
- **Cloud Run Sandbox Execution:** Allows the agent to dynamically write and execute Python or shell commands inside the Cloud Run sandbox.
- **Google Sheets Integration:** Reads operational data and writes approved tasks to the manager's spreadsheet.
- **Human-in-the-Loop Approval:** Requires explicit manager approval before modifying spreadsheet data.
- **TODO-2026 Task Management:** Creates the `TODO-2026` sheet tab when necessary and records approved operational tasks.
- **WebSocket Chat Interface:** Provides an interactive conversation channel between the manager and the agent.
- **HTTP API Fallback:** Provides a `/chat` endpoint for sending prompts without using the WebSocket interface.
- **Cloud Deployment:** Runs as a containerized application on Google Cloud Run.
- **Local Development Mode:** Detects when the Cloud Run sandbox is unavailable and supports local command execution for development.

---

## Tech Stack

| Technology                             | Purpose                                                 |
| -------------------------------------- | ------------------------------------------------------- |
| **Python 3.11**                        | Primary programming language                            |
| **Google Agent Development Kit (ADK)** | Agent development and runtime framework                 |
| **Gemini**                             | LLM inference and response generation                   |
| **FastAPI**                            | Backend application and API framework                   |
| **WebSockets**                         | Real-time manager-agent communication                   |
| **Google Sheets API**                  | Reading and updating operational spreadsheet data       |
| **Cloud Run**                          | Serverless container deployment                         |
| **Cloud Run Sandbox**                  | Isolated execution environment for agent-generated code |
| **Docker**                             | Application containerization                            |
| **Google Cloud**                       | Cloud infrastructure and deployment                     |
| **Google Auth**                        | Google Cloud and Sheets authentication                  |
| **Uvicorn**                            | ASGI server for FastAPI                                 |
| **Git**                                | Version control                                         |
| **GitHub**                             | Source code hosting and collaboration                   |

---

## Application Workflow

**CoffeeShop Manager Assistant** follows a data-driven, human-in-the-loop agent workflow.

1️⃣ **Manager Query**

  - The manager opens the CoffeeShop Manager Assistant web interface.
  - The manager asks the agent to analyze business data or provide operational recommendations.
  - Example requests:
    - "Analyze the historical POS data against this year's graduation schedule."
    - "Where are we likely to have the biggest bottlenecks?"
    - "What staffing changes should we make for the busiest ceremonies?"
  
2️⃣ **Request Processing**

  - The web interface sends the manager's message to the FastAPI application.
  - The application forwards the request to the ADK agent runner.

3️⃣ **Agent Analysis**

  - The LlmAgent interprets the manager's request.
  - The agent determines which available tools are required.
  - Historical POS information and the provided graduation schedule are used as inputs for the analysis.

4️⃣ **Data Retrieval**

  - The agent uses the Google Sheets API to read historical data from the `POS-2025` spreadsheet tab.  
  - The agent accesses the configured spreadsheet using the `SPREADSHEET_ID` environment variable.

5️⃣ **Sandbox Analysis**

  - When deeper analysis is required, the agent uses the sandbox tool to write and execute Python or shell commands.
  - The analysis correlates historical product spikes, ceremony timing, wait times, and staffing levels.
  - The agent uses these results to identify likely operational bottlenecks.

6️⃣ **Recommendation Generation**

  - The agent produces a focused set of findings and actionable recommendations.
  - Recommendations may include additional cashier coverage, a support barista, or inventory preparation.
  - The agent presents the recommendations as proposed tasks for the manager.

7️⃣ **Human Approval**

  - The agent explicitly asks whether the manager wants the recommended tasks added to the TODO-2026 sheet.
  - The agent does not modify spreadsheet data before receiving explicit approval.

8️⃣ **Spreadsheet Update**

  - After approval, the agent verifies whether the `TODO-2026` sheet tab exists.
  - If required, the agent creates the tab.
  - Approved tasks are written with fields such as:
    - Task
    - Category
    - Ceremony
    - Date_Added

9️⃣ **Response**

  - The agent confirms the completed spreadsheet updates.
  - The final response is returned through the WebSocket chat interface or HTTP endpoint.

---

## Coffee Shop Operations Data

The CoffeeShop Manager Assistant uses a Google Spreadsheet as its operational data source.

The spreadsheet contains historical `POS-2025` data used for analysis and a `TODO-2026` tab for manager-approved staffing and inventory tasks.

📊 **[View the Coffee Shop Operations Spreadsheet](https://docs.google.com/spreadsheets/d/1ZjCMNEjKtd51O3xk3uGjUj26nj_QDWq6s5xVlTy_Wj0/edit?gid=0#gid=0)**

> [!NOTE]
> The spreadsheet may require appropriate Google account permissions to access.

---

## Screenshots

### Google Sheets Analysis

<img width="1366" height="768" alt="Google Sheets Analysis" src="https://github.com/user-attachments/assets/f1cebb03-36eb-43ac-aaf3-5b517eeefb48" />

### TODO-2026 Spreadsheet

<img width="1366" height="768" alt="TODO-2026 Spreadsheet" src="https://github.com/user-attachments/assets/0418f835-7473-40f0-8931-63ba36653ba7" />

### Google Cloud Run Services

<img width="1366" height="677" alt="Google Cloud Run Services" src="https://github.com/user-attachments/assets/ab4721a5-0952-4efc-a19d-e619f7effb24" />

### Project Source Code

<img width="1363" height="687" alt="Project Source Code" src="https://github.com/user-attachments/assets/838733db-d199-425a-b86c-28fe8a80862e" />

### Cloud Run Overview

<img width="1366" height="686" alt="Cloud Run Overview" src="https://github.com/user-attachments/assets/829e1992-fe2a-4454-a69f-3ff5a81a0508" />

### Cloud Run Service Logs

<img width="1364" height="642" alt="Cloud Run Service Logs" src="https://github.com/user-attachments/assets/5ea9429b-2521-4d05-abbc-b8bc9003b35b" />

### Cloud Run Metrics

<img width="1366" height="642" alt="Cloud Run Metrics-1" src="https://github.com/user-attachments/assets/5dd2fc48-4563-419c-9547-f924d9cb8a78" />
<img width="1366" height="639" alt="Cloud Run Metrics-2" src="https://github.com/user-attachments/assets/99ea7b53-6089-4fd6-90c9-3c63ae79f5b0" />
<img width="1366" height="636" alt="Cloud Run Metrics-3" src="https://github.com/user-attachments/assets/24456639-bf2b-44a1-a1d9-188103c8b540" />
<img width="1366" height="641" alt="Cloud Run Metrics-4" src="https://github.com/user-attachments/assets/9a2960ec-dcb0-4366-978d-afe2cf67eca3" />
<img width="1366" height="634" alt="Cloud Run Metrics-5" src="https://github.com/user-attachments/assets/5e4c8402-615e-44a7-a8d7-45a23c453be4" />
<img width="1366" height="640" alt="Cloud Run Metrics-6" src="https://github.com/user-attachments/assets/1ad31ce3-9966-4744-9ebb-43d2d62c1919" />
<img width="1366" height="635" alt="Cloud Run Metrics-7" src="https://github.com/user-attachments/assets/18f484d8-731a-496a-9c66-459d08182e56" />
<img width="1366" height="643" alt="Cloud Run Metrics-8" src="https://github.com/user-attachments/assets/a4ac1a7a-7c62-4bc8-bb53-0f479408f0cd" />

---

## Agent Behavior and Safety

A key goal of **CoffeeShop Manager Assistant** is to provide useful operational recommendations while keeping the manager in control of spreadsheet modifications.

### Data-Driven Analysis

The agent is instructed to:

  - Read historical POS information from the configured `POS-2025` sheet.
  - Compare historical demand patterns with the provided graduation schedule.
  - Identify beverage demand spikes and potential operational bottlenecks.
  - Use data-driven findings to support staffing and inventory recommendations.

### Bottleneck Diagnostics

The agent evaluates operational conditions such as:

  - Historical wait times.
  - Number of cashiers working.
  - Demand for complex beverages such as Cold Brew, Extra Espresso, and Alt Milk.
  - Expected high-volume periods following ceremonies.

When the available data indicates a likely bottleneck, the agent can recommend operational changes such as additional cashier coverage or a dedicated support barista.

### Human-in-the-Loop Principle

The assistant should:
  - Present findings before making spreadsheet changes.
  - Provide a small number of focused recommendations.
  - Clearly distinguish recommendations from completed actions.
  - Ask for explicit approval before modifying the `TODO-2026` sheet.
  - Confirm exactly which tasks were written after approval.

### Sandbox Execution

The application uses the Cloud Run sandbox environment when the sandbox binary is available in the deployed environment. During local development, the application detects that the production sandbox is unavailable and uses the local execution path instead.

Because the local execution mode can execute commands directly on the developer's machine, it should only be used with trusted prompts and controlled development environments.

---

## AI-Assisted Development

**CoffeeShop Manager Assistant** was developed with the assistance of AI tools during the development and experimentation process.

AI assistance was used to support areas such as:

- Agent structure and implementation.
- Google ADK integration.
- Cloud Run deployment guidance.
- Google Sheets API integration.
- Sandbox tool integration.
- WebSocket and FastAPI implementation.
- Prompt and instruction design.
- Debugging and troubleshooting.
- Documentation and development guidance.

AI-generated suggestions and code were reviewed, modified, integrated, tested, and adapted as part of the development process.

The final project reflects the implemented agent workflow, business-analysis logic, sandbox execution model, Google Sheets integration, human-in-the-loop controls, and Google Cloud deployment configuration.

---

## Google Codelab Reference

This project is based on and extends the concepts demonstrated in Google's official hands-on codelab:

[Run a personal agent on a Cloud Run service (coffee shop manager assistant)](https://codelabs.developers.google.com/codelabs/cloud-run/cloud-run-personal-agent-coffee-shop)

The official codelab demonstrates how to build a coffee shop manager assistant using:

  - Google Agent Development Kit (ADK)
  - Gemini
  - Cloud Run
  - Cloud Run sandboxes
  - FastAPI
  - WebSockets
  - Google Sheets API
  - Historical POS data analysis
  - Staffing and inventory recommendations
  - Human-in-the-loop approval

**CoffeeShop Manager Assistant** follows the core concepts and workflow introduced in the codelab while providing a documented project repository and an implementation-focused presentation of the agent architecture, workflow, tooling, and deployment.

The project should be considered an implementation and extension of the official learning material rather than an entirely independent architecture.

---

## Future Enhancements

The following improvements could be considered in future iterations of **CoffeeShop Manager Assistant**:

- **Persistent Conversation Memory:** Add persistent session history for longer manager-agent interactions.
- **Advanced Forecasting:** Use more sophisticated forecasting models to predict demand beyond schedule-based comparisons.
- **Automated Data Ingestion:** Connect directly to POS systems instead of relying on manually maintained spreadsheet data.
- **Richer Analytics:** Add dashboards for sales, wait times, staffing utilization, inventory, and demand trends.
- **Multi-Store Support:** Extend the assistant to analyze multiple coffee shop locations.
- **Role-Based Access:** Add authentication and separate permissions for managers, staff, and administrators.
- **Automated Alerts:** Notify managers when predicted demand or wait times exceed configured thresholds.
- **Improved Task Management:** Support task status, priority, ownership, and completion tracking.
- **Persistent Database Storage:** Move operational data from spreadsheets to a managed database when the application grows.
- **Agent Evaluation:** Add automated evaluation cases for analytical accuracy, tool usage, and recommendation quality.
- **Observability:** Add structured logging, tracing, and monitoring for agent and sandbox execution.
- **Enhanced Security Controls:** Further restrict and audit sandbox command execution and external resource access.

---

## Resources

[![Google ADK](https://img.shields.io/badge/Google%20ADK-Documentation-4285F4?logo=google)](https://google.github.io/adk-docs/)
[![Gemini API](https://img.shields.io/badge/Gemini%20API-Documentation-8E75B2?logo=google)](https://ai.google.dev/gemini-api/docs)
[![Google Cloud Run](https://img.shields.io/badge/Google%20Cloud%20Run-Documentation-4285F4?logo=googlecloud)](https://cloud.google.com/run/docs)
[![Google Cloud](https://img.shields.io/badge/Google%20Cloud-Documentation-4285F4?logo=googlecloud)](https://cloud.google.com/docs)
[![Gemini Models](https://img.shields.io/badge/Gemini%20Models-Agent%20Platform-8E75B2?logo=google)](https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/google-models)
[![Docker](https://img.shields.io/badge/Docker-Documentation-2496ED?logo=docker)](https://docs.docker.com/)
[![Python](https://img.shields.io/badge/Python-Documentation-3776AB?logo=python)](https://docs.python.org/3/)
[![ADK Python](https://img.shields.io/badge/ADK%20Python-API%20Reference-4285F4?logo=google)](https://google.github.io/adk-docs/api-reference/python/)
[![FastAPI](https://img.shields.io/badge/FastAPI-Documentation-009688?logo=fastapi)](https://fastapi.tiangolo.com/)
[![Google Sheets API](https://img.shields.io/badge/Google%20Sheets%20API-Documentation-34A853?logo=google)](https://developers.google.com/workspace/sheets/api/guides/concepts)
[![Google Codelabs](https://img.shields.io/badge/Google-Codelabs-4285F4?logo=google)](https://codelabs.developers.google.com/)

---

## Disclaimer

**CoffeeShop Manager Assistant** is an AI-powered application developed for learning, experimentation, and demonstration purposes.

The project uses third-party services and technologies including **Google Cloud**, **Cloud Run**, **Cloud Run sandboxes**, **Google Agent Development Kit (ADK)**, **Gemini**, and the **Google Sheets API**. Their availability, functionality, usage limits, pricing, and applicable policies are subject to the respective providers' terms and documentation.

AI-generated analysis and recommendations may contain errors or omissions. Business decisions, staffing changes, inventory planning, and other operational actions should be reviewed by a qualified human before implementation.

The application may execute generated commands through a sandbox environment. Production sandbox behavior and local development behavior are different; local execution should only be used in a trusted development environment.

The project is provided "as is" without warranties of any kind, to the extent permitted by applicable law.

---

## Contributing

Contributions are welcome. Before submitting changes, please review:

- [Contributing Guide](./CONTRIBUTING.md)
- [Code of Conduct](./CODE_OF_CONDUCT.md)
- [Security Policy](./SECURITY.md)

---

## License

This project is licensed under the **Apache License 2.0**.

See the [**LICENSE**](./LICENSE) file for details.

---

## Author

[**Sahil Sharma**](https://github.com/sahil-me)

Thank you for exploring **CoffeeShop Manager Assistant.**. If you found the project useful, consider giving the repository a ⭐ to show your support.
