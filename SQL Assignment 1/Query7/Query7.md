## Newly Created Sales Orders and Payment Methods

## Business Problem:
Finance teams need to see new orders and their payment methods for reconciliation and fraud checks.

## Fields to Retrieve:

```
ORDER_ID
TOTAL_AMOUNT
PAYMENT_METHOD
Shopify Order ID (if applicable)
```

## Solution :

```sql
select
	oh.order_id,
    oh.grand_total as total_amount,
    opp.payment_method_type_id,
    oh.external_id as shopify_order_id
from order_header oh
join order_payment_preference opp on oh.order_id = opp.order_id
where oh.order_type_id='sales_order'
and oh.order_date between '2023-08-01 00:00:00' and '2023:08:31 23:59:59'
```

![alt text](image.png)

## Query Cost : 9895.18