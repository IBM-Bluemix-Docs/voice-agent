---

copyright:

  years: 2019

lastupdated: "2019-06-06"
subcollection: "voice-agent"

keywords: Voice Agent IAM, Voice Agent user access, get started with IAM, IAM tutorial, IAM quick start, user access, SMS IAM, SMS user access

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}

# Configuring IAM and User Access
{: #iam}

This tutorial is intended to help you get up and running quickly with IBM Cloud Identity and Access Management (IAM) by inviting users to your account and assigning Cloud IAM access to those users for a {{site.data.keyword.iva_short}} instance.
{:shortdesc}

## Before you begin
{: #iam-before-you-begin}

If you are new to using IAM, check out the following documentation to understand more about the features, concepts, and components of the access management system.

* [IBM Cloud Identity and Access Management](/docs/iam?topic=iam-iamoverview) provides a quick overview of what IAM is in IBM, the available features, and links to available CLI and API docs.
* [IAM concepts](/docs/iam?topic=iam-iamconcepts) outlines the high-level concepts in IAM that can help you understand the different components as you get started.
* [IAM access](/docs/iam?topic=iam-userroles) gives a more in-depth review of how access management works by using access policies.

This guide will cover the most common scenarios for adding and assigning access to users. There are many other options and configurations for user access and roles. The preceding links provide more detail. 

## Step 1. Invite users and assign initial access
{: #step1}

You can invite one or more users and set an initial access policy for the users on the invitation. If you invite multiple users in one invitation, the same access is assigned to each of the users. In the **access** section of the **Invite users** page, you see only the user roles that you have permission to assign.

The account owner can assign Cloud IAM roles for users that are invited in the **Services** section. As the account owner, you can provide access to:
* all resources in a resource group
* all resources for a specific service in a resource group 
* all Identity and Access enabled services in the account
* a single resource in the account
* access to account management services

Use the following procedure to assign Cloud IAM roles for users in your account.

1. Go to **Manage** &gt; **Access (IAM)**, and select **Users**.
2. Click **Invite users**.
3. Specify the email address of the users that you want to invite.
4. In the **Access** section, expand the **Services** option.
5. Choose to assign access to a **Resource**, resources within a **Resource group**, or **Account management services**.
6. Depending on your selection, follow the prompts to specify the desired access. If you selected the _Resource Group_ option, you can also provide the user with access to view, edit, or manage access to the resource group by selecting a role for access to the resource group.
7. In the **Services** input box, select *{{site.data.keyword.iva_short}}* from the dropdown menu, or type it into the box and press enter. 
8. Select the appropriate **Region** and **Service Instance**.
9. Under the **Select Roles** section, choose from *Manager*, *Writer*, and *Reader*. If your {{site.data.keyword.iva_short}} *Service Instance* is using SMS, then you **must** select the *Writer* or *Manager* role, in addition to any other roles you wish to grant.
    - For more information about **Roles**, see [Service Access Roles](/docs/iam?topic=iam-userroles#service_access_roles).
10. If you have permission, you can also assign Cloud Foundry or infrastructure access on the invitation.
11. Click **Invite users**.

For more information, see [Inviting users and assigning access](/docs/iam?topic=iam-iamuserinv#iamuserinv).

## Step 2. Create access groups
{: #step2}

To streamline the process of assigning access to users in your account, you can create access groups. Access groups are a way to organize users and service IDs that you can then easily assign access to by defining a single policy for the entire group.

### Set up your groups
{: #group_setup}

To create an access group, complete the following steps.

1. From the menu bar, click **Manage** &gt; **Access (IAM)**, and select **Access Groups**.
2. Click **Create**.
3. Enter a name for your group. Adding a description is optional.
4. Click **Create**.

Next, continue to set up your group by adding users or service IDs.

1. You will be taken to the newly created access group page. This group will also appear in the _Group_ list on the **Access Groups** page on the menu bar.
2. Click **Add users**.
3. Select the users that you want to add from the list, and click **Add to group**.
4. To add service IDs to the group, click **Service IDs**.
5. Select the IDs that you want to add from the list, and click **Add to group**.

### Assign access to your groups
{: #group_access}

After you create your groups, you can assign access to all entities within the group with a single policy or multiple policies.

1. From the menu bar, click **Manage** &gt; **Access (IAM)**, and select **Access Groups**.
2. Select the group to which you want to assign access.
3. From the **Access policies** tab, click **Assign access** to set up an access policy. Repeat as needed to assign more access.

By organizing users in access groups, you can assign a group of users access to a single policy, which reduces the overall number of policies you need to manage.
{: tip}


## Step 3. Manage access for existing users
{: #user_access_manage}

The following section details how to manage and edit access for users and groups that you have already set up in your account.

### Assigning new access
{: #new_access}

To assign a new access policy, complete the following steps:

1. From the menu bar, click **Manage** &gt; **Access (IAM)**, and select **Users**.
2. Select the name of the user to whom you want to assign access.
3. Click **Access policies**.
4. Click **Assign access**.
5. Choose how you want to assign access:
    * Select **Assign access within a resource group** to assign access either to all resources within a group, or to resources that are designated for a specific service within a group. You can also grant users permission to view, edit, or manage access to the resource group by assigning them a user role for the resource group. Select **No access** if you want to grant a user access to only the specified resource and not to the resource group.
    * Select **Assign access to resources** to assign access to all Identity and Access enabled resources across the account, all resources of a specific service across the account, a single instance, or a single resource within a specific service instance.
    * Select **Assign access to Account management services** to assign access to all account management services or just one account management service.
5. Select any combination of roles to define the scope of access. For more information, see [Cloud IAM roles](/docs/iam?topic=iam-userroles#iamusermanrol).
6. Click **Assign**.


### Editing existing access
{: #editing_access}

You can update existing access by editing the assigned roles for a user.

1. From the menu bar, click **Manage** &gt; **Access (IAM)**, and select **Users**.
2. Select the name of the user for whom you want to edit access.
3. Click **Access policies**.
4. Click **Edit** from the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu on the row for the policy that you want to edit.
4. Edit the policy by updating the assigned roles.
5. Click **Save**.

You can remove access from a user by clicking the **Remove** option from the **Actions** ![List of actions icon](../icons/action-menu-icon.svg) menu for the policy that you want to remove.

## Step 4. Assign access to SMS or Voice + SMS agents (Optional)
{: #sms_access}

If the agent that you are assigning access to is an **SMS** or **Voice + SMS** agent, create a *New Credential*.

### Creating a New Credential
{: #new_cred}

You can create credentials only for roles that are already active in your account. For SMS and Voice + SMS agents, you must have the *Writer* or *Manager* role assigned. See [Step 9 of Invite users and assign initial access](/docs/services/voice-agent?topic=voice-agent-iam#step1).

1. On the *Dashboard* of your {{site.data.keyword.iva_short}} instance, click **New Credential (+)**. 
2. In the new dialog box that pops up, enter a **Name**, and under the **Role** dropdown menu, select *Writer* or *Manager*. 
    - **NOTE:** For any SMS-related functionality, you **_must_** select the *Writer* or *Manager* role. 
3. Click on the **Add** button.

## Troubleshooting
{: #troubleshoot}

If you see an error message on the **Service Credentials** page when trying to create a *New Credential* that says:
> You do not have the required permission to assign role ‘Writer’. Contact the account owner to update your access.

Then you must follow the instructions to assign *Writer* or *Manager* access to yourself, which is **required** for SMS-related functions. See [Step 9 of Assigning Access](/docs/services/voice-agent?topic=voice-agent-iam#step1) and then continue with [Creating a New Credential](/docs/services/voice-agent?topic=voice-agent-iam#new_cred).

## Next steps
{: #next}

Learn more about what Cloud IAM can do by checking out the [Cloud IAM features](/docs/iam?topic=iam-iamoverview#features) list.