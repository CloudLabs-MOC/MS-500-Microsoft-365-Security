# Module 11 - Lab 1 - Exercise 2 - Test DLP Policies


You are now at the point in your pilot project where you want to test policies. You have decided to test a DLP policy related to emails that contain sensitive information. 


### Task 1 – Test a DLP Policy for Sensitive Emails

In the previous exercise, you created a custom DLP policy that searches emails for sensitive information related to U.S. Social Security numbers in your Adatum tenant. In this exercise, you will send an email with a social security number from Holly Dickson to Alex Wilber.

1. On the Client 1 VM (**LON-CL1**), in which you should still be logged into Microsoft 365 as Holly Dickson (**holly@ZZZZZZ.onmicrosoft.com)** with a password given in Environment Dteails page of lab guide, where ZZZZZZ is your unique tenant suffix ID provided by your lab hosting provider.

1. You will now send an email from Holly to Alex; the email will contain US Social Security numbers. In **Microsoft Edge**, the **Outlook on the web** tab should still be open for Holly. Select the **Outlook on the web** tab.  If not open a browser to `https://portal.office.com`, make sure you are signed-in as Holly Dickson and select **Outlook**.

1. In the upper left corner of the screen, select **New message**. 

1. In the message pane that appears on the right-side of the screen, enter the following information:

	- To: start typing `Alex` and a drop-down menu displays with users whose name begins with that. Select **Alex Wilber**.

	- Add a subject: `DLP Policy Test`

	- Message area: type `This customer has social security number: 123-45-6789`.




1. Select **Send.**

1. You will now send a second message from Holly to Alex that contains multiple social security numbers.  In **Outlook**, in the upper left corner of the screen, select **New message**. 

1. In the message pane that appears on the right-side of the screen, enter the following information:

	- To: start typing `Alex` and a drop-down menu displays with users whose name begins with that. Select **Alex Wilber**.

	- Add a subject: `multiple SSN test`

	- Message area: `SSN = 123 45 6789 and another customer SSN 111 11 1111 and a third 222 22 2222`

![](../Media/142.png)

1. Select **Send.**

1. Open New InPrivate window and enter the following URL in the address bar: `https://outlook.office365.com`

1. You want to sign into **Outlook on the web** as **Alex Wilber**. If the **Pick an account** window appears, Alex’s account won’t appear since she hasn’t signed in before. Therefore, select **Use another account**. 

1. In the **Sign in** window, enter **AlexW@M365xZZZZZZ.onmicrosoft.com** (where ZZZZZZ is your unique tenant ID provided by your lab hosting provider) and then select **Next.**

1. In the **Enter password** window, enter Alex's password (hint: it's probably the same as the MOD admin password) and then select **Sign in**.

1. In the **Stay signed in?** window, select **Don’t show this again** and then select **Yes**.

1. If you approach the site for the first time, you may be asked for your language setting and your time zone:

	- From the **Language** dropdown select **English (United States).**

	- From the **Time zone** dropdown select your preferred time zone.

1. Select **Save**.

1. If a window is displayed asking whether you want to try the new outlook, select **Try the new Outlook.**

1. If a **Welcome** window appears, then close it now.

1. In **Outlook on the web**, in Alex’s **Inbox**, you should see the email message that Holly just sent to Alex containing a single SSN number.

1. The email with multiple SSNs should have been blocked and a warning message should appear in Holly's inbox (on LON-CL1) that looks something like this:

     ![Screenshot](../Media/DLP_policy_validation.png)

1. Delete the message from Alex’s Inbox as the last operation in this exercise. You have now successfully tested your custom DLP policy.

1. Leave both client VMs open for the next lab. Do not close any of the browser tabs.

**TROUBLESHOOTING this lab**

"Nothing happened, both emails went to Alex".
  
1. It can take many minutes for a DLP policy to propagate a tenant.  Most likely you sent the emails to Alex before the policy and subsequent scanning had a chance to be in place in your tenant.  If that happened come back to this lab later and resend the emails again.

1. Another possibility is that you didn't format the SSN's properly in the body of the email.  Sensitive information types in DLP policies scan for data formatted in a particular way that is common for that data type.  If you click the link below you can see exactly how US Social Security numbers must be formatted in content in order to be detected by DLP policy scans.
[https://docs.microsoft.com/en-us/microsoft-365/compliance/what-the-sensitive-information-types-look-for?view=o365-worldwide#us-social-security-number-ssn](https://docs.microsoft.com/en-us/microsoft-365/compliance/what-the-sensitive-information-types-look-for?view=o365-worldwide#us-social-security-number-ssn)

1. Check the DLP Policy configuration. Make sure you configured the policy as described in the previous exercise.

This is a good lab for testing various DLP policy configurations. Once you have successfully completed this lab consider reconfiguring this DLP policy to trigger other outcomes.


# End of Lab
