---

copyright:
  years: 2021, 2026
lastupdated: "2026-01-16"

keywords: direct link, terraform

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Setting up Terraform for Direct Link
{: #terraform-setup-dl}

Terraform on {{site.data.keyword.cloud}} enables predictable and consistent creation of {{site.data.keyword.cloud_notm}} services so that you can rapidly build complex, multitier cloud environments that follow Infrastructure as Code (IaC) principles. Similar to using the {{site.data.keyword.cloud_notm}} CLI or API and SDKs, you can automate the creation, update, and deletion of your Direct Link instances by using HashiCorp Configuration Language (HCL).
{: shortdesc}

Looking for a managed Terraform on {{site.data.keyword.cloud}} solution? Try out [{{site.data.keyword.bplong}}](/docs/schematics?topic=schematics-getting-started). With {{site.data.keyword.bpshort}}, you can use the Terraform scripting language that you are familiar with. You don't have to worry about setting up and maintaining the Terraform command line and the {{site.data.keyword.cloud}} Provider plug-in. {{site.data.keyword.bpshort}} also provides pre-defined Terraform templates that you can easily install from the {{site.data.keyword.cloud}} catalog.
{: tip}

## Installing Terraform and configuring resources for Direct Link
{: #install-terraform}

Before you can create an authorization by using Terraform, make sure that you have completed the following:

* Make sure that you have the [required access](/docs/dl?topic=dl-iam) to create and work with Direct Link resources.
* Install the Terraform CLI and configure the {{site.data.keyword.cloud_notm}} Provider plug-in for Terraform. For more information, see the tutorial for [Getting started with Terraform on {{site.data.keyword.cloud}}](/docs/ibm-cloud-provider-for-terraform?topic=ibm-cloud-provider-for-terraform-getting-started). The plug-in abstracts the {{site.data.keyword.cloud_notm}} APIs that are used to complete this task.
* Create a Terraform configuration file that is named `main.tf`. In this file, you add the configuration to create an authorization between services by using HashiCorp Configuration Language. For more information, see the [Terraform documentation](https://developer.hashicorp.com/terraform/language){: external}.

1. In your Terraform configuration file, find the Terraform code that you used to create the Direct Link instance.
1. Create a Direct Link instance by using the `ibm_resource_instance` resource argument in your `main.tf` file. The Direct Link zone in the following example is named `Gateway1`. The Direct Link resource in the following example is named `test_dl_routers` and is created as a dedicated gateway in the `dal10` location.

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

1. After you finish building your configuration file, initialize the Terraform CLI. For more information, see [Initializing Working Directories](https://developer.hashicorp.com/terraform/cli/init){: external}.

   ```terraform
   terraform init
   ```
   {: pre}

1. Provision the resources from the `main.tf` file. For more information, see [Provisioning Infrastructure with Terraform](https://developer.hashicorp.com/terraform/cli/run){: external}.

   1. Run `terraform plan` to generate a Terraform execution plan to preview the proposed actions.

      ```terraform
      terraform plan
      ```
      {: pre}

   1. Run `terraform apply` to create the resources that are defined in the plan.

      ```terraform
      terraform apply
      ```
      {: pre}

1. From the [{{site.data.keyword.cloud_notm}} resource list](/resources){: external}, select the Direct Link instance that you created and note the instance ID.

1. Verify that the access policy is successfully assigned. For more information, see [Reviewing assigned access in the console](/docs/account?topic=account-assign-access-resources&interface=ui#review-your-access-console).

## What's next?
{: #terraform-setup-next}

Now that you successfully created your first Direct Link service instance with Terraform on {{site.data.keyword.cloud_notm}}, you can visit the Direct Link [Direct Link Terraform registry](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/dl_gateway){: external} to perform additional tasks using Terraform.
