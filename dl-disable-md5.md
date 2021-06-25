---

copyright:
  years: 2020, 2021
lastupdated: "2021-06-24"

keywords:

subcollection: dl

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:term: .term}
{:generic: data-hd-programlang="generic"}
{:download: .download}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Enabling and disabling BGP MD5 authentication
{: #enable-disable-md5}

You can enable BGP MD5 authentication when you create a {{site.data.keyword.dl_short}} gateway, or after the gateway is provisioned. You can disable MD5 authentication at any time.

## Enabling BGP MD5 authentication
{: #dl-enable-md5}

To enable MD5 authentication on a provisioned gateway, follow these steps:

**Important**:

   * You must configure the same BGP MD5 authentication key on both your Edge router and the IBM cross-connect router (XCR). The shared authentication key on the IBM device must be stored in your HPCS or Key Protect instance and shared with the Direct Link service. For more information, see [Setting up BGP Message Digest 5 (MD5) authentication keys](/docs/dl?topic=dl-dl-md5).
   * You can achieve hitless key refresh if the keys are updated on both your Edge router and on the IBM cross-connect router (XCR) within 90 seconds. As a pre-condition, you must configure the BGP hold time on your router to a minimum of 90 seconds. All Direct Link routers have a 90-second configuration by default. Either side can initiate the key refresh, but both sides must refresh within the configured BGP hold time to avoid traffic disruption.

**WARNING**: If a BGP peering session was established and you enable BGP MD5 authentication (or change the authentication key to a different value), BGP sessions are re-established, which will interrupt communication between the BGP peers.

1. [Set up BGP Message Digest 5 (MD5) authentication keys](/docs/dl?topic=dl-dl-md5).
1. Log in to the [Direct Link console](https://cloud.ibm.com/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details.
1. Use the Edit configuration panel to re-enable BGP MD5 authentication, or change the key of a specific direct link. To access this panel, click **Change key** or **Actions > Edit** in the gateway's details page.

   Alternatively, you can select **Edit** from the gateway's overflow ![Overflow menu](images/overflow.png) menu in the table view.
   {: note}

   For example:

   ![Edit configuration side panel](/images/md5-side-panel.png)

## Disabling BGP MD5 authentication
{: #dl-disable-md5}

To disable BGP MD5 authentication, follow these steps:

1. Log in to the [Direct Link console](https://cloud.ibm.com/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details.
1. In the Details section, click the **Disable** button for the BGP MD5 authentication keystore instance.

   ![Disable BGP MD5 authentication](/images/dl-disable-md5.png)

   The confirmation window displays.

1. Enter the name of the key to confirm, then click **Disable**. Your key is removed in the process.

   ![Disable BGP MD5 authentication](/images/disable-bgp-md5.png)
