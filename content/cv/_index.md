---
title: '. career'
description: '13+ years in software engineering across product teams and consultancy, with a focus on backend systems and recent work on agentic AI.'
ShowRssButtonInSectionTermList: false
---

---

#### PagerDuty — Senior Software Engineer

Lisbon, Portugal • Jun 2022–Present
*CSOps Status team, then PD Advance / LABS (incubation)*

**AI incident response — 2024 to present**

Backend services and agent orchestration for an AI incident-response product, built with Python and LangGraph.

- Designed and led the metering service behind AI Actions, PagerDuty Advance's usage-based consumption model. It handles every metered call: over 2,000 requests per minute at roughly 50ms, keeping usage accounting accurate and per-account limits enforced.
- Built the shared memory layer where agents store context. Defined its contracts and use cases with the teams whose agents depend on it. It backs three production agents at roughly 500 requests per minute within a 120ms budget.
- Separated durable state from transient state in the LangGraph checkpointer. Resumed runs now replay persisted state without re-emitting intermediate tool traffic. This removed a recurring class of context-overflow failures.
- Worked on Agent Connectors, which link the SRE Agent to a customer's observability and knowledge sources over API or MCP so it can query their existing tooling.
- Shipped the Skills mechanism for the SRE Agent: custom instructions and runbooks it loads at run time to follow a team's procedures. Presented it internally at PagerDuty's AI showcase.

**Status Pages — 2022 to 2024**

- Project lead for subscriptions and notifications, two of the product's three critical user journeys. Designed the notification service so channels could land incrementally, then shipped email, Slack, webhooks, and SMS across three consecutive quarterly releases, each on its committed date.
- Modelled the persistence schema and documented the decision in ADRs. Estimated a reduction in read latency from roughly 200ms to under 10ms.
- Built bring-your-own-identity-provider support for Private Status Pages. Customers can restrict access through OIDC providers including Azure, Okta, PingID, Salesforce, and JumpCloud with minimal setup. Cached JWKS and OpenID Connect discovery data in CloudFront to reduce calls to customer identity providers. The capability supported premium-tier upsell into enterprise accounts; I ran setup calls with those customers and wrote the provider configuration guides for the company knowledge base.
- Co-led custom-domain provisioning for DNS and email white-labelling, allowing notifications to send from the customer's domain. Diagnosed de-provisioning timeouts and moved the flow to asynchronous processing. Documented the decision in an ADR and kept the original release date.
- Co-authored the product design document, led the Kubernetes migration, and bootstrapped the codebase for a new team. It went from first commit to GA in six months. Ran the notification build-versus-buy analysis against the internal platform the team adopted.
- Owned observability, including SLIs and SLOs behind the team's SLAs, structured JSON logging with request correlation, and a monitoring overhaul that reduced on-call alert fatigue. Migrated the service to TypeScript and raised test coverage past 70%.

Stack: Python, Elixir, Node.js/TypeScript, LangGraph, AWS (Lambda, SQS, DynamoDB, CloudFront), Kubernetes, Terraform, MySQL, Redis, Elasticsearch

#### Defined.ai — Senior Software Engineer → Lead

Lisbon, Portugal • Jul 2019–May 2022
*Speech and NLP training-data platform built on a global crowd workforce.*

- Led a team of eight: four backend engineers, two front-end engineers, and two QA engineers, working alongside a PM. Built automation and data tooling that replaced manual crowd workflows, reducing human handling per task and improving margin on delivered datasets.
- Owned the technical design for human-in-the-loop quality systems, contributor e-learning, and gamification. My scope included pre-screening tests for expert-level work. Contributors had to pass a language-specific assessment, such as an en-US test before translation tasks, before they could receive that work. Raised task throughput by 60%.

Stack: .NET, React, TypeScript, Azure, SQL Server, Spark, Kafka, Superset

#### Truphone — Software Engineer

Lisbon, Portugal • Aug 2017–Jun 2019
*Global eSIM provider and mobile network operator.*

- Gathered stakeholder requirements and defined the architecture for customer-facing portals and mobile apps, on the product line responsible for over 60% of company revenue.
- Part of the team that shipped one of the first iPhone apps built on Apple's initial eSIM release, supporting over-the-air data plans and profile provisioning.

Stack: .NET, React Native, TypeScript, MongoDB, Elasticsearch, SQL, Java, Spark

#### BookedBy — Software Engineer

Lisbon, Portugal • Jan 2016–Aug 2017
*Booking and management SaaS for multi-location service businesses.*

- Shipped an online booking product that ran standalone or embedded in client sites, removing the need for per-client custom development.
- Built a central management platform pushing promotions, inventory and users across multi-store chains, plus the data warehouse behind manager reporting.

Stack: Node.js, React, Backbone.js, .NET, PostgreSQL, Docker, AWS

#### ROFF — Developer

Lisbon, Portugal • Mar 2012–Jan 2016

- Designed an API integrating SAP QM with touchscreen shop-floor workflows and led technical direction for SAP integrations.
- Warehouse management with path optimisation; automated production cost allocation for manufacturing clients.

Stack: .NET, SQL, SAP ABAP, Excel add-ins, JavaScript

#### InspirennovIT — Developer

Almada, Portugal • Sep 2011–Mar 2012

- R&D for public-sector productivity tooling.
- Built a PDF digital-signature workflow using the Portuguese citizen card, with SharePoint approval routing.

Stack: .NET, EF, SQL Server, SharePoint, JavaScript

#### Research Grant — FCT-NOVA

Almada, Portugal • 2011–2012 *(concurrent)*

- Academic data warehouse for candidate analytics; extraction tooling and geographic clustering/visualisation.

Stack: SQL, MySQL, Pentaho BI, Java

---

#### Education

- MSc, Knowledge Management & Information Systems — ISCTE-IUL, 2018
- Postgraduate Diploma, Computer Science — FCT-NOVA, 2012
- BSc, Computer Science — FCT-NOVA, 2010

---

<i class="fa-solid fa-arrow-left"></i> [About me, skills & contact](/about/)
