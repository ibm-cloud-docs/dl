---

copyright:
  years:  2023, 2024
lastupdated: "2024-08-13"

keywords:

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Protecting resources with context-based restrictions
{: #cbr}

Context-based restrictions give account owners and administrators the ability to define and enforce access restrictions for {{site.data.keyword.cloud}} resources based on the context of access requests. Access to Direct Link resources can be controlled with context-based restrictions and identity and access management policies.
{: shortdesc}

These restrictions work with traditional IAM policies, which are based on identity, to provide an extra layer of protection. Unlike IAM policies, context-based restrictions don't assign access. Context-based restrictions check that an access request comes from an allowed context that you configure. Since both IAM access and context-based restrictions enforce access, context-based restrictions offer protection even in the face of compromised or mismanaged credentials. For more information, see [What are context-based restrictions](/docs/account?topic=account-context-restrictions-whatis).

A user must have the Administrator role on the Direct Link service to create, update, or delete rules. And a user must have either the Editor or Administrator role on the Context-based restrictions service to create, update, or delete network zones.
{: note}

Any {{site.data.keyword.cloudaccesstraillong_notm}} or audit log events that are generated come from the context-based restrictions service, and not Direct Link. For more information, see [Monitoring context-based restrictions](/docs/account?topic=account-cbr-monitor).

To protect your Direct Link with context-based restrictions, see the tutorial for [Leveraging context-based restrictions to secure your resources](/docs/account?topic=account-context-restrictions-tutorial).

## Limitations
{: #cbr-limitations}

Context-based restrictions protect only the actions associated with the [Direct Link API](/apidocs/direct_link). Actions that are associated with the following platform APIs are not protected by context-based restrictions. Reference the API docs for the specific action IDs.

- [Resource Instance APIs](/apidocs/resource-controller/resource-controller#list-resource-instances)
- [Resource Keys APIs](/apidocs/resource-controller/resource-controller#list-resource-keys)
- [Resource Bindings APIs](/apidocs/resource-controller/resource-controller#list-resource-bindings)
- [Resource Aliases APIs](/apidocs/resource-controller/resource-controller#list-resource-aliases)
- [IAM Policy APIs](/apidocs/iam-policy-management#list-policies)
- [Global Search APIs](/apidocs/search)
- Global Tagging [Attach](/apidocs/tagging#attach-tag) and [Detach](/apidocs/tagging#detach-tag) APIs
- [Context-based Restriction Rule APIs](/apidocs/context-based-restrictions#create-rule)

## Creating rules
{: #dl-creating-rules}

Context-based restrictions for the Direct Link service can be scoped to a Direct Link service resource type. The Direct Link service has two applicable resource types:`connect` and `dedicated`.

Also, rules can be scoped to a specific instance of the service, or a resource group by using resource attributes.

### Creating rules by using the CLI
{: #dl-creating-rules-cli}
{: cli}

1. To create rules from the CLI, [install the CBR CLI plug-in](/docs/account?topic=account-cbr-plugin).
1. Use the [`ibmcloud cbr rule-create` command](/docs/account?topic=account-cbr-plugin#cbr-cli-rule-create-command) to create CBR rules. For more information, see the CBR [CLI reference](/docs/account?topic=account-cbr-plugin#cbr-zones-cli).

The examples in this section are enforcement rules. You can make them report-only by adding `--enforcement-mode report`.

These example CLI commands create a context-based restriction rule for Direct Link service instances in the current account:

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
   ibmcloud cbr rule-create --description directlink-rule3 --service-name directlink --resource-type dedicated --resource-attributes "resource=<id_y>,resourceGroupId=<rg_x_id>" --zone-id=<zone_id> --enforcement-mode enabled
   ```
   {: pre}

## How Direct Link integrates with context-based restrictions
{: #cbr-overview}

Direct Link may call Key Protect and HPCS for key management support. These calls perform authority checks against the Direct Link service making the call. If a CBR Rule is ever created against Key Protect or HPCS, a Direct Link Service Reference must be added to the network zone of the rule.
