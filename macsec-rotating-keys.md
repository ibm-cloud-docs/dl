---

copyright:
  years: 2025
lastupdated: "2025-12-31"

keywords: direct link, macsec, dedicated

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Rotating CAKs for Direct Link Dedicated with MACsec
{: #macsec-cak-rotation}

If MACsec is configured with the `must secure` security policy, rotation of either primary or fallback CAKs can lead to dropped frames during the rotation process if there are unforeseen failures to establish a valid session.
{: important}

## Rotating the primary CAK for Direct Link Dedicated with MACsec
{: #macsec-primary-cak-rotation}

Rotating keys regularly helps you meet industry standards and cryptographic best practices.
{: shortdesc}

When using Direct Link Dedicated with MACsec, follow these steps to rotate the primary Connectivity Association Key (CAK). This process, if implemented properly, does not result in dropped packets. However, you can configure an optional fallback CAK to take over if there is an unexpected failure to establish a session using the primary CAK.

   This procedure assumes that a new primary CAK material is securely generated on-premises.
   {: important}

1. Temporarily disable the Secure Association Key (SAK) expiration timer on your device, if set. This helps avoid SAK renewal failures due to a primary key mismatch on peers during rotation.

   You might have to wait a few minutes before proceeding to the next step. Consult your device manual for details.
   {: note}

1. Configure the new primary CAK name and material on your device. Your device attempts to establish a new MACsec session with the new primary CAK. However, because the peer (IBM device) has not been updated yet, the session remains in `init` state.

   The existing MACsec session is not disrupted and remains secured using the old primary CAK.
   {: note}

1. Store the primary CAK material used in Step 2 in the HPCS instance.  
1. Send a PATCH request to the primary CAK using the IBM Direct Link API, providing the CAK name and the HPCS key CRN containing the material. IBM Direct Link securely retrieves the updated CAK material from HPCS and configures it with the specified name on the IBM cross-connect switch (XCS) that peers with your device. 

   Any operation that can be performed using the API can also be performed through the UI and CLI.
   {: note}

1. Wait for the new MACsec session to be established with the new key.

   You might have to wait a few minutes after a session is established before proceeding to the next step. Consult your device manual for details.
   {: note}

1. Delete the old primary CAK from your device. If using the SAK expiration timer, re-enable it on your device.

   IBM does the same on the XCS.
   {: note}

IBM actions corresponding to steps in this procedure are triggered when you update the primary CAK.

## Rotating the fallback CAK for Direct Link Dedicated with MACsec
{: #macsec-fallback-cak-rotation}

Use of a fallback CAK is optional. If you configure a fallback CAK, you might need to rotate it periodically as well. To avoid dropped frames, it is recommended to rotate the fallback CAK only when a MACsec session is established with the primary CAK. Because the fallback CAK is used only if a session cannot be established using the primary CAK, the process to rotate the fallback CAK is simpler.

   This procedure assumes that a new fallback CAK material is securely generated on-premises.
   {: important}

1. Delete the old fallback CAK and configure the new fallback CAK name and material on your device.  
1. Store the fallback CAK material used in Step 2 in the HPCS instance.  
1. Then, call an IBM Direct Link API to inform the Direct Link service about the availability of the new CAK. IBM Direct Link securely retrieves the new CAK and configures it on the IBM (XCS) that peers with your device.
