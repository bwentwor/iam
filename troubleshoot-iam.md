---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-03"

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Troubleshooting for IAM
{: #troubleshoot_iam}

General problems with using IAM might include needing access to a resource or account to perform a task or identifying the right type of access to assign users in your account to perform specific tasks. In many cases, you can recover from these problems by following a few easy steps.
{:shortdesc}

## How do I know what access I am assigned?
{: #troubleshoot-myaccess}
{: troubleshoot}

If you don't have access to complete a particular task, such as creating a service instance and adding it to a resource group or inviting other users to the account, you might need to check what access you are assigned.

I'm not sure what level of access I'm assigned to complete actions in an account of which I am a member. 
{: tsSymptoms}
   
You might not be assigned the correct access. 
{: tsCauses}

To check what you have access to and the level of access, complete the following steps. If you need to request access, contact the account owner.

Go to **Manage** &gt; **Access (IAM)**, and select your name on the **Users** page. Then, depending on the access you're looking for, select the different tabs:
{: tsResolve}

* To determine what access you have through the access groups you are assigned, select **Access groups**.
* To see IAM access policies that are assigned to you, select the **Access policies**.
* To see your Cloud Foundry access for all orgs and spaces, select **Cloud Foundry access**.


## How can I get access to invite users to the account? 
{: #troubleshoot-invite}
{: troubleshoot}

If you are not the account owner and aren't assigned the correct access, then you can't invite users to an account. 

I can't invite users to the account.
{: tsSymptoms}
   
You might not be assigned the correct access. 
{: tsCauses}

To invite users and manage outstanding invitations, you must be an account owner, an organization manager, a user with an IAM access policy with Editor or higher role on the user management account management service, or you must have classic infrastructure permissions to add users.
{: tsResolve}


## How can I view classic infrastructure permissions for other users?
{: #troubleshoot-classicinfra}
{: troubleshoot}

Account owners have full access to the account, so they do not see the permissions for themselves. Individual users can't edit their own permissions, so they see permissions on their classic infrastructure page, but can't edit them. You must have specific access to view and edit permissions for another user in the account.

You see a message that states that you can't view another user's classic infrastructure permissions.
{: tsSymptoms}
   
You might not be assigned the correct access.
{: tsCauses}

You must ask the account owner to be assigned the **Manage users** classic infrastructure permission, but you must also be an ancestor of the user within the classic infrastructure user hierarchy to view and manage another user's permissions.
{: tsResolve}

## How can I manage migrated billing and support case permissions in IBM Cloud?
{: #troubleshoot-migrated-permissions}
{: troubleshoot}

With the initial migration of users and permissions for managing billing and support cases from your SoftLayer account to your linked {{site.data.keyword.Bluemix_notm}} account, some users might have been missing these permissions. However, all migrated permission access groups are now assigned the correct IAM access policies, ensuring that all users are assigned the correct access that they had previously.

Users don't seem to have the same managing billing and support case permissions in the {{site.data.keyword.Bluemix_notm}} console that they were previously assigned in your SoftLayer account.
{: tsSymptoms}
   
Your migrated permissions access groups might not have been assigned the correct access policies when the users were initially migrated.
{: tsCauses}

As of 20 May 2019, all [migrated permission access groups](/docs/iam?topic=iam-migrated_permissions) have the correct policies assigned for managing billing information and support cases. If you tried to use these groups before this date, the access groups missing equivalent IAM access policies might have caused a mismatch in the assigned access between the SoftLayer permissions and IAM access. This has been resolved. You can go to **Manage** > **Access (IAM)**, and then select **Access groups** to review the users and policies that are assigned to each access group.
{: tsResolve}


## How can I access infrastructure services in my account? 
{: #troubleshoot-infrastructure-access}
{: troubleshoot}

When you attempt to access infrastructure sections of the IBM Cloud Console, you see a message that states:
"This page can't be loaded because your infrastructure account is not fully configured as an IBM Cloud account."
{: tsSymptoms}

There are multiple reasons why you might see this error message:
* You have a [Lite account] (/docs/account?topic=account-accounts#liteaccount), which does not allow access to infrastructure services. 
* Your IBM Cloud account is not linked to an infrastructure account. 
{: tsCauses}

To resolve this issue, you must upgrade to a Pay Per Use or paid Subscription account. For information, see [Upgrading to a Pay-As-You-Go account](/docs/account?topic=account-upgrading-account#upgrade-paygo) or [Upgrading to a Subscription account](/docs/account?topic=account-upgrading-account#upgrade-subscription).
{: tsResolve}
