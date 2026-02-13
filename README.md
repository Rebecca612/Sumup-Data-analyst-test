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


Data Quality 
1. Campaign ID Data Type: CAMPAIGN_ID required explicit type casting to numeric.
2. Null and Missing Values
3. Outliers in Top-of-Funnel Metrics: Using IQR-based outlier detection:TOTAL_IMPRESSIONS: 404 outliers, TOTAL_CLICKS: 342 outliers, TOTAL_SPEND: 351 outliers. Outliers were concentrated in high-volume campaigns. Lower funnel metrics (Leads, SQLs, Deals) showed minimal to no outliers.
<img width="1392" height="662" alt="image" src="https://github.com/user-attachments/assets/d3e123b6-83ea-48d0-83ee-b55d59f083c8" />

Marketing Recommendations 
Diversify channel allocation to reduce concentration risk. A significant portion of marketing spend and lead volume is concentrated on Facebook. While performance may currently be strong, heavy dependency on a single channel introduces structural risk. Platform policy changes, algorithm shifts, or rising acquisition costs could materially impact lead generation. Gradually reallocating part of the budget toward alternative high-performing channels would reduce exposure and improve long-term acquisition resilience.

AI Tool and Policy
I used AI to support documentation writing, explanation and to help structure high-level explanations of the dbt project architecture, anomaly detection approach, and code refinement. 
Struggle with AI
I used AI while working with SOQL (Salesforce Object Query Language). Initially, it struggled to generate the correct query structure required to implement a dashboard aggregation toggle. To resolve this, I gave the AI prompts with official Salesforce documentation links and example queries. I began drafting the query manually and asked the AI to complete or refine specific sections.
It required several iterations and cross-referencing external examples. Still, through guided prompting and validation against documentation, I was able to identify the missing logic and finalise the correct query structure.
 
Dashboard 
<img width="1875" height="1500" alt="image" src="https://github.com/user-attachments/assets/7295af5f-1044-417b-b537-837f3f23c9da" />

Overall Performance
A total of 33,959 POS Lite deals were generated during the  period, with a Blended Cost per Deal of €49.33 and total marketing investment of approximately €1.67M. Approximately 61.36% of total deals originate from the Sales-Assisted funnel. The Lead → Deal conversion rate is 50.07%, indicating that roughly half of the generated leads convert into closed deals. The self-service funnel (Sessions → Signups → Orders) shows lower conversion compared to the sales-assisted path, which is expected in product-led acquisition. Marketing spend is heavily concentrated in a single channel (Facebook), which also drives a significant portion of leads.
