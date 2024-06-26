---

copyright:
  years: 2021, 2024
lastupdated: "2024-06-19"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Why isn't the BGP peering session established?
{: #troubleshoot-bgp-not-up}
{: troubleshoot}
{: support}

My BGP peering session isn't coming up. What should I do?
{: shortdesc}

The BGP peering session cannot be established.
{: tsSymptoms}

Possible causes are a problem with the IP configuration, an ASN mismatch, or your BGP peers are not configured with the same key to establish a BGP neighbor relationship.
{: tsCauses}

Try the following fixes to resolve this issue:
{: tsResolve}

1. Ensure that the peer IPs for both sides of the BGP peering session are configured correctly.
1. If an MD5 authentication key is configured, ensure that the MD5 authentication key is configured the same on both your Edge router and the IBM cross-connect router (XCR).
1. If necessary, contact IBM Support.

For more information, see [Setting up BGP Message Digest 5 (MD5) authentication keys](/docs/dl?topic=dl-dl-md5).
