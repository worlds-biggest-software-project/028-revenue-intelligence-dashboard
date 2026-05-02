# Revenue Intelligence Dashboard — Feature & Functionality Survey

> Candidate #28 · Researched: 2026-05-02

## Solutions Analysed

| Tool | Type | Licence / Model | URL |
|------|------|-----------------|-----|
| ChartMogul | Commercial SaaS | Proprietary; free up to $10K MRR, then usage-based | https://chartmogul.com |
| Baremetrics | Commercial SaaS | Proprietary; ~$108–$500+/mo by MRR volume | https://baremetrics.com |
| ProfitWell (by Paddle) | Commercial Freemium | Proprietary; free core metrics; paid add-ons | https://www.paddle.com/profitwell-metrics |
| Clari (merged with Salesloft) | Commercial Enterprise | Proprietary; ~$100–$200+/user/mo | https://www.clari.com |
| Gong | Commercial Enterprise | Proprietary; ~$1,300–$3,000/user/year | https://www.gong.io |
| Metabase | Open Source + Cloud | OSS: AGPL v3 (core); Proprietary (Enterprise); Cloud from $85/mo | https://www.metabase.com |

## Feature Analysis by Solution

### ChartMogul

**Core features**
- Real-time MRR/ARR, churn, ARPA, LTV, and CLV calculation from billing source data
- MRR movement waterfall: new, expansion, contraction, churn, and reactivation breakdowns
- Cohort analysis tracking retention curves across customer groups by signup date or plan
- Customer segmentation by plan, geography, billing interval, and custom attributes
- Subscription analytics covering trials, leads, and conversion funnels
- Built-in CRM functionality (CRM Pro) with task management, email sequences, and activity feed alongside live MRR data
- Finance-grade metrics for ASP, ARR, and investor reporting exports

**Differentiating features**
- Multi-source ingestion across Stripe, Braintree, Recurly, Chargify, PayPal, and custom data imports in a single unified view
- CRM functionality embedded alongside live subscription data (not a separate product)
- Usage-based pricing model that aligns cost with business scale (free tier up to $10K MRR)
- Data Import API and webhooks for custom billing systems not served by native connectors

**UX patterns**
- Dashboard-first design with metric tiles and pre-built charts requiring no configuration
- Segmentation builder uses dropdown filters rather than code or SQL
- Chart export for board presentations and investor reporting is a first-class workflow
- Alert system for unusual MRR movements delivered via email or Slack

**Integration points**
- Native connectors: Stripe, Braintree, Recurly, Chargify, Zuora, PayPal, App Store / Google Play
- CRM integrations: HubSpot, Salesforce (read)
- Notification integrations: Slack, Zapier
- REST API and webhooks for custom pipelines
- Intercom integration for in-app customer data enrichment

**Known gaps**
- Forecasting capability is limited; projections rely on simple trend extrapolation rather than ML-based models
- No native conversation intelligence or pipeline-level CRM workflow automation
- Limited in-product alerting logic (cannot build custom anomaly detection rules)
- Reporting UI has fewer customisation options than general-purpose BI tools
- No built-in dunning (payment recovery) — requires separate tool or Paddle integration

**Licence / IP notes**
- Fully proprietary SaaS; no open-source component. No patent concerns identified from public sources. Standard SaaS terms apply; data residency options limited at lower tiers.

---

### Baremetrics

**Core features**
- Tracks over 26 subscription KPIs including MRR, ARR, ARPU, LTV, CAC, quick ratio, and churn rate
- Automatic MRR movement segmentation: new, expansion, contraction, churn, and reactivation streams
- Cohort analysis with retention visualisation
- Dunning (Recover): automated failed-payment recovery workflows reduce involuntary churn
- Cancellation Insights: collects structured cancellation reasons at the moment of churn
- Customer dashboard with individual account MRR history, plan, and health signals
- Benchmarking against anonymised data from 34,000+ subscription businesses

**Differentiating features**
- Recover (dunning) is native and tightly integrated, not a third-party add-on
- Cancellation flow capture (Cancellation Insights) surfaces qualitative churn data alongside metrics
- Competitor benchmarking against an industry dataset is unique at this price point
- Direct Stripe integration is among the deepest in the market (handles multiple Stripe accounts)

**UX patterns**
- Opinionated, minimal UI prioritising simplicity over configurability
- Pre-built metric dashboards require near-zero setup for Stripe users
- Customer-level drilldown accessible directly from aggregate metrics
- Email digest and Slack notification support for daily/weekly metric summaries

**Integration points**
- Native billing connectors: Stripe, Braintree, Recurly, App Store, Google Play, Paddle
- Webhook and REST API for data export
- Zapier for lightweight automation workflows
- Limited native CRM integrations compared to ChartMogul

