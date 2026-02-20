---

copyright:
  years: 2020, 2026
lastupdated: "2026-02-20"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Deleting a direct link
{: #delete-direct-link}

IBM Cloud Direct Link gateways provide private, high-speed connections between on-premises networks or colocation facilities and IBM Cloud. Proper deletion ensures resources are cleaned up, virtual connections are detached, and billing stops. This topic explains how to remove a direct link for all major offerings: Direct Link Connect, Direct Link Dedicated, and Dedicated Hosting.
{: shortdesc}

## Before you begin
{: #before-you-begin-delete-direct-link}

Ensure that the direct link is in a stable state suitable for deletion. `In review`,`In progress`, or similar transient states cannot be deleted.

## Deleting a direct link in the console
{: #delete-direct-link-console}
{: ui}

To delete a direct link in the [{{site.data.keyword.cloud_notm}} console](/login){: external},  follow these steps:

1. Detach all virtual connections:

   1. Select the **Navigation menu** ![Menu icon](../icons/icon_hamburger.svg), then click **Infrastructure** ![VPC icon](../../icons/vpc.svg) > **Network** > **Direct link**.
   1. In the list, select the direct link to open its **Details** page.
   1. In the Virtual connections section, click the ![Delete icon](../icons/delete.svg) icon next to each virtual connecton.
   1. Confirm the deletion for each virtual connection when prompted.

1. Delete the direct link:

   1. Go back to the Direct Link list page.
   1. Locate the direct link that you want to delete.
   1. Click **Delete** from the Actions ![Actions menu](../icons/action-menu-icon.svg) menu.
   1. Confirm the deletion.

## Deleting a direct link from the CLI
{: #delete-direct-link-cli}
{: cli}

To delete a direct link and its associated virtual connections from the CLI, follow these steps:

1. List all virtual connections:

   ```sh
   ibmcloud dl vc-list --gateway-id GATEWAY_ID
   ```
   {: pre}

1. Delete each virtual connection:

   ```sh
   ibmcloud dl virtual-connection-delete VIRTUAL_CONNECTION_ID
   ```
   {: pre}

   Repeat for all virtual connections.

1. Delete the direct link:

   ```sh
   ibmcloud dl gateway-delete GATEWAY_ID --force
   ```
   {: pre}

## Deleting a direct link with the API
{: #delete-direct-link-api}
{: api}

Before deleting a direct link, you must first remove all virtual connections attached to the gateway. If virtual connections remain, the gateway delete call fails with an error indicating that they must be removed first.

To delete a direct link with the API, follow these steps:

1. List all virtual connections for the gateway:

   ```sh
   curl -X GET \
     "https://directlink.cloud.ibm.com/v1/gateways/$GATEWAY_ID/virtual_connections?version=2019-12-13" \
     -H "Authorization: Bearer $IAM_TOKEN"
   ```
   {: pre}

   This returns the virtual connections associated with the gateway.

1. Delete each virtual connection:

   ```sh
   curl -X DELETE \
        "https://directlink.cloud.ibm.com/v1/gateways/$GATEWAY_ID/virtual_connections/$VC_ID?version=2019-12-13" \
        -H "Authorization: Bearer $IAM_TOKEN"
   ```
   {: pre}

   Repeat this call for each virtual connection ID returned by the list call. The API deletes each specified virtual connection.

1. After all virtual connections have been removed, delete the direct link:

   ```sh
   curl -X DELETE \
     "https://directlink.cloud.ibm.com/v1/gateways/$GATEWAY_ID?version=2019-12-13" \
     -H "Authorization: Bearer $IAM_TOKEN"
   ```
   {: pre}

### Python example
{: #python-example}
{: api}

```sh
from ibm_cloud_networking_services import DirectLinkV1

direct_link = DirectLinkV1(authenticator=auth)

# List and delete all virtual connections
vc_list = direct_link.list_gateway_virtual_connections(gateway_id=gateway_id).get_result()
for vc in vc_list.get("virtual_connections", []):
    direct_link.delete_gateway_virtual_connection(gateway_id=gateway_id, id=vc["id"])

# Delete the gateway
direct_link.delete_gateway(id=gateway_id)
```
{: codeblock}

For more information, including Java, Node, and Go examples, see "Delete gateway" in the [Direct Link API reference](/apidocs/direct_link?code=python#delete-gateway).
{: note}

## Deleting a direct link with Terraform
{: #delete-direct-link-terraform}
{: terraform}

If using Terraform, destroy virtual connections first, then the gateway:

```sh
terraform destroy -target=ibm_dl_virtual_connection.vc_example
terraform destroy -target=ibm_dl_gateway.gateway_example
```
{: pre}

Deleting the gateway before virtual connections can fail due to dependencies.

## Offering-specific tasks
{: #offering-specific-tasks}

Here are additional steps to follow depending on the type of direct link that you are deleting.

* For Direct Link Connect, remove the corresponding connection in the provider portal.
* For Direct Link Dedicated, put in a delete request for your cross-connects with your provider.
* For Direct Link Dedicated Hosting, coordination with the hosting provider is required to de-provision the physical infrastructure and complete contract closure.

Billing stops after the direct link and associated virtual connections are removed.
{: note}
