 Meta Ads Performance Analysis | Power BI Dashboard

An interactive Power BI dashboard designed to analyze Meta advertising performance, audience engagement, conversion behavior, and campaign budgets. This project demonstrates data modeling, KPI development, data visualization, and business analysis.



Project Overview

This project uses advertising event data and campaign information to investigate how Meta advertising campaigns perform across audience segments, countries, platforms, and ad formats.

The dashboard brings key performance indicators and interactive visualizations together to help users explore reach, clicks, engagement, purchases, and campaign budgets.

The analysis focuses on understanding the relationship between advertising visibility, audience interaction, and purchase conversions.

 Business Problem

Advertising teams need to understand whether their campaigns are reaching relevant audiences, attracting attention, and generating purchases.

High engagement does not necessarily mean high sales or profitability. Businesses need to investigate the complete conversion funnel and compare performance across different audiences, advertising formats, and time periods.

This project explores these questions using Power BI and business-focused data analysis.

Project Objectives

- Measure impressions, clicks, shares, comments, and purchases.
- Monitor click-through rate, engagement rate, and conversion rate.
- Analyze engagement across gender, age, and geographic segments.
- Compare advertising performance by ad type and platform.
- Explore weekly and hourly engagement patterns.
- Examine campaign budget information.
- Identify opportunities to improve conversion performance and campaign efficiency.

 Tools and Skills

- Power BI Desktop: dashboard development and interactive reporting.
- DAX: KPI calculations and analytical measures.
- Data Modeling: fact and dimension tables and table relationships.
- Data Visualization: KPI cards, bar charts, donut charts, line charts, and tables.
- Marketing Analytics: conversion funnel and campaign performance analysis.
- Business Analysis: interpreting results and developing data-driven recommendations.

 Dataset Description

The project documentation describes four logical tables.

 1. ad_events

Contains event-level records representing interactions with advertisements.

Important fields:
- event_id
- ad_id
- user_id
- timestamp
- day_of_week
- time_of_day
- event_type

Example event types include Impression, Click, Share, Comment, and Purchase.

 2. ads

Contains advertising and targeting information.

Important fields:
- ad_id
- campaign_id
- ad_platform
- ad_type
- target_gender
- target_age_group
- target_interests

 3. campaigns

Contains campaign-level information.

Important fields:
- campaign_id
- name
- start_date
- end_date
- duration_days
- total_budget

 4. users

Contains demographic and geographic attributes.

Important fields:
- user_id
- user_gender
- user_age
- age_group
- country
- location
- interests

Data Model and Relationships

The intended model uses ad_events as the central fact table, supported by three descriptive tables: ads, campaigns, and users.

![Meta Ads Data Model](images/data-model.png)

Relationship Design

| One Side | Many Side | Expected Cardinality |
|---|---|---|
| campaigns[campaign_id] | ads[campaign_id] | One-to-many |
| ads[ad_id] | ad_events[ad_id] | One-to-many |
| users[user_id] | ad_events[user_id] | One-to-many |

 How the Tables Work Together

- ad_events connects each recorded interaction to the relevant advertisement and user.
- ads provides platform, ad format, targeting, and campaign information.
- campaigns provides campaign dates and budget details.
- users provides demographic, geographic, and interest information.

These relationships are intended to support analysis by campaign, ad type, platform, audience, country, and time.

Note: The relationships and cardinalities above are based on the dataset documentation. Verify them against the actual Power BI Model view before presenting them as the implemented model.

 Key Performance Indicators

 Reach and Engagement

- Impressions: Total recorded impression events.
- Clicks: Total recorded click events.
- Shares: Total recorded share events.
- Comments: Total recorded comment events.
- Purchases: Total recorded purchase events.
- Engagements: The combined engagement events included in the report's definition.

 Advertising Efficiency

- Click-Through Rate (CTR): Percentage of impressions that resulted in clicks.
- Engagement Rate: Engagements divided by the defined denominator.
- Conversion Rate: Purchases divided by clicks.
- Purchase Rate: Purchases divided by impressions.

 Budget Metrics

- Total Budget: Sum of campaign budgets.
- Average Budget per Campaign: Average campaign budget.

Budget metrics describe allocated budgets unless actual advertising spend is available and used separately.

 Dashboard Features

 1. KPI Overview
Displays key metrics for impressions, clicks, shares, comments, purchases, engagements, CTR, engagement rate, conversion rate, purchase rate, total budget, and average campaign budget.

2. Audience Analysis
Explores engagement patterns by gender and age to understand which audience segments contribute to advertising interactions.

 3. Geographic Analysis
