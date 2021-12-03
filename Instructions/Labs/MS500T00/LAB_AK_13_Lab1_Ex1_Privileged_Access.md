# Module 13 - Lab 1 - Exercise 1 - Set up privileged access management and process a request


In your role as Holly Dickson, Adatum’s Security Administrator, you have been tasked with establishing privileged access management in Microsoft 365 as an additional layer of access management for global admins. Specifically, Adatum wants to prevent global admins from moving Exchange Mailboxes without getting specific approval from the MOD Administrator.

In this exercise, you will set up Privileged Access Management and create an access policy.

### Task 1 – Create an approver's group

Before you start using privileged access, determine who needs approval authority for incoming requests for access to elevated and privileged tasks. Any Global Admin who is part of the Approvers' group is able to approve access requests.  Adatum has decided to make the MOD Administrator, the user who will approve access requests.


1. You should still be logged into your Client 1 VM (**LON-CL1**) as the **LON-CL1\Admin** account, and you should be logged into Microsoft 365 as **Holly Dickson** and Password as **Pa55w.rd**. 

2. In your **Microsoft Edge** browser, if you have the **Microsoft 365 admin Center** open in a tab, then select it; otherwise, open a new tab and enter the following URL in the address bar: `https://admin.microsoft.com`.

3. In the admin center, click **Teams & Groups** and then select **Active Groups**.  In the **Active Teams & Groups** screen select **Add a group**.

4.  In the **Choose a group type** screen select **Mail-enabled security** and select **Next**.

5.  In the **Set up the basics** screen enter the Name `Privileged Access Approval Group` and enter a similar description and then select **Next**.

6.  In the **Edit settings** screen for the group email alias type `access`, tab to the next field to ensure it's acceptable, then select **Next**.

7.  In the **Review and finish adding group** screen select **Create group**. Select **Close**.

8.  In the **Active Groups** screen select **Mail-enabled security** tab and check the group you just created.  You may have to click **refresh** after several minutes for the group to appear in the list.

9.  In the **Privileged Access Approval Group** screen click the **Members** tab and then select **View all and manage members**.

10.  Select **+ Add members**. Search for **MOD Administrator**. Select **MOD Administrator** and click **Add (1)**. Close the **Privileged Access Approval Group** screen to return to the Groups screen.

**Note:** Holly Dickson is listed as the owner of the group you just created. She is therefore part of the Privileged Access Approval Group. In practice, and to support the scenario, you would make MOD Administrator the owner of the group and leave Holly out of it to prevent her from being able to approve her own privileged access requests.


### Task 2 – Enable privileged access

1. In the Microsoft 365 admin center, signed in as global administrator Holly Dickson. Select **Settings** then select **Org settings**.

2. In the Org settings screen select the **Security & privacy** tab and then select **Privileged access**.

3. In the Privileged Access screen make sure **Allow Priviledged access requests and choose default approval group** is **Checked**.

4.  Select the **Privileged Access Approval Group** as the **Default approval group**.  Click **Save** and close the **Privileged Access** window.


### Task 3 - Create a privileged access policy

It has been decided that Exchange mailbox moves tasks will require privileged access approval for Global Admins to complete such tasks.  In this task you will configure this policy.

1. In the Microsoft 365 admin center, signed in as global administrator Holly Dickson. Select **Settings** then select **Org settings**.  

2. In the Org settings screen select the **Security & privacy** tab and then select **Privileged access**. 

3. In the Privileged Access screen select **Create policies and manage requests**.

4. Select **manage policies** and then select **+ Add policy**.

5. In the **Add policy** window select the following:

Policy type = **Role**

Policy scope = **Exchange**

Policy name = **Move Mailboxes**

Approval type = **Manual**

6. Select the **Privileged Access Approval group** as the **Approvers** and select **Create**.  Close the **Request access** window.



### Task 4 - Submit a request for privileged access.

In this task you will request access to the Compliance Admin role to attain temporary access to perform certain Compliance actions.

1. In the Microsoft 365 admin center, signed in as global administrator Holly Dickson. Select **Settings** then select **Org settings**.  

2. In the Org settings screen select the **Security & privacy** tab and then select **Privileged access**. 

3. In the Privileged Access screen select **Create policies and manage requests**.

4. Select **Access Requests** Then **+ Request Access**.  In the **Request Access** screen select the following and then **Create**

Request type:  **Role**

Request scope:  **Exchange**

Request for:  **Move Mailboxes** 

Duration(hours): `8`

Comments: `I need to move mailboxes for the new department today`. 

5. When the access request is done processing select **Close** 


### Task 5 - Approve a privileged access request.

1. Switch to **LON-CL2** virtual machine.  In the Microsoft 365 admin center (`https://admin.microsoft.com`), sign in as **MOD Administrator** the password for this account was assigned by your lab hosting provider. Select **Settings** (you may need to click **... Show all** first) then select **Org settings**.  

2. In the Org settings screen select the **Security & privacy** tab and then select **Privileged access**. 

3. In the Privileged Access screen select **Create policies and manage requests**.

4. By default the **All Requests** view should display all Privileged Access Requests.

5. Select the request for **Move Mailboxes** access with the status of **Pending**.

6. In the **Compliance Admin** screen select **Approve**.  Select **Close**.

Summary: Global Admin Holly Dickson required short-term authorization to move mailboxes.  She requested 8 hours of access to those role tasks which was approved by the MOD Administrator.

**Important:** It would be prudent to disable Privileged Access Management after completing this lab so it doesn't accidentally interfere with actions in the remaining labs.
