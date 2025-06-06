---

copyright:
  years: 2025
lastupdated: "2025-06-02"

keywords: direct link, direct link dedicated

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Prerequisites for the Direct Link Dedicated MACsec feature
{: #macsec-prerequisites}

Before you can enable and configure MACsec on IBM Cloud Direct Link Dedicated, there are several tasks that need to be completed. These prerequisites ensure that your network is properly prepared for secure communication over a dedicated Ethernet connection.

## Verifying MACsec device readiness
{: #readiness-macsec-device}

Ensure that your MACsec-capable device is properly configured and supports the required encryption standards (such as AES) for your network setup. Verify that the device has the necessary hardware and software support for MACsec, and ensure that its ports or interfaces are configured to enable encryption. 

Work with your network provider to select the appropriate data center or Point of Presence (PoP) and confirm that the necessary infrastructure and network connections are in place to support MACsec. Also, ensure that a key management system is in place for secure key exchange, and assess the performance impact to ensure that the device can handle encryption without affecting network speed.

## Preparing for key exchange
{: #prepare-key-exchange}
   
Configure an HPCS instance on IBM Cloud to manage the encryption keys and ensure that your device is ready for secure key exchange. To do so, follow these steps:
   
1. Create a Hyper Protect Crypto Services (HPCS) instance on the standard plan with the Keep Your Own Key capability. For more information, see [Provisioning service instances](/docs/hs-crypto?topic=hs-crypto-provision).
1. Initialize the HPCS instance and load the [master keys](#x2908413){: term}.
   
   For example, if you choose to use the IBM Cloud Trusted Key Entry (TKE) CLI, here are some basic steps:
   
   * [Provision the HPCS instance using the CLI](/docs/hs-crypto?topic=hs-crypto-provision&interface=cli#provision-cli).
   * [Set up key protect CLI](/docs/hs-crypto?topic=hs-crypto-get-started#initialize-crypto).
   * [Initialize the HPCS instance and load the master keys](/docs/hs-crypto?topic=hs-crypto-initialize-hsm).
   * After HPCS instance setup, run the following commands:
   
      ```sh
     export CLOUDTKEFILES=~/tke-files
     ibmcloud target -r us-south -g Default
     ```
     {: codeblock}
   
   * Then, initialize the HPCS instance using the following series of commands:
   
      ```sh
      ibmcloud tke cryptounit-add
      ibmcloud tke sigkey-add
      ibmcloud tke sigkey-sel
      ibmcloud tke cryptounit-admin-add
      ibmcloud tke cryptounit-thrhld-set
      ibmcloud tke mk-add --random
      ibmcloud tke mk-add --random
      ibmcloud tke cryptounit-mk-load
      ibmcloud tke cryptounit-mk-load
      ibmcloud tke cryptounit-mk-commit
      ibmcloud tke cryptounit-mk-setimm
      ```
      {: codeblock}
   
      For more information, see [Creating and importing encryption keys](/docs/hs-crypto?topic=hs-crypto-tutorial-import-keys#tutorial-import-prereqs).
      {: note}

1. After initializing the HPCS instance, add standard keys (using the **Import a key** option) for any keys that you want to use with MACsec; for example, add a standard key for the primary CAK. Optionally, it is a good idea to configure MACsec with a fallback CAK. To do this, you must add a fallback key to the HPCS instance as well. To add a key, see [Hyper Protect Crypto Services](https://cloud.ibm.com/catalog/services/hyper-protect-crypto-services) catalog page. For instructions, see [Getting started with IBM Cloud Hyper Protect Crypto Services](/docs/hs-crypto?topic=hs-crypto-get-started). {: #key-conventions}
   
   The key material that you choose must follow specific MACsec conventions. The key material must be a 64-character hexadecimal string. Note that if you have 32 characters, you can add trailing 0000s to make up the 64 character length. To import the key material into the HPCS instance, it must be base64-encoded. 
   {: note}
   
   This HPCS key is used as the CAK value. When configuring MACsec, you are asked for a CAK name to pair with this key. The same key value pair must be configured on the MACsec keystore on the customer device.
   
   You must configure the same name and key octet string (value) on your switch. Otherwise, the MACsec key negotiation fails.
   {: important}
   
1. After creating keys for Direct Link, you must use IBM Cloud Identity and Access Management (IAM) to grant authorization between your Hyper Protect Crypto Service (HPCS) instance and the Direct Link service. Due to known limitations, you must grant access at the HPCS instance level, which grants the Direct Link service access to all the keys inside that instance. For instructions, see [Using authorizations to grant access between services](/docs/account?topic=account-serviceauth). The Direct Link service will never access any key besides those used for the MACsec feature.
   
   You should grant access to all keys in the HPCS instance; otherwise, you must grant a new service-to-service authorization each time that you want to use a different key for Direct Link with MACsec. As long as a key is in use by your gateway, it shouldn’t be deleted and the service-to-service authorization must not be revoked.
   {: note} 
