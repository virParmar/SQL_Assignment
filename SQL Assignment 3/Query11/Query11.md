## Transfer Orders Without Inventory Reservation

## Business Problem:
When transferring stock between facilities, the system should reserve inventory. If it isn’t reserved, the transfer may fail or oversell.

## Fields to Retrieve:

```
TRANSFER_ORDER_ID
FROM_FACILITY_ID
TO_FACILITY_ID
PRODUCT_ID
REQUESTED_QUANTITY
RESERVED_QUANTITY
TRANSFER_DATE
STATUS
```

## Solution :

```sql
select
	it.inventory_transfer_id as TRANSFER_ORDER_ID,
    it.facility_id as FROM_FACILITY_ID,
    it.facility_id_to as TO_FACILITY_ID,
    it.product_id,
    it.quantity as REQUESTED_QUANTITY,
    oisgir.quantity as RESERVED_QUANTITY,
    it.send_date,
    it.status_id
from inventory_transfer it
join order_item_ship_grp_inv_res oisgir on it.inventory_item_id = oisgir.inventory_item_id
```

![alt text](image.png)

## Query Cost : 14.62