# Restrict installation of macOS Sierra

Apple has yet to provide a way to prevent the update to a major OS release.

But, I believe it's for the greater good. Everyone should work toward supporting macOS on the day it is released. Apple gives us plenty of time to do this, thanks to the Developer, Apple Seed and Public betas.

If something goes wrong and you want to make sure your user don't upgrade to the newest macOS, follow these steps.

## Restrict Beta Version

If your goal is to restrict the Beta version, Apple provides the following kbase: [https://support.apple.com/en-us/HT203018](https://support.apple.com/en-us/HT203018) 

On Casper Suite, simply create a Configuration profile with a "Software Update" payload and deselect "Allow installation of OS X beta releases".

![][1]

[1]: images/restrict-major-os-update/restrict-beta-version.png

## Restrict Retail Version

As stated above, Apple doesn't provide a way to disable a major OS upgrade.

We'll use JSS built-in "Restricted Software" mechanism to kill the Installation app as soon as it's launched by the user. 

It is not super user-friendly, so make sure you communicate to the users first. 

## Restricted Software Records

1. Open your JSS
1. Go to Computers > Restricted Software
1. Click + "New"

![][2]

[2]: images/restrict-major-os-update/restricted-software-records.png

## Add Restricted Software Record

macOS Sierra installer uses the process "osinstallersetupd" to setup installation.

Blocking this process will ensure that no user will be able to launch the installation, even if renaming "Install macOS Sierra.app".

![][3]

[3]: images/restrict-major-os-update/add-restricted-software-record.png

## Scope Restricted Software Record

Choose the right Scope. "All Managed Clients" is usually a good choice. 

I exclude from this Smart Group my test machines and my BYOD clients.

![][4]

[4]: images/restrict-major-os-update/scope-restricted-software-record.png

## Restricted Software Records

Our Record is now ready.

![][5]

[5]: images/restrict-major-os-update/restricted-software-records-1.png

## Computer Inventory Collection

1. Navigate to Computers > Management Settings
1. Click on "Inventory Collection"

![][6]

[6]: images/restrict-major-os-update/computer-inventory-collection.png

## Edit Computer Inventory Collection

Check "Collect active services".

Note: I couldn't find relevant ressources to confirm this was needed, but my tests indicate so

![][7]

[7]: images/restrict-major-os-update/edit-computer-inventory-collection.png

## On the client

You may want to try a "jamf manage" and a "jamf policy" to refresh the management framework.

If you launch "Install macOS Sierra.app", you'll get the following screen.

![][8]

[8]: images/restrict-major-os-update/on-the-client.png