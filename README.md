##Table of Contents

1. [Introduction](#introduction)
2. [Add The 3rd Party Developer](#add-the-3rd-party-developer)
  - [Definition of Roles](#definition-of-roles)
	- [Add The Developer To The Team](#add-the-developer-to-the-team)
3. [Prepare the Local Computer](#prepare-the-local-computer)
	- [Install xcode from apple](#install-xcode-from-apple)
	- [Create CSR file](#create-csr-file)
4. [Prepare the Developer Account](#prepare-the-developer-account)
	- [Create App ID](#create-app-id)
	- [Create push notification certificate](#create-push-notification-certificate)
	- [Create Distribution Certificate](#create-distribution-certificate)
	- [Create Provisioning Profile](#create-provisioning-profile)
5. [Prepare iTunes Connect](#prepare-itunes-connect)
	- [Create new application](#create-new-application)
6. [Publish The Application](#publish-the-application)
	- [Import the .xarchive](#import-the-xarchive)
    
# <a name="introduction"></a>1. Introduction

This document outlines the process of publishing an application to the Apple App Store.  

# <a name="add-the-3rd-party-developer"></a>2. Add The 3rd Party Developer

## <a name="definition-of-roles"></a>2.1 Definition of Roles

#### Team Agent
A team agent is legally responsible for the team and acts as the primary contact with Apple.  The team agent has access to iTunes Connect to submit applications to the app store.

#### Team Admin
A team admin can create and approve certificates, provisioning profiles and add devices.  A team admin cannot submit applications to the app store.

#### Team Member
A team member cannot create certificates or add devices.   Certificates must be approved by a team administrator as well as the app id and push notification certificate.

## <a name="add-the-developer-to-the-team"></a>2.2 Add The Developer To The Team
Navigate to the iOS Dev Center (developer.apple.com) and direct to the “Member Center” in the upper navigation bar. 

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/invitemember_1.png?raw=true)

Login with your Apple ID.   Once in the Member Center, click on the “People” tab in the upper left corner. 

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/invitemember_2.png?raw=true "Member Center")

Click "Invitations" in the side bar, and then click the "Invite Person" button. 

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/invitemember_3.png?raw=true "Member Center")

Fill out the invitation to add the team member.  

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/invitemember_4.png?raw=true "Member Center")

The level of access you give to the developer determines the amount of work that they can do without needing approval from the team agent (or other team admin).  See above section on roles, or further information by clicking the "iOS Developer Program Roles Overview" link.

# <a name="prepare-the-local-computer"></a>3. Prepare the Local Computer
### <a name="install-xcode-from-apple"></a>3.1 Install xcode from apple
Login to the iOS Dev Center (developer.apple.com), and download the latest version of XCode. (or download from the Mac App Store)

### <a name="create-csr-file"></a>3.2 Create CSR file

Launch the application 'Keychain Access' in /Applications/Utilities

From the menu, click Keychain Access->Certificate Assistant->Request a Certificate from a Certificate Authority...

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/csr_1.png?raw=true "CSR")

Inside the Certificate Assistant, enter your email address, your name, keep 'CA Email Address' blank.  Also, choose that request be 'Saved to Disk'.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/csr_2.png?raw=true "CSR")

Click 'continue' and save the CSR file somewhere handy.


# <a name="prepare-the-developer-account"></a>4. Prepare the Developer Account

Navigate to the iOS Provisioning Portal by clicking the link on the right hand side:

![](https://raw.github.com/evertrue/apple-team-member-doc/new-dev-center/pageimages/certs_ids_profiles.png "Portal")

Here is where you will setup the developer account.

If the 3rd party developer was added as an administrator, skip next 2 sections, go to [Create Distribution Certificate](#create-distribution-certificate)

### <a name="create-app-id"></a>4.1 Create App ID

**(ONLY NEEDED DEVELOPER ADDED AS NON-ADMIN)**

Navigate to the App Ids section by clicking the link in the left side:

![](https://raw.github.com/evertrue/apple-team-member-doc/new-dev-center/pageimages/app_id_1.png "AppIds")

Click the 'New App Id' button.

![](https://raw.github.com/evertrue/apple-team-member-doc/new-dev-center/pageimages/app_id_2.png "AppIds")

For the description, enter something that clearly indentifies this application.   You will choose this from a list later, so don't make it to generic.  Leave the Seed Id as 'Use Team Id'.  **The bundle id should be provided to you by the developer**.

![](https://raw.github.com/evertrue/apple-team-member-doc/new-dev-center/pageimages/app_id_3.png "AppIds")
![](https://raw.github.com/evertrue/apple-team-member-doc/new-dev-center/pageimages/app_id_4.png "AppIds")

Click 'Continue' and confirm the settings on the following page.

![](https://raw.github.com/evertrue/apple-team-member-doc/new-dev-center/pageimages/app_id_5.png "AppIds")
### <a name="create-push-notification-certificate"></a>4.2 Create push notification certificate

**(ONLY NEEDED DEVELOPER ADDED AS NON-ADMIN)**

After creating the app id, you will be redirected back to the list of app ids. Click on the list item corresponding to the newly created app id, and click 'Settings'. scroll down the page to the section with the newly created app id, and click ‘configure’.

![](https://raw.github.com/evertrue/apple-team-member-doc/new-dev-center/pageimages/push_settings_1.png "AppIds")

Scroll down to 'Push Notifications' and click 'Create Certificate...' 

![](https://raw.github.com/evertrue/apple-team-member-doc/new-dev-center/pageimages/push_settings_2.png "AppIds")

Follow the instructions for creating a push notification certificate. This involves uploading a certificate signing request file, which was created above. Once the push certificate is created, download it and double click it to load it into the keychain. Keychain Access should automatically open.

With the 'iOS Push Services' certificate hilighted in Keychain Access. From the 'File' menu, choose 'Export Items'.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/appids_6.png?raw=true "AppIds")

Make sure to export it as a .p12 file. Send this file to your developer.

### <a name="create-distribution-certificate"></a>4.3 Create Distribution Certificate

In order to submit an application, a distribution certificate needs to be created.  This certificate needs to be created by the person doing the submission to the app store or the signing won't work correctly.  The team agent is the only team member with access to iTunes Connect, so the team agent needs to be the one that creates the distribution certificate.

On the main page of the portal, under 'Certificates', choose 'Distribution'

![](https://raw.github.com/evertrue/apple-team-member-doc/new-dev-center/pageimages/distro_cert_1.png "AppIds")

On the following page, make sure 'App Store and Ad Hoc' is selected as the type of certificate.

![](https://raw.github.com/evertrue/apple-team-member-doc/new-dev-center/pageimages/distro_cert_2.png "AppIds")

### <a name="create-provisioning-profile"></a>4.4 Create Provisioning Profile

Back in the provisioning portal, navigate to the Provisioning section by clicking the link in the left side.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/prov_1.png?raw=true "Prov")

Click the 'Distribution' tab, and then click the 'New Profile' button.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/prov_2.png?raw=true "Prov")

Choose ‘App Store’ as the type. Give the profile a name. Choose the distribution certificate you created above.  (There should be only one) Under ‘App ID’, choose the application id that was created above (or provided by your developer).

It may take a second for the profile to be created, refresh the page until it gives you a download button.  Download the profile and double click it to load it into the XCode Organizer.  You will know the process worked if you have a green checkmark in the status next to the profile.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/prov_3.png?raw=true "Prov")

# <a name="prepare-itunes-connect"></a>5. Prepare iTunes Connect

### <a name="create-new-application"></a>5.1 Create new application

Log in to iTunes Connect (itunesconnect.apple.com).  The developer will provide you with the information you need to enter, as shown in the following video.

<video width="560" height="340" controls>
  <source src="https://dl.dropbox.com/u/2836123/DEMOVIDEO_iTunesConnect_AppSetup.mp4" type='video/mp4; codecs="avc1.42E01E, mp4a.40.2"'>
</video>

https://dl.dropbox.com/u/2836123/DEMOVIDEO_iTunesConnect_AppSetup.mp4

# <a name="publish-the-application"></a>6. Publish The Application

### <a name="import-the-.xarchive"></a>6.1 Import the .xarchive

After your application is built, the developer will send an .xarchive file.  Double click the .xarchive file to load it into the XCode organizer.

Choose the .xarchive and click ‘Distribute’. 

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/xcode_1.png?raw=true "xcode")

Select the ‘Submit to App Store’ option. Login using your agent credentials. Choose the distribution provisioning profile that was created above, to re-sign the xarchive for distribution.

If there were no errors during upload, the application should be flipped to ‘waiting for review’ in iTunes Connect.
