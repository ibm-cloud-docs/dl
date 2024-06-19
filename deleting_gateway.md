---

copyright:
  years: 2020, 2024
lastupdated: "2024-06-19"

keywords: direct link

subcollection: dl
---

{{site.data.keyword.attribute-definition-list}}

# Deleting a direct link and its attached connections
{: #delete-direct-link-gateway}
{: help}
{: support}

You can delete a direct link either before or after the gateway moves to the `Provisioned` state. However, you cannot delete a gateway during the `In review` and some `In progress` states.
{: shortdesc}

## Deleting a direct link in the UI
{: #deleting-a-direct-link-using-the-ui}
{: ui}

To delete a gateway from the {{site.data.keyword.dl_short}} table, click **Delete** from the Actions ![Actions menu](images/overflow.png) menu for the gateway that you want to delete. Alternatively, you can click **Actions > Delete** on the gateway's details page. Click **Delete** again to confirm the deletion.

If any virtual connections are attached to the gateway, you must detach them before you delete the gateway. To detach a virtual connection, click Delete ![Delete icon](images/garbage_icon.png) next to the connection entry on the gateway's details page. Then, click **Delete** to confirm.
{: important}

## Deleting a direct link from the CLI
{: #deleting-direct-link-cli}
{: cli}

You can delete an existing direct link with the CLI by using the [`ibmcloud dl gateway-delete`](/docs/dl?topic=dl-dl-cli#delete-gateway) command. For example, this command shows how to delete a direct link without confirmation.

```sh
ibmcloud dl gateway-delete e281b18b-0dba-49ee-9c64-aea588b7f1fd
```
{: pre}

## Deleting a direct link with the API
{: #deleting-direct-link-api}
{: api}

Curl example:

```sh
DL_ENDPOINT="directlink.cloud.ibm.com"
curl -X DELETE   https://$DL_ENDPOINT/v1/gateways/$GATEWAY_ID?version=2019-12-13   -H "authorization: Bearer $IAM_TOKEN"
```

Python example:

```sh
from ibm_cloud_networking_services import DirectLinkV1

# Initializing {direct_link} refer Authentication
direct_link.delete_gateway(id=${gatewayId})
```
{: pre}

For more information, including Java, Node, and Go examples, see "Delete gateway" in the [Direct Link API reference](/apidocs/direct_link?code=python#delete-gateway).
{: note}
