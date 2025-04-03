## Products Missing NetSuite ID

## Business Problem:
A product cannot sync to NetSuite unless it has a valid NetSuite ID. The OMS needs a list of all products that still need to be created or updated in NetSuite.

## Fields to Retrieve:

PRODUCT_ID, INTERNAL_NAME, PRODUCT_TYPE_ID, NETSUITE_ID (or similar field indicating the NetSuite ID; may be NULL or empty if missing)

## Solution

select
	pr.product_id,
	pr.internal_name,
	pr.product_type_id,
	gi.good_identification_type_id,
	gi.id_value
from product pr
join good_identification gi on pr.product_id = gi.product_id and gi.good_identification_type_id='ERP_ID'
where gi.id_value is null or gi.id_value=''

file:///home/virendraparmar/Pictures/Screenshots/Screenshot%20from%202025-04-03%2012-15-52.png

## Query Cost : 3.19