**Known gaps**
- Tightly coupled to Stripe — less capable for organisations with complex multi-billing-system stacks
- No AI-powered forecasting or anomaly explanation; trend projection is rule-based
- Limited custom segmentation compared to ChartMogul
- Not suitable as a standalone CRM; customer management features are read-oriented
- Enterprise-grade access controls and SSO only available on higher-priced plans

**Licence / IP notes**
- Fully proprietary SaaS. No open-source component. No patent concerns identified in public sources.

---

### ProfitWell (by Paddle)

**Core features**
- Core subscription metrics (MRR, ARR, LTV, CAC, churn, ARPU) available free with unlimited historical data
- Revenue retention breakdown by cohort with expansion/contraction analysis
- Customer health scores surfacing accounts at risk of churn
- Retain: automated churn-reduction product using personalised offers and smart dunning
- Benchmarking against a proprietary dataset of 30,000+ SaaS companies
- Native integration into Paddle Billing dashboard with no additional setup

**Differentiating features**
- Only major subscription analytics product with a genuinely free tier covering core metrics with no MRR cap (up to $120K ARR for core Pro)
- Paddle ownership means billing and analytics are natively unified for Paddle customers
- Industry benchmarking dataset is among the largest available (30,000+ SaaS companies)
- Retain uses A/B-tested, personalised deflection offers rather than generic dunning emails

**UX patterns**
- Dashboard focus on simplicity; minimal configuration required after billing system connection
- Reports refresh every 3–6 hours rather than real-time (latency is a known trade-off)
- Retain flows are managed through a separate interface, creating context switching

**Integration points**
- Deeply integrated with Paddle Billing; also supports Stripe, Braintree, Recurly, Chargebee
- Retain webhooks allow custom deflection logic
- Limited REST API surface compared to ChartMogul

**Known gaps**
- The free tier covers only core metrics; advanced retention, dunning, and revenue recognition require paid add-ons sold as separate products, making total cost less transparent
- Product suite feels fragmented following Paddle acquisition (Metrics, Retain, and Recognised are separate purchasable products)
- Dashboard refresh latency (3–6 hours) is a disadvantage vs. real-time tools
- Limited segmentation depth and no native CRM functionality
- Non-Paddle billing integration quality varies

**Licence / IP notes**
- Fully proprietary SaaS (Paddle-owned). No open-source components. No patent concerns identified.

---

### Clari (merged with Salesloft, December 2025)

**Core features**
- AI-powered pipeline forecasting with deal-level risk scoring and commit/upside categorisation
- Revenue Cadences: structured playbooks linking forecasting insights to sales execution actions
- Conversation intelligence (via former Copilot / Salesloft capability): call recording, transcription, and AI analysis of deal language
- AI Action Hub: automated deal health monitoring, risk flagging, and recommended next actions
- CRM data hygiene: automated pipeline updates based on activity signals
- Revenue analytics dashboards for CRO, VP Sales, and RevOps personas
- MCP Server (released April 2026): opens live revenue data to external AI tools via Model Context Protocol

**Differentiating features**
- Post-merger combination of forecasting precision and sales execution is unique among revenue intelligence platforms
- Ingests over 10 billion revenue actions and 1 trillion data signals annually — one of the largest proprietary training datasets for revenue AI
- MCP Server exposes live pipeline data to third-party AI agents, enabling integration with tools like Claude and custom enterprise AI
- Revenue Cadences connect forecast anomalies directly to rep workflows without leaving the platform

**UX patterns**
- Enterprise-grade UI targeting VP and C-level personas, not individual contributors
- Forecast dashboard uses a waterfall and deal-level grid with AI confidence indicators
- Heavy Salesforce and HubSpot CRM embedding — many users access Clari from within their CRM
- Significant onboarding time; typical deployment spans several weeks with professional services

**Integration points**
- Deep bidirectional integrations with Salesforce, HubSpot, Microsoft Dynamics
- Email/calendar capture: Gmail, Outlook, Google Calendar
- Video conferencing: Zoom, Teams, Webex (for conversation intelligence)
- MCP Server for external AI tool connectivity (April 2026)
- Slack for notifications and deal alerts

**Known gaps**
- Price point ($100–$200+/user/mo) is prohibitive for SMB and mid-market
- Post-merger platform integration between Clari and Salesloft is still in progress (as of 2026); some features remain siloed
- Subscription/billing-metric coverage (MRR/ARR SaaS metrics) is weaker than purpose-built tools like ChartMogul
- No self-serve free tier; sales-led procurement only
- 87% of enterprises surveyed by Clari Labs still miss revenue targets despite AI spend, suggesting forecasting accuracy remains imperfect

