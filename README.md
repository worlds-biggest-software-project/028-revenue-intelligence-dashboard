# Revenue Intelligence Dashboard

**Status:** Candidate Project  
**Market Size:** $274–315B (SaaS market) growing at 15–22% CAGR; Revenue intelligence is sub-segment  
**Last Updated:** 2026-05-02

## Overview

An open-source, AI-native revenue intelligence platform for SaaS companies that combines subscription metrics dashboarding with AI-powered anomaly explanation and scenario forecasting. Today's tools split into:

1. **Subscription metrics platforms** (ChartMogul, Baremetrics): Great dashboards but limited forecasting
2. **Enterprise revenue forecasting** (Clari, Gong): AI forecasting but $100–$200/user/month and CRM-centric

This project bridges the gap with:

- **Real-time MRR/ARR/NRR dashboards** feeding from Stripe, Chargebee, Recurly in a single unified view
- **AI-powered anomaly explanation:** Automatically correlate revenue movements with product usage signals, support ticket volume, or pricing changes—turning a number into a diagnosis
- **Natural-language revenue querying:** "Which customer segments drove expansion MRR this quarter vs. last year?"—without SQL or data team
- **Predictive expansion/churn scoring:** Account-level probability scores with feature attribution for CS teams
- **Monte Carlo scenario forecasting:** Transparent uncertainty bands and assumption controls for finance teams

## The Market Gap

The revenue intelligence market is underserved at the SMB/mid-market level:

- **Free/cheap ($0–$500/mo):** ChartMogul, Baremetrics, ProfitWell—excellent dashboards but no AI
- **Mid-market/enterprise ($1K–$200K+/yr):** Clari, Gong—AI forecasting but expensive, sales-motion-centric, complex
- **Predictive analytics ($5K–$50K/mo):** Pecan AI—strong churn models but no subscription metrics, batch-only, requires data warehouse engineering

**The gap:** No open-source tool provides production-ready MRR/ARR dashboarding + AI anomaly explanation + scenario forecasting in one place. Teams want:
- Free or low-cost entry (eliminates $100K+/yr contracts)
- Zero data engineering (direct Stripe/Chargebee integration)
- AI-powered insights, not just static dashboards
- Self-hosting for financial data sovereignty

## Core Features

### MVP (Must-Have)
- Connect to at least Stripe (optionally Recurly, Chargebee) to ingest subscription events and calculate MRR, ARR, churn, NRR, LTV, and ARPA in real time
- MRR waterfall visualisation (new, expansion, contraction, churn, reactivation) with time-range filtering
- Cohort retention analysis with configurable grouping (plan, signup month, geography)
- Customer-level drilldown showing account MRR history, plan changes, and payment status
- Alerting for anomalous metric movements (threshold-based, delivered via Slack/email)
- Dashboard export (PNG, CSV) suitable for board and investor reporting

### Should-Have (v1.1)
- **AI-powered anomaly explanation** correlating MRR movements with contextual signals (product usage, support volume)
- **Natural-language query interface** allowing users to ask ad-hoc questions about subscription data without SQL
- **Account-level churn and expansion probability score** using ML trained on cohort patterns
- **Automated ARR bridge narrative generation** for CFO / finance team reporting
- **Multi-billing-source ingestion** (Stripe + Recurly + Chargebee unified view)

### Nice-to-Have (Backlog)
- **Monte Carlo / Bayesian scenario forecasting** with transparent uncertainty bands and assumption controls
- Native dunning / failed-payment recovery workflows
- Industry benchmarking against an anonymised peer dataset
- Embedded CRM lightweight task management for CS and RevOps users
- MCP server endpoint exposing live revenue signals to external AI agents

## AI-Native Opportunities

1. **Automated anomaly detection in revenue movements**
   - Existing tools surface MRR waterfalls but don't explain *why* contraction or churn spikes
   - An AI-native tool could correlate revenue anomalies with product usage signals, support ticket volume, pricing change dates, or macro seasonality—turning a number into a diagnosis
   - Example: "Contraction MRR dropped 15% last week because support ticket volume doubled and product logins fell 40% vs. historical average"

2. **Natural-language revenue querying**
   - Most dashboards are fixed-metric grids; business users cannot ask ad-hoc questions without data team support
   - An LLM-powered query layer over structured subscription data eliminates this bottleneck
   - Example: "Which customer segments drove expansion MRR this quarter vs. last year?" → instant query, chart, and narrative

3. **Predictive expansion and churn scoring at account level**
   - Rule-based health scores (usage thresholds) are brittle and noisy
   - A model trained on historical expansion/contraction patterns per cohort, product tier, and sales motion could produce calibrated probability scores with feature attribution
   - No current SMB/mid-market tool provides this natively

