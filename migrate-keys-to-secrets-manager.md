---

copyright:
  years: 2026
lastupdated: "2026-03-17"

keywords:

subcollection: dl
---

{{site.data.keyword.attribute-definition-list}}

# Migrating Direct Link MACsec CAKs and MD5 keys from HPCS to Secrets Manager
{: #hpcs-migration}

IBM Cloud Direct Link supports referencing authentication keys stored in IBM Cloud Secrets Manager. Migrating your MACsec Connectivity Association Keys (CAKs) and BGP MD5 authentication keys from Hyper Protect Crypto Services (HPCS) to Secrets Manager enables centralized lifecycle management, controlled access through IAM, and simplified rotation workflows.

This topic describes prerequisites, operational considerations, migration steps, validation, and rollback guidance.

## Before you begin
{: #hpcs-migration-before-you-begin}

Ensure that you meet the following prerequisites:

* You have Administrator or Editor access to Direct Link.
* You have Secrets Reader and Writer access to Secrets Manager.
* Direct Link is authorized to read secrets from the Secrets Manager instance (IAM policy and any required resource policy are configured).
* You can retrieve the existing CAK or MD5 key values from HPCS, including the region, HPCS instance ID, and key ID for each key.
* You have validated the existing key format (length, encoding, and syntax).
* You have access to the peer router or device for coordinated configuration changes.
* You have confirmed rollback access to both Direct Link and the peer device.
* A maintenance window is scheduled, if required by your operational policy. Expect a brief service interruption during the change.

Review the following important considerations:

* When you update a MACsec CAK or BGP MD5 key reference, Direct Link renegotiates the session.
* When you update a BGP MD5 key, Direct Link resets the BGP session.
* When you update a MACsec CAK, Direct Link renegotiates the secure channel.
* Expect a brief service interruption during the change.
* Ensure that the authentication key matches exactly on both ends of the connection.
* Secrets Manager stores values exactly as you enter them, including whitespace.
* Avoid formatting errors, such as trailing spaces or encoding mismatches, because they can prevent session establishment.
* When you rotate a secret, Secrets Manager might create a new secret version.
* If a new secret version is created, you might need to update the Direct Link configuration.
* Do not delete HPCS key material until you validate the migration.
* Coordinate peer-side configuration changes to minimize downtime. Expect the session to reset during this step.

## Migrating your keys
{: #migrating-keys-console}

To migrate MACsec CAKs or BGP MD5 authentication keys from HPCS to Secrets Manager, complete the following steps:

1. In the IBM Cloud console, click **Resource list > Networking > Direct link.**
1. Review each Direct Link instance and identify connections that have MACsec or BGP MD5 authentication enabled.
1. For each Direct Link connection that uses MACsec or BGP MD5 authentication, determine whether the authentication key references HPCS.
1. For each connection that uses an HPCS key, record the following information:

   * HPCS region
   * HPCS instance ID
   * Key ID

   Gather this information for every MACsec CAK or MD5 key that you plan to migrate.

1. Retrieve the key material from HPCS by using the IBM Cloud CLI:

   To retrieve key material from HPCS, ensure that the IBM Cloud CLI and Key Protect plugin are installed and configured. For setup instructions, see [Performing key management operations with the CLI – Standard Plan only](/docs/hs-crypto?topic=hs-crypto-set-up-cli). For command syntax and additional examples, see the [`kp key show`](/docs/key-protect?topic=key-protect-key-protect-cli-reference#kp-key-show) CLI reference.

   ```bash
   ibmcloud kp key show KEY_ID -i HPCS_INSTANCE_ID -r REGION -o json
   ```
   {: pre}

   Example output:

   ```json
   {
     "id": "86be0466-e699-43c1-ac90-a1b18e70fe37",
     "name": "ibm",
     "algorithmType": "AES",
     "extractable": true,
     "imported": true,
     "payload": "SUJN",
     "state": 1
   }
   ```
   {: codeblock}

   **Notes:**

   * The authentication key is the Base64-encoded string contained in the `payload` field. When creating the secret in Secrets Manager, paste the value exactly as shown, excluding the surrounding double quotes. Do not decode the Base64 string.
   * Ensure that `"extractable": true`.
   * Ensure that `"state": 1` (active).
   * Do not delete the HPCS key at this stage.

1. In the IBM Cloud console, go to **Resource list > Security > Secrets Manager**, and select your Secrets Manager instance.
1. Click **Create secret**, and select **Arbitrary secret**.
1. Paste the existing CAK or MD5 key value exactly as retrieved from HPCS. Ensure that no extra spaces or formatting changes are introduced.
1. Provide a descriptive name for the secret, such as  `dl-macsec-cak-CONNECTION_NAME` or `dl-bgp-md5-CONNECTION_NAME`.
1. Click **Create secret**.
1. Copy the **Secret CRN** and confirm that the secret status is **Active**.
1. Verify that Direct Link has permission to read the secret by confirming that the required IAM policies and any necessary resource policies are properly configured.
1. Return to **Resource list > Networking > Direct link**, and select your Direct Link instance.
1. Select the connection that is configured with MACsec or MD5 authentication, then click **Edit**.
1. Replace the existing HPCS key reference with the Secrets Manager secret CRN, then save the configuration.

   The MACsec or BGP session is expected to reset during this update.
   {: note}

1. Verify that connectivity is restored and functioning as expected:

   * For MACsec, confirm that the MACsec session is secure and operational.
   * For BGP, confirm that the session state is **Established** and routes are exchanged.

If you encounter connectivity issues:

* Revert the Direct Link configuration to reference the original HPCS key.
* Confirm that connectivity is restored.
* Review the secret value, CRN, IAM permissions, and peer device configuration for mismatches.

After you confirm successful migration, remove any unused key material from HPCS and update your documentation to reference the Secrets Manager CRNs.
