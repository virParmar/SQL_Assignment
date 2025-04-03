## Returns and Appeasements

## Business Problem:
The retailer needs the total amount of items, were returned as well as how many appeasements were issued.

## Fields to Retrieve:

```
TOTAL RETURNS
RETURN $ TOTAL
TOTAL APPEASEMENTS
APPEASEMENTS $ TOTAL
```

## Solution :

```sql
select
	count(rh.return_id) as TOTAL_RETURNS,
    sum(ri.return_price * ri.return_quantity) as RETURN_$_TOTAL,
    count(ra.return_id) as TOTAL_APPEASEMENTS,
    sum(ra.amount) as APPEASEMENTS_$_TOTAL
from return_header rh
join return_item ri on rh.return_id = ri.return_id
join return_adjustment ra on ra.return_id = rh.return_id
	and ra.return_adjustment_type_id = 'APPEASEMENT'
```

![alt text](image.png)

## Query Cost : 472.08