# User Sync – SCIM

With SCIM, users can be automatically managed: that means created (incl. contact data), updated and deleted. It is even posible to control order of physical business cards.

## Instructions for Azure AD
1. Open Azure Active Directory
2. Add Enterprise Application (if not already done)
3. Select Provisioning
4. Select Provisioning again
5. Select Automatic mode, add tenant URL and Secret Token and click on "Test Connection"  
    <img src="assets/scim-step-5.png" style="max-width: 750px; border: 1px solid #ccc!important; padding: 5px; border-radius: 4px;" />
6. Click on Mappings and select "Provision Azure Active Directory Users"  
    <img src="assets/scim-step-6.png" style="max-width: 750px; border: 1px solid #ccc!important; padding: 5px; border-radius: 4px;" />
7. Set up similar to the following, mapping the fields you need. The full spec of attributes can be found here: https://scim-api.stage.contactify.biz/api/scim/Schemas  
    <img src="assets/scim-step-7.png" style="max-width: 750px; border: 1px solid #ccc!important; padding: 5px; border-radius: 4px;" />  
    Azure Active Directory Attribute | customappsso Attribute
    --- | ---
    userPrincipalName | userName
    Switch([IsSoftDeleted],, "False", "True", "True", "False") | active
    jobTitle | title
    mail | emails[type eq "work"].value
    givenName | name.givenName
    surname | name.familyName
    streetAddress | addresses[type eq "work"].streetAddress
    city | addresses[type eq "work"].locality
    postalCode | addresses[type eq "work"].postalCode
    telephoneNumber | phoneNumbers[type eq "work"].value
    mobile | phoneNumbers[type eq "mobile"].value
    SingleAppRoleAssignment([appRoleAssignments]) | roles[primary eq "True"].value
    department | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department
    True | urn:ietf:params:scim:schemas:extension:contactify:2.0:User:orderCard

    The only required field is actually `userName`. All other fields are optional.

    In Order to add the contactify extension fields, click on "Show advanced options" and then "Edit attribute list for customappsso"

    <img src="assets/scim-step-7-1.png" style="max-width: 750px; border: 1px solid #ccc!important; padding: 5px; border-radius: 4px;" />

    There you can add all the fields you need from the following table (or the full spec mentioned above):
    Attribute | Type | Primary Key | Required | Multi-Value | Exact Case | Muatbility | Api Expression | Referenced Object Attribtue
    --- | --- | --- | --- | --- | --- | --- | --- | ---
    urn:ietf:params:scim:schemas:extension:contactify:2.0:User:uid | String | No | No | No | Yes | ReadWrite | - | -
    urn:ietf:params:scim:schemas:extension:contactify:2.0:User:externalCompanyId |String | No | No | No | No | ReadWrite | - | -
    urn:ietf:params:scim:schemas:extension:contactify:2.0:User:orderCard | Boolean | No | No | No | No | immutable | - | -
    urn:ietf:params:scim:schemas:extension:contactify:2.0:User:deliverCardToHeadquarters | Boolean | No | No | No | No | ReadWrite | - | -