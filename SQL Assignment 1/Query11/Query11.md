## Canceled Orders (Last Month)

## Business Problem:
The merchandising team needs to know how many orders were canceled in the previous month and their reasons.

## Fields to Retrieve:

```
TOTAL ORDERS
CANCELATION REASON
```

## Solution :

```sql
select
	count(oh.order_id) as TOTAL_ORDERS,
    os.change_reason as CANCELATION_REASON
from order_header oh
join order_status os on oh.order_id = os.order_id
where oh.status_id='order_cancelled'
	and oh.order_type_id='sales_order'
    and os.status_datetime >= DATE_FORMAT(now() - interval 1 month, '%Y-%m-01')
    and os.status_datetime < DATE_FORMAT(now(), '%Y-%m-01')
group by os.change_reason
```

![alt text](image.png)

## Query Cost : 64527.87