---

copyright:
  years: 2020, 2025
lastupdated: "2025-06-17"

subcollection: dl

keywords: command line interface, commands, CLI, cli plug-in

---

{{site.data.keyword.attribute-definition-list}}

# Direct Link CLI
{: #dl-cli}

The {{site.data.keyword.dl_full}} command line interface (CLI) is organized into sections, which are listed in the navigation window.
{: shortdesc}

## Before you begin
{: #cli-ref-prereqs}

Complete these steps to use the Direct Link CLI, which is implemented as an {{site.data.keyword.cloud_notm}} CLI plug-in. This plug-in provides you with the means to manage your service instance and its associated resources through a CLI interface.

1. Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli){: external}.
1. Install the `dl-cli` plug-in to the {{site.data.keyword.cloud_notm}} CLI.

   To install the plug-in, enter the following command.

   ```sh
   ibmcloud plugin install dl-cli
   ```
   {: pre}

---

## `ibmcloud plugin show dl-cli`
{: #show-plugin-info}

Show Direct Link CLI plug-in information.

```sh
ibmcloud plugin show dl-cli
```

## `ibmcloud dl --help`
{: #command-help}

Get help on Direct Link commands.

```sh
ibmcloud dl -h|--help
```

## `ibmcloud dl asprepends`
{: #list-all-asprepends}

List all AS prepends on the specified gateway.

```sh
ibmcloud dl asprepends GATEWAY_ID
```

### Command options
{: #command-options-list-all-asprepends}

`GATEWAY_ID`
:   Specify the ID of the gateway. Required.


### Examples
{: #example-list-all-asprepends}

- `ibmcloud dl asprepends 5cc19d0a-792c-4595-adfc-f90fc650de01`
- `ibmcloud dl asps 22f799e8-b4ab-44ca-856b-897be9b0e53d`

## `ibmcloud dl asprepends-replace`
{: #replace-all-asprepends}

Replace all AS prepends on the specified gateway.

```sh
ibmcloud dl asprepends-replace GATEWAY_ID --file JSON_FILE --etag ETAG
```

### Command options
{: #command-options-replace-all-asprepends}

`GATEWAY_ID`
:   Specify the ID of the gateway. Required.

`-file JSON_FILE`
:   JSON file for input data. This file contains the AS prepends to be applied to the gateway.

`--etag ETAG`
:   Etag value for the currently defined AS prepends. This value is returned on `ibmcloud dl asprepends` and the response of the command after you apply the update.

### Examples
{: #example-replace-all-asprepends}

- `ibmcloud dl asprepends-replace 5cc19d0a-792c-4595-adfc-f90fc650de01 --file update.json --etag 'W/\"20-3e8f21374fef9e548af910e4ad4322abe25bfb41\"'`
- `ibmcloud dl aspsr 22f799e8-b4ab-44ca-856b-897be9b0e53d --file update.json --etag 'W/\"20-3e8f21374fef9e5477770e4ad4322abe25bfb41\"'`

## `ibmcloud dl cak`
{: #cak}

View details of a CAK by ID.

```sh
ibmcloud dl cak GATEWAY_ID CAK_ID [-–help|-h] [--output format]
```

### Command options
{: #command-options-cak-details}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`CAK_ID`
:   Specify the ID of the CAK that you want to list.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-cak}

- `ibmcloud dl cak beec5de0-a1c0-4730-8888-2ce4a3020ec8 c3df351b-ff64-4444-ba64-92cb7622dfd6`

## `ibmcloud dl caks`
{: #caks}

List all CAKs.

```sh
ibmcloud dl caks GATEWAY_ID [-–help|-h] [--output format]
```

### Command options
{: #command-options-caks-details}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Example
{: #example-caks}

`ibmcloud dl caks beec5de0-a1c0-4730-8888-2ce4a3020ec8`

## `ibmcloud dl cak-create`
{: #cak-create}

Create a CAK.

```sh
ibmcloud dl cak-create|cakc GATEWAY_ID --name NAME --crn CRN --session primary|fallback [-–help|-h] [--output format]
```

### Command options
{: #command-options-cak-create}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--name NAME`
:   Specify the name of the CAK.

`--crn CRN`
:   Specify CRN of the key.

`--session`
:   Specify the session type of the CAK (`primary` or `fallback`).

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-cak-create}

- `ibmcloud dl cakc dc206f57-5693-442f-8888-6d43b6c82d73 --name 1000 --crn $crn --session primary`

## `ibmcloud dl cak-delete`
{: #cak-delete}

Delete a CAK.

```sh
ibmcloud dl cak-delete|cakd GATEWAY_ID CAK_ID [-–help|-h] [--output format]
```

### Command options
{: #command-options-cak-delete}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`CAK_ID`
:   Specify the ID of the CAK that you want to delete.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-cak-delete}

- `ibmcloud dl cakd beec5de0-a1c0-4730-8888-2ce4a3020ec8 c3df351b-ff64-4444-ba64-92cb7622dfd6`

## `ibmcloud dl cak-update`
{: #cak-update}

Update a CAK. Both the name and CRN values must be updated together.

```sh
ibmcloud dl cak-update|caku GATEWAY_ID CAK_ID --name NAME --crn CRN [-–help|-h] [--output format]
```

### Command options
{: #command-options-cak-update}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`CAK_ID`
:   Specify the ID of the CAK that you want to update.

`--name NAME`
:   Specify the name of the CAK.

`--crn CRN`
:   Specify CRN of the key.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-cak-update}

- `ibmcloud dl caku beec5de0-a1c0-4730-8888-2ce4a3020ec8 c3df351b-ff64-4444-ba64-92cb7622dfd6 --name 2000 -crn $crn2`

## `ibmcloud dl completion-notice`
{: #completion-notice-download}

Download the completion notice for the gateway in either the current working directory or in an output directory path.

```sh
ibmcloud dl completion-notice|cn GATEWAY_ID [--file OUTPUT_DIRECTORY_PATH][--help|-h]
```

### Command options
{: #command-options-completion-notice-download}

`GATEWAY_ID`
:   Specify the ID of the gateway. Required.

`--file OUTPUT_DIRECTORY_PATH`
:   Specify the output directory path where you want to download the completion notice. For example, specify to download the completion notice in the `/tmp` directory.

`--help|-h`
:   Get help on this command.

### Examples
{: #example-completion-notice-download}

- `ibmcloud dl completion-notice 0e28b9bc-06df-44f1-b5d7-08085b9fc935`
- `ibmcloud dl cn 0e28b9bc-06df-44f1-b5d7-08085b9fc935 --file /tmp`

## `ibmcloud dl completion-notice-update`
{: #completion-notice-upload}

Upload the completion notice from either the working directory or a specified directory.

```sh
ibmcloud dl completion-notice-update GATEWAY_ID [-i INPUT_DIRECTORY_PATH]
```

### Command options
{: #command-options-completion-notice-upload}

`GATEWAY_ID`
:   Specify the ID of the gateway. Required.

`-i INPUT_DIRECTORY_PATH`
:   Specify the directory in which you want to upload the completion notice.

### Examples
{: #example-completion-notice-upload}

- `ibmcloud dl completion-notice-update 5cc19d0a-792c-4595-adfc-f90fc650de01`
- `ibmcloud dl cnu 22f799e8-b4ab-44ca-856b-897be9b0e53d -i /tmp/`

## `ibmcloud dl connect-gateway-create`
{: #create-connect-gateway}

Create a Connect gateway.

The `BGP_BASE_CIDR` option is deprecated. Remove this option as it is ignored. See `BGP_CER_CIDR` and `BGP_IBM_CIDR` to create a gateway by using either automatic or explicit IP assignment.
{: deprecated}

```sh
ibmcloud dl connect-gateway-create {--file JSON_FILE | GATEWAY_NAME --billing BILLING --bgp-asn BGP_ASN --port-id PORT_ID --routing ROUTING --speed-mbps SPEED_MBPS [--bfd-interval interval] [--bfd-multiplier multiplier] [--bgp-base-cidr BGP_BASE_CIDR] [--bgp-cer-cidr BGP_CER_CIDR] [--bgp-ibm-cidr BGP_IBM_CIDR] [--connection CONNECTION_TYPE] [--resource-group-id RESOURCE_GROUP_ID]} [--help|-h] [--output format]
```

### Command options
{: #command-options-connect-gateway-create}

`--file JSON_FILE`
:   JSON file for input data. Input method for AS Prepend and Route Filter values. Required or specify `GATEWAY_NAME`.

`GATEWAY_NAME`
:   Specify a name for the new gateway. Required or specify `--file JSON_FILE`.

`--billing BILLING`
:   Billing of resources (`metered` | `non-metered`). Select `metered` to charge per GB and `non-metered` for a flat rate. Required.

`--bgp-asn BGP_ASN`
:   Specify either the default value of `64999`, or select an ASN from allowed ranges. Required.

`--port-id PORT_ID`
:   Port ID for the gateway. Required when type is `connect`. Required.

`--routing ROUTING`
:   Gateway routing of resources (global | local). Select global to connect resources across regions. Required.

`--speed-mbps SPEED_MBPS`
:   Specify a value for the speed. Required.

`--bfd-interval VALUE`
:   Configures the minimum interval (in milliseconds) between the transmitted and received BFD packets. Range [300 - 255000]

`--bfd-multiplier VALUE`
:   The number of BFD packets not received by a neighbor that causes the originating interface to be declared down. Range [1 - 255]

`--bgp-base-cidr BGP_BASE_CIDR`
:   Specify the BGP Base CIDR.

`--bgp-cer-cidr BGP_CER_CIDR`
:   Specify the BGP customer edge router CIDR.

`--bgp-ibm-cidr BGP_IBM_CIDR`
:   Specify the BGP IBM CIDR.

`--connection CONNECTION_TYPE:`
:   Type of network connection that you want to bind to your direct link. One of: `direct`, `transit`.

`--default-export-route-filter VALUE`
:   Default export route filter. One of `permit`, `deny`.

`--default-import-route-filter VALUE`
:   Default import route filter. One of `permit`, `deny`.

`--resource-group-id RESOURCE_GROUP_ID`
:   Resource group ID for this resource. If unspecified, the account's default resource group is used.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

To enable [MD5 authentication for BGP peers](/docs/dl?topic=dl-dl-md5), or create [BGP AS prepends](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link&interface=ui#dl-bgp-path-selection), use the `--file` option to create the gateway as stated in the [template](/apidocs/direct_link#create-gateway).
{: note}

### Examples
{: #example-create-connect-gateway}

- `ibmcloud dl connect-gateway-create dl-gw --billing metered --bgp-asn 64999 --bgp-base-cidr 169.254.0.51/30 --port-id 2f41cf65-e72a-4522-9526-e156e4ca02b5 --routing local --speed-mbps 1000 --bgp-cer-cidr 169.254.0.53/30 --bgp-ibm-cidr 169.254.0.52/30 --connection direct`
- `ibmcloud dl connect-gateway-create dl-gw --billing metered --bgp-asn 64999 --bgp-base-cidr 169.254.0.51/30 --port-id 2f41cf65-e72a-4522-9526-e156e4ca02b5 --routing local --speed-mbps 1000 --bgp-cer-cidr 169.254.0.53/30 --bgp-ibm-cidr 169.254.0.52/30 --output json`
- `ibmcloud dl connect-gateway-create --file ~/gateway.json`

## `ibmcloud dl dedicated-gateway-create`
{: #create-dedicated-gateway}

Create a dedicated gateway.

The `BGP_BASE_CIDR` option is deprecated. Remove this option as it is ignored. See `BGP_CER_CIDR` and `BGP_IBM_CIDR` to create a gateway by using either automatic or explicit IP assignment.
{: deprecated}

```sh
ibmcloud dl dedicated-gateway-create {--file JSON_FILE | GATEWAY_NAME --billing BILLING --bgp-asn BGP_ASN --carrier-name CARRIER_NAME --ccr CROSS_CONNECT_ROUTER --customer-name CUSTOMER_NAME --location-name LOCATION_NAME --routing ROUTING --speed-mbps SPEED_MBPS [--bfd-interval interval] [--bfd-multiplier multiplier] [--bgp-base-cidr BGP_BASE_CIDR] [--bgp-cer-cidr BGP_CER_CIDR] [--bgp-ibm-cidr BGP_IBM_CIDR] [-vlan VLAN] [--connection CONNECTION_TYPE] [--resource-group-id RESOURCE_GROUP_ID]} [--output format]
```

### Command options
{: #command-options-dedicated-gateway-create}

`GATEWAY_NAME`
:   Specify a name for the new gateway.

`--file VALUE`
:   JSON file for input data. Input method for AS Prepend and Route Filter values.

`--bfd-interval VALUE`
:   Configures the minimum interval (in milliseconds) between the transmitted and received BFD packets. Range [300 - 255000]

`--bfd-multiplier VALUE`
:   The number of BFD packets not received by a neighbor that causes the originating interface to be declared down. Range [1 - 255]

`--bgp-asn VALUE`
:   Specify either the default value of `64999`, or select an ASN from allowed ranges.

`--bgp-base-cidr BGP_BASE_CIDR`
:   Specify the BGP Base CIDR.

`--bgp-cer-cidr BGP_CER_CIDR`
:   Specify the BGP customer edge router CIDR.

`--bgp-ibm-cidr BGP_IBM_CIDR`
:   Specify the BGP IBM CIDR.

`--billing VALUE`
:   Billing of resources (`metered` | `non-metered`). Select `metered` to charge per GB and `non-metered` for a flat rate.

`--carrier-name VALUE`
:   Specify the gateway CARRIER NAME.

`--connection VALUE`
:   Type of network connection that you want to bind to your direct link. One of: `direct`, `transit`.

`--ccr XCR`
:   Select the IBM cross-connect router for the Direct Link connection.

`--customer-name VALUE`
:   Specify the gateway CUSTOMER NAME.

`--default-export-route-filter VALUE`
:   Default export route filter. One of `permit`, `deny`.

`--default-import-route-filter VALUE`
:   Default import route filter. One of `permit`, `deny`.

`--location-name LOCATION`
:   Specify the location name; for example, `dal10`.

`--resource-group-id VALUE`
:   Resource group ID for this resource. If unspecified, the account's default resource group is used.

`--routing VALUE`
:   Gateway routing of resources (`global` | `local`). Select `global` to connect resources across regions.

`--speed-mbps SPEED_MBPS`
:   Specify a value for the speed.

`--vlan VLAN`
:   Specify the VLAN number. Range [`2`-`3967`]. Use `null` to reset.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

To create a MACsec-enabled gateway, enable [MD5 authentication for BGP peers](/docs/dl?topic=dl-dl-md5), or create [BGP AS prepends](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link&interface=ui#dl-bgp-path-selection), use the `--file` option to create the gateway as stated in the [template](/apidocs/direct_link#create-gateway).
{: note}

### Examples
{: #example-create-dedicated-gateway}

- `ibmcloud dl dedicated-gateway-create dl-gw --billing metered --bgp-asn 64999 --bgp-base-cidr 169.254.0.51/30 --carrier-name carrier --ccr LAB-xcr01.dal09 --customer-name customer --location-name dal09 --routing local --speed-mbps 1000 --bgp-ibm-cidr 169.254.0.52/30 --bgp-cer-cidr 169.254.0.53/30 --vlan 10 --connection direct`
- `ibmcloud dl dedicated-gateway-create dl-gw --billing metered --bgp-asn 64999 --bgp-base-cidr 169.254.0.51/30 --carrier-name carrier --ccr LAB-xcr01.dal09 --customer-name customer --location-name dal09 --routing local --speed-mbps 1000 --bgp-ibm-cidr 169.254.0.52/30 --bgp-cer-cidr 169.254.0.53/30 --output json`
- `ibmcloud dl dedicated-gateway-create --file ~/gateway.json`

## `ibmcloud dl export-route-filter`
{: #export-route-filter}

View details of an export route filter by ID.

```sh
ibmcloud dl export-route-filter|erf GATEWAY_ID FILTER_ID [-–help|-h] [--output format]
```

### Command options
{: #command-options-export-route-filter-details}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`FILTER_ID`
:   Specify the ID of the export route filter that you want to list.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-exportroutefilter}

- `ibmcloud dl erf beec5de0-a1c0-4730-8888-2ce4a3020ec8 c3df351b-ff64-4444-ba64-92cb7622dfd6`

## `ibmcloud dl export-route-filters`
{: #export-route-filters}

List all export route filters.

```sh
ibmcloud dl export-route-filters|erfs GATEWAY_ID [-–help|-h] [--output format]
```

### Command options
{: #command-options-export-route-filters-details}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Example
{: #example-exportroutefilters}

`ibmcloud dl erfs beec5de0-a1c0-4730-8888-2ce4a3020ec8`

## `ibmcloud dl export-route-filter-create`
{: #export-route-filter-create}

Create an export route filter.

```sh
ibmcloud dl export-route-filter-create|erfc GATEWAY_ID --action ACTION --prefix PREFIX [--before BEFORE] [--ge GE] [--le LE] [-–help|-h] [--output format]
```

### Command options
{: #command-options-export-route-filter-create}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--action ACTION`
:   Specify the action for the export route filter. One of `permit`, `deny`.

`--prefix PREFIX`
:   Specify an IPv4 subnet CIDR indicating both the address and mask length.

`--before BEFORE`
:   To prioritize this filter in the export route filter list, specify the ID of the route filter that comes before this filter.

`--ge GE`
:   Specify a minimum matching length (GE, greater than or equal to). For more information, see [About route filtering](/docs/dl?topic=dl-filter-routes&interface=ui).

`--le LE`
:   Specify a maximum matching length (LE, less than or equal to). For more information, see [About route filtering](/docs/dl?topic=dl-filter-routes&interface=ui).

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-exportroutefilter-create}

- `ibmcloud dl erfc dc206f57-5693-442f-8888-6d43b6c82d73 --action permit --prefix 10.10.0.0/24`
- `ibmcloud dl erfc dc206f57-5693-442f-8888-6d43b6c82d73 --action deny --prefix 10.10.0.0/24 -le 29`

## `ibmcloud dl export-route-filter-delete`
{: #export-route-filter-delete}

Delete an export route filter.

```sh
ibmcloud dl export-route-filter-delete|erfd GATEWAY_ID FILTER_ID [-–help|-h] [--output format]
```

### Command options
{: #command-options-export-route-filter-delete}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`FILTER_ID`
:   Specify the ID of the export route filter that you want to delete.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-exportroutefilter-delete}

- `ibmcloud dl erfd beec5de0-a1c0-4730-8888-2ce4a3020ec8 c3df351b-ff64-4444-ba64-92cb7622dfd6`

## `ibmcloud dl export-route-filter-replace`
{: #export-route-filter-replace}

Replace all export route filters.

```sh
ibmcloud dl export-route-filter-replace|erfr GATEWAY_ID --file JSON_FILE --etag ETAG [-–help|-h] [--output format]
```

### Command options
{: #command-options-export-route-filter-replace}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--file JSON_FILE`
:   Specify the JSON file for input data.

`--etag ETAG`
:   Specify the eTag.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Example
{: #example-exportroutefilter-replace}

`ibmcloud dl erfr 58e4f46f-0dab-4025-9999-3df974db0618 --etag 'W/"182-9c1ba4f4ab697f4080f662c18e664d5763ae4b8dcb0542b4b473d661"' --file ~/export.txt`

## `ibmcloud dl export-route-filter-update`
{: #export-route-filter-update}

Update an export route filter.

```sh
ibmcloud dl export-route-filter-update|erfu GATEWAY_ID FILTER_ID [--action ACTION] [--prefix PREFIX] [--before BEFORE] [--ge GE] [--le LE] [-–help|-h] [--output format]
```

### Command options
{: #command-options-export-route-filter-update}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`FILTER_ID`
:   Specify the ID of the export route filter that you want to update.

`--action ACTION`
:   Specify the action of the export route filter. One of `permit`, `deny`.

`--prefix PREFIX`
:   Specify an IPv4 subnet CIDR indicating both the address and mask length.

`--before BEFORE`
:   To prioritize this filter in the export route filter list, specify the ID of the route filter that comes before this filter.

`--ge GE`
:   Specify a minimum matching length (GE, greater than or equal to). For more information, see [About route filtering](/docs/dl?topic=dl-filter-routes&interface=ui).

`--le LE`
:   Specify a maximum matching length (LE, less than or equal to). For more information, see [About route filtering](/docs/dl?topic=dl-filter-routes&interface=ui).

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-exportroutefilter-update}

- `ibmcloud dl erfu beec5de0-a1c0-4730-8888-2ce4a3020ec8 c3df351b-ff64-4444-ba64-92cb7622dfd6 --action permit`
- `ibmcloud dl erfu beec5de0-a1c0-4730-8888-2ce4a3020ec8 c3df351b-ff64-4444-ba64-92cb7622dfd6 --le 28`

## `ibmcloud dl gateway`
{: #get-help-specific-gateway}

View details of a specific gateway.

```sh
ibmcloud dl gateway|gw GATEWAY_ID [-–help|-h] [--output format]
```

### Command options
{: #command-options-gateway-view-details}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-get-gateway}

- `ibmcloud dl gateway a771366f-2c8c-49f6-a23b-9d49fad035a3`
- `ibmcloud dl gw a771366f-2c8c-49f6-a23b-9d49fad035a3 --output json`

## `ibmcloud dl gateway-change-approve`
{: #gateway-change-approve-cmd}

Approve gateway change request.

```sh
ibmcloud dl gateway-change-approve GATEWAY_ID {--file JSON_FILE | [--action Action] [--bfd-interval interval] [--bfd-multiplier multiplier] [--bgp-asn BGP_ASN] [--bgp-cer-cidr BGP_CER_CIDR] [--bgp-ibm-cidr BGP_IBM_CIDR] [--billing BILLING] [--connection CONNECTION_TYPE] [--resource-group-id RESOURCE_GROUP_ID] [--routing ROUTING] [--speed-mbps SPEED_MBPS] [--vlan VLAN]} [--output format]
```

### Command options
{: #command-options-gateway-change-approval}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--file VALUE`
:   JSON file for input data. Input method for AS Prepend values.

`--action ACTION`
:   Action request. One of: `gateway-create`, `gateway-delete`, `gateway-attribute-update`.

`--bfd-interval VALUE`
:   Configures the minimum interval (in milliseconds) between the transmitted and received BFD packets. Range [300 - 255000]

`--bfd-multiplier VALUE`
:   The number of BFD packets not received by a neighbor that causes the originating interface to be declared down. Range [1 - 255]

`--bgp-asn VALUE`
:   Gateway BGP-ASN. Excluded ASNs: 0, 13884, 36351, 64512, 64513, 65100, 65201‍–‍65234, 65402‍–‍65433, 65500, and 4201065000‍–‍4201065999

`--bgp-cer-cidr VALUE`
:   BGP customer edge router CIDR

`--bgp-ibm-cidr VALUE`
:   BGP IBM CIDR

`--billing VALUE`
:   Billing (`metered` | `non-metered`). Select `metered` to charge per GB and `non-metered` for a flat rate. Set for gateway-create requests to select the gateway's metered billing option.

`-connection VALUE`
:   Type of network connection that you want to bind to your direct link. One of: `direct`, `transit`.

`--resource-group-id VALUE`
:   Resource group ID for this resource. Set for gateway-create requests to select the gateway's resource group.

`--routing ROUTING`
:   Gateway routing (`global` | `local`). Select `global` to connect resources across regions. Set for gateway-create requests to select the gateway's routing option.

`--speed-mbps SPEED_MBPS`
:   Speed of the gateway in Mbps.

`--vlan VALUE`
:   Gateway VLAN ID

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

`--help|-h`
:   Get help on this command.

To approve the provider-created gateways with [MD5 authentication for BGP peers](/docs/dl?topic=dl-dl-md5), or create [BGP AS prepends](/docs/dl?topic=dl-models-for-diversity-and-redundancy-in-direct-link&interface=ui#dl-bgp-path-selection), use the `-file` option to approve the gateway as stated in the [template](/apidocs/direct_link#create-gateway-action).
{: note}

### Examples
{: #example-gateway-change-approve-ex}

- `ibmcloud dl gateway-change-approve a771366f-2c8c-49f6-a23b-9d49fad035a3 --action gateway-create --routing global --billing metered`
- `ibmcloud dl gateway-change-approve a771366f-2c8c-49f6-a23b-9d49fad035a3 --action gateway-create --routing global --billing metered --connection direct --output json`

## `ibmcloud dl gateway-change-reject`
{: #gateway-change-reject}

Reject gateway change request.

```sh
ibmcloud dl gateway-change-reject|gwcr GATEWAY_ID [--action Action] [--bgp-asn BGP_ASN] [--bgp-cer-cidr BGP_CER_CIDR] [--bgp-ibm-cidr BGP_IBM_CID] [--speed-mbps SPEED_MBPS] [--vlan VLAN] [--output format]
```

### Command options
{: #command-options-gateway-change-approve-parms}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--action ACTION`
:   Action request. One of: `gateway-create`, `gateway-delete`, `gateway-attribute-update`.

`--bgp-asn VALUE`
:   Gateway BGP-ASN. Excluded ASNs: 0, 13884, 36351, 64512, 64513, 65100, 65201‍–‍65234, 65402‍–‍65433, 65500, and 4201065000‍–‍4201065999

`--bgp-cer-cidr VALUE`
:   BGP customer edge router CIDR

`--bgp-ibm-cidr VALUE`
:   BGP IBM CIDR

`--speed-mbps SPEED_MBPS`
:   Speed of the gateway in Mbps.

`--vlan VLAN`
:   Gateway VLAN ID

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

`--help|-h`
:   Get help on this command.

### Examples
{: #example-gateway-change-reject}

- `ibmcloud dl gateway-change-reject a771366f-2c8c-49f6-a23b-9d49fad035a3 --action gateway-create`
- `ibmcloud dl gateway-change-reject a771366f-2c8c-49f6-a23b-9d49fad035a3 --action gateway-create --output json`

## `ibmcloud dl gateway-create`
{: #create-gateway}

Create a gateway.

This command is deprecated. See [connect-gateway-create](/docs/dl?topic=dl-dl-cli&interface=ui#create-connect-gateway) and [dedicated-gateway-create](/docs/dl?topic=dl-dl-cli&interface=ui#create-dedicated-gateway) for creating Connect and Dedicated gateways.
{: deprecated}

The `BGP_BASE_CIDR` option is deprecated. Remove this option as it is ignored. See `BGP_CER_CIDR` and `BGP_IBM_CIDR` to create a gateway by using either automatic or explicit IP assignment.
{: deprecated}

```sh
ibmcloud dl gateway-create|gwc GATEWAY_NAME --billing BILLING --bgp-asn BGP_ASN  --bgp-base-cidr BGP_BASE_CIDR --routing ROUTING --speed-mbps SPEED_MBPS --type TYPE [--bgp-cer-cidr BGP_CER_CIDR] [--bgp-ibm-cidr BGP_IBM_CIDR] [--carrier-name CARRIER_NAME] [--cross-connect-router CROSS_CONNECT_ROUTER] [--customer-name CUSTOMER_NAME] [--location-name LOCATION_NAME] [--port-id PORT_ID] [--resource-group-id RESOURCE_GROUP_ID] [-–help|-h] [--output format]
```

### Command options
{: #command-options-gateway-create}

`GATEWAY_NAME`
:   Specify a name for the new gateway.

`--billing VALUE`
:   Billing of resources (metered | nonmetered). Select metered to charge per gigabyte and nonmetered for flat rate.

`--bgp-asn VALUE`
:   Specify either the default value of `64999`, or select an ASN from allowed ranges.

`--bgp-base-cidr BGP_BASE_CIDR`
:   Specify the BGP Base CIDR.

`--bgp-cer-cidr BGP_CER_CIDR`
:   Specify the BGP customer edge router CIDR.

`--bgp-ibm-cidr BGP_IBM_CIDR`
:   Specify the BGP IBM CIDR.

`--carrier-name VALUE`
:   Specify the gateway carrier name.

`--cross-connect-router XCR`
:   Select the IBM cross-connect router for the Direct Link connection.

`--customer-name VALUE`
:   Specify the gateway customer name.

`--location-name LOCATION`
:   Specify the location name; for example, `dal10`.

`--port-id`
:   Port ID for the gateway. Required when type is `connect`.

`--resource-group-id VALUE`
:   Resource group ID for this resource. If unspecified, the account's default resource group is used.

`--routing VALUE`
:   Gateway routing of resources (`global | local`). Select global to connect resources across regions.

`--speed-mbps SPEED_MBPS`
:   Specify a value for the speed.

`--type TYPE`
:   Specify the Direct Link offering type. One of: `dedicated`, `connect`.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-create-gateway}

- `ibmcloud dl gateway-create dl-gw --bgp-asn 64999 --cross-connect-router LAB-xcr01.dal09 --routing local --billing metered --location-name dal09 --speed-mbps 1000 --type dedicated --bgp-base-cidr 169.254.0.51/30 --bgp-ibm-cidr 169.254.0.52/30 --bgp-cer-cidr 169.254.0.53/30`
- `ibmcloud dl gateway-create dl-gw --bgp-asn 64999 --cross-connect-router LAB-xcr01.dal09 --routing local --billing metered --location-name dal09 --speed-mbps 1000 --type dedicated --bgp-base-cidr 169.254.0.51/30 --bgp-ibm-cidr 169.254.0.52/30 --bgp-cer-cidr 169.254.0.53/30 --output json`

## `ibmcloud dl gateway-delete`
{: #delete-gateway}

Delete a specific gateway.

```sh
ibmcloud dl gateway-delete|gwd GATEWAY_ID [--help|-h] [--force|-f]
```

### Command options
{: #command-options-gateway-delete}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--help|-h`
:   Get help on this command.

`--force|-f`
:   Force the delete operation without confirmation.

### Examples
{: #example-delete-gateway1}

- `ibmcloud dl gateway-delete e281b18b-0dba-49ee-9c64-aea588b7f1fd`
- `ibmcloud dl gateway-delete 8ba9e7b0-dded-400e-ad7e-6481dad0b157 -f`

## `ibmcloud dl gateway-statistics`
{: #gateway-statistics}

Fetch the statistics for a specific gateway.

```sh
ibmcloud dl gateway-statistics|gw-stats GATEWAY_ID --type STATISTIC_TYPE [--help|-h]
```

### Command options
{: #command-options-gateway-stats}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`type VALUE`
:   Type of the statistics to retrieve. One of: `macsec_mka_session`, `macsec_policy`, `macsec_mka_statistics`, `bfd_session`.

`--help|-h`
:   Get help on this command.

### Example
{: #example-gateway1-stats}

`ibmcloud dl gateway-statistics e281b18b-0dba-49ee-9c64-aea588b7f1fd --type macsec_mka_session`

## `ibmcloud dl gateway-status`
{: #gateway-status}

Retrieve gateway status

```sh
ibmcloud dl gateway-status GATEWAY_ID --type STATUS_TYPE [--output format] [--help|-h]
```

### Command options
{: #command-options-gateway-statistics}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--type VALUE`
:   Specify the status to retrieve. One of `bgp`|`bfd`|`link`.

`--output VALUE`
:   Specify the output format. Only JSON is supported.

`--help|-h`
:   Get help on this command.

### Example
{: #example-gateway1-statistics}

`ibmcloud dl gateway-statistics e281b18b-0dba-49ee-9c64-aea588b7f1fd --type macsec_mka_session`

## `ibmcloud dl gateway-update`
{: #update-gateway}

Update a specific gateway.

```sh
ibmcloud dl gateway-update GATEWAY_ID {--file JSON_FILE | [--bfd-interval interval] [--bfd-multiplier multiplier] [--bgp-asn BGP_ASN] [--bgp-cer-cidr BGP_CER_CIDR] [--bgp-ibm-cidr BGP_IBM_CIDR] [--billing BILLING] [--connection CONNECTION_TYPE]  [--default-export-route-filter DEFAULT_ACTION] [--default-import-route-filter DEFAULT_ACTION] [--loa-reject-reason LOA_REJECT_REASON] [--name NAME] [--operational-status OPERATION_STATUS] [--routing ROUTING] [--speed-mbps SPEED_MBPS]} [--vlan VLAN] [--clear-vlan VALUE] [--output format]
```

### Command options
{: #command-options-specific-gateway}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--file VALUE`
:   JSON file for input data.

`--bfd-interval VALUE`
:   Configures the minimum interval (in milliseconds) between the transmitted and received BFD packets. Range [300 - 255000]

`--bfd-multiplier VALUE`
:   The number of BFD packets not received by a neighbor that causes the originating interface to be declared down. Range [1 - 255]

`--bgp-asn VALUE`
:   Gateway BGP-ASN. Excluded ASNs: 0, 13884, 36351, 64512, 64513, 65100, 65201‍–‍65234, 65402‍–‍65433, 65500, and 4201065000‍–‍4201065999

`--bgp-cer-cidr VALUE`
:   BGP customer edge router CIDR.

`--bgp-ibm-cidr VALUE`
:   BGP IBM CIDR.

`--billing VALUE`
:   Billing of resources (`metered` | `non-metered`). Select `metered` to charge per GB and `non-metered` for a flat rate.

`--connection VALUE`
:   Type of network connection that you want to bind to your direct link. One of: `direct`, `transit`.

`--default-export-route-filter VALUE`
:   Default export route filter. One of:`permit`, `deny`.

`--default-import-route-filter VALUE`
:   Default import route filter. One of:`permit`, `deny`.

`--loa-reject-reason LOA_REJECT_REASON`
:   Specify the reason for the Letter of Authorization (LOA) rejection.

`--name NAME`
:   Name of the gateway.

`--operational-status OPERATIONAL_STATUS`
:   Specify the gateway's operational status. Values are `loa_accepted` or `loa_rejected`.

`--routing VALUE`
:   Gateway routing of resources (`global` | `local`). Select `global` to connect resources across regions.

`--speed-mbps SPEED_MBPS`
:   Specify the speed of the gateway in Mbps.

`--vlan VALUE`
:   Specify the VLAN number. Range [`2`-`3967`]. Use `null` to reset. The gateway must have a `type` of `dedicated`. Optional.

`--clear-vlan`
:   Clear the mapped VLAN from the Dedicated gateway.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

To clear/update the [MD5 authentication for BGP peers](/docs/dl?topic=dl-dl-md5), use the `--file` option to update the gateway as stated in the [template](/apidocs/direct_link#update-gateway).
{: note}

### Examples
{: #example-update-gateway1}

- `ibmcloud dl gateway-update 8ba9e7b0-dded-400e-ad7e-6481dad0b157 --speed-mbps 5000 --vlan 99 --name dl-gw-updated`
- `ibmcloud dl gateway-update 8ba9e7b0-dded-400e-ad7e-6481dad0b157 --speed-mbps 5000 --vlan null --name dl-gw-updated --output json`
- `ibmcloud dl gateway-update 8ba9e7b0-dded-400e-ad7e-6481dad0b157 --connection transit --output json`
- `ibmcloud dl gateway-update 8ba9e7b0-dded-400e-ad7e-6481dad0b157 --file ~/gateway-update.json`

## `ibmcloud dl gateways`
{: #list-all-gateways}

List all gateways.

```sh
ibmcloud dl gateways|gws [-–help|-h] [--output format]
```

### Command options
{: #command-options-help-list-gateways}

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

## `ibmcloud dl import-route-filter`
{: #import-route-filter}

View details of an import route filter by ID.

```sh
ibmcloud dl import-route-filter|irf GATEWAY_ID FILTER_ID [-–help|-h] [--output format]
```

### Command options
{: #command-options-import-route-filter-details}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`FILTER_ID`
:   Specify the ID of the import route filter that you want to list.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Example
{: #example-importroutefilter}

`ibmcloud dl irf beec5de0-a1c0-4730-8888-2ce4a3020ec8 c3df351b-ff64-4444-ba64-92cb7622dfd6`

## `ibmcloud dl import-route-filters`
{: #import-route-filters}

List all import route filters.

```sh
ibmcloud dl import-route-filters|irfs GATEWAY_ID [-–help|-h] [--output format]
```

### Command options
{: #command-options-import-route-filters-details}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Example
{: #example-importroutefilters}

`ibmcloud dl irfs beec5de0-a1c0-4730-8888-2ce4a3020ec8`

## `ibmcloud dl import-route-filter-create`
{: #import-route-filter-create}

Create an import route filter.

```sh
ibmcloud dl import-route-filter-create|irfc GATEWAY_ID --action ACTION --prefix PREFIX [--before BEFORE] [--ge GE] [--le LE] [-–help|-h] [--output format]
```

### Command options
{: #command-options-import-route-filter-create}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--action ACTION`
:   Specify the action of the import route filter. One of `permit`, `deny`.

`--prefix PREFIX`
:   Specify an IPv4 subnet CIDR indicating both the address and mask length.

`--before BEFORE`
:   To prioritize this filter in the import route filter list, specify the ID of the route filter that comes before this filter.

`--ge GE`
:   Specify a minimum matching length (GE, greater than or equal to). For more information, see [About route filtering](/docs/dl?topic=dl-filter-routes&interface=ui).

`--le LE`
:   Specify a maximum matching length (LE, less than or equal to). For more information, see [About route filtering](/docs/dl?topic=dl-filter-routes&interface=ui).

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-importroutefilter-create}

- `ibmcloud dl irfc dc206f57-5693-442f-8888-6d43b6c82d73 --action permit --prefix 10.10.0.0/24`
- `ibmcloud dl irfc dc206f57-5693-442f-8888-6d43b6c82d73 --action deny --prefix 10.10.0.0/24 -le 29`

## `ibmcloud dl import-route-filter-delete`
{: #import-route-filter-delete}

Import an export route filter.

```sh
ibmcloud dl import-route-filter-delete|irfd GATEWAY_ID FILTER_ID [-–help|-h] [--output format]
```

### Command options
{: #command-options-import-route-filter-delete}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`FILTER_ID`
:   Specify the ID of the import route filter that you want to delete.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Example
{: #example-importroutefilter-delete}

`ibmcloud dl irfd beec5de0-a1c0-4730-8888-2ce4a3020ec8 c3df351b-ff64-4444-ba64-92cb7622dfd6`

## `ibmcloud dl import-route-filter-replace`
{: #import-route-filter-replace}

Replace all import route filters.

```sh
ibmcloud dl import-route-filter-replace|irfr GATEWAY_ID --file JSON_FILE --etag ETAG [-–help|-h] [--output format]
```

### Command options
{: #command-options-import-route-filter-replace}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--file JSON_FILE`
:   Specify the JSON file for input data.

`--etag ETAG`
:   Specify the eTag.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Example
{: #example-importroutefilter-replace}

`ibmcloud dl irfr 58e4f46f-0dab-4025-9999-3df974db0618 --etag 'W/"182-9c1ba4f4ab697f4080f662c18e664d5763ae4b8dcb0542b4b473d661"' --file ~/import.txt`

## `ibmcloud dl import-route-filter-update`
{: #import-route-filter-update}

Update an import route filter.

```sh
ibmcloud dl import-route-filter-update|irfu GATEWAY_ID FILTER_ID [--action ACTION] [--prefix PREFIX] [--before BEFORE] [--ge GE] [--le LE] [-–help|-h] [--output format]
```

### Command options
{: #command-options-import-route-filter-update}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`FILTER_ID`
:   Specify the ID of the import route filter that you want to update.

`--action ACTION`
:   Specify the action of the import route filter. One of `permit`, `deny`.

`--prefix PREFIX`
:   Specify an IPv4 subnet CIDR indicating both the address and mask length.

`--before BEFORE`
:   To prioritize this filter in the import route filter list, specify the ID of the route filter that comes before this filter.

`--ge GE`
:   Specify a minimum matching length (GE, greater than or equal to). For more information, see [About route filtering](/docs/dl?topic=dl-filter-routes&interface=ui).

`--le LE`
:   Specify a maximum matching length (LE, less than or equal to). For more information, see [About route filtering](/docs/dl?topic=dl-filter-routes&interface=ui).

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-importroutefilter-update}

- `ibmcloud dl irfu beec5de0-a1c0-4730-8888-2ce4a3020ec8 c3df351b-ff64-4444-ba64-92cb7622dfd6 --action permit`
- `ibmcloud dl irfu beec5de0-a1c0-4730-8888-2ce4a3020ec8 c3df351b-ff64-4444-ba64-92cb7622dfd6 --le 28`

## `ibmcloud dl loa`
{: #loa-download}

Download the LOA for the gateway in either the current working directory or in the specified directory.

```sh
ibmcloud dl loa GATEWAY_ID [--file OUTPUT_DIRECTORY_PATH] [--help|-h]
```

### Command options
{: #command-options-loa-download}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--file OUTPUT_DIRECTORY_PATH`
:   Specify the output directory path. For example, specify to download the LOA in the `/tmp` directory.

`--help|-h`
:   Get help on this command.

### Examples
{: #example-loa-download}

- `ibmcloud dl loa 5cc19d0a-792c-4595-adfc-f90fc650de01`
- `ibmcloud dl loa 5cc19d0a-792c-4595-adfc-f90fc650de01 --file /tmp`

## `ibmcloud dl location`
{: #location-retrieve}

Retrieves location-specific information for a specific offering type.

```sh
ibmcloud dl location|loc LOCATION_NAME OFFERING_TYPE [--help|-h] [--output format]
```

### Command options
{: #command-options-location}

`LOCATION_NAME`
:   Specify the name of the location.

`OFFERING_TYPE`
:   Specify the Direct Link offering type. Currently only `dedicated` is supported.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-update-location}

- `ibmcloud dl location "Washington 2" dedicated`
- `ibmcloud dl loc "Washington 2" dedicated --output json`

## `ibmcloud dl locations`
{: #list-locations-offering-type-json}

List the locations for a specific Direct Link offering type.

```sh
ibmcloud dl locations|locs OFFERING_TYPE [–-output format] [--help|-h]
```

### Command options
{: #command-options-locations-offering_type}

`OFFERING_TYPE`
:   Specify the Direct Link offering type. Values are `dedicated` or `connect`.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

`--help|-h`
:   Get help on this command.

### Examples
{: #example-locations-offering-type}

- `ibmcloud dl locations dedicated`
- `ibmcloud dl locs dedicated --output json`

## `ibmcloud dl macsec`
{: #macsec}

View details of the MACsec configuration.

```sh
ibmcloud dl macsec|mac GATEWAY_ID [-–help|-h] [--output format]
```

### Command options
{: #command-options-masec}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-macsec}

- `ibmcloud dl mac beec5de0-a1c0-4730-8888-2ce4a3020ec8`

## `ibmcloud dl macsec-set`
{: #macsec-set}

Set the MACsec configuration.

```sh
ibmcloud dl macsec-set|macst GATEWAY_ID --file JSON_FILE [--etag ETAG] [-–help|-h] [--output format]
```

### Command options
{: #command-options-macsec-set}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--file JSON_FILE`
:   Specify the JSON file for input data.

`--etag ETAG`
:   Specify the eTag.  ETag is required when there is an existing macsec configuration being replaced.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-macsec-set}

- `ibmcloud dl macsec-set 58e4f46f-0dab-4025-9999-3df974db0618 --etag 'W/"182-9c1ba4f4ab697f4080f662c18e664d5763ae4b8dcb0542b4b473d661"' --file ~/macsec.txt`

## `ibmcloud dl macsec-unset`
{: #macsec-unset}

Remove the macsec configuration.

```sh
ibmcloud dl macsec-unset|macun GATEWAY_ID [--force] [-–help|-h] [--output format]
```

### Command options
{: #command-options-macsec-unset}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--force`
:   Force removal without confirmation dialog.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-macsec-unset}

- `ibmcloud dl macsec-unset beec5de0-a1c0-4730-8888-2ce4a3020ec8`

## `ibmcloud dl macsec-update`
{: #macsec-update}

Update the MACsec configuration.

```sh
ibmcloud dl macsec-update|caku GATEWAY_ID [--active true|false] [--sakrekey-mode MODE] [--sakrekey-interval INTERVAL] [--security-policy POLICY] [--window-size SIZE] [-–help|-h] [--output format]
```

### Command options
{: #command-options-macsec-update}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`CAK_ID`
:   Specify the ID of the CAK that you want to update.

`--active ACTIVE`
:   Specify if MACsec should be active. [`true`|`false`]

`--sakrekey-mode MODE`
:   Specify SAK rekey mode to be used. [`timer`|`packet_number_rollover`]

`--sakrekey-interval INTERVAL`
:   When SAK rekey mode is timer, interval value is used.

`--security-policy POLICY`
:   Specify MACsec security policy. [`must_secure`|`should_secure`]

`--window-size SIZE`
:   Specify window size to be used.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-macsec-update}

- `ibmcloud dl macu beec5de0-a1c0-4730-8888-2ce4a3020ec8 --size 128`
- `ibmcloud dl macu beec5de0-a1c0-4730-8888-2ce4a3020ec8 --active false`

## `ibmcloud dl offering-speeds`
{: #offering-speeds-list}

Lists all offering speeds for an offering type.

```sh
ibmcloud dl offering-speeds|ospeeds OFFERING_TYPE [--output format] [--help|-h]
```

### Command options
{: #command-options-offering-speeds-type}

`OFFERING_TYPE`
:   Specify the Direct Link offering type. Values are `dedicated` or `dedicated_hosting`.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

`--help|-h`
:   Get help on this command.

### Examples
{: #example-offering-type}

- `ibmcloud dl offering-speeds dedicated`
- `ibmcloud dl ospeeds dedicated_hosting --output json`

## `ibmcloud dl port`
{: #port-retrieve}

View details of a port.

```sh
ibmcloud dl port PORT_ID [--help|-h] [--output format]
```

### Command options
{: #command-options-port}

`PORT_ID`
:   Specify the ID of the port.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-get-port}

- `ibmcloud dl port a771366f-2c8c-49f6-a23b-9d49fad035a3`
- `ibmcloud dl port a771366f-2c8c-49f6-a23b-9d49fad035a3 --output json`

## `ibmcloud dl ports`
{: #list-all-ports}

List all ports.

```sh
ibmcloud dl ports [--help|-h] [--output format]
```

### Command options
{: #command-options-ports}

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-list-ports}

- `ibmcloud dl ports`
- `ibmcloud dl ports --output json`

## `ibmcloud dl route-report`
{: #route-report-view}

View details of a route report.

```sh
ibmcloud dl route-report|rr GATEWAY_ID REPORT_ID [--output format] [--help|-h]
```

### Command options
{: #command-options-view-details-route-report}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`REPORT_ID`
:   Specify the ID of the route report ID.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

`--help|-h`
:   Get help on this command.

### Examples
{: #example-show-details-route-report}

- `ibmcloud dl route-report a771366f-2c8c-49f6-a23b-9d49fad035a3 dea35ba0-7323-4d8d-9c8d-d7ecda55e23d`
- `ibmcloud dl rr a771366f-2c8c-49f6-a23b-9d49fad035a3 dea35ba0-7323-4d8d-9c8d-d7ecda55e23d --output json`

## `ibmcloud dl route-report-create`
{: #route-report-create-view}

Create a route report.

```sh
ibmcloud dl route-report-create|rrc GATEWAY_ID [--output format] [--help|-h]
```

### Command options
{: #command-options-create-route-report}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

`--help|-h`
:   Get help on this command.

### Examples
{: #example-create-route-report}

- `ibmcloud dl route-report-create a771366f-2c8c-49f6-a23b-9d49fad035a3`
- `ibmcloud dl rrc a771366f-2c8c-49f6-a23b-9d49fad035a3 --output json`

## `ibmcloud dl route-report-delete`
{: #route-report-delete-view}

Delete a route report.

```sh
ibmcloud dl route-report-delete|rrd GATEWAY_ID REPORT_ID [--output format] [--help|-h]
```

### Command options
{: #command-options-delete-route-report}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`REPORT_ID`
:   Specify the ID of the route report ID.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

`--help|-h`
:   Get help on this command.

### Examples
{: #example-delete-route-report}

- `ibmcloud dl route-report-delete a771366f-2c8c-49f6-a23b-9d49fad035a3 dea35ba0-7323-4d8d-9c8d-d7ecda55e23d`
- `ibmcloud dl rrd a771366f-2c8c-49f6-a23b-9d49fad035a3 dea35ba0-7323-4d8d-9c8d-d7ecda55e23d --output json`

## `ibmcloud dl route-reports`
{: #route-report-list-view}

List all route reports.

```sh
ibmcloud dl route-reports|rrs GATEWAY_ID [--output format] [--help|-h]
```

### Command options
{: #command-options-list-route-report}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

`--help|-h`
:   Get help on this command.

### Examples
{: #example-list-route-report}

- `ibmcloud dl route-reports a771366f-2c8c-49f6-a23b-9d49fad035a3`
- `ibmcloud dl rrs a771366f-2c8c-49f6-a23b-9d49fad035a3 --output json`

## `ibmcloud dl virtual-connection`
{: #virtual-connection-view}

View details of a virtual connection.

```sh
ibmcloud dl virtual-connection|vc GATEWAY_ID VIRTUAL_CONNECTION_ID [--output format] [--help|-h]
```

### Command options
{: #command-options-view-details-virtual-connection}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`VIRTUAL_CONNECTION_ID`
:   Specify the ID of the virtual connection.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

`--help|-h`
:   Get help on this command.

### Examples
{: #example-show-details-virtual-connection}

- `ibmcloud dl virtual-connection a771366f-2c8c-49f6-a23b-9d49fad035a3 dea35ba0-7323-4d8d-9c8d-d7ecda55e23d`
- `ibmcloud dl vc a771366f-2c8c-49f6-a23b-9d49fad035a3 dea35ba0-7323-4d8d-9c8d-d7ecda55e23d --output json`

## `ibmcloud dl virtual-connection-create`
{: #virtual-connection-create}

Creating a virtual connection.

```sh
ibmcloud dl virtual-connection-create|vcc --type TYPE --network-id NETWORK_ID --name VIRTUAL_CONNECTION_NAME [--help|-h] [--output format]
```

### Command options
{: #command-options-create-virtual-connection}

`--type TYPE`
:   Specify the type of virtual connection. Values are `classic` or `vpc`.

`--network-id NETWORK_ID`
:   Specify the ID of the network. Not required when you use `classic` type.

`--name NAME`
:   Specify the name of the virtual connection.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

`--help|-h`
:   Get help on this command.

### Examples
{: #example-create-virtual-connection}

- `ibmcloud dl virtual-connection-create fb0df64a-ef8d-4b3c-b473-dc0230593529 --type vpc --network-id crn:v1:staging:public:is:us-south:a/28e4d90ac7504be694471ee66e70d0d5::vpc:r134-b8b62f60-f152-471f-971a-376da52721e0 --name newVC`
- `ibmcloud dl vcc fb0df64a-ef8d-4b3c-b473-dc0230593529 --type vpc --network-id crn:v1:staging:public:is:us-south:a/28e4d90ac7504be694471ee66e70d0d5::vpc:r134-b8b62f60-f152-471f-971a-376da52721e0 --name newVC --output json`

## `ibmcloud dl virtual-connection-delete`
{: #delete-virtual-connection}

Delete a virtual connection.

```sh
ibmcloud dl virtual-connection-delete|vcd GATEWAY_ID VIRTUAL_CONNECTION_ID [--help|-h] [--force|-f]
```

### Command options
{: #command-options-delete-virtual-connection}

`GATEWAY_ID`
:   Specify the ID of the gateway.

`VIRTUAL_CONNECTION_ID`
:   Specify the ID of the virtual connection.

`--help|-h`
:   Get help on this command.

`--force|-f`
:   Force the delete operation without confirmation.

### Examples
{: #example-delete-virtual-connection}

- `ibmcloud dl virtual-connection-delete fb0df64a-ef8d-4b3c-b473-dc0230593529 0b1e165c-a89c-4682-9771-dbe062e3acf7`
- `ibmcloud dl vcd fb0df64a-ef8d-4b3c-b473-dc0230593529 26284b6e-78a9-416c-ba5e-2b6ec085f18b -f`

## `ibmcloud dl virtual-connection-update`
{: #example-update-virtual-connection}

Update a virtual connection.

```sh
ibmcloud dl virtual-connection-update|vcu [--name NAME] [--status STATUS] [--help|-h] [--output format]
```

### Command options
{: #command-options-update-virtual-connection}

`--name NAME`
:   Specify the name of the virtual connection.

`--status STATUS`
:   Specify the virtual connection status. Values are `attached` or `rejected`.

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-update-virtual}

- `ibmcloud dl virtual-connection-update fb0df64a-ef8d-4b3c-b473-dc0230593529 3d577350-9450-4fd0-94b6-2f6da21b828e --name newVCUpdated`
- `ibmcloud dl vcu adaa0879-3509-4e71-b02b-0c7587ccbcfa 9b11fa61-6e74-4a8f-b978-bca1bead097f --name newVCUpdated --output json`

## `ibmcloud dl virtual-connections`
{: #virtual-connections-list}

List virtual connections.

```sh
ibmcloud dl virtual-connections|vcs [--help|-h] [--output format]
```

### Command options
{: #command-options-offering-speeds}

`--help|-h`
:   Get help on this command.

`--output VALUE`
:   Specify whether you want the output to display in JSON format. Currently, `json` is the only supported format.

### Examples
{: #example-list-details-virtual-connection}

- `ibmcloud dl virtual-connections a771366f-2c8c-49f6-a23b-9d49fad035a3`
- `ibmcloud dl vcs a771366f-2c8c-49f6-a23b-9d49fad035a3 --output json`
