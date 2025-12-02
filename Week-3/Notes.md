Objective

Enhance the analytical depth of the dashboard by writing advanced DAX measures, creating session-level grouping logic, and building traffic & campaign performance pages.

1. Advanced DAX Development
A. Cart Abandonment Rate
Measures the % of users who added items to cart but did not purchase.

Cart Abandonment % =
DIVIDE(
    [AddToCart Sessions] - [Purchase Sessions],
    [AddToCart Sessions]
)

B. Cost Per Acquisition (CPA)
Calculates ad spend required to acquire one converted customer.

CPA = DIVIDE(SUM(fCampaignCost[cost]), [Orders])

C. Session Grouping (If Required)
Used to cluster events into meaningful session blocks.

Session Group =
CALCULATE(
    MIN(fWebEvents[timestamp]),
    ALLEXCEPT(fWebEvents, fWebEvents[session_id])
)

2. Additional Performance Metrics
Created additional measures for deeper insights:

Impressions
Clicks
CTR (Click-Through Rate)
Revenue
ROAS (Return on Ad Spend)
These allow campaign-level efficiency tracking.

3. Building Traffic & Campaign Pages

A. Traffic Source Analysis Page
Components:
Sessions by Traffic Source (Google, Facebook, Email, Organic)
Orders by Source
Source-wise Conversion Rate
Engagement heatmap (optional)

Goal: Identify which traffic sources bring high-quality users.

B. Campaign Performance Page
Components:
Orders by Campaign
CPA by Campaign
ROI / ROAS
Clicks vs Conversions comparison
Campaign drop-off insights

Goal: Show which campaigns waste money and which ones drive profitable conversions.

4. Drill-Through Page Development
Created a dedicated drill-through page linked from funnel stages.
Shows:
All sessions that dropped off at a selected funnel stage
Last page visited
Device / browser filters
Time spent in session
No. of page views before exit

Purpose: Reveal exact reasons behind user abandonment.

5. Week 3 Output Summary
Advanced DAX formulas implemented
Campaign & Traffic KPI pages completed
Drill-through functionality added
Session grouping logic finalized

Dashboard now provides actionable insights beyond the funnel
