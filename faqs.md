---



copyright:

  years: 2018, 2019

lastupdated: "2019-05-23"

keywords: frequently asked question, faq

subcollection: iam

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}
{:faq: data-hd-content-type='faq'}
{:note: .note}

# FAQs
{: #iamfaq}

## What is {{site.data.keyword.cloud_notm}} Identity and Access Management?
{: #whatisiam}
{: faq}

Identity and Access Management (IAM) enables you to securely authenticate users for platform services and control access to resources across the {{site.data.keyword.cloud_notm}} platform. A set of IBM Cloud services is enabled to use Cloud IAM for access control. They are organized into resource groups within your account to enable giving users quick and easy access to more than one resource at a time. Cloud IAM access policies are used to assign users and service IDs access to the resources within your account. For more information, see [{{site.data.keyword.cloud_notm}} Identity and Access Management](/docs/iam?topic=iam-iamoverview#iamoverview).

## What is an IAM-enabled service?
{: #iam-enabled}
{: faq}

An IAM-enabled service must be in a resource group and access to the service is given by using IAM access policies. When you create an IAM-enabled service from the catalog, you must assign it to a resource group. For more information, see [What is a resource?](/docs/resources?topic=resources-resource#resource)

{{site.data.keyword.containerlong_notm}} is the only exception; it’s IAM-access controlled, but it's always assigned to the default resource group. Therefore, you aren’t given the option to choose one when you create it from the catalog. And, it can’t be assigned to any other resource group.

## What is an IAM access policy?
{: #iam-policies}
{: faq}

An IAM access policy is how users, services IDs, and access groups in an account are given permission to work with a specific IAM-enabled service or resource instance, manage a resource group, or complete account management tasks. Each IAM access policy is made of a subject, target, and role. A subject is the who has the access. The target is what the subject can have access to. And, the role, whether it is a platform or service role depending on the context of the selected target, defines what level of access the subject has on the target. 

A subject is a user, service ID, or access group. A target can be a service in the account, a resource group in the account, a specific resource instance or type, or an account management service. And, the roles that are provided as choices depend on your selected target. Some services have service-specific roles that are defined, and some use platform roles only. To understand this concept visually, check out the following graphic with an outline of the options for creating an IAM policy:

![Creating IAM policies](images/IAM.svg "How IAM access policies are created by using a subject, target, and role")

## Are IAM and Cloud Foundry related?
{: #iam-cloudfoundry}
{: faq}

They aren't related. Cloud Foundry is an open source platform that uses organizations, spaces, and Cloud Foundry roles for access management. IAM is the secure way to authenticate users for platform services and control access to resources across the {{site.data.keyword.cloud_notm}} platform by using resource groups and IAM access roles.

The access management systems are entirely different. IAM resources belong to a resource group and Cloud Foundry resources belong to an organization and space. IAM access policies are used to provide access to resources in a resource group. And, Cloud Foundry org and space roles are used to provide users access to Cloud Foundry resources in a space. IAM doesn’t give you access to anything within Cloud Foundry spaces, and Cloud Foundry roles can’t grant access to resources within a resource group.

## How do I find out what I have access to?
{: #iam-access}
{: faq}

Go to **Manage** &gt; **Access (IAM)**, and select your name on the Users page. Then, depending on the access you're looking for, open the different tabs:

* To determine what access you have through the access groups you are assigned, select **Access groups**.
* To see IAM access policies assigned to you, select the **Access policies**.
* To see your Cloud Foundry access for all orgs and spaces, select **Cloud Foundry access**.


## How do I request access to a resource?
{: #request-access}
{: faq}

The account owner can update your access to any resource in the account, or you can contact any user who is assigned the administrator role on the service or service instance.

## Why should I use resource groups and access groups?
{: #resource-groups}
{: faq}

A resource group is a logical container for resources. When a resource is created, it's assigned to a resource group and can’t be moved after it's added.

An access group is used to easily organize a set of users and service IDs into a single entity to make access assignments easy. You can assign a single policy to an access group to grant all members those permissions. If you have more than one user or service ID that needs the same access, create an access group instead of assigning the same access multiple times per individual user or service ID.

By using both resource groups and access groups, you can streamline the access assignment policy by assigning a limited number of policies. You can organize all the resources a specific group of users and service IDs needs access to in a single resource group, group all the users or service IDs into an access group, and then assign a single policy giving access to all resources in the resource group.

For more information, see [Best practices for assigning access](/docs/iam?topic=iam-account_setup#account_setup).

## How do I ensure that my users can create resources within a resource group?
{: #resources}
{: faq}

To create a resource in a resource group, the user must have two access policies: one assigned to the resource group itself, and one assigned to the resources in the group. Access to the resource group itself is simply access to the container that organizes the resources, and this type of policy allows a user to view, edit, or manage access to the group, but not the resources within it. Access to services within the resource group enables a user to work with the service instances, which means the user can create a service instance.

So, minimally the user must have the following access:

* Viewer role or higher on the resource group itself
* Editor role or higher on the service or all services in the resource group


## What access do I need to provide others access?
{: #user-access}
{: faq}

For IAM-enabled services, you must have Administrator role on the service or resource that you want to assign users access to. If you want to assign access to all services or resources in the account, you need a policy on all Identity and Access enabled services with the Administrator role. And, to assign users access to account management services, you must be assigned the Administrator role on the specific service or all account management services.

For Cloud Foundry services, you must have Cloud Foundry org and space manager roles to give access to Cloud Foundry resources.

For classic infrastructure, you must have the Manage user classic infrastructure permission and the service and device category permissions for the resources that you want to give the user access to.

## What's the difference between access to manage a resource group and access to resources within a resource group?
{: #providing-access}
{: faq}

When you have access to manage a resource group, you can view, edit the name, and manage access for the resource group itself depending on the assigned role. Access to a resource group itself doesn't give a user access to the resources within the group.

When you have access to resources within a resource group, you can edit, delete, and create instances, or have all management actions for the specified services within the resource group depending on the assigned role.

For example, platform management roles and actions for account management services, see [Platform roles table](/docs/iam?topic=iam-userroles#platformrolestable2).

## Who can remove users?
{: #remove-users}
{: faq}

The account owner can remove any users from the account, and any user with the following access can remove users from an account:

* An IAM policy for the User management account management service with the Administrator role assigned and be the Cloud Foundry org manager if the user belongs to a Cloud Foundry org.
* If you have classic infrastructure in your account, then a user must have an IAM policy for the User management account management service with the Administrator role assigned, be the Cloud Foundry org manager if the user belongs to a Cloud Foundry org, and be an ancestor of the user in the classic infrastructure user hierarchy with the Manage user classic infrastructure permission assigned.

## How do I require IBMid multifactor authentication for my account?
{: #multi-factor}
{: faq}

1. Go to **Manage** &gt; **Access (IAM)**, and select **Settings**.
2. From the Account login section, select **Update** to select MFA for all users or non-federated users only.

For more information, see [Requiring MFA for users in your account](/docs/iam?topic=iam-enablemfa#enablemfa).

## What is the difference between service and platform roles?
{: #service-platform-roles}
{: faq}

Service and platform roles are two different types of roles:

* Platform roles are how you work with a service within an account such as creating instances, binding instances, and managing user's access to the service. For platform services these roles enable users to create resource groups and manage service IDs, for example. Platform roles are: administrator, editor, operator, and viewer.

* Service roles define the ability to perform actions on a service and are specific to every service such as performing API calls or accessing the UI. Service roles are: manager, writer, and reader. For more information about how these roles apply, refer to the specific service's documentation.

## What is the difference between a resource group and Cloud Foundry orgs and spaces?
{: #groups-organizations}
{: faq}

With the start of {{site.data.keyword.Bluemix_notm}}, an open source platform service for access control and the organization of resources called Cloud Foundry was the single method for organizing and controlling access to resources. As {{site.data.keyword.Bluemix_notm}} has expanded, a new method was needed that might be used by all types of services and resources. Resource groups are now used to group and organize many types of resources, and IAM is used to consistently control access to services and resources. A number of services have already adopted by using resource groups and IAM, and additional services will move over time to the new method for organizing resources and managing access.

Access control and account resource organization are the major differences between resource groups and Cloud Foundry orgs and spaces. Resource groups organize IAM-enabled services in an account that are access controlled by using IAM policies. Orgs and spaces are managed by using Cloud Foundry roles for access control, and Cloud Foundry resources are assigned to spaces. Orgs and spaces can be used to organize and control access to resources only within the Cloud Foundry realm, while resource groups and IAM can be used for multiple types of resources across {{site.data.keyword.Bluemix_notm}}.

## How do I delegate account administrator capabilities?  
{: #account-administrator}
{: faq}

To delegate the account administrator capabilities, assign the following access:

* An IAM policy with Administrator and Manager roles on All Identity and Access enabled services, which enables a user to create service instances and assign users access to all resources in the account.
* An IAM policy with Administrator role on All account management services, which enables a user to complete tasks like inviting and removing users, managing access groups, managing service IDs, managing private catalog offerings, and track billing and usage.
* The Super user permission set for classic infrastructure
* Cloud Foundry manager for all orgs

## How do I assign access to infrastructure and devices?
{: #infrastructure-devices}
{: faq}

1. Go to **Manage** &gt; **Access (IAM)**, and select **Users**.
2. Select a user's name.
3. Click **Classic infrastructure**.
4. Assign permissions from the **Permissions** section, assign access to devices from the **Devices** section, and assign access to VPN subnets for the devices that the user is assigned access from the **VPN access** section.

## How do I manage access for users previously assigned billing and support permissions in my SoftLayer account?
{: #migrated-permissions-faq}
{: faq}

All permissions that were previously assigned in your SoftLayer account can be managed in the {{site.data.keyword.Bluemix_notm}} console. Account permissions for managing billing information and support cases are now available in [migrated permissions access groups](/docs/iam?topic=iam-migrated_permissions). All users who were previously assigned these permissions in your SoftLayer account were migrated to these access groups, which are assigned the same level of access by using an IAM policy on the access group.

## Can every user in my account see all the other users?
{: #users}
{: faq}

An account owner can view all users in the account and choose how users can view other users in the account on the Users page. An account owner can adjust the [user list visibility setting](/docs/iam?topic=iam-userlistview#userlistview) on the Settings page by selecting one of the following options:

* **Unrestricted view**: All users in your account can view everyone else in the account.
* **Restricted view**: Limits the ability to view users on the Users page to only those who have been granted explicit access, along with those who have visibility of other users through a shared Cloud Foundry org or a classic infrastructure user hierarchy relationship.


## Do I need to assign access to a user when I invite them to the account?
{: #account-invite}
{: faq}

Yes. You must assign a user access within one of the three access management systems:

* An IAM access policy on a resource, resource group, or account management services
* A Cloud Foundry role for an org and space
* A permission set for classic infrastructure


## How do I add authentication into my web and mobile apps?
{: #appid}
{: faq}

IAM is used to manage access to your {{site.data.keyword.cloud_notm}} services and resources. With {{site.data.keyword.appid_full_notm}}, you can take cloud security one step further by adding authentication into your web and mobile apps. With just a few lines of code, you can easily secure your Cloud-native apps and services that run on {{site.data.keyword.cloud_notm}}. Ready to get started? [Check out the docs](/docs/services/appid?topic=appid-getting-started#getting-started).
