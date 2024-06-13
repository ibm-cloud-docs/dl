---

copyright:
  years:  2023
lastupdated: "2023-01-27"

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

Any {{site.data.keyword.cloudaccesstraillong_notm}} or audit log events generated will come from the context-based restrictions service, and not Direct Link. For more information, see [Monitoring context-based restrictions](/docs/account?topic=account-cbr-monitor).

To get started protecting your Direct Link with context-based restrictions, see the tutorial for [Leveraging context-based restrictions to secure your resources](/docs/account?topic=account-context-restrictions-tutorial).

## How Direct Link integrates with context-based restrictions
{: #cbr-overview}

Direct Link may call Key Protect and HPCS for key management support. These calls will perform authority checks against the Direct Link service making the call. If a CBR Rule is ever created against Key Protect or HPCS, a Direct Link Service Reference must be added to the network zone of the rule.

_If context-based restrictions don't apply holistically to all components of your service's resources, provide a paragraph that categorizes the scope of what’s enforced or impacted and what isn't. Also, consider the following use cases to determine what you need to document for your service:_

_1. Include common examples across all interface types (UI, CLI, API). See platform task topics, but if there's something specific in CLI/API as far as scoping a rule, then you might want to include those here--similar to examples for fine-grained access by using the interfacer switcher._

_2. Consider the different access patterns for your service's APIs, if any. How does a customer use the APIs? How does your service have it set up for creating context-based restriction rules and how does that impact operations a customer can perform (for example, scoping a rule to protect specific APIs)? Think about a user creating a rule. When you select and scope resources for a rule, you must select the service, resources, and then you might have the option to scope protection to APIs. Depending on what level of this your service supports, you might need to document what's available and how this works for your service. Name this section "Protecting specific APIs". Include information about each API or API type, such as the actions and action descriptions that map to each._

   _Tip: Ask your development team for the CBR service registration json file to help you get started. In the file, you'll find the APIs that customers can use to scope a rule._

_3. Document resource attributes. Check the UI for the resource attributes that customers can use to scope the rule to specific resources. Documenting these resource attributes can help customers that are using the CLI or API because there is currently no programmatic way to retrieve the available resource attributes for a given service. Name this section "Protecting specific resources"._

_4. If you use private endpoints, private endpoints might already have an allowlist concept, so how would integration with context-based restrictions work? Honor both, honor one over the other, an intersection of these, how will this work if you have a legacy system in place?_

_5. State any limitations on how the context-based restrictions work with your service's resources when it's working with another service or generally within the platform. You can use a note format if this is only a sentence or two. For example, "Context-based restrictions are not supported in Object Storage for Satellite."_ See also the Limitations section below.

_6. Are there service to service authorizations required to be in place? If so, you would want to create rules to allow for those service to service authorizations to continue working once a rule is in place._

   _Example:_
   1. There is an existing IAM S2S authorization to allow COS to access key protect.
   2. Someone creates a CBR rule on key protect.
   3. For the rule in step 2, a CBR zone would need to specify a service reference allowing COS to access key protect. Without this step network access would be blocked.

_7. Is your service a composite service? Document how to scope a rule to each composite service. As an example of how to document CBR for composite services, see [Protecting the IAM Access Management service](/docs/account?topic=account-iam-services-cbr&interface=ui#cbr-iam-access-management). The sub-sections titled "Restricting the ability to manage..." describe scoping a rule Resource type and selecting the child service. If your service uses a different attribute to specify a specific child service, document that._

_For an example of how to document your service's integration with context-based restrictions, see [Protecting specific APIs](/docs/containers?topic=containers-cbr&interface=api#protect-api-types-cbr)._

## Limitations
{: #cbr-limitations}

Context-based restrictions protect only the actions associated with the [Direct Link API](/apidocs/direct_link). Actions associated with the following platform APIs are not protected by context-based restrictions. Reference the API docs for the specific action IDs.

- [Resource Instance APIs](/apidocs/resource-controller/resource-controller#list-resource-instances)
- [Resource Keys APIs](/apidocs/resource-controller/resource-controller#list-resource-keys)
- [Resource Bindings APIs](/apidocs/resource-controller/resource-controller#list-resource-bindings)
- [Resource Aliases APIs](/apidocs/resource-controller/resource-controller#list-resource-aliases)
- [IAM Policy APIs](/apidocs/iam-policy-management#list-policies)
- [Global Search APIs](/apidocs/search)
- Global Tagging [Attach](/apidocs/tagging#attach-tag) and [Detach](/apidocs/tagging#detach-tag) APIs
- [Context-based Restriction Rule APIs](/apidocs/context-based-restrictions#create-rule)
- [Secrets Manager APIs](/apidocs/secrets-manager)

## Creating network zones
{: #network-zone}

A network zone represents an allowlist of IP addresses where an access request is created. It defines a set of one or more network locations that are specified by the following attributes:

* IP addresses, which include individual addresses, ranges, or subnets.
* VPCs
* Service references, which allow access from other {{site.data.keyword.cloud_notm}} services.

Make sure to add _serviceName_ to network zones for rules that target other {{site.data.keyword.cloud_notm}} resources, or some operations in your workflow might fail.
{: important}

### Service references
{: #dl-service-references}

List the services that customers should add to network zones as a service reference. This way, they can include it in the rule that targets your service, and still allow the two services to communicate.

### Creating network zones in the console
{: #network-zone-ui}
{: ui}

*Insert your examples here.*

### Creating network zones by using the API
{: #network-zone-api}
{: api}

You can create network zones by using the `create-zone` command. For more information, see the [API docs](/apidocs/context-based-restrictions#create-zone). You can add _serviceName_ to network zones as a service reference to allow _serviceName_ to access resources and services in your account that are the subject of a rule.

The `serviceRef` attribute for _serviceName_ is `your-service`.
{: tip}

*Insert your examples here.*

### Creating network zones by using the CLI
{: #network-zone-cli}
{: cli}

You can use the `cbr-zone-create` command to add network locations, VPCs, and service references to network zones. For more information, see the CBR [CLI reference](/docs/account?topic=account-cbr-plugin#cbr-zones-cli). Add _serviceName_ to network zones as a service reference to allow _serviceName_ to access resources and services in your account that are the subject of a rule.

    To find a list of available service refs, run the `ibmcloud cbr service-ref-targets` [command](/docs/account?topic=account-cbr-plugin#cbr-cli-service-ref-targets-command). The `service_name` for _serviceName_ is `_serviceName_`.
    {: tip}

*Insert your examples here.*

## Creating rules
{: #dl-creating-rules}

Context-based restrictions for the Direct Link service can be scoped to a Direct Link service resource type. The Direct Link Service has two applicable resource types: `connect` and `dedicated`.

Additionally, rules can be scoped to a specific instance of the service, or a resource group by using resource attributes.

### Creating rules in the console
{: #rules-ui}
{: ui}

Review the following examples to learn how to create rules for _serviceName_.

*Insert your examples here. Include more complex use cases, like scoping a rule to protect specific APIs.*

### Creating rules by using the API
{: #rules-api}
{: api}

Review the following examples to learn how to create rules for _serviceName_. For more information, see the [API docs](/apidocs/context-based-restrictions#create-rule).

*Insert your examples here. Include more complex use cases, like scoping a rule to protect specific APIs.*

### Creating rules by using the CLI
{: #dl-creating-rules-cli}
{: cli}

1. To create rules from the CLI, [install the CBR CLI plug-in](/docs/account?topic=account-cbr-plugin#install-cbr-plugin).
1. Use the [`ibmcloud cbr rule-create` command](/docs/account?topic=account-cbr-plugin#cbr-cli-rule-create-command) to create CBR rules. For more information, see the CBR [CLI reference](/docs/account?topic=account-cbr-plugin).

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
