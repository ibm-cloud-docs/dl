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
{:preview: .preview}
{:note: .note}
{:beta: .beta}
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

# AT&T NetBond for Cloud ordering considerations
{: #netbond}

Follow these steps to request a VLAN assignment from AT&T NetBond for Cloud:

1. Order the NetBond connect on the AT&T portal.

   NetBond is responsible for making sure that this VLAN is not in use with any NetBond connections within IBM.
   {: note}
   
1. Order an {{site.data.keyword.cloud}} Direct Link (2.0) Connect gateway by using the [{{site.data.keyword.cloud_notm}} console](https://cloud.ibm.com){: external}. For instructions, see [Ordering IBM Cloud Direct Link Connect](/docs/dl?topic=dl-how-to-order-ibm-cloud-dl-connect).

   * When defining the IP range to be used for BGP, select **Manual-select IP**.
   * Choose the IP range that you want to use with this gateway.

      Ensure that the range you choose is the range that you specified in the NetBond portal.
      {: note}

   * In the BGP ASN field, specify the ASN provided by AT&T.

1. Open an IBM Support case. For details, see [Create a case](https://cloud.ibm.com/unifiedsupport/cases/add) in the IBM Support Center.

   * Select the **Direct Link Connect** tile.
   * In the IBM Support case, add the following information:

      * **Subject**: DL 2.0 Connect manual implementation AT&T NetBond
      * **Description**:
      * Route this ticket directly to the Special Network Services (SNS) queue for Direct Link 2.0 Connect implementation with AT&T NetBond.
      * Include the NetBond connection service key that was assigned by NetBond (as provided in Step 1).
      * Include the Direct Link gateway name or service key from the Direct Link 2.0 page. For example, `0xx43ex3-b8f0-4d52-8b84-x91af2x02yy3`.

The SNS team receives the IBM Support case and initiates a series of steps to bring routers and the IBM portal database into synchronization.

After completion, the IBM Support case is annotated and closed. The timeframe for this activity is five business days from receipt of the case in the SNS queue.
