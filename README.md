# Sumup-Data-analyst-test
Part 1 – KPI Definitions
This section defines the core KPIs used to evaluate performance across the POS Lite Self-Service and Sales-Assisted acquisition funnels.

i. Total POS Lite Deals

Definition
Total POS Lite Deals represents the total number of closed POS Lite deals acquired through both acquisition paths:
Self-Service (Website Orders)
Sales-Assisted (Closed Deals from Leads Funnel)
Formula
Total POS Lite Deals = Web Orders + Sales-Assisted POS Lite Deals

ii. Blended Cost per Deal
Definition
Blended Cost per Deal measures the total marketing investment required to acquire one closed POS Lite deal across both acquisition paths.
Formula
Blended Cost per Deal = Total Marketing Spend ÷ Total POS Lite Deals
Where:
Total Marketing Spend = Web Marketing Spend + Sales-Assisted Marketing Spend

iii. Sales-Assisted Share (%)
Definition
Sales-Assisted Share represents the proportion of total POS Lite deals originating from the Sales-Assisted funnel.
Formula
Sales-Assisted Share (%) = Sales-Assisted POS Lite Deals ÷ Total POS Lite Deals

iv. Sales Funnel Effectiveness (Lead → Deal Conversion Rate)
Definition
Sales Funnel Effectiveness measures the proportion of marketing-generated leads that convert into closed POS Lite deals within the Sales-Assisted funnel.

Formula
Lead → Deal Conversion Rate (%) = Sales-Assisted POS Lite Deals ÷ Total Leads

v. Self-Service Funnel Efficiency (Session → Order Conversion Rate)
Definition
Self-Service Funnel Efficiency measures the proportion of website sessions that result in completed POS Lite orders.
Formula
Session → Order Conversion Rate (%) = Total Orders ÷ Total Sessions

2. Interpreting Cost per Lead vs. Sales Cycle Duration
A decreasing Cost per Lead is generally positive, as it indicates improved marketing efficiency, while an increasing Sales Cycle Duration is typically negative because it implies higher sales effort and resource usage per deal. When these trends occur together, it often signals a trade-off in lead quality: cheaper leads tend to be lower-intent or less qualified, requiring more time and effort from Sales to convert. Unless this shift is a deliberate strategy to pursue higher-value deals with naturally longer sales cycles, the data would suggest increased cost of customer acquisition and reduced overall funnel efficiency despite lower upfront marketing costs.

DBT Project Structure
1. Staging Layer: Each raw source table (WEB_ORDERS, LEADS_FUNNEL, CHANNELS) would have a corresponding staging model.In this layer, I would: Standardise column names and formats, Typecast fields to appropriate data types, Handle NULLs and invalid values. No joins or business aggregations occur in this layer.

2. Intermediate Layer: This layer contains reusable business logic and transformations. Here I would: Join related entities (e.g., campaigns to channels), Apply business rules ,Derive funnel metrics and reusable calculations, Prepare clean, analysis-ready datasets

3. Mart Layer (fact and dim)This layer contains business-facing models designed to power dashboards and reporting. I would create:
Fact tables (e.g., sales-assisted performance, self-service performance, mission overview)
Dimension tables (e.g., channel, campaign, country, date). These models would contain aggregated metrics at the required reporting grain (e.g., monthly by channel).

 
