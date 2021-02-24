---

copyright:
  years: 2020, 2021
lastupdated: "2021-02-14"

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

# Equinix ordering considerations
{: #equinix}

After you create your Direct Link Connect order, follow these steps to create a connection for your Equinix service provider.

For Exchange on Classic instructions, see [Steps to order Direct Link Exchange on Classic for Equinix](/docs/direct-link?topic=direct-link-how-to-order-ibm-cloud-direct-link-exchange#provisioning-ibm-cloud-direct-link-exchange-for-equinix).
{: note}

1. Log in to the Equinix Cloud Exchange (ECX) Fabric portal.
   * Navigate to [https://ecxfabric.equinix.com](https://ecxfabric.equinix.com).
   * Enter your username and password.
   * Click **Sign In**.   
1. In the Frequent Connections section, click the **IBM Cloud** tile.
1. In the **IBM Cloud Direct Link 2** profile, click **Create Connection**.

   ![Equinix ordering](/images/equinix-ibm-cloud-2.png "Equinix ordering")
1. In the Origin section, click **Port**.

   ![Select a Port, Location, and Destination](/images/equinix-port.png "Select a Port, Location, and Destination")   
1. Select a **Location**, followed by a **Destination**. Then, click **Next**.
1. On the Connection Details page, enter the connection information. For the IBM Cloud Account ID, enter the service key (for example, `aaa-bbbb-cccc`) that was generated when you provisioned your direct link. This key can be found on the Direct Link details page.

   ![Connection Details](/images/equinix-connection-details.png "Connection Details")   
1. Select a **Connection Speed**, then click **Next**.   
1. Review and click **Submit Your Order**.

The IBM Special Network Services (SNS) team receives your request and is able approve the connection in the buyer-side portal. You can view your newly created virtual connection for Direct Link by going to **Connections**. The connection will be in a pending, provisioning state (**Pending Provider VLAN**).

Accept the connection request by navigating to the IBM Cloud Direct Link page and clicking **Accept** from the Action menu. The virtual connection shows as **Provisioned** in the Equinix Fabric portal.

The timeline for approval is within 24 hours. If the 24-hour Service Level Agreement (SLA) is not acceptable, you can [create an IBM Support case](https://cloud.ibm.com/unifiedsupport/cases/form) and request that it be routed to the SNS team.
{: note}
