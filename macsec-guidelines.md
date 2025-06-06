---

copyright:
  years: 2020, 2025
lastupdated: "2025-06-02"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Guidelines and restrictions for Direct Link Dedicated with MACsec
{: #limitations-macsec}

MACsec for Direct Link Dedicated has the following guidelines and restrictions:

* The MACsec feature is only supported on the Direct Link Dedicated offering
* Direct Link supports MACsec Key Agreement (MKA) protocol 
* Multiple MACsec peers (different SCI values) for the same interface are not supported

## Key restrictions
{: #key-restrictions}

A Connectivity Association Key (CAK) consists of both a name and material. Both name and material must match on your MACsec device and the IBM MACsec device. The CAK name is provided to the service directly, while the material must be secured as an imported key in a Hyper Protect Crypto Services (HPCS) instance. You must configure an IAM service-to-service authorization to enable the Direct Link service access to your HPCS instance.

The service-to-service authorization must be given at the instance level. This is a known limitation with the HPCS service.
{: note}

CAK names must follow specific MACsec naming conventions. The name must consist of an even number of hexadecimal characters (`0-9`, `a-f`, `A-F`) with a maximum length of 64 characters.

You must use unique CAK names for each CAK, primary or fallback.
{: note}

The CAK material must be 64 hexadecimal characters in length. If your generated material is fewer than 64 characters, it must be right-padded with zeros until it reaches the required length. The material must then be imported as a key into your HPCS instance.

You must [base64-encode](/docs/dl?topic=dl-create-encryption-keys) the material to import it into your HPCS instance. The unencoded material is configured on the IBM MACsec device.
{: note}
  
Make sure to use the **Add key** > **Import a key** option. If you use the **Create a key** option, the generated key string breaks the key length check for 64 characters.
{: important}

## Fallback restrictions
{: #fallback-restrictions}

* A fallback MACsec session is only initiated if the peer devices cannot establish a primary session due to a CAK name or material mismatch.

* During primary CAK rotation, the MACsec session is secured with the previous primary CAK until it is able to secure it with the newer primary CAK. If there's a mismatch on the newer primary CAK, the devices remain secured with the previous primary CAK, and will not initiate a fallback session.

* Only a single fallback CAK with an inifite lifetime is supported. Multiple fallback CAKs are not supported.

* You cannot remove the fallback configuration on an interface unless you also remove the complete MACsec configuration on the interface as well.

## MACsec policy restriction
{: #macsec-policy-restriction}

* You cannot modify an existing MACsec policy. Instead, you must create a new MACsec policy and attach it to the interface, or you can remove the MACsec policy from the interface, edit it, and then reattach it. Any change to the policy might cause network disruptions.

* BPDU packets might be transmitted before a MACsec session becomes secure.

Interoperability restriction:

* Peer MACsec devices must support the XPN cipher suite. 

## Related link
{: #known-issues-limitations=related-link}

[Known issues and limitations](/docs/dl?topic=dl-known-limitations)
