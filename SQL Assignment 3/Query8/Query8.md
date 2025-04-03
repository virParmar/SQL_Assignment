## List of Warehouse Pickers

## Business Problem:
Warehouse managers need a list of employees responsible for picking and packing orders to manage shifts, productivity, and training needs.

## Fields to Retrieve:

```
PARTY_ID (or Employee ID)
NAME (First/Last)
ROLE_TYPE_ID (e.g., “WAREHOUSE_PICKER”)
FACILITY_ID (assigned warehouse)
STATUS (active or inactive employee)
```

## Solution :

```sql
select
	pe.party_id,
    concat(pe.first_name, ' ' ,pe.last_name) as NAME,
    fp.role_type_id,
	fp.facility_id,
    p.status_id
from facility f
join facility_party fp on fp.facility_id = f.facility_id and fp.role_type_id in ('WAREHOUSE_PICKER','WAREHOUSE_PACKER')
join person pe on fp.party_id = pe.party_id
join party p on pe.party_id = p.party_id
where f.facility_type_id like '%WAREHOUSE'
```

![alt text](image.png)

## Query Cost : 3317.94