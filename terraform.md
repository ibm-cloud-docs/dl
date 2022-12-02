---

copyright:
  years: 2021
lastupdated: "2021-08-06"

keywords: direct link, terraform

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Setting up Terraform for Direct Link
{: #terraform-setup-dl}

Terraform on {{site.data.keyword.cloud}} enables predictable and consistent provisioning of {{site.data.keyword.cloud_notm}} services so that you can rapidly build complex, multi-tier cloud environments following Infrastructure as Code (IaC) principles. Similar to using the {{site.data.keyword.cloud_notm}} CLI or API and SDKs, you can automate the provisioning, update, and deletion of your Direct Link instances by using HashiCorp Configuration Language (HCL).
{: shortdesc}

Looking for a managed Terraform on {{site.data.keyword.cloud}} solution? Try out [{{site.data.keyword.bplong}}](/docs/schematics?topic=schematics-getting-started). With {{site.data.keyword.bpshort}}, you can use the Terraform scripting language that you are familiar with, but you don't have to worry about setting up and maintaining the Terraform command line and the {{site.data.keyword.cloud}} Provider plug-in. {{site.data.keyword.bpshort}} also provides pre-defined Terraform templates that you can easily install from the {{site.data.keyword.cloud}} catalog.
{: tip}

## Installing Terraform and configuring resources for Direct Link (2.0)
{: #install-terraform}

Before you begin, make sure that you have the [required access](/docs/dl?topic=dl-iam) to create and work with Direct Link resources.

1. Follow the [Terraform on {{site.data.keyword.cloud}} getting started tutorial](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started) to install the Terraform CLI and configure the {{site.data.keyword.cloud}} Provider plug-in for Terraform. The plug-in abstracts the {{site.data.keyword.cloud}} APIs that are used to provision, update, or delete Direct Link service instances and resources.
1. Create a Terraform configuration file that is named `main.tf`. In this file, you add the configuration to create a Direct Link service instance and to assign a user an access policy in Identity and Access Management (IAM) for that instance by using HashiCorp Configuration Language (HCL). For more information, see the [Terraform documentation](https://www.terraform.io/docs/language/index.html){: external}.

   The Direct Link resource in the following example is named `test_dl_routers` and is created as a Dedicated gateway in the `dal10` location.

   For more information about arguments and attributes, see the [`ibm_dl_gateway`](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/dl_gateway){: external} usage example.
   {: note}

   ```terraform
   data "ibm_dl_routers" "test_dl_routers" {
           offering_type = "dedicated"
           location_name = "dal10"
       }

   resource "ibm_dl_gateway" "test_dl_gateway" {
     bgp_asn =  64999
     global = true
     metered = false
     name = "Gateway1"
     resource_group = "bf823d4f45b64ceaa4671bee0479346e"
     speed_mbps = 1000
     type =  "dedicated"
     cross_connect_router = data.ibm_dl_routers.test_dl_routers.cross_connect_routers[0].router_name
     location_name = data.ibm_dl_routers.test_dl_routers.location_name
     customer_name = "Customer1"
     carrier_name = "Carrier1"

   }
   ```
   {: codeblock}

1. Initialize the Terraform CLI.

   ```terraform
   terraform init
   ```
   {: pre}

1. Create a Terraform execution plan. The Terraform execution plan summarizes all the actions that need to be run to create the Direct Link instance in your account.

   ```terraform
   terraform plan
   ```
   {: pre}

1. Create the Direct Link instance and IAM access policy in {{site.data.keyword.cloud_notm}}.

   ```terraform
   terraform apply
   ```
   {: pre}

1. From the [{{site.data.keyword.cloud_notm}} resource list](/resources){: external}, select the Direct Link instance that you created and note the instance ID.

1. Verify that the access policy is successfully assigned. For more information, see [Reviewing assigned access in the console](/docs/account?topic=account-assign-access-resources#review-your-access-console).
