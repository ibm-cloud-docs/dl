---

copyright:
  years: 2025
lastupdated: "2025-06-02"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Why is my direct link failing when I configure MACsec CAKs?
{: #troubleshoot-macsec-caks}
{: troubleshoot}
{: support}

When setting up MACsec on a Direct Link Dedicated connection, you provide Connectivity Association Keys (CAKs) to secure the link. If there’s an issue with key configuration, the setup might fail.
{: shortdesc}

The Direct Link service attempts to configure the provided CAKs on your direct link. During this process, the MACsec configuration status on your direct link might enter a `failed` state. If the failure is caused by improper key setup, the `status_reasons` shows the code `macsec_cak_failed`, and the CAK responsible for the failure has a `failed` status.
{: tsSymptoms}

This failure can occur due to changes in the CAK itself or in the permissions granted to the Direct Link service. These issues can prevent successful application of the MACsec configuration.
{: tsCauses}

While your `macsec` resource is in a `failed` state, you can update your MACsec configuration. You can submit CAKs for use, remove a fallback CAK, disable MACsec on your direct link, or remove the MACsec feature entirely if allowed. If reusing the same CAK, make sure to resolve any issues with the key or service permissions before resubmitting it.
{: tsResolve}
