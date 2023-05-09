---
lab:
    title: 'Lab1: Exercise 1 - Setting up your organization for identity synchronization  '
    type: 'Answer Key'
    module: 'Module 2: Identity Synchronization and Protection'
---

# Module 2 - Lab 1 - Exercise 1 - Setting up your organization for identity synchronization 

You are Holly Dickson the security administrator for Adatum Corporation, and you have Microsoft 365 deployed in a virtualized lab environment. In this lab, you will implement identity synchronization between your Microsoft 365 tenant accounts and your local active directory accounts.

### Task 1 - Configure your UPN suffix

1.	On LON-DC1, log on as **Adatum\Administrator** and password assigned from your lab hoster.
2.	Using Windows PowerShell as administrator, update the UPN suffix for the domain and on the UPN on every user in AD DS with “@zzzzzzz.onmicrosoft.com” (where zzzzzzz is your unique UPN name) for the domain name. To do this, run the following command (remember to change zzzzzzz to your unique UPN name):

	```powershell
	Set-ADForest -identity "adatum.com" -UPNSuffixes @{replace="zzzzzzz.onmicrosoft.com"}
	```

3.	Next type the follow command (remember to change zzzzzzz to your unique UPN name):

    ```powershell
	Get-ADUser –Filter * -Properties SamAccountName | ForEach-Object { Set-ADUser $_ -UserPrincipalName ($_.SamAccountName + "@zzzzzzz.onmicrosoft.com" )}
	```
		
4.	At the Windows PowerShell prompt, type the following command, and then press Enter:

    ```powershell
	Set-ExecutionPolicy Unrestricted  
	```
5.	To confirm the execution policy change, enter **A** for Yes to All press Enter key.
 
### Task 2 - Enable Directory Synchronization

1.	Open your browser and go to `https://portal.office.com/`   
2.	Sign in as **holly@M365xZZZZZZ.onmicrosoft.com** with the password that you set earlier for this account.    
3.	Click **Admin** to go to the Microsoft 365 admin center.
4.	If asked about **update your admin contact information** click the Cancel button to skip this request.  
	**Note:** If you see the Active Directory synchronization is being activated warning, you can ignore it at this time, but you will not be able to run directory synchronization later in this exercise. You must wait until directory synchronization is activated. However, you can complete the following steps, even if you do see the warning message.  
5.	In the left navigation, select **users** icon and select **Active users**, click on the ellipses at the top menu and choose **Directory Synchronization**. Click **Next**.
1. In the **Select a migration option** window that opens, select **Continuous sync**. Click **Next**. When prompted to optionally download IdFix, click **Next**.
6.	Select **Azure AD Connect** from the list of synchronization tools. Download and Run the download once prompted.
    
### Task 3 - Run Azure AD Connect

1.	On the Microsoft Azure Active Directory Connect setup wizard, proceed through the wizard. 
2.	Agree to the license terms and privacy notice.
3.	Click on **Use express settings**.   
4.	On the **Connect to Azure AD** screen enter your Microsoft 365 admin username of **holly@M365xZZZZZZ.onmicrosoft.com** and click Next.   
5.	If there is a pop up sign in window **Connect to AD DS** screen enter your domain administrator **Admin@M365xZZZZZZ.onmicrosoft.com** and password **provided by your lab hosting provider** and select **Next**.   
6.	On the **Connect to AD DS** screen enter your domain administrator **ADATUM\Administrator** and password `Pa55w.rd` and select **Next**.
7.	Select **Continue without matching all UPN suffixes to verified domains** checkbox. Select **Next** on the Azure AD sign-in configuration screen.   
8.	On the **Ready to configure** screen make sure the check box for **Start the synchronization process when configuration completes** is marked and select **Install**.   
9.	Wait for the installation to complete (this may take several minutes).   
10.	Select **Exit**.   

### Task 4 - Validate the results of directory synchronization and license a user. 

**Note**  When your M365 subscription was provisioned, all available licenses were allocated. Because we need a few licenses for this and future labs, you can remove
license assignments for a few users.

1.	To verify the new user you created open the Microsoft 365 Admin Center in the browser by typing `https://admin.microsoft.com/` in the address bar.  
2.	Sign in as Holly Dickson with the User name: **holly@M365xZZZZZZ.onmicrosoft.com** 
3.	In the left navigation, select **users** icon and select **Active users** 
4.	You should now see many users that have become synced from the local Active Directory.  You may need to click the refresh button to update the data in the page.  
5.	**Only complete if these users exist** Edit the following users to remove **both** the Microsoft 365 E5 and the Enterprise Mobility + Security E5 licenses:
	-Debra Berger
	-Irvin Sayers
	-Johanna Lorenz
	-Lidia Hallowey
	-Pradeep Gupta
**Note**  When your M365 subscription was provisioned,it may have been that all available licenses were allocated. Because we need a few licenses for this and future labs, you can remove license assignments for a few users that don't need them.
6.	Select Abbie Parsons.  Abbie is a user that was only in the AD DS domain prior to our synchronization. Edit Abbie Parsons Product licenses as follows: 
	- Location = United Kingdom
	- Product License = Enterprise Mobility + Security E5
7.	Click **Save changes** to make the changes. Close the window.

You have successfully synced local ADATUM users into Microsoft 365 and licensed the synced user Abbie Parsons.

# End of lab  

 
