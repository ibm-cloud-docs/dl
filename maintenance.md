---

copyright:
  years: 2021, 2024
lastupdated: "2024-07-18"

keywords: troubleshooting, direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# The connection is down after scheduled Direct Link maintenance. What can be done?
{: #troubleshoot-connection-down-after-scheduled-maintenance}
{: troubleshoot}
{: support}

Experiencing no connectivity after scheduled maintenance on the direct link.
{: shortdesc}

My connection is down.
{: tsSymptoms}

Possible causes:
{: tsCauses}

1. Address Resolution Protocol (ARP) cache issue
1. Border Gateway Protocol (BGP) negotiation failure

Resolution:
{: tsResolve}

1. Clear ARP on your network gear.

   Since IBM is moving the link to a different router, the MAC address associated with our IP address changes. If your router does not accept gratuitous ARP, connectivity might be down until the ARP cache is cleared on your router.

1. Open a ticket to troubleshoot BGP sessions.

   The new router is running a newer version of firmware that supports more BGP capabilities. If BGP was established before the move, but does not establish after the move, IBM opens a ticket on your account to troubleshoot the problem after the maintenance is completed.
