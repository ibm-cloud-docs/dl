---

copyright:
  years:  2022
lastupdated: "2022-10-27"

keywords: 

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Protecting resources with context-based restrictions
{: #cbr}

Context-based restrictions give account owners and administrators the ability to define and enforce access restrictions for {{site.data.keyword.cloud}} resources based on the context of access requests. Access to Direct Link resources can be controlled with context-based restrictions and identity and access management policies.
{: shortdesc}

The preview of this functionality is available only to authorized accounts. 
{: preview}

These restrictions work with traditional IAM policies, which are based on identity, to provide an extra layer of protection. Unlike IAM policies, context-based restrictions don't assign access. Context-based restrictions check that an access request comes from an allowed context that you configure. Since both IAM access and context-based restrictions enforce access, context-based restrictions offer protection even in the face of compromised or mismanaged credentials. For more information, see [What are context-based restrictions](/docs/account?topic=account-context-restrictions-whatis).

A user must have the Administrator role on the Direct Link service to create, update, or delete rules. And a user must have either the Editor or Administrator role on the Context-based restrictions service to create, update, or delete network zones.
{: note}

Any {{site.data.keyword.cloudaccesstraillong_notm}} or audit log events generated will come from the context-based restrictions service, and not Direct Link. For more information, see [Monitoring context-based restrictions](/docs/account?topic=account-cbr-monitor).

To get started protecting your Direct Link with context-based restrictions, see the tutorial for [Leveraging context-based restrictions to secure your resources](/docs/account?topic=account-context-restrictions-tutorial). 

## Creating rules
{: #dl-creating-rules}

Context-based restrictions for the Direct Link service can be scoped to a Direct Link service resource type. The Direct Link Service has two applicable resource types: `connect` and `dedicated`.

Additionally, rules can be scoped to a specific instance of the service, or a resource group by using resource attributes.

### Creating rules by using the CLI
{: #dl-creating-rules-cli}
{: cli}

1. To create rules from the CLI, [install the CBR CLI plug-in](/docs/account?topic=cli-cbr-plugin#install-cbr-plugin).
1. Use the [`ibmcloud cbr rule-create` command](/docs/account?topic=cli-cbr-plugin#cbr-cli-rule-create-command) to create CBR rules. For more information, see the CBR [CLI reference](/docs/account?topic=cli-cbr-plugin#cbr-zones-cli).

The examples in this section are enforcement rules. You can make them report-only by adding `--enforcement-mode report`.  

The following example CLI commands create a context-based restriction rule for Direct Link service instances in the current account:

* Creates a report-only rule against all Direct Link Connect service instances in the current account:

   ```sh
   ibmcloud cbr rule-create --description directlink-rule1 --service-name directlink --resource-type connect --zone-id=<zone_id> --enforcement-mode report
   ```
   {: pre}

* Creates a disabled rule against all Direct Link Dedicated service instances in the current account that are in ResourceGroup `x`.

   ```sh
   ibmcloud cbr rule-create --description directlink-rule2 --service-name directlink --resource-type dedicated --resource-attributes "resourceGroupId=<rg_x_id>" --zone-id=<zone_id> --enforcement-mode disabled
   ```
   {: pre}

* Creates an enabled rule against the Direct Link Connect service instance in the current account with an ID of `y` in ResourceGroup `x`.

   ```sh
   ibmcloud cbr rule-create --description directlink-rule3 --service-name directlink --resource-type dedicated --resource-attributes "resource=<id_y>,resourceGroupId=<rg_x_id>" --zone-id=<zone_id> --enforcement-mode disabled
   ```
   {: pre}

## How Direct Link integrates with context-based restrictions
{: #cbr-overview}

Direct Link may call Key Protect and HPCS for key management support. These calls will perform authority checks against the Direct Link service making the call. If a CBR Rule is ever created against Key Protect or HPCS, a Direct Link Service Reference must be added to the network zone of the rule.