---
title: '. career'
description: 'Career timeline: agentic AI systems, Status Pages from zero to GA, and 13+ years of backend engineering across product and consultancy.'
ShowRssButtonInSectionTermList: false
---

---

#### PagerDuty — Senior Software Engineer

Lisbon, Portugal • Jun 2022–Present
*CSOps Status team, then PD Advance / LABS (incubation)*

**AI incident response — 2024 to present**

Agentic incident-response product: LangGraph orchestration over Python services, an SSE streaming layer, a Node BFF, and a Vite single-page client.

- Designed and led the metering platform behind credit-based consumption of AI capabilities, a pricing model new to PagerDuty. Every metered call passes through it, at high throughput inside a tight latency budget, so billing stays accurate and fair-use limits hold without latency users can feel.
- Built the shared memory layer agents write their context into — designed the contracts and use cases directly with the other teams whose agents would depend on it, rather than shipping an interface and asking them to adapt. Now backs several agents in production.
- Separated durable from transient state in the LangGraph checkpointer, so resumed runs replay persisted state without re-emitting intermediate tool traffic — removing a recurring class of context-overflow failures.
- Worked on Agent Connectors, bring-your-own-MCP support that lets agents reach a customer's existing integrations instead of waiting on first-party ones being built.
- Shipped the Skills mechanism for the SRE agent: procedural playbooks loaded at run time instead of hard-coded into prompts. Presented internally at PagerDuty's AI showcase.
- Currently prototyping deeper-reasoning agents for diagnosis and remediation, to shift investigation load off whoever is on call.

**Status Pages — 2022 to 2024**

- Project lead for subscriptions and notifications, two of the three critical user journeys. Designed the notification service to be modular so channels could land incrementally, then shipped email, Slack, webhooks and SMS across three consecutive quarterly releases, each on its committed date.
- Led the storage migration from S3 to DynamoDB once the original design's performance assumptions stopped holding under growth: modelled the schema, wrote the ADRs, and delivered the provisioning. Read latency improved by roughly an order of magnitude.
- Built bring-your-own-identity-provider support for Private Status Pages: customers gate their page behind their own OIDC provider — Azure, Okta, PingID, Salesforce, JumpCloud — instead of exposing it publicly, with onboarding kept to minimal setup. Session handling and JWKS/openid-configuration caching served provider metadata from CloudFront to cut round-trips out to customer identity providers. I ran the setup calls with enterprise customers directly and wrote the provider configuration guides into the company knowledge base.
- Co-led custom domain provisioning — DNS and email white-labelling so notifications send from the customer's own domain. Diagnosed timeouts in de-provisioning and moved the flow async via an ADR, without moving the release date.
- Co-authored the product design document, led the Kubernetes migration, and bootstrapped the codebase for a newly formed team, taking it from first commit to GA in six months. Ran the notification build-versus-buy analysis against the internal platform the team ultimately adopted.
- Owned observability: SLIs and SLOs behind the team's SLAs, structured JSON logging with request correlation, and a monitoring overhaul that cut on-call alert fatigue. Migrated the service to TypeScript and raised test coverage past 70%.

Stack: Python, Elixir, Node.js/TypeScript, LangGraph, AWS (Lambda, SQS, DynamoDB, CloudFront), Kubernetes, Terraform, MySQL, Redis, Elasticsearch

#### Defined.ai — Senior Software Engineer → Lead

Lisbon, Portugal • Jul 2019–May 2022
*Speech and NLP training-data platform built on a global crowd workforce.*

- Led a cross-functional team of eight — four backend, two front-end, two QA, working alongside a PM — building automation and data tooling that replaced manual crowd workflows, cutting human handling per task and improving margin on delivered datasets.
- Owned the technical design for human-in-the-loop quality systems, contributor e-learning and gamification. My scope was the pre-screening tests that gate expert-level work: a contributor had to pass a language-specific assessment — an en-US test before translation tasks, for instance — before that work was offered to them. Raised task throughput by 60%.

Stack: .NET, React, TypeScript, Azure, SQL Server, Spark, Kafka, Superset

#### Truphone — Software Engineer

Lisbon, Portugal • Aug 2017–Jun 2019
*Global eSIM provider and mobile network operator.*

- Gathered stakeholder requirements and defined the architecture for customer-facing portals and mobile apps, on the product line responsible for over 60% of company revenue.
- Part of the team that shipped one of the first iPhone apps built on Apple's initial eSIM release — over-the-air data plans and profile provisioning.

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

#### Patents

Co-inventor on three patent filings at PagerDuty.

#### Education

- MSc, Knowledge Management & Information Systems — ISCTE-IUL, 2018
- Postgraduate Diploma, Computer Science — FCT-NOVA, 2012
- BSc, Computer Science — FCT-NOVA, 2010

---

<i class="fa-solid fa-arrow-left"></i> [About me, skills & contact](/about/)
