---
title: Road map to modern management of Microsoft 365 Apps in the enterprise
author: manoth-msft
ms.author: manoth
manager: laurawi
audience: ITPro 
ms.topic: article 
ms.service: o365-proplus-itpro
localization_priority: Normal
description: "Field best practices: Road map to modern management of Microsoft 365 Apps in the enterprise"
ms.custom: 
- Ent_Office_ProPlus
- Ent_Office_FieldNotes
ms.collection: 
- Ent_O365
- M365-modern-desktop
---

# Best practices from the field: Road map to modern management of Microsoft 365 Apps in the enterprise

> [!IMPORTANT]
> This is pre-release documentation for a preview program that isn’t available to everyone and is subject to change.

> [!NOTE]
> This article was written by Microsoft experts in the field who work with enterprise customers to deploy Office.

Microsoft recently released to public preview a set of [new admin capabilities](../admincenter/overview.md#whats-new-in-preview) to monitor, manage, and update the installation of Microsoft 365 Apps for enterprise. Based on our work with customers during the preview, we've developed some best practices on how to adopt these new features.

There's no definitive way to adopt these new features. But the following the order enables admins to quickly recognize the benefits while keeping the rate of change manageable. But adjust the approach according to the needs of your organization.

## Get insights within minutes: Microsoft 365 Apps health

A good starting point is to adopt [Microsoft 365 Apps health](../admincenter/microsoft-365-apps-health.md). This feature gives you insights into the stability, performance, and deployed builds of the Microsoft 365 Apps in your environment. This feature uses diagnostic data sent by your devices, so there's no need to deploy additional infrastructure or software agents. You can get insights into the health of your Microsoft 365 Apps within minutes.

How to enable Microsoft 365 Apps health:

1. Log into the Apps Admin Center at [config.office.com](https://config.office.com/).
2. Navigate to **Health** > **Apps health**. Read and accept the Preview EULA (end-user license agreements).
3. It will take about 10 minutes for the service to be provisioned.

You can then delve right into:

- Crash rates on a per-application level, grouped by version.
- Performance metrics such as application launch times and document load times.
- Channel metrics such as which channels and builds are sending diagnostic data.

You can also compare two builds. This step, enables you to quickly assess if a newly deployed build is more stable and faster than the previous one. You then can proactively address issues, as opposed to waiting for issues to surface after you release a new build into your environment.

There is a minimum number of sessions required per app and version. This minimum ensures that Microsoft 365 Apps health can calculate reliable insights. A session is the period from launching an application until it is closed. For example, you are likely to see more sessions from an app like Excel than Outlook.

If you've disabled Diagnostic Data for Office on your devices, you might only see a subset of your devices or none at all. To use Microsoft 365 Apps health, you have to [enable Diagnostic Data](../privacy/manage-privacy-controls.md#policy-setting-for-diagnostic-data) and set the level to Optional.

## Get insights per device: Inventory and Security Update Status

After you join the Preview program, Microsoft 365 Apps that are installed and running on Current Channel or Monthly Enterprise Channel version 2008 or higher will start registering in [Inventory](../admincenter/inventory.md). The Inventory page in the Apps Admin Center provides a consolidated view of your Microsoft 365 Apps and key information, such as:

- Update channel
- Versions deployed
- Apps deployed
- Architecture
- Installed add-ins
- If macros are used on the device

It will also populate the [Security Update Status](../admincenter/security-update-status.md) page, which provides you with an easy overview of which channels are deployed, how many devices are on the latest security update, and which ones are behind and need attention.

The Microsoft 365 Apps installation itself is providing the inventory information, so there's no conflict with existing management solutions. For example, a device can be managed by both Microsoft Endpoint Manager and registered into the new tenant-based inventory at the same time.

## Move devices to Monthly Enterprise Channel

Moving your devices to the [Monthly Enterprise Channel](../overview-update-channels.md#monthly-enterprise-channel-overview) provides a good balance between receiving monthly feature and quality updates (similar to [Current Channel](../overview-update-channels.md#current-channel-overview)), while having a predictable cadence with only one update per month.

With these new preview features, there are two scenarios to consider when moving devices to the Monthly Enterprise Channel:

- If you're planning to adopt Servicing Profiles at some point (see below), devices will automatically be moved to the Monthly Enterprise Channel. In this scenario, there's no need to move devices upfront.
- If you want to control the rate of devices switching to Monthly Enterprise Channel, aren't ready to adopt Servicing Profiles yet, or want to manage on-prem bandwidth with existing on-prem tools, then you should do the switch up front.

If you prefer to move your devices first, we have detailed guidance on how to [prepare your environment for multi-channel management](build-dynamic-lean-configuration-manager.md), and how to perform the [actual switch to Monthly Enterprise Channel using Configuration Manager](switch-to-monthly-enterprise-channel.md). If you are not using Configuration Manager, you can adapt the [generic change update channel guidance](../change-update-channels.md).

## Prepare your network for receiving updates from the internet

If you are planning to use Servicing Profiles to manage updates directly from the cloud, your devices will download those profiles from the internet going forward. To determine if your network configuration can handle this traffic without any disruptions, see [published sizes of the update downloads](https://docs.microsoft.com/officeupdates/download-sizes-microsoft365-apps-updates). There are several ways to optimize your network for taking updates directly from the cloud:

For users on-premises, you should consider:

- [Enable Delivery Optimization](../delivery-optimization.md) to allow devices to share content with each other through P2P mechanisms.
- If you have Configuration Manager deployed, you can enable [Connected Cache](https://docs.microsoft.com/mem/configmgr/core/plan-design/hierarchy/microsoft-connected-cache) on your distribution points. Use client settings to [enable devices](https://docs.microsoft.com/mem/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#enable-connected-cache) to use Microsoft Connected Cache servers for content download.

For users working from home or on the road using VPN, you should consider:

- Configure VPN with [selective tunnel](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-vpn-implement-split-tunnel#4-vpn-selective-tunnel) instead of [forced tunnel](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-vpn-implement-split-tunnel#1-vpn-forced-tunnel). Then the VPN tunnel is used only for corpnet-based services. Default route (Internet and all Internet-based services) goes direct, so does the Microsoft 365 Apps updates.
- If your VPN is configured for [forced tunnel with exceptions](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-vpn-implement-split-tunnel#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) and supports using FQDNs for Dynamic Split Tunneling, ensure that the [URL for the Office CDN is included in the exclusion list](https://docs.microsoft.com/microsoft-365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) (#92). We have [how-to guides for common VPN solutions](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-vpn-implement-split-tunnel#howto-guides-for-common-vpn-platforms) available.
- If your VPN is configured for forced tunnel and doesn't support FQDN-based exceptions, reach out to your Microsoft representative for support implementing an IP-based static solution.

## Use Servicing Profiles to keep devices current

With [Servicing Profiles](../admincenter/servicing-profile.md), you can enable your tenant to take control over the update deployment to all devices connected to this tenant, regardless of how the device is managed (if at all). You can set up rules to control which devices are in-scope for the update deployment and monitor progress through tailored reports.

There is no other infrastructure or software agent required to enable this feature. If a device has provisioned itself into inventory, its characteristics will be evaluated by Servicing Profiles. If it matches the rules set by the admin, it will manage Microsoft 365 Apps updates on this device going forward. This enables you to cover installations on BYOD, personal or unmanaged devices that are connected to your tenant and as devices managed by Configuration Manager or Microsoft Endpoint Manager.

Note that Servicing Profiles currently only supports managing Monthly Enterprise Channel updates, so any device that falls into the scope of the rules will be moved to this channel.

Before you adopt Servicing Profiles, consider the following factors:

- All devices matching the rule set will be switched over to Monthly Enterprise Channel and kept up to date going forward.
- There is currently no way to include or exclude specific devices.
- Double-check if your network is set up to handle the traffic caused by moving devices to Monthly Enterprise Channel and the monthly updates.

If everything mentioned above checks out, navigate to the Servicing Profile blade, and follow the instructions in the wizard. Note that the Servicing Profile is active immediately after you save the profile. So, if an eligible device checks in with the service right after you finished the wizard, it will get the instructions to move to the latest Monthly Enterprise update.
