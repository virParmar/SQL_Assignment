## Single-Return Orders (Last Month)

## Business Problem:
The mechandising team needs a list of orders that only have one return.

## Fields to Retrieve:

```
PARTY_ID
FIRST_NAME
```

## Solution :

```sql
select
	rh.from_party_id,
    pe.first_name
from return_header rh
join person pe on rh.from_party_id = pe.party_id
where month(rh.return_date) = month(current_date()) - 1
	and year(rh.return_date) = year(current_date())
group by rh.from_party_id,pe.first_name
having count(rh.return_id) = 1
```

![alt text](image.png)

## Query Cost : 6165.85