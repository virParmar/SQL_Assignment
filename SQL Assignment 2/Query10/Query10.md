## Total Orders by Sales Channel

## Business Problem:
Marketing and sales teams want to see how many orders come from each channel (e.g., web, mobile app, in-store POS, marketplace) to allocate resources effectively.

## Fields to Retrieve:

```
SALES_CHANNEL
TOTAL_ORDERS
TOTAL_REVENUE
REPORTING_PERIOD
```

## Solution

```sql
select
	oh.sales_channel_enum_id,
	count(oh.order_id),
    sum(oh.grand_total),
    concat(min(date(oh.order_date)),' to ', max(date(oh.order_date)))
from order_header oh
group by oh.sales_channel_enum_id
```

![alt text](image.png)

## Query Cost : 8450.55