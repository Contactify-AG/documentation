# Contactify CRM Webhook

This Webhook allows to reveive events from the "Share-Contact" form.

## Transmission

The data can be sent either as JSON or as Form URL encoded (`application/x-www-form-urlencoded`) to a defined URL.

## Description

Field | Type | Optional | Notes
--- | --- | --- | ---
email | string | No |
phone_number | string | Yes |
first_name | string | Yes |
last_name | string | Yes |
position | string | Yes |
company | string | Yes |
message | string | Yes | May be multiline
timestamp | ISO-8601 timestamp, no fractional seconds | No |
lead_email | string | Yes | Email of the user, whose digital business card was shown. Can be null if user was deleted, and contact is edited by Admin User.
event_type | string | No | either "create" or "update". However we do not deduplicate contacts. An udpate event event can occur when a user updates a contact in the User portal, however this only applies, if we still store the data in our database.
birthday | string | Yes | This is just a freetext field and can contain any string.
address | string | Yes |
zip_code | string | Yes |
city | string | Yes |
contact_form_type | string | No | Either "B2B", "B2C" or "Contest".

## Example-Payload
```json
{
    "email": "max@muster.ch",
    "phone_number": "123 456 78 90",
    "first_name": "Max",
    "last_name": "Muster",
    "position": "Abteilungsleiter",
    "company": "Mustercorp",
    "message": "Hallo Welt!\nMehrzeilige Nachricht!",
    "timestamp": "2022-10-19T14:42:03Z",
    "lead_email": "nicolas.damutten@contactify.ch",
    "event_type": "create",
    "birthday": "01.01.2022",
    "address": "Musterstrasse 1",
    "zip_code": "1234",
    "city": "Musterstadt",
    "contact_form_type": "B2B"
}
```