**Licence / IP notes**
- Fully proprietary enterprise SaaS. No open-source components. The merger with Salesloft (Dec 2025) creates a large combined IP portfolio; no specific patent encumbrances identified in public sources, but the breadth of AI model IP in conversation intelligence is a consideration for competitive products.

---

### Gong

**Core features**
- Conversation intelligence: records, transcribes, and AI-analyses every sales call, email, and meeting
- Gong Forecast: AI-powered pipeline and revenue forecasting using deal engagement signals, not just CRM fields
- Gong Engage: sales engagement layer for prioritising and personalising outreach
- Gong Enable: AI Call Reviewer grades rep performance against a customisable methodology; AI Trainer lets reps practice against AI simulations
- Gong Agents: automate post-call follow-ups, CRM updates, and forecast corrections
- Initiative Tracking: links specific coaching programmes to measurable revenue outcomes
- Mission Andromeda (2026): AI coaching, sales chatbot, unified account management, and MCP-based interoperability with rival AI systems

**Differentiating features**
- Industry benchmark for call intelligence quality and rep coaching based on real conversation data
- AI Trainer using a company's own winning call patterns to simulate realistic sales conversations is unique
- MCP-based interoperability (Mission Andromeda, 2026) opens Gong data to external AI agents
- Initiative Tracking linking coaching to revenue metrics bridges the coaching-to-outcome gap
- Breadth of signal capture (calls, emails, meetings) provides a richer dataset than CRM-only tools

**UX patterns**
- Deal-centric view shows all conversation activity and risk signals per account
- Call review interface highlights key moments, topic tags, and talk-time ratios
- Manager dashboards for coaching pipeline, team performance, and forecast review
- Browser extension and Salesforce embedded widget for in-context access
- High-quality mobile apps for on-the-go call review

**Integration points**
- CRM: Salesforce, HubSpot, Microsoft Dynamics (bidirectional)
- Video conferencing: Zoom, Teams, Webex, Google Meet
- Email and calendar: Gmail, Outlook, Google Calendar
- Slack for deal alerts and coaching nudges
- MCP Server for external AI tool connectivity (2026)
- API for custom data extraction

**Known gaps**
- Pricing ($1,300–$3,000/user/year) makes it inaccessible for SMB
- Focused on sales-motion intelligence; subscription/billing metrics (MRR, ARR, churn) are outside its scope
- Conversation intelligence accuracy degrades for non-English languages and highly technical calls
- Heavy dependency on Salesforce limits value for CRM-free or HubSpot-primary organisations
- No native self-serve trial; procurement requires sales engagement

**Licence / IP notes**
- Fully proprietary enterprise SaaS. No open-source components. Gong holds multiple AI/ML patents related to conversation analysis and deal-risk scoring; competitive products should design independently to avoid infringement risk.

---

### Metabase / Redash (self-hosted BI)

**Core features**
- No-code query builder (Question interface) and SQL editor for flexible data access
- Dashboard creation with 20+ chart types, filters, and drill-through
- Alerts and scheduled dashboard subscriptions delivered via email, Slack, or webhook
- Data Studio for creating and governing reusable metrics and canonical dataset definitions
- Embedded analytics SDK for white-labelled analytics within third-party products
- Metabot: AI assistant for query writing and data questions (2025 addition)
- 60,000+ active organisations; 40,000+ GitHub stars; 2–3 releases per month

**Differentiating features**
- Strongest open-source BI tool for embedded analytics use cases (white-label, iframe, component library)
- No-subscription-metric semantics out of the box — but fully configurable once billing data is in a warehouse
- AGPL v3 core is free to self-host with unlimited users at no licence cost
- Metabot AI assistant for query writing is built in at no extra cost on Cloud plans

**UX patterns**
- Consumer-grade UI design compared to enterprise BI tools; low barrier to entry for non-analysts
- "Ask a question" metaphor abstracts SQL for business users
- Dashboard subscriptions and alerts are first-class features, not add-ons
- Setup requires a connected data warehouse — no built-in billing source ingestion

**Integration points**
- Database connectors: PostgreSQL, MySQL, BigQuery, Snowflake, Redshift, MongoDB, and 30+ others
- BI embedding via SDK and REST API
- Notification: Slack, email, webhooks
- SSO: SAML, LDAP (Enterprise edition)
- No native Stripe/Recurly billing connector — billing data must flow through a warehouse first

**Known gaps**
- Zero subscription-metric semantics; MRR/ARR calculations, churn cohorts, and payment-state logic must be coded from scratch
- Not a revenue intelligence tool — it is a general-purpose BI tool that can be adapted
- AGPL v3 licence requires open-sourcing modifications if distributed; enterprise features (SAML, auditing) require the proprietary Enterprise licence
- Data freshness depends on ETL/ELT pipeline cadence, not real-time billing webhooks
- No built-in dunning, cancellation flows, or billing system orchestration

