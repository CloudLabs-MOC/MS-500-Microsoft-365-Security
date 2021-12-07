# Module 7 - Lab 1 - Exercise 3 - Creating compliance and conditional access policies 

### Scenario

Datum would like to ensure that enrolled Windows 10 devices meet a minimum configuration specification.  The following are required:

* Minimum OS version: 10.0.17763.615
* Windows Defender Antimalware required
* iOS and MacOS platforms blocked

If the device does not meet these requirement, the device should be marked as non-compliant.

#### Task 1: Create and apply compliance policy and enrollment restrictions

1.  Sign in to **LON-CL1** as **ADATUM\\Administrator** with the password `Pa55w.rd`. 

2.  In Microsoft Edge, type `https://endpoint.microsoft.com` in the  address bar, and then press **Enter**. Sign in as as **admin\@yourtenant.onmicrosoft.com** with the default tenant password.

3.  From the navigation pane click **Devices**, then click **Compliance Policies**.

4.  On the **Compliance policies | Policies** blade, in the details pane click **Create Policy**.

5.  On the **Create a policy** blade, provide the following values and click **Create**:

    -  Platform: **Windows 10 and later**

6.  On the Basics tab, provide the following values and click **Next**:

    -  Name: `Compliance1`

7.  On the **Compliance settings** tab, click **Device Health** and review the available settings.

8.  On the **Compliance settings** tab, expand **Device Properties**. In the **Minimum OS version** field, type `10.0.16299.15`.

9.  On the **Compliance settings** tab, expand **System Security**. Scroll down and set the 
    **Windows Defender Antimalware** setting to **Require**. Click **Next**.

10. On the **Actions for noncompliance** tab, note that the schedule to **Mark device noncompliant** is immediately. Review how you can configure the number of days after which the device is marked as noncompliant, and configuration additional actions. Click **Next**. 

11. On the **Assignments** tab, under **Included groups**, click **+ Add groups**. Click `Enrolled Devices`, choose **Select**, and then click **Next**.

12. Click **Create**.

13. From the left menu click **Devices**, then click **Enroll devices**.

14. On the **Enrollment devices | Windows enrollment** blade, click **Enrollment restrictions**.

15. On the details pane, in the **Device Type Restrictions** section, on the **Default** line, click **All Users**.
    
16. On the **All Users** blade, click **Properties**. In the **Platform settings** section, click **Edit**.

17. On the **Platforms settings** tab, in the **Platform** column, on the rows with **iOS/iPadOS** and **macOS**, click **Block**. Click **Review + save** and then click **Save**.

18. Scroll left to the **Enroll devices | Enrollment restrictions** blade. In the **Device Limit Restrictions** section, click **All Users** and then click **Properties**.

19. In the **Device limit** section, click **Edit**, then change the value to **3**.  

20. Click **Review + Save**, and then click **Save**.


## Task 2: Creating a conditional access policy

### Scenario 

When devices are non-compliant, they should not be able to access their e-mail. You've been asked to configure a conditional access policy that enforces this rule, and verify it functions as expected.


1.  On **LON-CL1**, in the **Microsoft Endpoint Manager admin center** click **Devices**, then click **Conditional Access**.

2.  In the **Conditional Access | Policies** pane, click **+ New policy**.

3.  On the **New** blade, in the **Name** text box, type `Conditional1` and then click **Users and groups**.

4.  On the **Users and groups** blade, click the **All users** radio button.

5.  On the **New** blade, click **Cloud apps or actions**, click the **Select apps** radio button, click **Select**, click **Office 365**, and then click **Select**.

6.  On the **New** blade, click **Conditions** > **0 conditions selected**. Under **Device state** label, click **Not configured**. Under **Device state** pop-up window, click **Yes** below configure, click the **Select device platforms** radio button, click the **Windows** check box, and then click **Done**.

7.  On the **New** blade under **Access controls**, click **Grant**, click the **Require device to be marked as compliant** check box, and then click **Select**.

8.  On the **New** blade, click **On** for the **Enable policy** option and then click **Create**.

#### Task 3: Verify that the conditional access policy is working

1.  On **LON-CL2**, open a new Microsoft Edge tab, then and open `https://portal.office.com`.

2.  Click the **Outlook** icon. 

3.  Verify that you receive the message **"You can't get there from here"** or similar warning message.

4.  Click **More details**. You should see more information about why you are blocked. **Note:** This is because LON-CL1 is not joined to Azure AD and not managed by Intune, so not marked as compliant.

5.  **Close** the browser window.

6.  Return to **LON-CL1** and open EndPoint Manager. In Microsoft Edge, type `https://endpoint.microsoft.com` in the  address bar, and then press **Enter**. Sign in as as **admin\@yourtenant.onmicrosoft.com** with the default tenant password.

7.  Click **Devices** and then click **Conditional access**. Click the ellipses next to policy "Conditional1" and click **Delete**.  Click **Yes** to confirm deletion.  Note: If you don't delete this policy it will interfere with later labs.



**End of lab**
