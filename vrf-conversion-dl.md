---

copyright:
  years: 2020, 2024
lastupdated: "2024-07-18"

keywords:  VRF, direct link, virtual routing and forwarding

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Converting to virtual routing and forwarding
{: #what-happens-during-the-account-conversion-process}

Many {{site.data.keyword.cloud}} customers currently operate with a shared tenancy model on the {{site.data.keyword.cloud_notm}} network. During conversion, your shared tenancy is converted to use a customer VRF, most commonly with a new {{site.data.keyword.dl_short}} subscription.
{: shortdesc}

A "customer VRF" refers to multiple isolation network connectivity. For more information, see [Virtual routing and forwarding on IBM Cloud](/docs/dl?topic=dl-overview-of-virtual-routing-and-forwarding-vrf-on-ibm-cloud).
{: note}

## The conversion process
{: #process-description}

The conversion process involves a network disruption, while the VLANs and their subnets are detached from the ACL backbone and then attached to the customer VRF. This process results in a few moments of packet loss for traffic that enters or exits the VLANs. Packets within the VLAN continue to flow. In the cases where a network gateway, such as a FortiGate Security Appliance or Virtual Router Appliance is involved, no disruption occurs among the VLANs attached to that gateway. The servers see no network outage themselves, and most workloads automatically recover when the traffic flow resumes. The total duration of the disruption depends on the extent of the tenant’s topology, that is, the number of subnets, VLANs, and pods that your tenancy includes.

During migration, the VLANs are disconnected from the backbone and reconnected to the customer VRF. The duration of disruption varies, depending on the quantity of VLANs, pods, and data centers involved. Traffic among VLANs is disrupted; however, the servers stay connected to the network. The application might not be affected, depending on its sensitivity to packet loss.

## Initiating the conversion
{: #how-you-can-initiate-the-conversion}

Existing {{site.data.keyword.cloud_notm}} customers can [open an IBM Support case](/unifiedsupport/cases/add){: external} through the {{site.data.keyword.cloud_notm}} console, requesting to be migrated to a VRF. Have the support case state: “Private Network Question” and include the following text:

"We are requesting that account _your account number_ move to its own VRF. We understand the risks and approve the change. Reply with the scheduled windows of time where this change will be made so we can prepare for the migration."

The {{site.data.keyword.cloud_notm}}Network Engineering team completes the migration. No other information is required from you, except an "agreed to" schedule. Intermittent packet loss might last 15 - 30 minutes, depending on the complexity of your account. It might be longer if your account has legacy {{site.data.keyword.dl_short}} connections. The process is highly automated, requiring minimal interaction by the IBM team.

When you're opening the case, it is recommended to select the **Technical** support type option, with a category of **Networking > {{site.data.keyword.dl_short}}**.
