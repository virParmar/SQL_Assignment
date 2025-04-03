### List All Active Physical Products
Business Problem:
Merchandising teams often need a list of all physical products to manage logistics, warehousing, and shipping.

### Fields to Retrieve:

PRODUCT_ID, PRODUCT_TYPE_ID, INTERNAL_NAME

## Solution :

```sql
select 
pr.product_id,
pr.internal_name,
pr.product_type_id
from product pr
join product_type pt on pr.product_type_id=pt.product_type_id and pt.is_physical='Y'
where pr.sales_discontinuation_date is null and pr.support_discontinuation_date is null
```

![alt text](image.png)

### Query Cost : 80621.78