Compares engagement across countries to identify differences in audience activity and potential areas for further investigation.

 4. Weekly Engagement Trends
Visualizes engagement across days or weeks and compares the contribution of different advertising formats.

 5. Hourly Engagement Trends
Examines engagement variation by hour to identify periods of relatively higher or lower activity.

 6. Calendar Analysis
Displays engagement across calendar dates to explore daily activity patterns.

7. Ad-Type Performance
Compares advertising formats using metrics such as impressions, clicks, CTR, purchase rate, conversion rate, and engagement rate.

8. Interactive Reporting
Provides filters and dynamic measures to support exploration of different reporting dimensions.

 Key Findings

The following are preliminary interpretations of the supplied dashboard and domain documentation. Final numerical findings should be reconciled with the published Power BI report.

 1. Reach and Engagement
The dashboard reports substantial impression and click volumes. Engagement metrics help describe audience interaction, but they do not independently establish campaign profitability.

 2. Conversion Funnel
The displayed conversion rate is lower than the click-through rate, indicating that clicks and purchases represent different stages of the customer journey.

Further analysis could investigate the gap between clicks and purchases, including landing-page experience, offer relevance, and checkout friction.

 3. Audience Segmentation
The dashboard explores engagement by gender and age. Segment-level purchase counts and conversion rates should also be compared before deciding whether targeting changes are appropriate.

 4. Geographic Distribution
The country chart highlights differences in recorded engagement across geographic segments. Additional conversion and cost data would help distinguish high engagement from commercially valuable audiences.

 5. Time-Based Performance
Weekly and hourly charts allow users to investigate when engagement occurs. Scheduling changes should be validated through controlled tests and conversion outcomes.

6. Ad-Type Comparison
The dashboard compares Video, Stories, Image, and Carousel formats. Differences in CTR, engagement, and conversion metrics can help identify which formats warrant further testing.

 Business Recommendations

Improve Conversion Performance
Investigate the journey from click to purchase. Review landing-page usability, checkout friction, offer relevance, and tracking quality.

 Evaluate Audience Quality
Compare conversion rates across demographic and geographic segments instead of relying solely on engagement totals.

 Test Advertising Formats
Compare Video, Stories, Image, and Carousel campaigns using consistent measurement periods and comparable audience groups.

 Investigate Scheduling Opportunities
Use hourly and weekly engagement patterns to develop scheduling hypotheses, then validate them against purchases and actual advertising costs.

 Improve Budget Decisions
Evaluate actual spend, cost per click, cost per acquisition, and attributed revenue before reallocating campaign budgets.

 Strengthen Reporting
Maintain consistent KPI definitions, data relationships, filters, and reporting periods so that dashboard figures remain comparable.

 DAX Measures

The following examples illustrate possible measures for the documented event schema. They should be checked against the actual Power BI model and existing measures.

 Impressions

dax
Impressions =
CALCULATE(
    COUNTROWS(ad_events),
    ad_events[event_type] = "Impression"
)


Clicks

dax
Clicks =
CALCULATE(
    COUNTROWS(ad_events),
    ad_events[event_type] = "Click"
)


 Purchases

dax
Purchases =
CALCULATE(
    COUNTROWS(ad_events),
    ad_events[event_type] = "Purchase"
)


Click-Through Rate

dax
CTR =
DIVIDE([Clicks], [Impressions], 0)


 Conversion Rate

dax
Conversion Rate =
DIVIDE([Purchases], [Clicks], 0)


 Purchase Rate

dax
Purchase Rate =
DIVIDE([Purchases], [Impressions], 0)


Format the rate measures as percentages in Power BI. If event records can be duplicated or event_id is not unique, validate the counting logic before using COUNTROWS.

Engagement Rate should be documented using the exact numerator and denominator implemented in the report.

 Limitations

- The dashboard findings describe the supplied dataset and may not generalize to all advertising campaigns.
- Event counts do not necessarily represent unique users.
- Engagement and CTR do not independently measure profitability.
- Campaign budgets are not equivalent to actual advertising spend.
- ROAS requires appropriate actual spend and attributed revenue data.
- Audience and scheduling recommendations should be validated against conversion and cost metrics.
- The displayed KPI totals must be reconciled with the final report before publication.




Author

Mahroof Yoonuskhan

Aspiring Data Analyst | Business Analyst | Operations Analyst

Areas of interest: Power BI, Excel, data analysis, KPI reporting, business intelligence, and data-driven decision-making.

GitHub: https://github.com/mahyoukhan-sys
