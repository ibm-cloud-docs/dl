---

copyright:
  years: 2017, 2022
lastupdated: "2022-04-01"

keywords: vpe for Direct Link, virtual private endpoints for Direct Link, using vpe for vpc with Direct Link, isolation for Direct Link, private network for Direct Link, network isolation in Direct Link, non-public routes for Direct Link, private connection for Direct Link, private connectivity for Direct Link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Using virtual private endpoints for VPC to privately connect to {{site.data.keyword.dl_short}}
{: #vpe-connection}

{{site.data.keyword.cloud}} Virtual Private Endpoints (VPE) for VPC enables you to connect to {{site.data.keyword.dl_short}} from your VPC network by using the IP addresses of your choosing, allocated from a subnet within your VPC.
{: shortdesc}

VPEs are virtual IP interfaces that are bound to an endpoint gateway created on a per service, or service instance, basis (depending on the service operation model). The endpoint gateway is a virtualized function that scales horizontally, is redundant and highly available, and spans all availability zones of your VPC. Endpoint gateways enable communications from virtual server instances within your VPC and {{site.data.keyword.cloud}} service on the private backbone. VPE for VPC gives you the experience of controlling all the private addressing within your cloud. For more information, see [About virtual private endpoint gateways](/docs/vpc?topic=vpc-about-vpe).

## Before you begin
{: #prereq-service-endpoint}

Before you target a virtual private endpoint for {{site.data.keyword.cloud}}, you must complete the following tasks.

* Ensure that a [Virtual Private Cloud is created](/docs/vpc?topic=vpc-getting-started).
* Make a plan for your [virtual private endpoints](/docs/vpc?topic=vpc-planning-considerations).
* Ensure that [correct access controls](/docs/vpc?topic=vpc-configure-acls-sgs-endpoint-gateways) are set for your virtual private endpoint.
* Understand the [limitations](/docs/vpc?topic=vpc-limitations-vpe) of having a virtual private endpoint.
* Understand how to [view details](/docs/vpc?topic=vpc-vpe-viewing-details-of-an-endpoint-gateway) about a virtual private endpoint.

## Setting up a VPE for {{site.data.keyword.dl_short}}
{: #endpoint-setup}

When you create a VPE gateway by using the CLI or API, you must specify the [Cloud Resource Name (CRN)](/docs/account?topic=account-crn) of the region in which you want connect to {{site.data.keyword.dl_short}}. Review the following table for the available regions and CRNs to use to create your VPE gateway.
 

Direct Link (2.0) supports VPEs in all the VPC regions as shown.

| Location | Region | Cloud Resource Name (CRN) |
|---------|-------|----------------|
| Dallas | `us-south` | `crn:v1:bluemix:public:container-registry:us-south:::endpoint:vpe.us-south.container-registry.cloud.ibm.com` |
| Frankfort | `eu-de` | `crn:v1:bluemix:public:container-registry:eu-de:::endpoint:vpe.eu-de.container-registry.cloud.ibm.com` |
| London | `eu-gb` | `crn:v1:bluemix:public:container-registry:eu-gb:::endpoint:vpe.eu-gb.container-registry.cloud.ibm.com` |
| Osaka | `jp-osa` | `crn:v1:bluemix:public:container-registry:jp-osa:::endpoint:vpe.jp-osa.container-registry.cloud.ibm.com` |
| Sao Paulo | `br-sao` | `crn:v1:bluemix:public:container-registry:br-sao:::endpoint:vpe.br-sao.container-registry.cloud.ibm.com` |
| Sydney | `au-syd` | `crn:v1:bluemix:public:container-registry:au-syd:::endpoint:vpe.au-syd.container-registry.cloud.ibm.com` |
| Tokyo | `jp-tok` | `crn:v1:bluemix:public:container-registry:jp-tok:::endpoint:vpe.jp-tok.container-registry.cloud.ibm.com` |
| Toronto  | `ca-tor` | `crn:v1:bluemix:public:container-registry:ca-tor:::endpoint:vpe.ca-tor.container-registry.cloud.ibm.com` |
| Washington DC | `us-east` | `crn:v1:bluemix:public:container-registry:us-east:::endpoint:vpe.us-east.container-registry.cloud.ibm.com` |
{: caption="Table 1. Region availability and Cloud Resource Names (CRNs) for connecting {{site.data.keyword.dl_short}} over {{site.data.keyword.cloud_notm}} private networks" caption-side="bottom"}

### Configuring an endpoint gateway
{: #endpoint-gateway-servicename}

To configure a virtual private endpoint gateway, follow these steps:

1. List the available services, including {{site.data.keyword.cloud_notm}} infrastructure services available (by default) for all VPC users.
1. [Create an endpoint gateway](/docs/vpc?topic=vpc-ordering-endpoint-gateway) for {{site.data.keyword.dl_short}} that you want to be privately available to the VPC.  
1. [Bind a reserved IP address](/docs/vpc?topic=vpc-bind-unbind-reserved-ip) to the endpoint gateway. 
1. View the created VPE gateways associated with the {{site.data.keyword.dl_short}}. For more information, see [Viewing details of an endpoint gateway](/docs/vpc?topic=vpc-vpe-viewing-details-of-an-endpoint-gateway). 

Now your virtual server instances in the VPC can access your {{site.data.keyword.dl_short}} instance privately through it.

## Using your VPE for {{site.data.keyword.dl_short}}
{: #using-direct-link-vpe}

After you create an endpoint gateway for {{site.data.keyword.dl_short}}, follow these steps:

### Using the VPE with the CLI
{: #vpe-cli}
{: cli}

Use the following steps to update to the latest version of the CLI and the {{site.data.keyword.dl_short}} plug-in.

1. Update the {{site.data.keyword.cloud_notm}} CLI to the latest version:

   ```sh
   ibmcloud update
   ```
   {: pre}

1. Update the Direct Link CLI plug-in:

   ```sh
   ibmcloud plugin update dl-cli
   ```
   {: pre}

### Using the VPE with the VPC API
{: #vpe-api}
{: api}

After creating an endpoint gateway for the {{site.data.keyword.dl_short}} service, use the service endpoints FQDN `private.directlink.cloud.ibm.com` in the URL to access the service. For example:

```sh
curl https://private.directlink.cloud.ibm.com/v1/direct_links?version='2020-03-31' -H "Authorization: Bearer $iam_token"
```
{: pre}

### Using the VPE with the SDK
{: #vpe-sdk}
{: api}

After creating an endpoint gateway for {{site.data.keyword.dl_short}}, you must use the private endpoint's FQDN when setting the service's FQDN during construction of the Direct Link gateway service object.

```sh
private.directlink.cloud.ibm.com
```
{: pre}

For examples of setting the service's FQDN for the specific SDK language, see [SDK API examples](/apidocs/direct_link?code=go#authentication).

### Using the VPE with Terraform
{: #vpe-terraform}
{: terraform}

If you plan to access the Direct Link service using Terraform, make sure to set the `IBMCLOUD_DL_API_ENDPOINT` environment variable to `private.directlink.cloud.ibm.com`. For example:

```sh
export IBMCLOUD_DL_API_ENDPOINT=private.directlink.cloud.ibm.com
```
{: pre}

For more information, see [Direct Link Gateway resources](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-dl-gateway-resource) and [Direct Link Gateway data sources](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-dl-gateway-ds).
