---

copyright:
  years: 2019
lastupdated: "2019-03-15"
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

[comment]: # (After you have created your {{site.data.keyword.iva_full}} service instance, )

You can add multiple phone numbers to a single Agent, so that configuring the Agent will affect all the numbers associated with it. The _Manage Service Instance_ dashboard page will show the **Primary Number** associated with the Agent. See [Setting a Primary Number](/docs/services/voice-agent?topic=voice-agent-multi_num#primary_num).

You can access the **Manage** dialog box by clicking on **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page.

  * _**NOTE:**_ There is a limit of 1000 unique numbers per Agent configuration.
{: shortdesc}


## Adding a New Number
{: #add_num}

1. Click on **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page to open the **Manage** dialog box.

1. Click on the "Add Number" icon near the top right of the **Manage** dialog box. A new empty entry will be created in the list.

1. {: #format_num} For **Phone Number**, add the number from your SIP trunk, including the country and area codes. For example, for a United States 800 number, specify the phone number as 18883334444. The phone number can have spaces and + ( ) - characters, and a maximum of 30 characters.  

  * _**NOTE:**_ There is a limit of 1000 unique numbers per voice agent configuration.

1. You may optionally provide a description for your phone number in the **Description** field, up to a maximum of 64 characters.

1. Click the "Check Mark" icon to save the number to the list, or click the "X" icon to cancel the addition.

1. A "Success!" message will be shown at the top, along with an entry in the list with the new number. Otherwise, an error message with a description will be shown.

1. The number will have a **Green** checkmark under the Status column in the list, indicating that the number is free of errors.

1. Click **Done** to save and confirm the number to the Agent.

## Editing a Number and/or Description
{: #edit_num}

1. Click on **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page. Alternatively, if you already have multiple numbers in the Voice Agent, simply click on the greyed out **Phone Number** field to open the **Manage** dialog box.

1. Highlight the number entry you wish to edit, and click the options list, represented by **three dots** icon, that appears on the right side of the list.

1. From the dropdown menu that appears, select **Edit**.

1. You may now edit and make changes to the **Phone Number** and/or the **Description**.

1. Click the "Check Mark" icon to accept the update, or click the "X" icon to discard the update.

1. A "Success!" message will be shown at the top, along with the entry in the list being updated. Otherwise, an error message with a description will be shown.

1. Click **Done** to save changes to the Agent.

## Deleting Numbers
{: #delete_num}

1. Click on **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page.

1. Check the white box next to all the numbers that you wish to delete. To select _all_ the numbers, simply check the white box next to the **Phone Number** header.

1. Click the "Delete Item" icon near the top right of the **Manage** dialog box.

1. A "Success!" message will be shown at the top, and the selected entries will be removed from the list. Otherwise, an error message with a description will be shown.

1. Alternatively, to delete a single number, instead of checking the box, you can highlight the number entry you wish to delete, and click the options list, represented by **three dots** icon, that appears on the right side of the list.

1. From the dropdown menu that appears, select **Delete**.

1. A "Success!" message will be shown at the top, and the highlighted entry will be removed from the list. Otherwise, an error message with a description will be shown.

1. Click **Done** to save and confirm the deletion of the number(s) from the Agent.

## Importing Numbers
{: #import_num}

A list of numbers may be uploaded into the Agent all at once. The list _must_ be a file of type **.csv**. The file may have up to and including 1000 unique **Phone Numbers**, with one number per line, along with an optional **Description** for each number.

  * _**NOTE:**_ Uploading numbers from a .CSV file will replace _ALL_ current numbers in the Agent. The number list will _not_ be appended with the numbers from the .CSV file.

  * Numbers in the .CSV file _must_ conform to the same format as adding a number through the Dashboard, and must be unique. See [Number Format](/docs/services/voice-agent?topic=voice-agent-multi_num#format_num).

1. Click on **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page.

1. Click the "Upload CSV File" icon near the top right of the **Manage** dialog box.

1. You will be presented with a window to confirm that you will be replacing all existing numbers in the list with the numbers from the .CSV file. Click **OK** to acknowledge and proceed.

1. In the new window, browse to the .CSV file, select it, and click **Open**.

1. A "Success!" message will be shown at the top, and all the new numbers will be added to the list. Otherwise, an error message with a description will be shown, along with error messages next to each number with a problem.

1. The individual imported numbers will have a **Green** checkmark under the _Status_ column in the list, indicating that the number is free of errors. Otherwise, a specific error will be displayed in the _Status_ column.

1. Click **Done** to save and confirm the addition of the number(s) from the Agent.

## Exporting Numbers
{: #export_num}

A list of numbers and their descriptions may be exported from the Agent into a **.CSV** file and downloaded to your computer. This will let you modify the numbers and/or descriptions as you wish, and you may upload them again to the Agent. See [Importing Numbers](/docs/services/voice-agent?topic=voice-agent-multi_num#import_num).

1. Click on **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page.

1. Click the "Download CSV File" icon near the top right of the **Manage** dialog box.

1. A .CSV file of all the numbers saved in the Agent will be downloaded to your computer.

1. You may click **Done** to exit the **Manage** dialog box.

## Setting a Primary Number
{: #primary_num}

The _Primary Number_ is for display purposes only and does not serve any functional purpose. By default, the first number added to the Agent will be labelled as the **Primary Number**, which is the number displayed on the _Manage Service Instance_ dashboard page. At least one **Primary Number** must exist in a Voice Agent.

You may change the **Primary Number** label to any number you wish in the Voice Agent.

1. Click on **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page.

1. Highlight the number entry you wish to edit, and click the options list, represented by **three dots** icon, that appears on the right side of the list.

1. From the dropdown menu that appears, select **Set as primary**.

1. A "Success!" message will be shown at the top. Your chosen entry will have the **Primary** label under the _Status_ column. Otherwise, an error message with a description will be shown.

1. Click **Done** to save changes to the Agent.

## Sorting and Navigating Phone Numbers
{: #sort_num}

You may sort the list of numbers based on the _Phone Numbers_ or on the _Descriptions_, in either ascending or descending order. By default, the phone number list is sorted ascending order by the **Phone Number**.

1. Click on the **Phone Number** header to sort the numbers numerically in the list.

1. Click on the **Description** header to sort the numbers alphabetically by their _Description_ in the list.  

You may also choose varying amounts of numbers shown per page in the list. You can show 5, 10, or 30 numbers per page. You may navigate to different pages of numbers as well.

1. Click on the number next to **Items per page** to choose how many number entries will be shown in the list. By default, 5 are shown per page.

1. Click on _Right_ or _Left_ arrow above the **Status** header to navigate between pages.

1. Alternatively, click on the number between the arrows to manually choose a page to navigate.

1. Click **Done** to save changes to the Agent.

## Saving Changes
{: #save_changes}

If you wish to make changes to the numbers list in the Voice Agent, you _must_ save the changes on the **Manage** dialog box, followed by saving the changes on the _Edit Voice Agent_ page.

1. Click on **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page.

1. Make any changes to the numbers in the list as you wish.

1. Click on **Done** to save changes to the Agent.

1. You will be taken back to the _Edit Voice Agent_ page, click on **Save Changes** in the top right to apply all your changes.

* _**NOTE:**_ You _must_ click both **Done** on the **Manage** dialog box _and_ **Save Changes** on the _Edit Voice Agent_ page to save your changes, otherwise they will be discarded.

## Searching For Numbers or Description
{: #search_num}

You can search for numbers stored by searching for the number or description.

1. Click on **Manage** next to **Phone Number** from the _Create a Voice Agent_ or _Edit Voice Agent_ page.

1. In the _Search_ bar, you may type a number or description to search for in the list. As you type, the search results will be updated automatically.

1. Click on **Done** to save changes to the Agent.
