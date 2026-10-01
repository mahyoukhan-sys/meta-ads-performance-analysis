# meta-ads-performance-analysis
Meta Ads Performance Analysis using Power BI, DAX, data modeling, KPI tracking, and business insights.
# Meta Ads Performance Analysis

## Project Overview
An interactive Power BI dashboard for analyzing Meta advertising performance across Facebook, Instagram, and different ad formats. The project examines audience engagement, advertising efficiency, conversion behavior, and budget allocation to support data-driven marketing decisions.

## Business Problem
Advertising teams need to understand whether their campaigns are reaching the right audience, generating engagement, and converting interest into purchases. This project uses advertising event data and campaign information to identify performance patterns and opportunities for improvement.

## Objectives
- Measure campaign reach, clicks, engagement, and purchases.
- Evaluate CTR, engagement rate, conversion rate, and purchase rate.
- Compare performance by gender, age, country, platform, and ad type.
- Explore weekly and hourly engagement trends.
- Review campaign budgets and identify opportunities for further investigation.

## Tools and Skills
- Power BI Desktop
- DAX measures and KPI calculations
- Data modeling and relationship design
- Data visualization and dashboard design
- Marketing analytics and business interpretation

## Data Model
The project uses four logical tables:
- ad_events: event records such as impressions, clicks, shares, comments, and purchases.
- ads: platform, ad type, campaign association, and targeting details.
- campaigns: campaign dates, names, and budgets.
- users: demographic, country, location, and interest attributes.

Relationships:
- ad_events[ad_id] -> ads[ad_id]
- ads[campaign_id] -> campaigns[campaign_id]
- ad_events[user_id] -> users[user_id]

The intended model is a central event fact table connected to descriptive dimension tables. Confirm the actual relationships and cardinalities in the Power BI model before publishing.

## Key Performance Indicators
- Impressions: number of recorded impression events.
- Clicks: number of recorded click events.
- CTR = Clicks / Impressions
- Engagements: the events included in the report's engagement definition.
- Engagement Rate: engagements divided by the chosen denominator.
- Conversion Rate = Purchases / Clicks
- Purchase Rate = Purchases / Impressions
- Total Budget: sum of campaign budgets, subject to campaign-grain checks.

Confirm the exact formulas used in the report, including whether the engagement rate uses impressions or another denominator.

## Dashboard Features
- KPI cards for reach, clicks, engagement, purchases, and budget.
- Engagement analysis by gender and age.
- Geographic distribution of engagement.
- Weekly and hourly engagement trends.
- Campaign calendar and ad-type performance comparison.
- Interactive filters and dynamic measures.

## Key Findings
Use the final dashboard values to describe:
- How much reach and engagement the campaigns generated.
- Which audience groups and countries contributed the most engagement.
- Which ad formats had different CTR and conversion outcomes.
- When engagement was relatively high or low.
- Whether high engagement translated into purchases.

## Business Recommendations
- Investigate the drop-off between clicks and purchases.
- Review landing-page experience, offer relevance, and checkout friction.
- Compare conversion performance and cost efficiency across ad types and countries.
- Test audience segments and advertising schedules rather than assuming that engagement alone indicates profitability.
- Allocate budget based on verified conversion and cost metrics.

## Limitations
- Engagement does not necessarily mean a sale.
- High CTR does not by itself prove profitability.
- Budget allocation should be evaluated alongside actual spend, revenue, and conversion costs.
- Findings describe the supplied dataset and should not automatically be generalized to all Meta campaigns.

## Project Files
- Power BI dashboard: `powerbi/Meta_Ads_Dashboard.pbix`
- Dashboard preview: `images/dashboard.png`
- Data dictionary: `docs/data-dictionary.md`
- Additional insights: `docs/insights.md`

## Data Source and Attribution
Dataset/domain documentation provided by Data Tutorials: http://www.youtube.com/@datatutorials1
Confirm the dataset's original source and sharing permissions before redistributing the underlying data.

## Author
Mahroof Yoonuskhan
