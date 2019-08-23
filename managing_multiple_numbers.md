---

copyright:
  years: 2019
lastupdated: "2019-03-15"

keywords: CSV, multiple phone numbers, agent

subcollection: "voice-agent"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}


# Configuring Multiple Phone Numbers to a _Single Agent_
{: #multi_num}

[comment]: # (After you create your {{site.data.keyword.iva_full}} service instance, )

You can add multiple phone numbers to a single Agent, so that configuring the Agent affects all the numbers that are associated with it. The _Manage Service Instance_ dashboard page shows the **Primary Number that is associated with the Agent. See [Setting a Primary Number](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

You can access the **Manage** dialog box by clicking **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page.

  * _**NOTE:**_ There is a limit of 1000 unique numbers per Agent configuration.
{: shortdesc}


## Adding a New Number
{: #add_num}

1. Click **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page to open the **Manage** dialog box.

1. Click the "Add Number" icon near the upper right of the **Manage** dialog box. A new empty entry is created in the list.

1. {: #format_num} For **Phone Number**, add the number from your SIP trunk, including the country and area codes. For example, for a United States 800 number, specify the phone number as 18883334444. The phone number can have spaces and + ( ) - characters, and a maximum of 30 characters.  

  * _**NOTE:**_ There is a limit of 1000 unique numbers per voice agent configuration.

1. You can optionally provide a description for your phone number in the **Description** field, up to a maximum of 64 characters.

1. Click the "check mark" icon to save the number to the list, or click the "X" icon to cancel the addition.

1. A "Success!" message is shown at the top, along with an entry in the list with the new number. Otherwise, an error message with a description will be shown.

1. The number has a **Green** check mark under the Status column in the list, indicating that the number is free of errors.

1. Click **Done** to save and confirm the number to the Agent.

## Editing a Number or Description
{: #edit_num}

1. Click **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page. Alternatively, if you already have multiple numbers in the Voice Agent, click the grayed out **Phone Number** field to open the **Manage** dialog box.

1. Highlight the number entry that you want to edit, and click the options list, represented by **three dots** icon, that appears on the right side of the list.

1. From the dropdown menu that appears, select **Edit**.

1. You can now edit and make changes to the **Phone Number** and the **Description**.

1. Click the "check mark" icon to accept the update, or click the "X" icon to discard the update.

1. A "Success!" message is shown at the top, along with the entry in the list that is being updated. Otherwise, an error message with a description is shown.

1. Click **Done** to save changes to the Agent.

## Deleting Numbers
{: #delete_num}

1. Click **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page.

1. Check the white box next to all the numbers that you want to delete. To select _all_ the numbers, check the white box next to the **Phone Number** header.

1. Click the "Delete Item" icon near the upper right of the **Manage** dialog box.

1. A "Success!" message is shown at the top, and the selected entries are removed from the list. Otherwise, an error message with a description will be shown.

1. Alternatively, to delete a single number, instead of checking the box, you can highlight the number entry that you want to delete. Then, click the options list, represented by **three dots** icon, that appears on the right side of the list.

1. From the dropdown menu that appears, select **Delete**.

1. A "Success!" message is shown at the top, and the highlighted entry is removed from the list. Otherwise, an error message with a description will be shown.

1. Click **Done** to save and confirm the deletion of the number or numbers from the Agent.

## Importing Numbers
{: #import_num}

A list of numbers can be uploaded into the Agent all at once. The list _must_ be a file of type **.csv**. The file can have up to and including 1000 unique **Phone Numbers**, with one number per line, along with an optional **Description** for each number.

  * _**NOTE:**_ Uploading numbers from a .CSV file replaces _ALL_ current numbers in the Agent. The number list will _not_ be appended with the numbers from the .CSV file.

  * Numbers in the .CSV file _must_ conform to the same format as adding a number through the Dashboard, and must be unique. See [Number Format](/docs/services/voice-agent?topic=voice-agent-multi_num#format_num).

1. Click **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page.

1. Click the "Upload CSV File" icon near the upper right of the **Manage** dialog box.

1. You are presented with a window to confirm that you are replacing all existing numbers in the list with the numbers from the .CSV file. Click **OK** to acknowledge and proceed.

1. In the new window, browse to the .CSV file, select it, and click **Open**.

1. A "Success!" message is shown at the top, and all the new numbers are added to the list. Otherwise, an error message with a description is shown, along with error messages next to each number with a problem.

1. The individual imported numbers have a **Green** check mark under the _Status_ column in the list, indicating that the number is free of errors. Otherwise, a specific error is displayed in the _Status_ column.

1. Click **Done** to save and confirm the addition of the number or numbers from the Agent.

## Exporting Numbers
{: #export_num}

A list of numbers and their descriptions can be exported from the Agent into a **.CSV** file and downloaded to your computer. This lets you modify the numbers and descriptions as you want, and you can upload them again to the Agent. See [Importing Numbers](/docs/services/voice-agent?topic=voice-agent-multi_num#import_num).

1. Click **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page.

1. Click the "Download CSV File" icon near the upper right of the **Manage** dialog box.

1. A .CSV file of all the numbers that are saved in the Agent will be downloaded to your computer.

1. You can click **Done** to exit the **Manage** dialog box.

## Setting a Primary Number
{: #primary_num}

The _Primary Number_ is for display purposes only and does not serve any functional purpose. By default, the first number that is added to the Agent is labeled as the **Primary Number**, which is the number that is displayed on the _Manage Service Instance_ dashboard page. At least one **Primary Number** must exist in a Voice Agent.

You can change the **Primary Number** label to any number you want in the Voice Agent.

1. Click **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page.

1. Highlight the number entry that you wish to edit, and click the options list, represented by **three dots** icon, that appears on the right side of the list.

1. From the dropdown menu that appears, select **Set as primary**.

1. A "Success!" message is shown at the top. Your chosen entry has the **Primary** label under the _Status_ column. Otherwise, an error message with a description will be shown.

1. Click **Done** to save changes to the Agent.

## Sorting and Navigating Phone Numbers
{: #sort_num}

You can sort the list of numbers based on the _Phone Numbers_ or on the _Descriptions_, in either ascending or descending order. By default, the phone number list is sorted ascending order by the **Phone Number**.

1. Click the **Phone Number** header to sort the numbers numerically in the list.

1. Click the **Description** header to sort the numbers alphabetically by their _Description_ in the list.  

You can also choose varying amounts of numbers that are shown per page in the list. You can show 5, 10, or 30 numbers per page. You can navigate to different pages of numbers as well.

1. Click the number next to **Items per page** to choose how many number entries will be shown in the list. By default, 5 are shown per page.

1. Click _Right_ or _Left_ arrow above the **Status** header to navigate between pages.

1. Alternatively, click the number between the arrows to manually choose a page to navigate.

1. Click **Done** to save changes to the Agent.

## Saving Changes
{: #save_changes}

If you want to make changes to the numbers list in the Voice Agent, you _must_ save the changes on the **Manage** dialog box, followed by saving the changes on the _Edit Voice Agent_ page.

1. Click **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page.

1. Make any changes to the numbers in the list as you want.

1. Click **Done** to save changes to the Agent.

1. You are taken back to the _Edit Voice Agent_ page, click **Save Changes** in the top right to apply all your changes.

* _**NOTE:**_ You _must_ click both **Done** on the **Manage** dialog box _and_ **Save Changes** on the _Edit Voice Agent_ page to save your changes, otherwise they are discarded.

## Searching For Numbers or Description
{: #search_num}

You can search for numbers that are stored by searching for the number or description.

1. Click **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page.

1. In the _Search_ bar, you can type a number or description to search for in the list. As you type, the search results are updated automatically.

1. Click **Done** to save changes to the Agent.
