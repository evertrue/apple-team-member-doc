# 3rd Party Apple Publisher Setup

### Table of Contents
1.  [Introduction](#introduction)
2.  Add The 3rd Party Developer
    - Definition of Roles
    - Add the Team Member
3.  Prepare the Local Computer
    - Install xcode from apple
    - Create CSR File
4.  Prepare the Developer Account
    - Create App ID - (Non-Admin Team Member)
    - Create push notification certificate - (Non-Admin Team Member)
    - Create Distribution Certificate
    - Create Provisioning Profile
5.  Prepare iTunes Connect
    - Create new application
6.  Publish The Application
    -  Import the .xarchive

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

![](/images/invitemember_1.png "Member Center")

Login with your Apple ID.   Once in the Member Center, click on the “People” tab in the upper left corner. 

![](/images/invitemember_2.png "Member Center")

Click "Invitations" in the side bar, and then click the "Invite Person" button. 

![](/images/invitemember_3.png "Member Center")

Fill out the invitation to add the team member.  

![](/images/invitemember_4.png "Member Center")

The level of access you give to the developer determines the amount of work that they can do without needing approval from the team agent (or other team admin).  See above section on roles, or further information by clicking the "iOS Developer Program Roles Overview" link.

# Prepare the Local Computer
### Install xcode from apple
Login to the iOS Dev Center (developer.apple.com), and download the latest version of XCode. (or download from the Mac App Store)

### Create CSR file

Launch the application 'Keychain Access' in /Applications/Utilities

From the menu, click Keychain Access->Certificate Assistant->Request a Certificate from a Certificate Authority...

![](/images/csr_1.png "CSR")

Inside the Certificate Assistant, enter your email address, your name, keep 'CA Email Address' blank.  Also, choose that request be 'Saved to Disk'.

![](/images/csr_2.png "CSR")

Click 'continue' and save the CSR file somewhere handy.


# Prepare the Developer Account

Navigate to the iOS Provisioning Portal by clicking the link on the right hand side:

![](/images/provportal_1.png "Portal")

Here is where you will setup the developer account.

If the 3rd party developer was added as an administrator, skip next 2 sections, go to [Create Distribution Certificate](#create-distribution-certificate)

### Create App ID

**(ONLY NEEDED DEVELOPER ADDED AS NON-ADMIN)**

Navigate to the App Ids section by clicking the link in the left side:

![](/images/appids_1.png "AppIds")

Click the 'New App Id' button.

![](/images/appids_2.png "AppIds")

For the description, enter something that clearly indentifies this application.   You will choose this from a list later, so don't make it to generic.  Leave the Seed Id as 'Use Team Id'.  **The bundle id should be provided to you by the developer**.

![](/images/appids_3.png "AppIds")

### Create push notification certificate

**(ONLY NEEDED DEVELOPER ADDED AS NON-ADMIN)**

After creating the app id, scroll down the page to the section with the newly created app id, and click ‘configure’.

![](/images/appids_4.png "AppIds")

Then, click the checkbox next to ‘Enable for Apple Push Notification service’, and click the ‘Configure’ button next to 'Production Push SSL Certificate'. 

![](/images/appids_5.png "AppIds")

Follow the instructions for creating a push notification certificate. This involves uploading a certificate signing request file, which was created above. Once the push certificate is created, download it and double click it to load it into the keychain. Keychain Access should automatically open.

With the 'iOS Push Services' certificate hilighted in Keychain Access. From the 'File' menu, choose 'Export Items'.

![](/images/appids_6.png "AppIds")

Make sure to export it as a .p12 file. Send this file to your developer.

### Create Distribution Certificate

In order to submit an application, a distribution certificate needs to be created.  This certificate needs to be created by the person doing the submission to the app store or the signing won't work correctly.  The team agent is the only team member with access to iTunes Connect, so the team agent needs to be the one that creates the distribution certificate.

(TODO:  better description of creating distribution certificate, including screenshot)

In the developer center, on the right hand side, click the ‘iOS Provisioning Portal’.
From the provisioning portal, under the Certificates tab, click the ‘Request Certificate’ button.
Follow the stated directions, and upload the CSR from the previous section.


### Create Provisioning Profile
Under the Provisioning tab, create a distribution profile. Click ‘New Profile’. Choose ‘App Store’ as the type. Give the profile a name. Under ‘App ID’, choose the application id that was created above (or provided by your developer)

Download the profile and double click it to load it into XCode.

(TODO:  I don't like the order here, since Admin team members can do this step, but the distribution certificate needs to have already been created, by the Agent)


# Prepare iTunes Connect

### Create new application

Log in to iTunes Connect (itunesconnect.apple.com), click ‘Add New App’ and use the above provided information to fill out everything required. After finishing creation, click ‘Ready to Upload’

(show video)


# Publish The Application

### Import the .xarchive

After your application is built, the developer will send an .xarchive file.  Double click the .xarchive file to load it into the XCode organizer.

Choose the .xarchive and click ‘distribute’. Select the ‘Submit to App Store’ option. Login using your agent credentials. Choose the distribution provisioning profile that was created above, to re-sign the xarchive for distribution.
If there were no errors during upload, the application should be flipped to ‘waiting for review’.
