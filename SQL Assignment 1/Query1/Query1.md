### New Customers Acquired in June 2023

### Business Problem:
The marketing team ran a campaign in June 2023 and wants to see how many new customers signed up during that period.

### Fields to Retrieve:

PARTY_ID
FIRST_NAME
LAST_NAME
EMAIL
PHONE
ENTRY_DATE

### Solution :

```
select
p.party_id,
pr.role_type_id,
pe.first_name,
pe.last_name,
cm.info_string as email,
tn.contact_number as phone
from party p
join party_role pr on p.party_id = pr.party_id and pr.role_type_id='customer'
join person pe on p.party_id = pe.party_id
join party_contact_mech pcm on p.party_id = pcm.party_id
join contact_mech cm on pcm.contact_mech_id = cm.contact_mech_id
join telecom_number tn on cm.contact_mech_id = tn.contact_mech_id
where p.CREATED_STAMP BETWEEN '2023-06-01 00:00:00' AND '2023-06-30 23:59:59'
```

![alt text](<Screenshot from 2025-04-03 09-59-27.png>)

