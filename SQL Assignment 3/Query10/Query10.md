## Total Items in Various Virtual Facilities

## Business Problem:
Retailers need to study the relation of inventory levels of products to the type of facility it's stored at. Retrieve all inventory levels for products at locations and include the facility type Id. Do not retrieve facilities that are of type Virtual.

## Fields to Retrieve:

```
PRODUCT_ID
FACILITY_ID
FACILITY_TYPE_ID
QOH (Quantity on Hand)
ATP (Available to Promise)
```

## Solution :

```sql
select
	pf.product_id,
    f.facility_id,
    f.facility_type_id,
    ii.quantity_on_hand_total,
    ii.available_to_promise_total,
    f.facility_type_id
from facility f 
join product_facility pf on f.facility_id = pf.facility_id
join inventory_item ii on pf.product_id = ii.product_id
where f.facility_type_id not in ('VIRTUAL_FACILITY')
```

![alt text](image.png)

## Query Cost : 9184294.33