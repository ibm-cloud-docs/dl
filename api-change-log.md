---

copyright:
  years: 2022, 2025
lastupdated: "2025-06-03"

keywords: direct link api change log

subcollection: dl

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}

# Direct Link API change log
{: #direct-link-api-changelog}

Check back regularly to see what's new with {{site.data.keyword.cloud}} Direct Link API.
{: shortdesc}

## 03 June 2025
{: #dl-june0325}

MACsec support for Direct Link Dedicated

: New commands

   * Get MACsec CAK - `GET /gateways/{id}/macsec/caks/{cak_id}`
   * List MACsec CAKs - `GET /gateways/{id}/macsec/caks`
   * Create MACsec CAK - `POST /gateways/{id}/macsec/caks`
   * Delete MACsec CAK - `DELETE /gateways/{id}/macsec/caks/{cak_id}`
   * Update MACsec CAK - `PATCH /gateways/{id}/macsec/caks/{cak_id}`
   * Set MACsec configuration - `PUT /gateways/{id}/macsec` 
   * Unset MACsec configuration - `DELETE /gateways/{id}/macsec`
   * Get MACsec configuration - `GET /gateways/{id}/macsec`
   * Update MACsec configuration - `PATCH /gateways/{id}/macsec` 

## 07 March 2024
{: #dl-marc0724}

VLAN tagging support for Direct Link Dedicated

: Updated commands

   * Create a dedicated gateway - `POST /gateways`
   * Update a gateway change request - `PATCH /gateways/{id}`

## 06 July 2023
{: #dl-ju0623}

Route report enhancements

: Added advertised routes to verify route filters and AS prepends applied to the Direct Link gateway.

: “AS path” information added to on-premises routes to verify AS prepends.

: Changed commands

   * List route reports - `GET /gateways/{gateway_id}/route_reports`
   * Create a route report - `POST /gateways/{gateway_id}/route_reports`
   * Delete route report - `DELETE /gateways/{gateway_id}/route_reports/{id}`
   * Get a route report - `GET /gateways/{gateway_id}/route_reports/{id}`

## 16 March 2023
{: #dl-march1623}

BGP route filter support
:   New commands: Export route filters

   * List export route filters - `GET /gateways/{gateway_id}/export_route_filters`
   * Create an export route filter - `POST /gateways/{gateway_id}/export_route_filters`
   * Replace existing export route filters - `PUT /gateways/{gateway_id}/export_route_filters`
   * Remove export route filter from Direct Link - `DELETE /gateways/{gateway_id}/export_route_filters/{id}`
   * Retrieves the specified Direct Link export route filter - `GET /gateways/{gateway_id}/export_route_filters/{id}`
   * Updates the specified Direct Link export route filter - `PATCH /gateways/{gateway_id}/export_route_filters/{id}`

:   New commands: Import route filters

   * List import route filters - `GET /gateways/{gateway_id}/import_route_filters`
   * Create an import route filter - `POST /gateways/{gateway_id}/import_route_filters`
   * Replace existing import route filters - `PUT /gateways/{gateway_id}/import_route_filters`
   * Remove import route filter from Direct Link - `DELETE /gateways/{gateway_id}/import_route_filters/{id}`
   * Retrieves the specified Direct Link import route filter - `GET /gateways/{gateway_id}/import_route_filters/{id}`
   * Updates the specified Direct Link import route filter - `PATCH /gateways/{gateway_id}/import_route_filters/{id}`

:   Changed commands

   * Add BGP route filter support during `create_gateway` - Create gateway - `POST /gateways`
   * Add BGP route filter support during `create_gateway_action` - Approve or reject change requests - `POST /gateways/{id}/actions`
   * Add BGP route filter support during `get_gateway` - Get gateway - `GET /gateways/{id}`
   * Add BGP route filter support during `update_gateway` - Update gateway - `PATCH /gateways/{id}`
   * Add BGP route filter support during `list_gateways` - List gateways - `GET /gateways`

## 21 September 2022
{: #dl-septem2122}

Route report support
:   New commands

   * List route reports - `GET /gateways/{gateway_id}/route_reports`
   * Create a route report - `POST /gateways/{gateway_id}/route_reports`
   * Delete route report - `DELETE /gateways/{gateway_id}/route_reports/{id}`
   * Get a route report - `GET /gateways/{gateway_id}/route_reports/{id}`

BGP AS prepends support
:   Changed commands

   * Add AS prepend support during create gateway - `POST /gateways`
   * Add AS prepend support during create gateway approve - `POST gateways/{id}/actions`

## 01 April 2022
{: #dl-april0122}
{: release-note}

Reduced unmetered plan pricing for Direct Link Connect
:   IBM is pleased to announce a significant reduction in unmetered pricing for IBM Cloud Direct Link Connect and Direct Link Dedicated. Direct Link also offers a metered pricing plan, which allows you to switch between metered and unmetered pricing plans to suit your bandwidth usage needs.
