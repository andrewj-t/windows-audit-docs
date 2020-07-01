---
title: Deploy Microsoft Defender ATP for Android with Microsoft Intune
ms.reviewer:
description: Describes how to deploy Microsoft Defender ATP for Android with Microsoft Intune
keywords: microsoft, defender, atp, android, installation, deploy, uninstallation,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
---

# Deploy Microsoft Defender ATP for Android with Microsoft Intune 

**Applies to:**

- [Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) for Android](microsoft-defender-atp-android.md)

This topic describes deploying Microsoft Defender ATP for Android on Intune
Company Portal enrolled devices. For more information about Intune device enrollment, see  [Enroll your
device](https://microsoft.sharepoint.com/teams/WDATPIndia/Shared%20Documents/General/PM%20Docs/External%20Documentation/aka.ms/enrollAndroid).


> [!NOTE]
> During public preview, instructions to deploy Microsoft Defender ATP for Android on Intune enrolled Android devices are different across Device Administrator and Android Enterprise entrollment modes. <br>
> **When Microsoft Defender ATP for Android reaches General Availability (GA), the app will be available on Google Play.**

## Deploy on Device Administrator enrolled devices

**Deploy Microsoft Defender ATP for Android on Intune Company Portal - Device
Administrator enrolled devices**

This topic describes how to deploy Microsoft Defender ATP for Android on Intune Company Portal - Device Administrator enrolled devices. Upgrade from the Preview APK to the GA version on Google Play would be supported.

### Download the onboarding package

Download the onboarding package from Microsoft Defender Security Center.

1. In [Microsoft Defender Security
Center](https://microsoft.sharepoint.com/teams/WDATPIndia/Shared%20Documents/General/PM%20Docs/External%20Documentation/securitycenter.microsoft.com), go to **Settings** \> **Machine Management** \> **Onboarding**.

2. In the first drop-down, select **Android** as the Operating system.

3. Select **Download Onboarding package** and save the downloaded .APK file.

    ![Image of onboarding package page](images/onboarding_package_1.png)

### Add as Line of Business (LOB) App

The downloaded Microsoft Defender ATP for Android onboarding package. It is a
.APK file can be deployed to user groups as a Line of Business app during the
preview from Microsoft Endpoint Manager Admin Center.

1. In [Microsoft Endpoint Manager admin
center](https://go.microsoft.com/fwlink/?linkid=2109431) , go to **Apps** \>
**Android Apps** \> **Add \> Line-of-business app** and click **Select**.

    ![Image of Microsoft Endpoint Manager Admin Center](images/eba67e1a3adfec2c77c35a34cb030fba.png)


2. On the **Add app** page and in the *App Information* section, click **Select
add package file** and then click the ![Icon](images/1a62eac0222a9ba3c2fd62744bece76e.png) icon and select the MDATP Universal APK file that was downloaded from the *Download Onboarding package* step.

    ![Image of Microsoft Endpoint Manager Admin Center](images/e78d36e06495c2f70eb14230de6f7429.png)


3. Select **OK**.

4. In the *App Information* section that comes up, enter the **Publisher** as
Microsoft. Other fields are optional and then select **Next**.

    ![Image of Microsoft Endpoint Manager Admin Center](images/190a979ec5b6a8f57c9067fe1304cda8.png)

5. In the *Assignments* section, go to the **Required** section and select **Add
group.** You can then choose the user group(s) that you would like to target
Microsoft Defender ATP for Android app. Click **Select** and then **Next**.

    >[!NOTE]
    >The selected user group should consist of Intune enrolled users.

      ![Image of Microsoft Endpoint Manager Admin Center](images/363bf30f7d69a94db578e8af0ddd044b.png)


6. In the **Review+Create** section, verify that all the information entered is
correct and then select **Create**.

    In a few moments, the Microsoft Defender ATP app would be created successfully,
and a notification would show up at the top-right corner of the page.

    ![Image of Microsoft Endpoint Manager Admin Center](images/86cbe56f88bb6e93e9c63303397fc24f.png)


7. In the app information page that is displayed, in the **Monitor** section,
select **Device install status** to verify that the device installation has
completed successfully.

    ![Image of Microsoft Endpoint Manager Admin Center](images/513cf5d59eaaef5d2b5bc122715b5844.png)


During Public Preview, to **update** Microsoft Defender ATP for Android deployed
as a Line of Business app, download the latest APK. Following the steps in
*Download the onboarding package* section and follow instructions on how to [update
a Line of Business
App](https://docs.microsoft.com/mem/intune/apps/lob-apps-android#step-5-update-a-line-of-business-app).

### Complete onboarding and check status

1. Once Microsoft Defender ATP for Android has been installed on the device, you'll see the app icon.

    ![Icon on mobile device](images/7cf9311ad676ec5142002a4d0c2323ca.jpg)

2. Tap the Microsoft Defender ATP app icon and follow the on-screen instructions
to complete onboarding the app. The details include end-user acceptance of Android permissions required by Microsoft Defender ATP for Android.

3. Upon successful onboarding, the device will start showing up on the Devices
list in Microsoft Defender Security Center.

    ![Image of device in Microsoft Defender ATP portal](images/9fe378a1dce0f143005c3aa53d8c4f51.png)

## Deploy on Android Enterprise enrolled devices

Microsoft Defender ATP for Android supports Android Enterprise enrolled devices.

For more information on the enrollment options supported by Intune, see 
[Enrollment
Options](https://docs.microsoft.com/mem/intune/enrollment/android-enroll) .

As Microsoft Defender ATP for Android is deployed via managed Google Play,
updates to the app are automatic via Google Play.

Currently only Work Profile enrolled devices are supported for deployment.


>[!NOTE]
>During Public Preview, to access Microsoft Defender ATP in your managed Google Play, contact [atpm@microsoft.com](mailto:atpm@microsoft.com) with the organization ID of your managed Google Play for next steps. This can be found under the **Admin Settings** of [managed Google Play](https://play.google.com/work/).<br>
> At General Availability (GA), Microsoft Defender ATP for Android will be available as a public app. Upgrades from preview to GA version will be supported.

## Add Microsoft Defender ATP for Android as a managed Google Play app

After receiving a confirmation e-mail from Microsoft that your managed Google
Play organization ID has been approved, follow the steps below to add Microsoft
Defender ATP app into your managed Google Play.

1. In [Microsoft Endpoint Manager admin
center](https://go.microsoft.com/fwlink/?linkid=2109431) , go to **Apps** \>
**Android Apps** \> **Add** and select **managed Google Play app**.

    ![Image of Microsoft Endpoint Manager admin center](images/579ff59f31f599414cedf63051628b2e.png)


2. On your managed Google Play page that loads subsequently, go to the search
box and lookup **Microsoft Defender.** Your search should display the Microsoft
Defender ATP app in your Managed Google Play. Click on the Microsoft Defender
ATP app from the Apps search result.

    ![Image of Microsoft Endpoint Manager admin center](images/0f79cb37900b57c3e2bb0effad1c19cb.png)

3. In the App description page that comes up next, you should be able to see app
details on Microsoft Defender ATP. Review the information on the page and then
select **Approve**.

    ![A screenshot of a Managed Google Play](images/07e6d4119f265037e3b80a20a73b856f.png)


4. You should now be presented with the permissions that Microsoft Defender ATP
obtains for it to work. Review them and then select **Approve**.

    ![A screenshot of Microsoft Defender ATP preview app approval](images/206b3d954f06cc58b3466fb7a0bd9f74.png)


5. You'll be presented with the Approval settings page. The page confirms
your preference to handle new app permissions that Microsoft Defender ATP for
Android might ask. Review the choices and select your preferred option. Select
**Done**.

    By default, managed Google Play selects *Keep approved when app requests new
permissions*

   ![Image of notifications tab](images/ffecfdda1c4df14148f1526c22cc0236.png)


6. After the permissions handling selection is made, select **Sync** to sync
Microsoft Defender ATP to your apps list.

    ![Image of sync page](images/34e6b9a0dae125d085c84593140180ed.png)


7. The sync will complete in a few minutes.

    ![Image of Android app](images/9fc07ffc150171f169dc6e57fe6f1c74.png)

8. Select the **Refresh** button in the Android apps screen and Microsoft
Defender ATP should be visible in the apps list.

    ![Image of list of Android apps](images/fa4ac18a6333335db3775630b8e6b353.png)


9. Microsoft Defender ATP supports App configuration policies for managed devices via Intune. This capability can be leveraged to autogrant applicable Android permission(s), so the end user does not need to accept these permission(s).

    a. In the **Apps** page, go to **Policy > App configuration policies > Add > Managed devices**.

    ![Image of Microsoft Endpoint Manager admin center](images/android-mem.png)

    b. In the **Create app configuration policy** page, enter the following details:
        - Name: Microsoft Defender ATP.
        - Choose **Android Enterprise** as platform.
        - Choose **Work Profile only** as Profile Type.
        - Click **Select App**, choose **Microsoft Defender ATP**, select **OK** and then **Next**.
    
    ![Image of create app configuration policy page](images/android-create-app.png)

    c. In the **Settings** page, go to the Permissions section click on Add to view the list of supported permissions. In the Add Permissions section, select the following permissions 
    - External storage (read)
    - External storage (write)

    Then select **OK**.

    ![Image of create app configuration policy](images/android-create-app-config.png)

    
    d. You should now see both the permissions listed and now you can autogrant both by choosing autogrant in the **Permission state** drop-down and then select **Next**.

     ![Image of create app configuration policy](images/android-auto-grant.png)


    e. In the **Assignments** page, select the user group to which this app config policy would be assigned to. Click **Select groups to include** and selecting the applicable group and then selecting **Next**.  The group selected here is usually the same group to which you would assign Microsoft Defender ATP Android app. 

    ![Image of create app configuration policy](images/android-select-group.png)
    

     f. In the **Review + Create** page that comes up next, review all the information and then select **Create**. <br>
    
    The app configuration policy for Microsoft Defender ATP auto-granting the storage permission is now assigned to the selected user group.

    ![Image of create app configuration policy](images/android-review-create.png)



10. Select **Microsoft Defender ATP** app in the list \> **Properties** \>
**Assignments** \> **Edit**.

    ![Image of list of apps](images/9336bbd778cff5e666328bb3db7c76fd.png)


11. Assign the app as a *Required* app to a user group. It is automatically installed in the *work profile* during the next sync of
the device via Company Portal app. This assignment can be done by navigating to
the *Required* section \> **Add group,** selecting the user group and click
**Select**.

    ![Image of edit application page](images/ea06643280075f16265a596fb9a96042.png)


12. In the **Edit Application** page, review all the information that was entered
above. Then select **Review + Save** and then **Save** again to commence
assignment.

## Complete onboarding and check status

1. Confirm the installation status of Microsoft Defender ATP for Android by
clicking on the **Device Install Status**. Verify that the device is
displayed here.

    ![Image of device installation status](images/900c0197aa59f9b7abd762ab2b32e80c.png)


2. On the device, you can confirm the same by going to the **work profile** and
confirm that Microsoft Defender ATP is available.

    ![Image of app in mobile device](images/c2e647fc8fa31c4f2349c76f2497bc0e.png)

3. When the app is installed, open the app and accept the permissions
and then your onboarding should be successful.

    ![Image of mobile device with Microsoft Defender ATP app](images/23c125534852dcef09b8e37c98e82148.png)

4. At this stage the device is successfully onboarded onto Microsoft Defender
ATP for Android. You can verify this on the [Microsoft Defender Security
Center](https://microsoft.sharepoint.com/teams/WDATPIndia/Shared%20Documents/General/PM%20Docs/External%20Documentation/securitycenter.microsoft.com)
by navigating to the **Devices** page.

    ![Image of Microsoft Defender ATP portal](images/9fe378a1dce0f143005c3aa53d8c4f51.png)


## Related topics
- [Overview of Microsoft Defender ATP for Android](microsoft-defender-atp-android.md)
- [Configure Microsoft Defender ATP for Android features](android-configure.md)
