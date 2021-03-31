---
title: "Move devices to Current Channel"
ms.author: danbrown
author: DHB-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-proplus-itpro
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
hideEdit: true
---

# Move devices to Current Channel

> [!IMPORTANT]
> The information in this article applies only to organizations that received a Message center post entitled "Microsoft 365 Apps channel selection will be set to Current Channel for all installations of Office" in the Microsoft 365 admin center.

Your update channel selection on the **Office installation options** page in the Microsoft 365 admin center is currently defaulted to Semi-Annual Enterprise Channel. In the next several weeks, this selection will change to Current Channel, which is our recommended update channel.

> [!TIP]
> - To get to the **Office installation options** page, sign in to the Microsoft 365 admin center with your admin account, and then go to **Show all** > **Settings** > **Org settings** > **Services** > **Office installation options**.
> - The Office apps are those apps that come with Microsoft 365 Apps, which is included with your subscription plan. For example, Word, Excel, and PowerPoint.

## Which installations of Office are affected by this change?

This selection will apply to both new and existing installations of the Office apps in your organization. We will automatically configure existing installations to begin receiving feature updates from Current Channel instead of from Semi-Annual Enterprise Channel.

If you change your selection on the **Office installation options** page at a later time, new and existing installations of Office will begin using that update channel. Keep in mind that changing to a different update channel also changes which features are available to your users. For more information about which features are available in each update channel, see [Release notes for Microsoft 365 Apps releases](/officeupdates/release-notes-microsoft365-apps#release-notes-for-microsoft-365-apps-releases).

> [!IMPORTANT]
> If you're already using some other method, such as Group Policy or Microsoft Endpoint Configuration Manager, to manage how your users get feature updates, then the settings you select in the Microsoft 365 admin center won't apply.

## What is Current Channel?

On Current Channel, new or updated features are usually released every month. These monthly releases might also contain security updates and non-security updates, such as stability or performance improvements for Office.

Customers on a monthly feature update cadence have reported higher satisfaction than those receiving semi-annual feature updates. In addition to receiving the latest features and fixes, having all devices on the same update frequency will enable better collaboration experience for users in your organization.

These releases are cumulative. The most current release contains all the features, security updates, and non-security updates from the previous releases.

For more information about update channels, see [Overview of update channels for Microsoft 365 Apps](../overview-update-channels.md).

## How to opt out of moving devices to Current Channel

If you don’t want your Office installations to be moved to Current Channel, choose **Don’t move the devices to Current Channel** button in the message on the **Office installation options** page, as shown in the following screenshot.

![Screenshot showing the "Office installation options" page in the Microsoft 365 admin center and showing a message that says devices will be moved to Current Channel.](../images/other/move-devices-current-channel-message-text.png) 

> [!NOTE]
> - The date shown in the screenshot is an example. The date that applies for your organization is listed in the Message center post that you received and will be reflected in the message that appears on the **Office installation options** page.
> - After that date, the message and the **Don't move the devices to Current Channel** option will no longer appear.

If you choose **Don’t move the devices to Current Channel**, you’ll be taken to another page (similar to the one shown in the following screenshot), where you can choose to move your devices to Monthly Enterprise Channel or to remain on Semi-Annual Enterprise Channel.

![Screenshot showing a page entitled "Don't move the devices to Current Channel" with options to choose to move to Monthly Enterprise Channel or to keep on Semi-Annual Enterprise Channel.](../images/other/move-devices-current-channel-dont-move-page.png) 

Of these two choices, we recommend Monthly Enterprise Channel, because you’ll still receive new features and other updates once a month, but on a predictable schedule (the second Tuesday of each month).

After you make a selection, devices will be notified within 12 hours. Once notified, the devices will move to the selected update channel the next time they check for Office updates.