---

copyright:
  years: 2020
lastupdated: "2020-09-23"

keywords: direct link, IAM, permissions, access

subcollection: dl

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:term: .term}
{:generic: data-hd-programlang="generic"}
{:download: .download}

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
| Administrator | Allows a user to assign {{site.data.keyword.dl_short}} IAM access policies to other users. | <ul><li>Create gateway</li><li>Delete gateway</li><li>Edit gateway</li><li>Add a virtual connection to a gateway&ast;</li> <li>Remove a virtual connection from a gateway&ast;</li><li>Edit a virtual connection (API only)</li><li>Update user access policies for the service</li></ul> |         
| Editor | Performs all actions, including managing gateways and virtual connections. |<ul><li>Create gateway</li><li>Delete gateway</li><li>Edit gateway</li><li>Add a virtual connection to a gateway&ast;</li> <li>Remove a virtual connection from a gateway&ast;</li><li>Edit a virtual connection (API only)</li></ul> |   
| Viewer/Operator | Performs actions that don't change the state of resources. |<ul><li>List gateways</li><li>Get gateways</li><li>List a gateway's virtual connections</li><li>View a gateway's virtual connections</li><li>Retrieve gateway-related information (completion notice/letter of authorization)</li><li>View incoming connection requests&ast;</li></ul> |
{: caption="Table 1. IAM platform-access user role and actions" caption-side="top"}

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
| Gateway account | Create and delete a cross-account virtual connection. | `directlink.dedicated.edit` or `directlink.connect.edit` <br />No VPC authorization required at create or delete time. |
| Network account | View read-only gateways and virtual connections. | Service-level `directlink.dedicated.view` or `directlink.connect.view` |
| Network account | Accept and reject pending connections. | Service-level `directlink.dedicated.view` or `directlink.connect.view`<br />Update authorization on the connected VPC. |
| Network account | `DELETE` attached virtual connection. | Service-level `directlink.dedicated.view` or `directlink.connect.view`<br /> Update authorization on the connected VPC. |
{: caption="Table 2. Authorization changes for cross-account virtual connections" caption-side="top"}
