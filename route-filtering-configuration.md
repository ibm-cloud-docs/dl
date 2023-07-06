---

copyright:
  years: 2023
lastupdated: "2023-02-28"

keywords: direct link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Configuring route filters
{: #configure-route-filters}

You can configure route filters using the UI, CLI, and API.
{: shortdesc}

## Before you begin
{: #route-filters-before-you-begin}

Before configuring a route filter, review the following information:

* The prefix must be an IPv4 subnet CIDR indicating both the address and mask length. 
* [Route filtering examples](/docs/dl?topic=dl-route-filtering-examples&interface=ui) 
* You can configure a maximum of 15 import/export route filters per direct link. To increase this quota for Direct Link Connect or Direct Link Dedicated, [contact IBM Support](/unifiedsupport/cases/form){: external}. 

## Configuring route filters in the UI
{: #configure-route-filters-ui}
{: ui}

To create and configure route filters on a provisioned gateway, follow these steps:

1. Log in to the [Direct Link console](/interconnectivity/direct-link){: external}, then click the Direct Link name in the table to show its details.
1. Click the **BGP** tab, then click **Route filters**.  Alternatively, you can use the **Route filters** shortcut. 
1. Depending on the route filter that you want to configure, click **Import route filters** or **Export route filters**. 
1. For Default, specify to permit or deny all routes not specified by a route filter.
1. To create filters to add to the list, or to prioritize filters, click **Configure filters**.    
1. Save your configuration. You are returned to the Details page where your route configuration is displayed. 

## Configuring route filters from the CLI
{: #create-route-filters-cli}
{: cli}

You can create route filters with the CLI using the [`exportroutefilter-create`](/docs/dl?topic=dl-dl-cli&interface=cli#export-route-filter-create) and [`importroutefilter-create`](/docs/dl?topic=dl-dl-cli&interface=cli#import-route-filter-create) commands. For example, the following command shows how to create an export route filter:

```sh
ibmcloud dl export-route-filter-create 58e4f46f-0dab-0000-9432-3df974db0618 --action deny --prefix 10.10.10.0/24 --ge 30 --le 26
```

Where:

`58e4f46f-0dab-0000-9432-3df974db0618` 
:   Specifies the ID of the gateway.

`--action deny` 
:   Specifies the export route filter action. Valid values are 'permit' or 'deny'.

`--prefix 10.10.10.0/24` 
:   Specifies an IPv4 subnet CIDR indicating both the address and mask length.

`--le LE` 
:   Specify a maximum matching length (LE, less than or equal to). Optional. For more information, see [Route filtering rules](/docs/dl?topic=dl-filter-routes&interface=ui#route-filtering-rules).

`--ge GE` 
:   Specify a minimum matching length (GE, greater than or equal to). Optional. For more information, see [Route filtering rules](/docs/dl?topic=dl-filter-routes&interface=ui#route-filtering-rules). 

## Configuring route filters with the API
{: #create-route-filters-api}
{: api}

To create route filters using the API, follow these steps:

1. Set up your [API environment](/docs/dl?topic=dl-set-up-environment) with the right variables.
1. Store any additional variables to be used in the API commands, for example:
   
   ```sh
   direct_link_id="11111111-b540-4766-a196-14368f328eb2"
   ```
   
1. Use either the [create an export route filter](/apidocs/direct_link#create-gateway-export-route-filter) or [create an import route filter](/apidocs/direct_link#create-gateway-import-route-filter) API. For example, the following Curl example creates an import route filter:
 
```curl
curl -kX POST "https://directlink.cloud.ibm.com/v1/gateways/9a3eac6d-1951-4696-8eca-8b0198f4ddaf/import_route_filters?version=2023-01-02" -H "Authorization: Bearer $token" -d {
  "action": "permit",
  "ge": 24,
  "le": 32,
  "prefix": "192.168.100.0/24"
}
``` 

For more information about export and import route filters, including Curl, Python, Java, Node, and Go examples, see the [Gateway Export Route Filters](/apidocs/direct_link#list-gateway-export-route-filters) and [Gateway Import Route Filters](/apidocs/direct_link#list-gateway-import-route-filters) API.

## Related links
{: #route-filtering-related}

* [About filtering routes](/docs/dl?topic=dl-filter-routes&interface=ui)
* [Filtering routes using Transit Gateway prefix filtering](/docs/dl?topic=dl-prefix-filtering)
