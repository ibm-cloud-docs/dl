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

# Accepting provider-created connections
{: #accepting-provider-created-connection}

This topic shows you how to accept provider-created connections (create, edit, delete connections) and enable BGP MD5 authentication.

## Accepting a Direct Link creation request
{: #accept-creation-request}

1. Log in to the IBM Cloud [Direct Link console](/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details.
1. In the Actions section, click **Review** to review the direct link configuration.

   ![Actions menu](/images/actions-review-creation.png){: caption="Actions menu" caption-side="bottom"}

   The Review configuration panel displays.

   ![Review configuration side panel for direct link creation](/images/review-configuration-creation.png){: caption="Review configuration side panel" caption-side="bottom"}

1. Review your settings and click **Accept**.

   The Finalize creation panel displays.

   ![Finalize side panel for direct link creation](/images/finalize-configuration-creation.png){: caption="Finalize side panel to create a direct link" caption-side="bottom"}

1. Select a resource group, routing type, and billing type. Then, select the checkbox indicating that you agree to the Direct Link prerequisites and click **Create**.    

   Optionally, you can enable MD5 authentication.  For instructions, see [Enabling MD5 authentication for BGP peers](/docs/dl?topic=dl-accepting-the-provider-created-connection#dl-enable-md5-provider).
   {: note}

## Accepting a Direct Link edit request
{: #accept-edit-request}

1. Log in to the IBM Cloud [Direct Link console](https://cloud.ibm.com/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details.
1. In the Actions section, click **Review** to review the direct link configuration.

   ![Actions menu](/images/actions-review-edit.png){: caption="Actions menu" caption-side="bottom"}


   The Review configuration panel displays.

   ![Review configuration side panel for direct link creation](/images/review-configuration-edit.png){: caption="Review configuration side panel" caption-side="bottom"}

1. Review your settings, select the checkbox indicating that you agree to the Direct Link prerequisites, and click **Accept**.

## Enabling MD5 authentication for BGP peers
{: #dl-enable-md5-provider}

Optionally, you can enable MD5 authentication to secure the BGP session by allowing routing of messages only from routers using a shared authentication key.

You must configure the same BGP MD5 authentication key on both your Edge router and the IBM cross-connect router (XCR). The shared authentication key on the IBM device must be stored in your HPCS or Key Protect instance and shared with the Direct Link service.
{: important}

To enable MD5 authentication after submitting your order, follow these steps:

1. [Set up BGP Message Digest 5 (MD5) authentication keys](/docs/dl?topic=dl-dl-md5).
1. Log in to the IBM Cloud [Direct Link console](/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details.
1. In the Actions section, click **Review** to review the direct link configuration.

   ![Actions menu](/images/actions-review.png){: caption="Actions menu" caption-side="bottom"}


   The Review configuration panel displays.

   ![Review configuration side panel](/images/review-configuration.png){: caption="Review configuration side panel" caption-side="bottom"}

1. Review your settings and click **Accept**.

   The Finalize creation panel displays.

   ![Finalize creation panel](/images/finalize-creation.png){: caption="Finalize direct link creation" caption-side="bottom"}


1. Click the MD5 authentication toggle button to enable it, then complete the following:

   * For the keystore, select **Hyper Protect Crypto Services** or **Key Protect**.
   * Choose an authentication keystore instance and authentication key.

1. Click **Create**.
