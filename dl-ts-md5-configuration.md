---

copyright:
  years: 2025
lastupdated: "2025-06-02"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Why is my direct link failing when I configure a BGP MD5 authentication key?
{: #troubleshoot-md5-configuration}
{: troubleshoot}
{: support}

When setting up BGP Message Digest 5 (MD5) authentication on your direct link, the key configuration process might fail.
{: shortdesc}

After you provide an authentication key, the Direct Link service attempts to configure the key on your direct link. During this process, the direct link's `operational_status` might enter a `failed` state. If the failure is caused by an improper key setup, the `operational_status_reasons` shows the code `authentication_key_failed`.
{: tsSymptoms}

This failure can occur due to changes to the authentication key itself or to the permissions granted to the Direct Link service. Either issue can prevent the service from successfully applying the key to the direct link.
{: tsCauses}

While your direct link is in a `failed` state, you can update the authentication key. You can resubmit the same key or provide a new one. If you choose to reuse the same key, make sure to resolve any related issues, such as incorrect values or missing permissions, before submitting it again.
{: tsResolve}
