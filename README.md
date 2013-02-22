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
    
# Introduction

This document outlines the process of publishing an application to the Apple App Store.  

# Add The 3rd Party Developer

## Definition of Roles

#### Team Agent
A team agent is legally responsible for the team and acts as the primary contact with Apple.  The team agent has access to iTunes Connect to submit applications to the app store.

#### Team Admin
A team admin can create and approve certificates, provisioning profiles and add devices.  A team admin cannot submit applications to the app store.

#### Team Member
A team member cannot create certificates or add devices.   Certificates must be approved by a team administrator as well as the app id and push notification certificate.

## Add The Developer To The Team
Navigate to the iOS Dev Center (developer.apple.com) and direct to the “Member Center” in the upper navigation bar. 

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/invitemember_1.png?raw=true)

Login with your Apple ID.   Once in the Member Center, click on the “People” tab in the upper left corner. 

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/invitemember_2.png?raw=true "Member Center")

Click "Invitations" in the side bar, and then click the "Invite Person" button. 

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/invitemember_3.png?raw=true "Member Center")

Fill out the invitation to add the team member.  

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/invitemember_4.png?raw=true "Member Center")

The level of access you give to the developer determines the amount of work that they can do without needing approval from the team agent (or other team admin).  See above section on roles, or further information by clicking the "iOS Developer Program Roles Overview" link.

# Prepare the Local Computer
### Install xcode from apple
Login to the iOS Dev Center (developer.apple.com), and download the latest version of XCode. (or download from the Mac App Store)

### Create CSR file

Launch the application 'Keychain Access' in /Applications/Utilities

From the menu, click Keychain Access->Certificate Assistant->Request a Certificate from a Certificate Authority...

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/csr_1.png?raw=true "CSR")

Inside the Certificate Assistant, enter your email address, your name, keep 'CA Email Address' blank.  Also, choose that request be 'Saved to Disk'.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/csr_2.png?raw=true "CSR")

Click 'continue' and save the CSR file somewhere handy.


# Prepare the Developer Account

Navigate to the iOS Provisioning Portal by clicking the link on the right hand side:

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/provportal_1.png?raw=true "Portal")

Here is where you will setup the developer account.

If the 3rd party developer was added as an administrator, skip next 2 sections, go to [Create Distribution Certificate](#create-distribution-certificate)

### Create App ID

**(ONLY NEEDED DEVELOPER ADDED AS NON-ADMIN)**

Navigate to the App Ids section by clicking the link in the left side:

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/appids_1.png?raw=true "AppIds")

Click the 'New App Id' button.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/appids_2.png?raw=true "AppIds")

For the description, enter something that clearly indentifies this application.   You will choose this from a list later, so don't make it to generic.  Leave the Seed Id as 'Use Team Id'.  **The bundle id should be provided to you by the developer**.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/appids_3.png?raw=true "AppIds")

### Create push notification certificate

**(ONLY NEEDED DEVELOPER ADDED AS NON-ADMIN)**

After creating the app id, scroll down the page to the section with the newly created app id, and click ‘configure’.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/appids_4.png?raw=true "AppIds")

Then, click the checkbox next to ‘Enable for Apple Push Notification service’, and click the ‘Configure’ button next to 'Production Push SSL Certificate'. 

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/appids_5.png?raw=true "AppIds")

Follow the instructions for creating a push notification certificate. This involves uploading a certificate signing request file, which was created above. Once the push certificate is created, download it and double click it to load it into the keychain. Keychain Access should automatically open.

With the 'iOS Push Services' certificate hilighted in Keychain Access. From the 'File' menu, choose 'Export Items'.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/appids_6.png?raw=true "AppIds")

Make sure to export it as a .p12 file. Send this file to your developer.

### Create Distribution Certificate

In order to submit an application, a distribution certificate needs to be created.  This certificate needs to be created by the person doing the submission to the app store or the signing won't work correctly.  The team agent is the only team member with access to iTunes Connect, so the team agent needs to be the one that creates the distribution certificate.

Navigate to the Certificates section by clicking the link in the left side.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/cert_1.png?raw=true "Certs")

Click the 'Distribution' tab, and then click the 'Request Certificate' button.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/cert_2.png?raw=true "Certs")

It will ask you for a CSR file, you can use the same one you created earlier.  After it is created, it will be 'Pending' for a second.  Refresh the page until it gives you a 'Download' button.  Click to download the certificate, and double-click it to load into your keychain.


### Create Provisioning Profile

Back in the provisioning portal, navigate to the Provisioning section by clicking the link in the left side.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/prov_1.png?raw=true "Prov")

Click the 'Distribution' tab, and then click the 'New Profile' button.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/prov_2.png?raw=true "Prov")

Choose ‘App Store’ as the type. Give the profile a name. Choose the distribution certificate you created above.  (There should be only one) Under ‘App ID’, choose the application id that was created above (or provided by your developer).

It may take a second for the profile to be created, refresh the page until it gives you a download button.  Download the profile and double click it to load it into the XCode Organizer.  You will know the process worked if you have a green checkmark in the status next to the profile.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/prov_3.png?raw=true "Prov")

# Prepare iTunes Connect

### Create new application

Log in to iTunes Connect (itunesconnect.apple.com).  The developer will provide you with the information you need to enter, as shown in the following video.

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/DEMOVIDEO_iTunesConnect_AppSetup.mp4?raw=true)

# Publish The Application

### Import the .xarchive

After your application is built, the developer will send an .xarchive file.  Double click the .xarchive file to load it into the XCode organizer.

Choose the .xarchive and click ‘Distribute’. 

![](https://github.com/evertrue/apple-team-member-doc/blob/master/pageimages/xcode_1.png?raw=true "xcode")

Select the ‘Submit to App Store’ option. Login using your agent credentials. Choose the distribution provisioning profile that was created above, to re-sign the xarchive for distribution.

If there were no errors during upload, the application should be flipped to ‘waiting for review’ in iTunes Connect.
