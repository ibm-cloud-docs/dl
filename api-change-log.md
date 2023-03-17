---

copyright:
  years: 2022, 2023
lastupdated: "2022-09-21"

keywords: direct link api change log

subcollection: dl

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}

# Direct Link API change log
{: #direct-link-api-changelog}

Check back regularly to see what's new with {{site.data.keyword.cloud}} Direct Link API.
{: shortdesc}

## 16 March 2023
{: #dl-mar1623}

BGP route filtering support
:   New commands

    Gateway export route filters

   * List export route filters - `GET /gateways/{gateway_id}/export_route_filters`
   * Create an export route filter - `POST /gateways/{gateway_id}/export_route_filters`
   * Replace existing export route filters - `PUT /gateways/{gateway_id}/export_route_filters`
   * Remove export route filter from Direct Link - `DELETE /gateways/{gateway_id}/export_route_filters/{id}`
   * Retrieves the specified Direct Link export route filter - `GET /gateways/{gateway_id}/export_route_filters/{id}`
   * Updates the specified Direct Link export route filter - `PATCH /gateways/{gateway_id}/export_route_filters/{id}`

    Gateway import route filters

   * List import route filters - `GET /gateways/{gateway_id}/import_route_filters`
   * Create an import route filter - `POST /gateways/{gateway_id}/import_route_filters`
   * Replace existing import route filters - `PUT /gateways/{gateway_id}/import_route_filters`
   * Remove import route filter from Direct Link - `DELETE /gateways/{gateway_id}/import_route_filters/{id}`
   * Retrieves the specified Direct Link import route filter - `GET /gateways/{gateway_id}/import_route_filters/{id}`
   * Updates the specified Direct Link import route filter - `PATCH /gateways/{gateway_id}/import_route_filters/{id}`

:   Changed commands

   * Add BGP route filtering support during `create_gateway` - Create gateway - `POST /gateways`
   * Add BGP route filtering support during `create_gateway_action` - Approve or reject change requests - `POST /gateways/{id}/actions`
   * Add BGP route filtering support during `get_gateway` - Get gateway - `GET /gateways/{id}`
   * Add BGP route filtering support during `update_gateway` - Update gateway - `PATCH /gateways/{id}`
   * Add BGP route filtering support during `list_gateways` - List gateways - `GET /gateways`

## 21 September 2022
{: #dl-sept2122}

Route report support
:   New commands

   * List route reports - `GET /gateways/{gateway_id}/route_reports`
   * Create a route report - `POST /gateways/{gateway_id}/route_reports`
   * Delete route report - `DELETE /gateways/{gateway_id}/route_reports/{id}`
   * Get a route report - `GET /gateways/{gateway_id}/route_reports/{id}`
   
BGP AS prepend support
:   Changed commands

   * Add AS prepend support during create gateway - `POST /gateways`
   * Add AS prepend support during create gateway approve - `POST gateways/{id}/actions`

## 01 April 2022
{: #dl-april0122}
{: release-note}

Reduced unmetered plan pricing for Direct Link Connect
:   IBM is pleased to announce _a significant reduction in unmetered pricing_ for IBM Cloud Direct Link Connect and Direct Link Dedicated. Note that Direct Link also offers a metered pricing plan, allowing you to switch between metered and unmetered pricing plans to suit your bandwidth usage needs. For more information, see [Pricing for IBM Cloud Direct Link](/docs/dl?topic=dl-pricing-for-ibm-cloud-dl).