4. **Automated narrative reporting**
   - CFOs and boards receive manual slide decks summarizing ARR movements
   - An AI layer could draft accurate, data-grounded revenue narratives (ARR bridge, cohort commentary, forecast variance) directly from underlying data
   - Reduces analyst hours significantly

5. **Scenario forecasting with explainability**
   - Current forecasting tools (e.g., Clari) are black-box ML or simple extrapolation
   - An open-source AI-native tool could offer Monte Carlo or Bayesian forecasting with transparent uncertainty bands
   - Empowers finance teams to stress-test assumptions rather than trust opaque model outputs

## Competitive Landscape

| Tool | Type | Real-Time MRR | AI Forecasting | NL Query | Account Scoring | Cost |
|------|------|--------------|----------------|----------|-----------------|------|
| **ChartMogul** | Commercial | ✓ | ❌ | ❌ | ❌ | Free–$599/mo |
| **Baremetrics** | Commercial | ✓ | ❌ | ❌ | ❌ | $108–$500+/mo |
| **ProfitWell** | Commercial | ✓ | ❌ | ❌ | ❌ | Free–$99/mo |
| **Clari** | Commercial | ❌ | ✓ | ❌ | ✓ | $100–$200+/user/mo |
| **Gong** | Commercial | ❌ | ✓ | ❌ | ✓ | $1,300–$3,000/user/yr |
| **Pecan AI** | Commercial | ❌ | ✓ | ❌ | ✓ | Quote-based |
| **Metabase** | OSS | ❌ (needs warehouse) | ❌ | ❌ | ❌ | Free self-hosted |
| **This Project** | OSS + SaaS | ✓ | ✓ (AI) | ✓ (NL) | ✓ (ML) | Free self-hosted |

## Technical Design Considerations

- **Billing ingestion:** Direct Stripe API connectors; support Recurly, Chargebee, Zuora via webhook or API polling
- **Metrics calculation:** PostgreSQL for state management; exact SaaStr / Bessemer definitions (MRR, ARR, NRR, GRR, LTV, CAC)
- **AI layer:** Claude API for anomaly explanation, NL query interpretation, and narrative generation
- **ML forecasting:** Prophet (Facebook) or ARIMA for time-series baseline; Bayesian posterior sampling for scenario analysis
- **Account scoring:** XGBoost or LightGBM trained on cohort churn/expansion patterns; SHAP for explainability
- **Deployment:** Docker Compose self-hosted; managed SaaS with team collaboration (similar to ChartMogul model)
- **Compliance:** ASC 606 / IFRS 15 revenue recognition standards built-in from start; audit trail for finance teams

## Market Validation

- **Market drivers:**
  - Clari/Salesloft merger (Dec 2025) consolidating forecasting market; creates opportunity for open-source alternative
  - Paddle acquired ProfitWell; bundling metrics into billing platform
  - Snowflake acquired Select Star; consolidating analytics-layer tooling

- **Customer personas:**
  - SaaS founders/operators needing real-time MRR visibility without data engineering
  - VP of Sales / CRO focused on pipeline-to-revenue conversion and forecast accuracy
  - CFO / finance teams requiring ASC 606-compliant numbers and integration with FP&A tools
  - Revenue Operations (RevOps) teams diagnosing expansion/contraction drivers

## Why Build This

1. **Market timing:** Clari/Salesloft merger and Paddle acquisition of ProfitWell create consolidation opportunity
2. **Technology maturity:** Time-series forecasting (Prophet, ARIMA) is well-established; SHAP-based ML explainability is standard
3. **Zero data engineering:** Direct Stripe integration eliminates ETL burden that blocks current open-source adoption
4. **Commercial opportunity:** Build on free tier; offer managed SaaS with integrations (Slack, Salesforce, QuickBooks) for SMB/mid-market
5. **Platform leverage:** Stripe API, Prophet forecasting, Claude for narratives; focus on UI and integration

## Success Metrics

- **Adoption:** 500+ GitHub stars within 12 months; featured as ChartMogul + Clari alternative for mid-market
- **Commercial:** Win 30+ SMB/mid-market customers with managed SaaS tier ($1K–$5K/mo)
- **Forecasting accuracy:** Achieve <10% mean absolute percentage error (MAPE) on real SaaS revenue patterns
- **Community:** Active issue triage; 3+ contributors beyond core team

---

**Resources:**
- [ChartMogul API Documentation](https://www.chartmogul.com/docs/api/)
- [Stripe Billing API](https://stripe.com/docs/api/billing)
- [Facebook Prophet Time Series Forecasting](https://facebook.github.io/prophet/)
- [SaaStr SaaS Metrics Definitions](https://www.saastr.com/)
- [ASC 606 Revenue Recognition Standard](https://www.fasb.org/facts-on-asc-606-revenue-from-contracts-with-customers)