**Licence / IP notes**
- Core is AGPL v3 (copyleft). The Enterprise edition adds proprietary features under a commercial licence. AGPL requires that any distribution of modified Metabase (e.g., as a hosted SaaS product) open-source those changes — this is a material concern for any commercial product built on top of Metabase. No patent encumbrances identified in public sources.

---

## Cross-Cutting Feature Themes

### Table-Stakes Features
- Real-time or near-real-time MRR/ARR/churn/NRR/GRR metric calculation from at least one billing source (Stripe minimum)
- MRR movement waterfall (new, expansion, contraction, churn, reactivation)
- Cohort retention analysis by signup date or plan
- Customer-level drilldown with subscription and payment history
- Basic alerting for metric anomalies (threshold-based)
- Dashboard sharing and export for investor / board reporting
- Secure authentication (OAuth, SSO at enterprise tier)

### Differentiating Features
- Multi-billing-source aggregation (Stripe + Recurly + Chargebee in one view)
- Native dunning / failed-payment recovery (Baremetrics Recover, ProfitWell Retain)
- Integrated CRM functionality alongside live MRR data (ChartMogul CRM Pro)
- Competitor / industry benchmarking dataset (Baremetrics, ProfitWell)
- Conversation intelligence linked to deal revenue (Clari, Gong)
- AI-powered pipeline forecasting with deal-level risk scoring (Clari, Gong)
- MCP-based data exposure to external AI tools (Clari, Gong 2026)

### Underserved Areas / Opportunities
- Causal anomaly explanation: tools surface revenue movements but rarely explain *why* contraction or churn spikes occurred with correlated signals
- Natural-language querying of subscription data without SQL or analyst dependency
- Account-level expansion/churn probability scoring with feature attribution, accessible at SMB price points
- Automated narrative generation for ARR bridge reports and board memos
- Monte Carlo / Bayesian scenario forecasting with transparent uncertainty bands for finance teams
- Unified view across billing + CRM + product usage signals in a single open-source package

### AI-Augmentation Candidates
- Anomaly detection on MRR movements correlated with product usage, support tickets, or pricing changes
- LLM-powered natural language revenue query interface (replace fixed metric grids)
- Predictive expansion and churn scoring per account cohort using historical patterns
- Automated drafting of ARR narratives for CFO / board reports
- Scenario forecasting with Bayesian uncertainty bands and plain-English sensitivity explanations

---

## Legal & IP Summary

All analysed tools are fully proprietary SaaS products except Metabase, whose core is AGPL v3. The AGPL v3 licence carries a strong copyleft obligation: any product that distributes or operates a modified version of Metabase as a network service must release its modifications under the same licence. Building a commercial revenue intelligence product on top of Metabase OSS would expose source code unless a commercial licence is negotiated with Metabase, Inc. Gong is known to hold AI/ML patents in conversation analysis and deal-risk scoring; a new product should build its own models independently. No patent encumbrances were identified for ChartMogul, Baremetrics, ProfitWell, or Clari based on publicly available information. All proprietary tools enforce standard SaaS data processor terms; handling financial revenue data will require SOC 2 Type II compliance and likely DPA agreements with enterprise customers.

---

## Recommended Feature Scope

**Must-have (MVP)**:
- Connect to at least Stripe (and optionally Recurly, Chargebee) to ingest subscription events and calculate MRR, ARR, churn, NRR, LTV, and ARPA in real time
- MRR waterfall visualisation (new, expansion, contraction, churn, reactivation) with time-range filtering
- Cohort retention analysis with configurable grouping (plan, signup month, geography)
- Customer-level drilldown showing account MRR history, plan changes, and payment status
- Alerting for anomalous metric movements (threshold-based, delivered via Slack/email)
- Dashboard export (PNG, CSV) suitable for board and investor reporting

**Should-have (v1.1)**:
- AI-powered anomaly explanation correlating MRR movements with contextual signals (product usage, support volume)
- Natural-language query interface allowing users to ask ad-hoc questions about subscription data without SQL
- Account-level churn and expansion probability score using ML trained on cohort patterns
- Automated ARR bridge narrative generation for CFO / finance team reporting
- Multi-billing-source ingestion (Stripe + Recurly + Chargebee unified view)

**Nice-to-have (backlog)**:
- Monte Carlo / Bayesian scenario forecasting with transparent uncertainty bands and assumption controls
- Native dunning / failed-payment recovery workflows
- Industry benchmarking against an anonymised peer dataset
- Embedded CRM lightweight task management for CS and RevOps users
- MCP server endpoint exposing live revenue signals to external AI agents
