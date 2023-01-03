# Hubspot CRM Integration

The Hubspot integration currently allows to reveive events from the "Share-Contact" form. If the business card owner has a user in Hubspot, it will be linked as owner.

## Instructions
1. Please create a “Private App” as described here: [Private Apps](https://developers.hubspot.com/docs/api/private-apps#create-a-private-app) and fill out the details accordingly.
    1. When selecting scopes, we need the following:
        ```
        crm.objects.contacts.write
        crm.objects.owners.read
        ```
    2. Add the following Logo: [assets/contactify_icon.jpg.zip](contactify_icon.jpg.zip)
2. Send us the API Key through some secure means.
