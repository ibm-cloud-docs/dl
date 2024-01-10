---

copyright:
  years: 2020, 2021
lastupdated: "2021-06-24"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Accepting provider-created connections
{: #accepting-provider-created-connection}

This topic shows you how to accept provider-created connections (create, edit, delete connections) and enable BGP MD5 authentication.

## Accepting a Direct Link creation request
{: #accept-creation-request}

1. Log in to the IBM Cloud [Direct Link console](/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details.
1. In the Actions section, click **Review** to review the direct link configuration. The Review configuration panel displays.
1. Review your settings and click **Accept**. The Finalize creation panel displays.
1. Select a resource group, routing type, and billing type. Then, select the checkbox indicating that you agree to the Direct Link prerequisites and click **Create**.
   Optionally, you can enable MD5 authentication. For instructions, see [Enabling MD5 authentication for BGP peers](/docs/dl?topic=dl-accepting-provider-created-connection#dl-enable-md5-provider).
   {: note}

## Accepting a Direct Link edit request
{: #accept-edit-request}

1. Log in to the IBM Cloud [Direct Link console](/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details.
1. In the Actions section, click **Review** to review the direct link configuration.

   The Review configuration panel displays.

1. Review your settings, select the checkbox indicating that you agree to the Direct Link prerequisites, and click **Accept**.

## Enabling MD5 authentication for BGP peers
{: #dl-enable-md5-provider}

Optionally, you can enable MD5 authentication to secure the BGP session by allowing routing of messages only from routers using a shared authentication key.

You must configure the same BGP MD5 authentication key on both your Edge router and the IBM cross-connect router (XCR). The shared authentication key on the IBM device must be stored in your HPCS or Key Protect instance and shared with the Direct Link service.
{: important}

To enable MD5 authentication after submitting your order, follow these steps:

1. [Set up BGP Message Digest 5 (MD5) authentication keys](/docs/dl?topic=dl-dl-md5).
1. Log in to the IBM Cloud [Direct Link console](/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details.
1. In the Actions section, click **Review** to review the direct link configuration. The Review configuration panel displays.
1. Review your settings and click **Accept**. The Finalize creation panel displays.
1. Click the MD5 authentication switch to enable it, then complete the following:

   * For the keystore, select **Hyper Protect Crypto Services** or **Key Protect**.
   * Choose an authentication keystore instance and authentication key.

1. Click **Create**.
