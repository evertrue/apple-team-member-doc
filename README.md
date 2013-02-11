# 3rd Party Apple Publisher Setup


### Table of Contents
1.  Introduction
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

This document outlines the process of publishing an application to the iTunes App Store.  The 'agent' on the account sets up an app for publication to the App Store.  



# Add The 3rd Party Developer

## Definition of Roles
(add description of what it means to be agent/admin/member)

## Add the Team Member
Login to the iOS Dev Center (developer.apple.com) and direct to the “Member Center” in the upper navigation bar. Once in the Member Center, click on the “People” tab in the upper left corner. Click “Invite a Person to Your Team”. Fill out the invitation to add the team member.  

(TODO: Add image, better description of fields)

(TODO: Add description of the work required should the member only be given 'member' access vs. 'admin' access.  To be discussed are topics like approval of developer certificates, adding test devices, creation of app ids and push notification certificates.)

# Prepare the Local Computer
### Install xcode from apple
Login to the iOS Dev Center (developer.apple.com), and download the latest version of XCode. (or download from the Mac App Store)

### Create CSR file

(TODO: put directions for creating CSR in keychain access)

# Prepare the Developer Account

(If added team member as ADMIN, skip next 2 sections, go to 'create certificate')]

### Create App ID - (Non-Admin Team Member)
The developer will provide the bundle id to use. Create the app id in the ‘App Ids’ section of the provisioning portal:

When creating the app id, use a description to clearly denote what the app identifier is being used for. The bundle seed should be set to ‘Team ID’.

(TODO: more detail - with screenshot)

### Create push notification certificate - (Non-Admin Team Member)
After creating the app id, scroll down the page to the section with the newly created app id, and click ‘configure’.

Then, click the checkbox next to ‘Enable for Apple Push Notification service’, and ‘Configure’. Follow the instructions for creating a push notification certificate. This involves uploading a certificate signing request file, which was created above. Once the push certificate is created, download it and double click it to load it into the keychain. Right click on the push certificate and choose ‘export’:  

(TODO:  more detail & screenshot)

This is save a .p12 file. Send this file to your developer.

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
