---

copyright:
  years: 2020, 2026
lastupdated: "2026-02-19"

keywords: direct link, macsec

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Viewing the details of a direct link
{: #viewing-details}

You can view details about a specific direct link, such as the link speed, BGP status, private key name, and more.
{: shortdesc}

To view information about a specific direct link, follow these steps:

1. Select the **Navigation menu** ![Menu icon](../icons/icon_hamburger.svg), then click **Infrastructure** ![VPC icon](../../icons/vpc.svg) > **Network** > **Direct link**.
1. Click **Direct Link** in the left navigation pane to view the Direct Link page, which lists existing Direct Link instances.
1. Click the Direct Link name in the table to open its Details page.

For Direct Link Dedicated with MACsec, you can also:

   * Review MACsec status and configuration information.
   * Click **Edit** to update values for the replay protection window.
   * Click **Rotate CAK** to replace either the primary or fallback CAK. If you did not provide a fallback CAK when creating your direct link, click **Add fallback key** to add a fallback CAK. It is recommended that you rotate these keys every 3 months.
   * Click **Monitor stats** to view or download information on MACsec policy and MACsec Key Agreement (MKA) summary and statistics.
   * Toggle the switch to **Activate** or **Deactivate** the MACsec feature.
