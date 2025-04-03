## Orders with Multiple Returns

## Business Problem:
Analyzing orders with multiple returns can identify potential fraud, chronic issues with certain items, or inconsistent shipping processes.

## Fields to Retrieve:

```
ORDER_ID
RETURN_ID
RETURN_DATE
RETURN_REASON
RETURN_QUANTITY
```

## Solution :

```sql
select
	ri.order_id,
	rh.return_id,
    rh.return_date,
    rr.description as RETURN_REASON,
    ri.return_quantity
from return_header rh
join return_item ri on rh.return_id = ri.return_id
join return_reason rr on ri.return_reason_id = rr.return_reason_id
where ri.order_id in (
	select order_id
    from return_item
    group by order_id
    having count( ri.return_id) > 1
)
```

![alt text](image.png)

## Query Cost : 3404.25