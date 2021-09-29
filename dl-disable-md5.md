---

copyright:
  years: 2020, 2021
lastupdated: "2021-09-15"

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

# Activating and deactivating BGP MD5 authentication
{: #enable-disable-md5}

You can activate BGP MD5 authentication when you create a {{site.data.keyword.dl_short}} gateway, or after the gateway is provisioned. You can deactivate MD5 authentication at any time.
{: shortdesc}

**Important**:

* You must configure the same BGP MD5 authentication key on both your Edge router and the IBM cross-connect router (XCR). The shared authentication key on the IBM device must be stored in your HPCS or Key Protect instance and shared with the Direct Link service. For more information, see [Setting up BGP Message Digest 5 (MD5) authentication keys](/docs/dl?topic=dl-dl-md5).
* You can achieve hitless key refresh if the keys are updated on both your Edge router and on the XCR within 90 seconds. As a pre-condition, you must configure the BGP hold time on your router to a minimum of 90 seconds. All Direct Link routers have a 90-second configuration by default. Either side can initiate the key refresh, but both sides must refresh within the configured BGP hold time to avoid traffic disruption.   
* Activating and deactivating MD5, or changing the MD5 key on the IBM side after the BGP session is established, causes BGP session downtime and network disruption until the BGP peer device is configured with the same change. 

## Activating BGP MD5 authentication
{: #dl-enable-md5}

To activate MD5 authentication on a provisioned gateway, follow these steps:

1. [Set up BGP Message Digest 5 (MD5) authentication keys](/docs/dl?topic=dl-dl-md5).
1. Log in to the [Direct Link console](https://cloud.ibm.com/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details.
1. In the BGP section, click the MD5 authentication **Deactivated** switch to open the MD5 authentication window.  
1. Complete the following information:
   * For the keystore, select either **Hyper Protect Crypto Services** or **Key Protect**.
   * Select an authentication keystore instance.
   * Select an authentication key.
1. Click **Activate**.

   ![MD5 activation window](/images/md5-side-panel.png)
  
   The information is added to the details page and the switch shows **Activated**.  

   ![MD5 activated](/images/md5-activated.png)

If you later want to edit BGP values, click **Edit** in the upper right of the BGP section. 
{: note}

For example:

![BGP edit side panel](/images/bgp-edit.png)

## Deactivating BGP MD5 authentication
{: #dl-disable-md5}

To deactivate BGP MD5 authentication, follow these steps:

1. Log in to the [Direct Link console](https://cloud.ibm.com/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details.
1. In the BGP section, click the MD5 authentication **Activated** switch to show the Deactivate BGP MD5 authentication window. 
1. Enter the name of the key to confirm, then click **Deactivate**. Your key is removed in the process.

   ![Deactivate BGP MD5 authentication](/images/disable-bgp-md5.png)
   
   The Details page is updated with your change.   
   
   ![Deactivated BGP MD5 authentication](/images/md5-deactivate.png)
