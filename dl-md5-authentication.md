---

copyright:
  years: 2021, 2025
lastupdated: "2025-05-29"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Setting up BGP Message Digest 5 (MD5) authentication keys
{: #dl-md5}

Border Gateway Protocol (BGP) authentication is an added layer of security that enables routers to share information only if they can verify that they are communicating with a trusted source, based on a key. TCP MD5 authentication between BGP peers verifies each transmitted message sent through the BGP session.
{: shortdesc}

## BGP authentication requirements
{: #bgp-md5-important-notices}

Make sure to adhere to the following BGP MD5 authentication requirements:

 * BGP MD5 keys must be created as an imported, **type-standard key** (not a root key). The key material that you provide must be base64-encoded and the original string cannot exceed a maximum of 126 printable ASCII characters in length. For more information, see [Creating base64-encoded encryption keys](/docs/dl?topic=dl-create-encryption-keys).

   The key material must be base64-encoded and can be up to 7,500 bytes. The key name (different from the key material) is a unique, human-readable name for easy identification of your key.
   {: note}

 * During an authenticated BGP session, BGP peers must be configured with the same key to establish a BGP neighbor relationship. Routers that are configured with a different key cannot maintain a BGP neighbor relationship.

## Setting up BGP MD5 authentication keys
{: #setting-up-bgp-md5-keys}

You can store your keys in either Key Protect or Hyper Protect Crypto Services (HPCS). To configure BGP MD5 authentication, follow these steps:

1. Set up a keystore instance with keys. For instructions, see [Key Protect: Getting started with encryption keys](/docs/key-protect?topic=key-protect-getting-started-tutorial) or [HPCS: Creating and importing encryption keys](/docs/hs-crypto?topic=hs-crypto-tutorial-import-keys).

   If you use HPCS, it is important to note that the `"extractable": <key_type>` value is set to `true` for standard keys.
   {: note}

1. After you create encryption keys for Direct Link, use IBM Cloud Identity and Access Management (IAM) to grant authorization between your instance and the Direct Link service. You can grant access at the instance level, which grants the Direct Link service access to all the keys inside that instance. You can also grant access on a key-by-key basis. For instructions, see [Using authorizations to grant access between services](/docs/account?topic=account-serviceauth).

   If you use Key Protect, select **Resources based on selected attributes** after you select **Direct Link** as the Source service. Then, select either **Resource type > Direct Link Connect** or **Resource type > Direct Link Dedicated** before selecting **Key Protect** as the Target service.
   {: important}

   You should grant access to all keys in the instance; otherwise, you must grant a new service-to-service authorization each time that you want to use a different key for Direct Link. As long as a key is in use by your gateway, you should never delete it, nor should you revoke the service-to-service authorization.

1. If the Key Protect or HPCS instance has a context-based restriction (CBR) rule, a Direct Link Service Reference must be added to the network zone of that rule. For instructions, see [How Direct Link integrates with context-based restrictions](/docs/dl?topic=dl-cbr&interface=cli#cbr-overview).

## Configuration failure
{: #configuration-failure}

After you provide an authentication key, the Direct Link Service attempts to configure the key on your direct link. During configuration, the direct link's `operational_status` might enter a failed state. If the failure is caused by an improper key setup, the `operational_status_reason` shows the code `authentication_key_failed`.

This failure can occur due to changes on the key itself or the permissions granted to the Direct Link service. While in this failed state, you can update the authentication key, either by resubmitting the same key or providing a new one. If you choose to reuse the same key, make sure to resolve any related issues before submitting it again.

## Next step
{: #md5-next-step}

[Activate BGP MD5 authentication](/docs/dl?topic=dl-enable-disable-md5#dl-enable-md5)
