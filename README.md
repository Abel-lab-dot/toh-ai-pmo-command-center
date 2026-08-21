# 🚀 TOH AI PMO Command Center

### AI-Powered Project Health Monitoring, Governance & Human-in-the-Loop Escalation

> A practical AI transformation prototype that uses **n8n + Google Gemini** to automate project health analysis, governance routing, management approvals, and stakeholder communication.

![Status](https://img.shields.io/badge/Status-Portfolio%20MVP-orange)
![n8n](https://img.shields.io/badge/Automation-n8n-red)
![Gemini](https://img.shields.io/badge/AI-Google%20Gemini-blue)
![Human in the Loop](https://img.shields.io/badge/Governance-Human--in--the--Loop-green)

---

## 🎯 Business Problem

Project Managers and PMOs often spend a significant amount of time manually:

- reviewing project status reports
- comparing delivery progress against budget consumption
- checking risks and issues
- monitoring governance compliance
- preparing escalation summaries
- chasing corrective actions
- preparing management communications

Much of this operational work can be automated.

The **TOH AI PMO Command Center** explores how AI can automate project monitoring and governance administration while ensuring that **important management decisions remain with people**.

---

# 💡 Solution

The workflow automatically retrieves project portfolio data and uses **Google Gemini** to analyse each project's health.

Each project is classified into one of three categories:

🟢 **GREEN** — Project is healthy and requires no escalation.

🟠 **AMBER** — Project requires Project Manager review and corrective-action monitoring.

🔴 **RED** — Project requires immediate Executive review.

The AI performs the analysis and prepares decision-support information.

Human decision-makers remain responsible for approving, rejecting, or escalating management actions.

---

# 🧠 How It Works

```text
                PROJECT PORTFOLIO DATA
                         │
                         ▼
                   HTTP Request
                         │
                         ▼
                 Split Projects
                         │
                         ▼
                Google Gemini AI
                         │
                         ▼
             Structured AI Assessment
                         │
                         ▼
              GREEN / AMBER / RED
                 HEALTH ROUTING
               /         |         \
              /          |          \
          GREEN        AMBER         RED
            │             │            │
            │             ▼            ▼
            │        PM Review      Executive
            │             │          Review
            │        ┌────┴────┐   ┌────┴────┐
            │        │         │   │         │
            │   ACKNOWLEDGE ESCALATE APPROVE REJECT
            │        │         │      │       │
            │        │         ▼      │       │
            │        │    Executive   │       │
            │        │      Review    │       │
            │        │                │       │
            └────────┴────────────────┴───────┘
                         │
                         ▼
             Automated Stakeholder
                 Notifications
```

---

# 🟢 GREEN Workflow

Projects classified as **GREEN** require no escalation.

The workflow records that the project is operating within acceptable project-health parameters and allows the governance process to continue without unnecessary intervention.

This helps prevent management teams from spending time reviewing projects that do not require attention.

---

# 🟠 AMBER Workflow

An AMBER project is automatically routed to the **Project Manager**.

The PM receives the AI-generated project assessment and must make a management decision.

### Option 1 — ACKNOWLEDGE

The Project Manager:

- acknowledges the issue
- defines a corrective action
- establishes a target completion date

The workflow then:

- registers the corrective action
- marks the project for continued monitoring
- generates a professional HTML notification
- automatically sends the action notification to the relevant stakeholder

### Option 2 — ESCALATE

If the Project Manager determines that the issue requires senior management intervention, the workflow escalates the project to an **Executive Review**.

The Executive can then:

**APPROVE**

or

**REJECT**

the proposed action.

The appropriate workflow path and stakeholder communication are then triggered automatically.

---

# 🔴 RED Workflow

Projects classified as RED bypass the normal PM review and move directly to **Executive review**.

The AI provides the Executive with a concise assessment containing information such as:

- project health
- delivery progress
- budget consumption
- milestone delays
- critical issues
- major risks
- resource constraints
- governance concerns

The Executive can then:

### APPROVE

The escalation is approved for action and the relevant stakeholders are notified.

### REJECT

The proposed escalation is stopped and the decision is communicated to the relevant project stakeholders.

---

# 👤 Human-in-the-Loop AI Governance

A core design principle of this project is:

> **AI analyses. Humans decide. Automation executes.**

The AI does not autonomously approve major project decisions.

Instead, Gemini acts as a **decision-support layer**.

Project Managers and Executives remain accountable for decisions involving corrective actions and escalations.

This architecture helps combine the speed of AI automation with appropriate management oversight.

---

# 🤖 AI Project Health Analysis

Gemini evaluates multiple project-health signals, including:

### Delivery

- progress percentage
- overdue milestones
- schedule pressure

### Financial Performance

- total project budget
- current spend
- relationship between budget consumption and delivery progress

### Issues & Risks

- number of open issues
- critical issues
- high-severity issues
- risk probability
- risk impact
- mitigation status

### Resources

- planned FTE
- actual FTE
- unfilled critical roles

### Governance

- status-report compliance
- risk-register status
- overdue Steering Committee meetings
- missing governance documentation

### Recent Project Updates

Free-text project information is also considered by the AI when generating its assessment.

---

# 📊 Demo Portfolio

The current demonstration portfolio contains three projects deliberately designed to represent different governance scenarios.

| Project | Business Area | Intended Scenario |
|---|---|---|
| **PRJ-001 — ERP Finance Migration** | Finance | 🔴 RED |
| **PRJ-002 — Employee Onboarding Automation** | HR | 🟢 GREEN |
| **PRJ-003 — Service Analytics Modernization** | Operations | 🟠 AMBER |

Because the health assessment is AI-generated, exact health scores and wording may vary slightly between executions.

---

# 📧 Dynamic Stakeholder Communication

The workflow dynamically identifies project stakeholders from the portfolio dataset.

Examples include:

```text
project_manager
project_manager_email
sponsor
sponsor_email
```

This enables notifications to be routed according to the project being processed rather than using a single fixed recipient.

Professional HTML emails are generated for scenarios including:

- PM corrective action registered
- Executive corrective-action approval
- Executive rejection / return to PM
- RED executive escalation approval
- RED executive escalation rejection

---

# ⚙️ Workflow Triggers

The workflow supports two execution modes.

### Manual Trigger

Used for development, testing and live demonstrations.

```text
Execute Workflow
      │
      ▼
PMO Analysis
```

### Webhook Trigger

Provides a production-style integration endpoint.

```text
POST /webhook/pmo-project-health
```

This allows another application or system to initiate the PMO analysis process.

The current portfolio deployment runs locally through Docker/n8n, so the production webhook is currently available within the local environment.

---

# 🛠 Technology Stack

| Technology | Purpose |
|---|---|
| **n8n** | Workflow orchestration and automation |
| **Google Gemini** | AI project-health analysis |
| **Structured Output Parser** | Enforces structured AI responses |
| **Gmail API / OAuth** | Automated stakeholder notifications |
| **GitHub** | Portfolio data and project source repository |
| **JSON** | Project portfolio data model |
| **Webhooks / REST** | Workflow triggering and integration |
| **Docker** | Local n8n runtime environment |

---

# 🏗 Architecture

```text
GitHub Portfolio Data
        │
        ▼
   HTTP Request
        │
        ▼
   n8n Workflow
        │
        ▼
 Google Gemini
        │
        ▼
Structured Output
        │
        ▼
Health Classification
        │
 ┌──────┼──────┐
 │      │      │
GREEN AMBER   RED
 │      │      │
 │   PM Review │
 │      │      │
 │   Executive │
 │     Review  │
 │      │      │
 └──────┼──────┘
        │
        ▼
 Gmail Notifications
```

---

# 🧩 Key Automation Components

The workflow currently includes:

- GitHub project-data retrieval
- portfolio project splitting
- Gemini-powered project-health analysis
- structured AI output validation
- GREEN / AMBER / RED routing
- Project Manager review forms
- corrective-action registration
- Executive approval forms
- approval/rejection routing
- dynamic stakeholder resolution
- professional HTML email generation
- Gmail automation
- manual execution trigger
- production-style webhook trigger

---

# 👨‍💻 What I Built

I designed and implemented the complete prototype, including:

- project portfolio data model
- AI project-health assessment logic
- Gemini integration
- structured output schema
- n8n orchestration architecture
- GREEN / AMBER / RED governance rules
- Project Manager review process
- Executive approval process
- human-in-the-loop decision architecture
- corrective-action routing
- dynamic email-recipient logic
- automated HTML stakeholder communications
- webhook execution capability
- workflow testing and debugging

The goal was not simply to create an AI chatbot.

The objective was to demonstrate how **AI can be embedded into an operational management process and connected directly to real business actions**.

---

# 🎯 AI Transformation Principles Demonstrated

This project demonstrates several principles relevant to enterprise AI transformation.

### Automation before administration

Repetitive reporting, routing and communication can be automated rather than manually coordinated.

### Prototype first

A functional prototype was built before designing a large enterprise architecture.

### Human accountability

High-impact management decisions remain with Project Managers and Executives.

### Decision support rather than AI replacement

AI identifies signals and generates insights; people provide organisational judgement.

### Integration over isolation

AI becomes significantly more useful when connected to business processes, data, approvals and communication systems.

### Supportability

The workflow separates project data, AI analysis, governance logic and communication steps so that the solution can be understood and extended.

---

# 📁 Repository Structure

```text
toh-ai-pmo-command-center/
│
├── data/
│   └── projects.json
│
├── prompts/
│   └── project-health-system-prompt.txt
│
├── schemas/
│   └── project-health-output-schema.json
│
├── workflows/
│   └── n8n workflow export
│
└── README.md
```

---

# 🧪 Example RED Scenario

Consider a project where:

```text
Delivery progress:      61%
Budget consumed:        82%
Overdue milestones:     2
Critical issues:        7
Critical role unfilled: 1
Steering Committee:     9 days overdue
Risk register:          Outdated
```

The AI identifies the combination of financial, delivery, risk, resource and governance signals and classifies the project as requiring executive attention.

The workflow then routes the project to Executive review rather than simply generating another status report.

---

# 📈 Current Version

## v0.9 — Portfolio MVP

Current capabilities include:

✅ AI project-health analysis  
✅ GREEN / AMBER / RED classification  
✅ Project Manager review  
✅ Executive approval/rejection  
✅ Human-in-the-loop governance  
✅ Corrective-action workflow  
✅ Dynamic stakeholder routing  
✅ Automated HTML email notifications  
✅ Manual execution  
✅ Webhook triggering  
✅ Published n8n workflow version  

---

# 🗺 Roadmap

Planned next iterations include:

- Jira integration
- Confluence integration
- Azure DevOps integration
- automated RAID-log monitoring
- persistent decision and audit history
- portfolio dashboard
- scheduled portfolio health checks
- AI-generated weekly PMO reporting
- automated meeting-summary ingestion
- escalation SLA monitoring
- configurable project-health thresholds
- enterprise authentication for external webhooks
- cloud deployment of n8n
- observability and workflow error handling

---

# 🌍 Potential Enterprise Use Cases

The same architecture can be extended beyond PMO governance to areas such as:

- transformation programme management
- IT portfolio governance
- digital transformation offices
- product portfolio management
- risk management
- operational governance
- client delivery management
- consulting programme oversight

---

# 📌 Project Status

This repository represents a **working portfolio MVP** built to demonstrate practical AI transformation, automation orchestration and human-in-the-loop governance.

It is intentionally designed as an evolving prototype rather than a finished commercial product.

---

## Author

**Abel Gnonsoa**

Digital Transformation | AI Automation | Technology Delivery | PMO

---

### ⭐ Project Vision

> **Remove administrative work from project management so people can focus on clients, priorities and decisions — while AI handles analysis, monitoring and workflow orchestration.**
