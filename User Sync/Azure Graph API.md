# User Sync – Azure Graph API

With the Azure Graph API integration, users can be automatically managed: that means created (incl. all contact data and picture), updated and deleted.

## Instructions
1. Open Azure Active Directory
2. Add App Registration

    Go to App Registrations  
    <img src="assets/azure-step-1.png" style="max-height: 300px; border: 1px solid #ccc!important; padding: 5px; border-radius: 4px;" />

    Create Registration  
    <img src="assets/azure-step-2.png" style="max-width: 750px; border: 1px solid #ccc!important; padding: 5px; border-radius: 4px;" />

    App Registration  
    <img src="assets/azure-step-3.png" style="max-width: 750px; border: 1px solid #ccc!important; padding: 5px; border-radius: 4px;" />
3. Open created app registration
4. Copy client id and tenant id and provide to Contactify  
    <img src="assets/azure-step-4.png" style="max-width: 750px; border: 1px solid #ccc!important; padding: 5px; border-radius: 4px;" />
5. Open Certificates and Secrets and add a new certificate  
    <img src="assets/azure-step-5.png" style="max-width: 750px; border: 1px solid #ccc!important; padding: 5px; border-radius: 4px;" />
6. Copy certificate value after creation and provide to Contactify  
    <img src="assets/azure-step-6.png" style="max-width: 750px; border: 1px solid #ccc!important; padding: 5px; border-radius: 4px;" />
7. Open Api Permissions and add `GroupMember.Read.All` and `User.Read.All` permissions and grant admin consent  
    <img src="assets/azure-step-7.png" style="max-width: 750px; border: 1px solid #ccc!important; padding: 5px; border-radius: 4px;" />
8. Create two azure ad groups:  
    
    - group for all contactify platform users
    - group for contactify platform administators

    All the users in the admins group should be members of the platform users group
9. Provide the group ids to Contactify.