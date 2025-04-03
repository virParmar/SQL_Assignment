## Total Facilities That Sell the Product

## Business Problem:
Retailers want to see how many (and which) facilities (stores, warehouses, virtual sites) currently offer a product for sale.

## Fields to Retrieve:

```
PRODUCT_ID
PRODUCT_NAME (or INTERNAL_NAME)
FACILITY_COUNT (number of facilities selling the product)
(Optionally) a list of FACILITY_IDs if more detail is needed
```

## Solution :

```sql
select
	pr.product_id,
    pr.product_name,
    count(pf.facility_id) as FACILITY_COUNT
from product pr
join product_facility pf on pr.product_id = pf.product_id
group by pr.product_id,pr.product_name
```

![alt text](image.png)

## Query Cost : 1278796.08