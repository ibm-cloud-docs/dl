---

copyright:
  years: 2021
lastupdated: "2021-05-05"

keywords: troubleshooting, problems, issues, known issues

subcollection: dl

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:support: data-reuse='support'}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# My connection is down after scheduled Direct Link maintenance. What should I do?
{: #troubleshoot-connection-down-after-scheduled-maintenance}
{: troubleshoot}
{: support}

There is no connectivity after scheduled maintenance on my direct link gateway.
{: shortdesc}

My connection is down.
{: tsSymptoms}

Possible causes:
{: tsCauses}

1. Address Resolution Protocol (ARP) cache issue
1. Border Gateway Protocol (BGP) negotiation failure


1. Clear ARP on your network gear.

   Since IBM is moving the link to a different router, the MAC address associated with our IP address changes. If your router does not accept gratuitous ARP, connectivity might be down until the ARP cache is cleared on your router.

2. Open a ticket to troubleshoot BGP sessions.

   The new router is running a newer version of firmware that supports more BGP capabilities. If BGP was established before the move, but does not establish after the move, IBM opens a ticket on your account to troubleshoot the problem after the maintenance is completed.
{: tsResolve}
