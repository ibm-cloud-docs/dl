---

copyright:
  years: 2017, 2021
lastupdated: "2021-03-04"

keywords: vpe

subcollection: dl

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank_"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:note: .note}
{:important: .important}

# Integrating with Virtual Private Endpoint for VPC
{: #vpe-for-ibm-cloud-direct-link}

{{site.data.keyword.cloud}} Virtual Private Endpoint (VPE) for VPC enables you to connect to supported {{site.data.keyword.cloud_notm}} services from your VPC network by using IP addresses of your choosing, allocated from a subnet within your VPC.

Currently, VPE support for {{site.data.keyword.dl_short}} is available only in the Dallas (DAL) and Washington DC (WDC) regions.  
{: important}

## Setting up a VPE gateway for the Direct Link service
{: #vpe-setup}

Follow instructions in [Getting started](/docs/vpc?topic=vpc-about-vpe#vpe-getting-started) for VPE for VPC to create and configure a VPE gateway for the {{site.data.keyword.cloud_notm}} Direct Link service offering.

### Using the CLI
{: #vpe-setup-cli}

After creating an endpoint gateway for Direct Link, follow these steps:

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

### Using the VPE for VPC API
{: #vpe-setup-api}

After creating an endpoint gateway for the {{site.data.keyword.dl_short}} service, use the service endpoints FQDN `private.directlink.cloud.ibm.com` in the URL to access the service. For example:

```sh
curl https://private.directlink.cloud.ibm.com/v1/direct_links?version='2020-03-31' -H "Authorization: Bearer $iam_token"
```
{: pre}

### Using the SDK
{: #dl-sdk}

After creating an endpoint gateway for {{site.data.keyword.dl_full_notm}}, you must use the private endpoint's FQDN when setting the service's FQDN during construction of the Direct Link gateway service object.

```sh
private.directlink.cloud.ibm.com
```
For examples of setting the service's FQDN for the specific SDK language, see [SDK API examples](https://{DomainName}/apidocs/direct_link?code=go#authentication).

### Using Terraform
{: #using-terraform}

If you plan to access the Direct Link service using Terraform, make sure to set the `IBMCLOUD_DL_API_ENDPOINT` environment variable to `private.directlink.cloud.ibm.com`. For example:

```sh
export IBMCLOUD_DL_API_ENDPOINT=private.directlink.cloud.ibm.com
```
{: pre}

For more information, see [Direct Link Gateway resources](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-dl-gateway-resource) and [Direct Link Gateway data sources](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-dl-gateway-ds).
