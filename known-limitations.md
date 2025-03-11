---

copyright:
  years: 2020, 2025
lastupdated: "2025-03-11"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Guidelines and restrictions for Direct Link Dedicated with MACsec
{: #limitations-macsec}

[MACsec updates]{: tag-red} MACsec for Direct Link Dedicated has the following guidelines and restrictions:

* Direct Link supports MACsec Key Agreement protocol (MKA)
* Multiple MACsec peers (different SCI values) for the same interface are not supported

## Key restrictions
{: #key-restrictions}

To replace the primary or fallback Connectivity Association Key (CAK), you must add a new standard key by importing a key into HPCS. Then, communicate the new key name to the Direct Link instance through the IBM Cloud console, CLI, or API.

The key names that you choose must follow specific Direct Link naming conventions. The hex key name must consist of alphanumeric characters (`0-9`, `a-f`, `A-F`) and be an even number of characters. The key name must also range from 1 octet to 64 (max size) characters in length. The key material string must be a base64-encoded string of 64 hexadecimal characters.

Make sure to use the **Add key** > **Import a key** option. If you use the **Create a key** option, the generated key string breaks the key length check for 64 characters.
{: important}

## Fallback restrictions
{: #fallback-restrictions}

* If a MACsec session is secured on an old primary key, it does not go to a fallback session in case of a mismatched latest active primary key. As a result, the session remains secure on the old primary key and will show as rekeying on the old CA under Status. In addition, the MACsec session on the new key on the primary PSK will be in the init state.

* Use only one key with an infinite lifetime in the fallback key chain. Multiple keys are not supported.

* You must use unique key names for each primary or fallback key that you generate.

* You cannot remove the fallback configuration on an interface unless you also remove the complete MACsec configuration on the interface as well.

## MACsec policy restriction
{: #macsec-policy-restriction}

* You cannot modify an existing MACsec policy. Instead, you must create a new MACsec policy and attach it to the interface, or you can remove the MACsec policy from the interface, edit it, and then reattach it. Any change to the policy might cause network disruptions.

* BPDU packets might be transmitted before a MACsec session becomes secure.

Interoperability restriction:

* Interoperability with other peer switches is supported only with the XPN cipher suite. 
