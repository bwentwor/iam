---

copyright:

  years: 2015, 2019

lastupdated: "2019-06-03"

keywords: IAM access, access policy, IAM roles, platform management roles, service access roles, types of access policies

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:new_window: target="_blank"}

# IAM access
{: #userroles}

All services that are organized in a resource group in your account are managed by using {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM). Account owners are automatically assigned the account administrator role for Cloud IAM. As the account administrator, you can assign and manage access for users, create resource groups, create access groups, view billing details and track usage, and create service instances. You provide access for users, service IDs, and access groups by creating policies that set a target for the subject of the policy to access and a role that defines what type of access that is allowed.
{: shortdesc}

## What are Cloud IAM policies and who can assign them?
{: #iamusermanpol}

A policy grants a subject one or multiple roles to a set of resources so that specific actions can be taken within the context of the specified target resources.

The following graphic helps to explain how the IAM policy is created. Policies are always created by specifying the subject first. The subject is a specific user, service ID, or an access group. Next, the target of the policy is selected which is what you are allowing the user to access, for example: all services in a resource group, all IAM-enabled services in the account, account management services, or a particular service instance. Finally, you complete your access policy by selecting from the available roles. These roles define exactly what actions a user can complete. More configuration options might be available, depending on the service you select.

![Creating IAM policies](images/IAM.svg "How IAM access policies are created by using a subject, target, and role")

You can assign and manage policies if you have the proper role. The following table shows policy management tasks and the role that is required for each.

| Action | Required Role |
|----------|---------|
| Create a policy in an account for all services and instances | Account owner or administrator on all account management services and all Identity and Access enabled services |
| Create a policy on a service in an account | Account owner, administrator on all Identity and Access enabled services, or administrator on the service in the account |
| Create a policy on a service instance | Account owner, administrator on all Identity and Access enabled services, administrator on the service in the account, administrator on all services in the relevant resource group, or administrator on the service instance |
{: caption="Table 1. Users allowed to create access policies" caption-side="top"}


## Common access policy types
{: #policytypes}

You can provide fine-grained access for users, service IDs, or access groups by assigning the following types of access policies:

* All account management services
* Specific account management service
* All resources within the account
* All resources within all services that belong to an individual resource group with the ability to manage the resource group
* All resources within a single service in a resource group with the ability to manage the resource group
* All resources within a single service across the account, regardless of the resource group they're assigned to
* Resources in an individual instance
* A single resource type within an instance, for example, a bucket in an {{site.data.keyword.objectstorageshort}} instance

To grant another user full access to the account for the purposes of managing user access and managing all account resources, you must assign two policies. One policy that gives the user access to all resources in the account by selecting **All Identity and Access enabled services** with the **Administrator** and **Manager** roles assigned. And, one policy that gives the user access to all account management services in the account by selecting **All account management services** with the **Administrator** role assigned.
{: tip}

## Cloud IAM roles
{: #iamusermanrol}

With Cloud IAM, you can manage and define access for users and resources in your account. Two types of roles can be assigned: platform management roles and service access roles.

<dl>
<dt>Platform management roles</dt>
<dd>Platform management roles cover a range of actions, including the ability to create and delete instances, manage aliases, bindings, and credentials, and manage access. The platform roles are administrator, editor, operator, viewer. Platform management roles also apply to [account management services](/docs/iam?topic=iam-account-services#account-services) that enable users to invite users, manage service IDs, access policies, catalog entries, and track billing and usage depending on their assigned role on an account management service.</dd>
<dt>Service access roles</dt>
<dd>Service access roles define a user or service’s ability to perform actions on a service instance, such as accessing the console or performing API calls. The service access roles are manager, writer, and reader. </dd>
</dl>

You might not see all of the roles that are listed here as options when you assign policies in the UI because only the roles available for the service that you chose are displayed. For more information on what roles are enabled and what actions each access role allows for each service, see the documentation for that service.
{: note}

### Platform management roles
{: #platformroles}

With platform management roles, users can be assigned varying levels of permission for performing platform actions within the account and on a service. For example, platform management roles that are assigned for catalog resources enable users to complete actions such as creating, deleting, editing, and viewing service instances. And, the platform management roles that are assigned for account management services enable users to complete actions such as inviting and removing users, working with resource groups, and viewing billing information. For more information about the account management services, see [Assigning access to account management services](/docs/iam?topic=iam-account-services#account-services).

Select all roles that apply when creating a policy. Each role allows separate actions to be completed and doesn't inherit the actions of the lesser roles.
{: tip}

The following tables provide examples for some of the platform management actions that users can take within the context of catalog resources, resource groups, and account management services. See the documentation for each catalog offering to understand how the roles apply to users within the context of the service that is being used.

The first row of the table describes separate options that you can choose from when creating a policy, and the first column describes the selected roles for the policy. The remaining cells map to which role is selected from the first column, and which type of policy has been selected from the options in the first row.

| Access Policy Details | Actions on Services in the Account | Actions on Resources within Resource Groups | Actions for Access to Resource Groups |
|:--------------|:------------|:-------------|:-------------|
|  | One or all IAM-enabled services | Selected service in a resource group | Selected resource group |
| Viewer role | View instances, aliases, bindings, and credentials | View only specified instances in the resource group | View resource group |
| Operator role |  View instances and manage aliases, bindings, and credentials |  Not applicable | Not applicable |
| Editor role |  Create, delete, edit, and view instances. Manage aliases, bindings, and credentials | Create, delete, edit, suspend, resume, view, and bind only specified instances in the resource group | View and edit name of resource group |
| Administrator role |  All management actions for services | All management actions for the specified instances in the resource group | View, edit, and manage access for the resource group |
{: caption="Table 2. Example platform management roles and actions for services in an account" caption-side="top"}
{: #platformrolestable1}

The following table describes the common actions that you can perform based on the role you're assigned for each account management service. Scroll horizontally to see all entries in the table.
{: #acctmgmt}

The first row of the table describes specific services that you can choose from when creating a policy, and the first column describes the selected type of role for the policy. The remaining cells map to which role is selected from the options in the first column, and which type of policy has been selected from the options in the first row.

| Access Policy Details |  Actions for Service IDs  | Actions for Managing Access Groups | Actions for Managing Catalog Access | Actions for Access to Manage Users | Actions for Support | Actions for Billing | Actions for all Account Management Services |
|:--------------|:-------------|:--------------|:--------------|:-----------|:--------------|:--------------|:--------------|
|  |  IAM Identity Service |  IAM Access Groups |  Global resource catalog |  User Management  | Support Center | Billing and usage | All account management services |
| Viewer role |  <ul><li>View IDs</li></ul> |  <ul><li>View access groups and members</li></ul> | <ul><li>View private services</li></ul>  |  <ul><li>View users in the account</li><li>View user profile settings</li></ul> | <ul><li>View cases</li><li>Search cases</li></ul> | <ul><li>View account feature settings</li><li>View subscriptions in account</li><li>View account name</li><li>View resource groups</li></ul> | All viewer role actions for the account management services |
| Operator role | <ul><li>Create and delete IDs and API keys</li></ul> |  <ul><li>Not applicable</li></ul> | <ul><li>Not applicable</li></ul> |  <ul><li>View users in the account</li><li>View user profile settings</li></ul> | <ul><li>Not applicable</li></ul> | <ul><li>View account feature settings</li><li>View subscriptions in account</li><li>View and change account name</li><li>View and update resource groups</li></ul> | All operator role actions for the account management services |
| Editor role |  <ul><li>Create, update, and delete IDs and API keys</li></ul> |  <ul><li>View, create, edit, and delete groups</li><li>Add or remove users from groups</li></ul> | <ul><li>Can change object metadata but can't change visibility for private services</li></ul>  | <ul><li>View, invite, remove, and update users from the account</li><li>View and update user profile settings</li></ul> |  <ul><li>View cases</li><li>Search cases</li><li>Update cases</li><li>Create cases</li></ul> | <ul><li>View and update account feature settings</li><li>View subscriptions in account</li><li>View offers in account</li><li>View and apply feature codes</li><li>View and change account name</li><li>View and update spending limits</li><li>View, create, and update resource groups</li></ul> | All editor role actions for the account management services and ability to create resource groups |
| Administrator role |   <ul><li>Create, update, and delete IDs and API keys</li><li>Assign access policies to IDs</li></ul> |  <ul><li>View, create, edit, and delete groups</li><li>Add or remove users</li><li>Assign access to a group</li><li>Manage access for working with access groups</li></ul> | <ul><li>Can change object metadata or visibility for private services, and restrict visibility of a public service</li></ul> | <ul><li>View, invite, remove, and update users from the account</li><li>View and update user profile settings</li></ul> |  <ul><li>View cases</li><li>Search cases</li><li>Update cases</li><li>Create cases</li></ul> |  <ul><li>View and update account feature settings</li><li>View subscriptions in account</li><li>View offers in account</li><li>View and apply feature codes</li><li>View and change account name</li><li>View and update spending limits</li><li>View subscription balances and track usage</li><li>View, create, update, and assign access to manage resource groups</li></ul> | All administrator role actions for the account management services and ability to create resource groups |
{: caption="Table 3. Example platform management roles and actions for account management services" caption-side="top"}
{: #platformrolestable2}

For the IAM Identity Service, these actions apply to service IDs within the account that the user didn't create. All users can create service IDs. They're the administrator for those IDs, and they can create the associated API key and access policies, but this account management service applies to the ability to view, delete, and assign access to service IDs in the account created by other users.
{: note}

Some services might map specific actions to the platform management roles that are related to the management of the service rather than to the access of the service. As an example, see the following table that details the {{site.data.keyword.containershort_notm}} service actions that are mapped to these roles.

| Platform Management Role | Actions | Example Actions for {{site.data.keyword.containershort_notm}} |
|:-----------------|:-----------------|:-----------------|
| Viewer | Can view service instances, but can't modify them  | <ul><li>List clusters</li><li>View details for a cluster</li></ul>|
| Editor | Perform all platform actions except for managing the account and assigning access policies |<ul><li>Bind a service to a cluster</li><li>Create a webhook</li></ul> |
| Operator | Perform platform actions required to configure and operate service instances, such as viewing a service's dashboard | <ul><li>Add or remove worker nodes</li><li>Restart or reload worker nodes</li><li>Bind a service to a cluster</li></ul> |
| Administrator | Perform all platform actions based on the resource this role is being assigned, including assigning access policies to other users |<ul><li>Remove a cluster</li><li>Create a cluster</li><li>Update user access policies</li><li>All actions a viewer, editor, and operator can perform</li></ul>|
{: caption="Table 4. Example platform management roles and actions for {{site.data.keyword.containershort_notm}} service" caption-side="top"}

### Service access roles
{: #service_access_roles}

Service access roles enable users to be assigned different levels of permission for calling the service's API and accessing the UI for the service. The following table provides example actions that can be taken depending on the assigned roles based on using the {{site.data.keyword.objectstorageshort}} service.

The actions that can be taken based on each assigned role vary based on the service that you selected for the policy. Not all services use these types of roles. See the documentation for the service for more details.
{: note}

| Service Access Role | Actions | Example Actions for {{site.data.keyword.objectstorageshort}} Service |
|:-----------------|:-----------------|:-----------------|
|  Reader | Perform read-only actions within a service, such as viewing service-specific resources | List and download objects |
| Writer | Permissions beyond the reader role, including creating and editing service-specific resources | Create and destroy buckets and objects |
| Manager | Permissions beyond the writer role to complete privileged actions as defined by the service, plus create and edit service-specific resources | Manage all aspects of data storage, create and destroy buckets and objects |
{: caption="Table 5. Example service access user roles and actions" caption-side="top"}
