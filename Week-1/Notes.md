Objective

Set up the full data foundation for the Clickstream Funnel Analysis project — including data import, cleaning, transformation, sessionization, and star-schema modeling.

1. Data Sources Used
  1.Web Event Logs (Clickstream)
    event_id
    user_id
    session_id
    event_type
    page_url
    timestamp
    device_type
    traffic_source
    campaign_id
   
   2.Orders Data
    order_id
    user_id
    session_id
    order_value
    order_date
    campaign_id
   
   3.Campaign Cost Data
    campaign_id
    date
    cos
    clicks
    impressions

3. Data Cleaning (Power Query)
  Key cleaning steps performed:
  Removed duplicates + blank rows
  Standardized event_type values (e.g., “Add to cart”, “add_to_cart”, “addcart” → Add to Cart)

  Converted datatypes:
  timestamp → DateTime
  order_value → Decimal
  IDs → Text

  Fixed invalid or missing session_id values
  Extracted UTM parameters where needed
  Ensured campaign_id matches across all tables

5. Star Schema Data Model
  Created a clean model with fact and dimension tables:
    Fact Tables
      fWebEvents (clickstream logs)
      fOrders (transactions)
      fCampaignCost (marketing cost data)
  Dimension Tables
    dUser
    dCampaign
    dDate
    dDevice
    
6. Relationships
  dUser → fWebEvents (user_id)
  dUser → fOrders (user_id)
  dCampaign → fOrders (campaign_id)
  dCampaign → fCampaignCost (campaign_id)
  dDate → fOrders (order_date)
  dDate → fCampaignCost (date)
  dDevice → fWebEvents (device_type)

  All relationships configured as:
    Single direction
    One-to-many
    Star schema — no snowflake, no many-to-many nonsense

6. Week 1 Output Summary
  All raw tables cleaned
  Full model structured
  Star schema built
