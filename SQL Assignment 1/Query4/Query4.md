## Product IDs Across Systems

## Business Problem:
To sync an order or product across multiple systems (e.g., Shopify, HotWax, ERP/NetSuite), the OMS needs to know each system’s unique identifier for that product. This query retrieves the Shopify ID, HotWax ID, and ERP ID (NetSuite ID) for all products.

## Fields to Retrieve:

```
PRODUCT_ID (internal OMS ID)
SHOPIFY_ID
HOTWAX_ID
ERP_ID or NETSUITE_ID (depending on naming)
```

### Solution :

```sql
select
	pr.product_id,
	shopify_product_id as shopify_id,
	pr.product_id as hotwax_id,
	gi.id_value as erp_id
from product pr
join good_identification gi on pr.product_id = gi.product_id
join shopify_product sp on pr.product_id = sp.product_id
where gi.good_identification_type_id='ERP_ID'
```

![alt text](image.png)

## Query Cost : 197094.88