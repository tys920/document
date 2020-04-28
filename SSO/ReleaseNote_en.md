## API 4.0.4.0-(2020-04-28)
### New Features
* New and MP permission split, SSO no longer has the concept of resource permission.
* The new SSO role is changed to global admin, subscriptionadmin, subscriptionuser, srpuser, unassigned.
* Add the SSO role field in the user list to record the user's permissions in SSO.
* During the first update, the data of SSO role will be filled in. The value of SSO role field is the highest of the user's permissions in SSO. The default value of datacenteradmin account is globaladmin. The other accounts take the highest level of each permission as the initial value.
* To ensure compatibility temporarily, SSO /users/me and /srprole API will query MP in real time.
* When creating a new user, you can specify the subscription number and add the user to the subscription number at the same time.
* Add API delete /clients/unsubscribe, and delete the client according to the client location and servicename.
* Add API delete /clients/resources to batch delete clients according to resource information.
* When creating a new user, you can specify the subscription number and add the user to the subscription number at the same time.
* New API /users/username/:userid gets username according to userid. This interface does not have permission requirements.
* New API /users/subscriptions obtains all subscription number information of current user, returns subscription number status, whether to try, etc. For the UI to determine the menu to display.
* New API /admin/users provides global admin to obtain user list, supports subscription number, client and other query modes.
* Add and reopen the verification of appid
* When you add OAuth and integrate myadvantech to log in, as long as the e-mail of Advantech is available, you will not go to marktplace to check whether there is a crmid
* Add API /clients/:ClientID/users get all users under a client


## Portal 4.0.3.0-(2020-4-28)
### New Features
* Menu modification, now there are: Subscription, Users, client, Profile, Role Introduction. 
* Subscription: The basic information of the subscription and trial subscription is presented in the list. It supports filtering by subscription name, company, and subscription ID. It supports filtering by subscription and trial subscription. The operation column adds subscription details. Permissions: globalAdmin and subscription user, subscription admin.
* Users: display a list of users and support filtering users based on all subscription, all trial subscription, and subscription.Permissions: globalAdmin and subscription user, subscription admin.
* User editing: remove resource permission information, and assign subscription permission, only users can modify their own basic information.

## Portal 4.0.2.2-(2020-4-9)
### New Features
* CRM ID is required when creating subscription.

## Portal 4.0.2.1-(2020-4-7)
### New Features
* Added trial subscription number menu, providing function of adding, deleting, and modifying trial subscription number, supporting to view billing information of using subscription number, and supporting trial subscription number user management
* Subscription number and trial subscription number support query by company and ID

## API 4.0.3.0-(2020-03-24)
### New Features
* Added api /subscriptions/{idOrCrmId}/accountInfo to get the accountInfo corresponding to the subscription
* Added api /users/me/info to get users information (excluding roles)
* Added api /clients/{clientId}/users/role to obtain the user's permissions for a specific client (similar to the previous srpRole, removed the role-related judgment)
* Added Cancel appId detection

### Fix bugs 
* Issue with refresh token setting cookie in return value
* Modify apidoc

## Portal 4.0.2.0-(2020-3-18)

### Fix bugs
* Remove the button in the navigation bar that is not implemented yet

## API 4.0.2.0-(2020-03-06)
### New Features
* Added subscription admin can create user function
* Added api /users/info to get user information in batches
* Added case-insensitive query for user under subscription

### Fix bugs 
* Modify datacneter admins cannot be deleted from each other
* Modify and marktplace synchronization API, return default if it fails
* Fix appId check when registering client
* Modify oauth client does not allow creation of srpUser
* Modify apidoc

## Portal 4.0.1.0-(2020-3-6)

### New Features
* Change the resource permission control on all pages to call the userme interface of ManagentPortal
* In the subscription management interface, click on the subscription to jump to the subscription user page and select the current subscription number by default.
* datacenter Admin can delete others, but it cannot be deleted between users who are also datacenter Admin
* The subscription Admin of the associated resource can view the resource permission menu, he can add users and assign resource permissions
* When the user selects a resource, if a duplicate resource permission is selected, a prompt is given

### Fix bugs
* On the subscription user page, when filtering the subscription, if the next page number is selected, the page is empty when the subscription with fewer users is selected again
* In the subscription number user field, the subscribers are not queried in real time after clearing the search content

## API 4.0.1-(2020-02-25)
### New Features
* Added support for oauth client mode
* Add get /users/me/info to get data from ManagentPortal in real time
* Added integration of marketplace APIs, synchronization during login, and provides an interface to determine whether changes have occurred
* Modify the subscription id generation rule to ensure that the same crmid can generate the same subscription Id

## Portal 4.0.0-(2020-02-18)

### New Features
* SSO supports single sign-on and forgot password functions
* Subscription: subscription management and subscription member management. Accessible members: datacenterAdmin, subscription members
* Subscription Management: Add, delete, and modify subscription. View subscription information (name, company, member, creation time, ID) and fuzzy filtering of subscription. Accessible members: datacenterAdmin, subscription members
* Subscription users: View, add, and remove members in the subscription, support datacenterAdmin to set subscription permissions for subscription members, and support fuzzy filtering for subscription members. Accessible members: datacenterAdmin, subscription members
* Resource permissions: The user's resource permission management and user addition, deletion, disablement, and information editing, support filtering by resources and roles, and fuzzy filtering of user names. Accessible members: workspaceOwner and above
* User edit: edit the user's basic information and resource permissions. Accessible members: workspaceOwner and above
* Client: Client management. Accessible members: all users
* Client Management: display client list, provide client add, edit, delete functions, support fuzzy filtering of client names. Accessible members: workspaceOwner and above
* Client Create: Basic information is required to create a client. After the creation is successful, a secret key and client ID will be provided. Users without client management rights will only see it once and need to save it properly. Accessible members: all users
* My profile: Show the user's basic information, resource permissions, subscription permissions, and application permissions. Provide personal information editing entry and password modification entry. Accessible members: all users
* Change password: The user changes the new password based on the old password. Accessible members: all users
* Role introduction: The roles of the tenant space role, subscription role, and application role are explained separately. Accessible members: all users

## API 4.0.0-(2020-02-19)
### New Features
* Added support for oauth client mode
* Add subscription related api / subscriptions / *, support adding, deleting, modifying, and checking subscription, and adding, deleting, modifying, and checking users under subscription
* The token supports two modes, long and short, to solve the problem that the token length exceeds the browser limit in v2
* The srp user permission supports the json mode format, which supports complex data structures
* Built-in service client, support to set permissions on sso interface through api

### Fix bugs 
* The subscription is queried based on the name. In case-insensitive case, if there is an uppercase letter in the name, it will not be found
* /patch/users/scopes cannot be deleted when action is remove
* Modify the address of the link in the registration letter
* Increase the log of operation records

