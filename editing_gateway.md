---

copyright:
  years: 2021, 2023
lastupdated: "2023-01-24"

keywords: direct link

subcollection: dl
---

{{site.data.keyword.attribute-definition-list}}

# Updating a direct link
{: #update-dl-gateway}
{: help}
{: support}

You can update a direct link either before or after the gateway moves to the **Provisioned** state. However, a gateway is restricted from editing during **In review**, **Configuring**, and some in-progress states.
{: shortdesc}

## Updating a direct link in the UI
{: #update-dl-gateway-ui}
{: ui}

To edit a direct link, follow these steps:

1. Click the Direct Link name in the table to show its details. Alternatively, you can click the **Actions** icon at the end of the table row of a provisioned direct link to edit gateway features.sc
   
   If your Direct Link connection was ordered through a third-party Connect provider (as described in [{{site.data.keyword.cloud_notm}} Getting started with IBM Cloud Direct Link](/docs/dl?topic=dl-get-started-with-ibm-cloud-dl), you might not be able to edit your BGP configuration as described here. The direct link's details page will display a note stating, "This direct link is read-only. Link-specific actions must be initiated through the provider portal." To edit your BGP configuration, contact your provider either directly, or through the provider's portal.
   {: important}

   ![Edit a direct link](/images/dl-edit.png){: caption="Edit a direct link" caption-side="bottom"}

1. Click **Edit** link in the upper right of the Details or BGP section. A page with the current configuration shows. For example, you can update the BGP Autonomous System Number (ASN), or enable a BGP feature.  

   ![Edit BGP content](/images/dl-bgp-edit.png){: caption="Edit BGP content" caption-side="bottom"}

   **Important**: Keep in mind that the following tasks result in downtime where traffic is interrupted:

   * Activating and deactivating MD5 authentication, or rotating MD5 key authentication after a BGP session is established
   * Activating and deactivating Bidirectional Forwarding Detection (BFD) after establishing a BGP session
   * Modifying BGP ASN and BGP peer IP addresses after initial configuration

1. Update the content as needed.

   If you modify the speed or routing option, the pricing changes. Any updated charges take effect during the next billing cycle.  
   {: note}

1. Read and agree to the [{{site.data.keyword.dl_short}} prerequisites](/docs/dl?topic=dl-ibm-cloud-dl-prerequisites).
1. Click **Submit** for your changes to take effect.

Configuration updates start automatically after you click **Submit**. Notice that the gateway changes to **Configuring** state in the Direct Link table, followed by **Provisioned** when the update is completed.

## Updating a direct link from the CLI
{: #updating-a-direct-link-using-cli}
{: cli}

You can update an existing direct link with the CLI with the  [`ibmcloud dl gateway-update`](/docs/dl?topic=dl-dl-cli&interface=cli#update-gateway) command. For example,
the following command shows how to update a direct link without confirmation.

```sh
ibmcloud dl gateway-update 8ba9e7b0-dded-400e-ad7e-6481dad0b157 --speed-mbps 5000 --name dl-gw-updated --output json
```
{: pre}

## Updating direct link with the API
{: #updating-direct-link-api}
{: api}

Curl example:

```sh
DL_ENDPOINT="directlink.cloud.ibm.com"
curl -X PATCH https://$DL_ENDPOINT/v1/gateways/$GATEWAY_ID?version=2019-12-13 -H "authorization: Bearer $IAM_TOKEN"-d '{
        "name": "new_gateway_name"
      }'
```

Python example:

```sh
Import json
From ibm_cloud_networking_services importDirectLinkV1
fromibm_cloud_networking_services.direct_link_v1 import(
     GatewayMacsecConfigPatchTemplate)
fromibm_cloud_networking_services.direct_link_v1 import(
     GatewayMacsecConfigPatchTemplateFallbackCak)
     
# Initializing {direct_link} refer Authenticationfallback_cak_template = GatewayMacsecConfigPatchTemplateFallbackCak(crn=${macsecCak})
macsec_patch_template = GatewayMacsecConfigPatchTemplate(fallback_cak=fallback_cak_template)
gateway = direct_link.update_gateway(id=${gatewayId}, macsec_config=macsec_patch_template).get_result()
print(json.dumps(gateway, indent=2))
```
{: pre}

For more information, including Java, Node, and Go examples, see "Update gateway" in the [Direct Link API reference](/apidocs/direct_link?code=python#update-gateway).
{: note}
