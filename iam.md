---

copyright:
  years: 2020
lastupdated: "2020-09-23"

keywords: IAM, permissions, access, direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Managing access for {{site.data.keyword.dl_full_notm}}
{: #iam}

{{site.data.keyword.dl_full}} enables connectivity between customer on-premises resources to {{site.data.keyword.cloud_notm}} resources that are hosted in classic and Virtual Private Cloud (VPC) infrastructures, including second-generation compute resources.
{: shortdesc}

{{site.data.keyword.dl_full_notm}} uses {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) platform access roles to manage access to the service's resources. IAM access roles allow account administrators to assign different levels of permission for calling the service's APIs and accessing the UI. The following table provides example actions that you can take against the {{site.data.keyword.dl_short}} service and its resources, depending on the user's assigned roles.

## Platform-access roles
{: #platform-access-roles}

{{site.data.keyword.dl_short}} supports Administrator, Editor, and Viewer platform-access roles.
{: shortdesc}

| Role | Description of actions | Example actions |
|---|---|---|
| Administrator | Allows a user to assign {{site.data.keyword.dl_short}} IAM access policies to other users. | Create gateway  \n Delete gateway  \n Edit gateway  \n Add a virtual connection to a gateway&ast;<  \n Remove a virtual connection from a gateway&ast;  \n Edit a virtual connection (API only)  \n Update user access policies for the service |         
| Editor | Performs all actions, including managing gateways and virtual connections. | Create gateway  \n Delete gateway  \n Edit gateway  \n Add a virtual connection to a gateway&ast;<  \n Remove a virtual connection from a gateway&ast;  \n Edit a virtual connection (API only) |   
| Viewer/Operator | Performs actions that don't change the state of resources. |  \n List gateways  \n Get gateways  \n List a gateway's virtual connections  \n View a gateway's virtual connections  \n Retrieve gateway-related information (completion notice/letter of authorization)  \n View incoming connection requests&ast; |
{: caption="Table 1. IAM platform-access user role and actions" caption-side="bottom"}

&ast; To add or remove virtual connections to VPCs, or to accept or reject a connection request, the user must also have Editor or Administrator platform-access role permissions to the VPC. See [VPC: Getting started with IAM](/docs/vpc?topic=vpc-iam-getting-started) for more information.

**Notes**:

* All {{site.data.keyword.dl_short}} resources exist in a resource group. Creating a {{site.data.keyword.dl_short}} resource requires Viewer access to the selected resource group.
* For information about assigning user roles in the console, see [Managing access to resources](/docs/account?topic=account-assign-access-resources).

## Authorization considerations for cross-account virtual connections
{: #xac-auth-considerations}

The following table shows the authorization changes for cross-account virtual connections.

   A cross-account virtual connection means that the gateway exists in an IBM Cloud account and a virtual connection in that gateway connects to a VPC in a different IBM Cloud account. This setup requires special authorization considerations because the objects (the directlink gateway and the VPC) and their resource groups do not exist in both accounts.
   {: note}

| Related account | Capability | Required authorization |
|---|---|---|
| Gateway account | Any capabilities not mentioned in this table. | No authorization changes. |
| Gateway account | Create and delete a cross-account virtual connection. | `directlink.dedicated.edit` or `directlink.connect.edit`  \n No VPC authorization required at create or delete time. |
| Network account | View read-only gateways and virtual connections. | Service-level `directlink.dedicated.view` or `directlink.connect.view` |
| Network account | Accept and reject pending connections. | Service-level `directlink.dedicated.view` or `directlink.connect.view`  \n Update authorization on the connected VPC. |
| Network account | `DELETE` attached virtual connection. | Service-level `directlink.dedicated.view` or `directlink.connect.view`  \n  Update authorization on the connected VPC. |
{: caption="Table 2. Authorization changes for cross-account virtual connections" caption-side="bottom"}
