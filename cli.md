---

copyright:
  years: 2019
lastupdated: "2019-12-15"

keywords: command line interface, commands, CLI

subcollection: dl
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:term: .term}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}
{:generic: data-hd-programlang="generic"}
{:download: .download}
{:DomainName: data-hd-keyref="DomainName"}

# CLI reference
{: #direct-link-cli-commands}

This document provides a reference of the command-line interface (CLI) commands available for {{site.data.keyword.cloud}} Direct Link Dedicated. The commands are organized into the sections listed in the navigation pane on the right.
{:shortdesc}

Set the environment variable `IBMCLOUD_DL_VERSION` to mention the version, which is used in query parameters for all the APIs. Set the variable in the format `YYYY-MM-DD`. For example:  
```
export IBMCLOUD_DL_VERSION=2019-10-25
```

## Before you begin
{: #cli-ref-prereqs}

Follow these instructions to use the Direct Link Command Line Interface, which is implemented as an {{site.data.keyword.cloud_notm}} CLI plug-in. It provides the user with the means to manage their service instance and its associated resource(s) via a command line user interface.

1. Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-install-ibmcloud-cli){: external}.
1. Install the `cloud-dl` CLI plug-in to the {{site.data.keyword.cloud_notm}} CLI.

   To install:

   ```
   ibmcloud plugin install dl-cli
   ```
   {: pre}

---

## General commands

### `ibmcloud plugin show dl-cli`
{: #show-plugin-info}

Show Direct Link CLI plug-in information.

`ibmcloud plugin show dl-cli`

---

### `ibmcloud dl --help`
{: #get-command-help}

Get help on Direct Link commands.

`ibmcloud dl --help|--h`

---

## Gateway commands
{: #gateway-commands}

### `ibmcloud dl gateways`
{: #list-all-gateways}

List all gateways.

`ibmcloud dl gateways|gws [--output JSON]`

#### Command options
{: #command-options-help-list-gateways}

   `--output JSON`: Specify if you want the output displayed in JSON format.

---

### `ibmcloud dl gateway <gateway_id>`
{: #get-help-specific-gateway}

View details of a specific gateway.

`ibmcloud dl gateway|gw <gateway_id> [--output JSON]`

#### Command options
{: #command-options-gateway-view-details}

   `<gateway_id>` : Specify the ID of the gateway.

   `--output JSON`: Specify if you want the output displayed in JSON format.

#### Examples
{: #example-get-gateway}

`ibmcloud dl gateway a771366f-2c8c-49f6-a23b-9d49fad035a3`

`ibmcloud dl gw a771366f-2c8c-49f6-a23b-9d49fad035a3 -output JSON`

---

### `ibmcloud dl gateway-create <gateway_name> <options>`
{: #create-gateway}

Create a gateway.

`ibmcloud dl gateway-create|gwc <gateway_name> <options> [-–help|--h] [-–output JSON]`

 #### Command options
{: #command-options-gateway-create}

   `<gateway_name>` : Specify a name for the new gateway.

   `--bgp-asn <value>` : Specify either the default value of `64999`, or select an ASN from allowed ranges.

   `--cross-connect-router <xcr>` : Select the IBM cross-connect router for the Direct Link connection.

   `--<routing_value>` : Specify `--global` or `--local` routing.

   `--<billing_value>` : Specify `--metered` or `--unmetered` billing.

   `--location-name <location>` : Specify the location name; for example, `dal10`.

   `--speed-mbps <speed_mbps>` : Specify a value for the speed.

   `--type <type>` : Specify the offering type; for example, `Dedicated`.

   `--bgp-base-cidr <cidr>` : Specify the CIDR.

   `--bgp-ibm-cidr <cidr>` : Specify the CIDR.

   `--bgp-cer-cidr <cidr>` : Specify the CIDR.

   `--help|--h` : Optional: Get help on this command.   

   `--output JSON`: Optional: Specify if you want the output displayed in JSON format.

#### Examples
{: #example-create-gateway}

`ibmcloud dl gateway-create dl-cli-gw --bgp-asn 64999 --cross-connect-router LAB-xcr01.dal09 --global --metered --location-name dal09 --speed-mbps 1000 --type dedicated --bgp-base-cidr 169.254.0.51/30 --bgp-ibm-cidr 169.254.0.52/30 --bgp-cer-cidr 169.254.0.53/30`

`ibmcloud dl gateway-create dl-cli-gw --bgp-asn 64999 --cross-connect-router LAB-xcr01.dal09 --global --metered --location-name dal09 --speed-mbps 1000 --type dedicated --bgp-base-cidr 169.254.0.51/30 --bgp-ibm-cidr 169.254.0.52/30 --bgp-cer-cidr 169.254.0.53/30 --output JSON`

---

### `ibmcloud dl gateway-delete *gateway_id*`
{: #delete-gateway}

Delete a specific gateway.

`ibmcloud dl gateway-delete|gwd <gateway_id> [--help|--h] [--force|--f]`

#### Command options
{: #command-options-gateway-delete}

   `<gateway_id>`: Specify the ID of the gateway.

   `--help|--h` : Optional: Get help on this command.   

   `--force|--f`: Optional: Force the delete operation without confirmation.

#### Examples
{: #example-delete-gateway1}

`ibmcloud dl gateway-delete e281b18b-0dba-49ee-9c64-aea588b7f1fd`

`ibmcloud dl gateway-delete 8ba9e7b0-dded-400e-ad7e-6481dad0b157 -f`

---

### `ibmcloud dl gateway-update <gateway_id>`
{: #update-gateway}

Update a specific gateway.

`ibmcloud dl gateway-update|gwu <gateway_id> [--global <value>] [--speed-mbps <speed_mbps>][--loa-reject-reason <loa_reject_reason>][--operational-status <operational_status>][--output JSON] [--help|--h]  `

#### Command options
{: #command-options-specific-gateway}

   `<gateway_id>`: Specify the ID of the gateway.

   `--global <value>` : Gateways with global routing can connect to networks outside their region. Specify a `true` or `false` value.

   `--speed-mbps <speed_mbps>` : Specify the speed of the gateway in mbps.

   `--loa-reject-reason <loa_reject_reason>` : Specify the reason for the Letter of Authorization (LOA) rejection.

   `--operational-status <operational_status>` : Specify the gateway's operational status. Values are `loa_accepted` or `loa_rejected`.

   `--output JSON`: Optional: Specify if you want the output displayed in JSON format.

   `--help|--h` : Optional: Get help on this command.   

#### Examples
{: #example-update-gateway1}

`ibmcloud dl gateway-update 8ba9e7b0-dded-400e-ad7e-6481dad0b157 --speed-mbps 5000 --name dl-cli-gw-updated`

`ibmcloud dl gateway-update 8ba9e7b0-dded-400e-ad7e-6481dad0b157 --speed-mbps 5000 --name dl-cli-gw-updated --output JSON`

---

## Location command
{: #location-command}

### `ibmcloud dl location <location_name> <offering_type>`
{: #location-retrieve}

Retrieves location-specific information for a given offering type.

`ibmcloud dl location|loc <location_name> <offering_type> [--output JSON] [--help|--h]`

#### Command options
{: #command-options-location}

  `<location_name>`: Specify the name of the location.

  `<offering_type>`: Specify the Direct Link offering type. Values are `Dedicated` or `Dedicated_Hosting`.

  `--output JSON`: Optional: Specify if you want the output displayed in JSON format.

   `--help|--h` : Optional: Get help on this command.   

#### Examples
{: #example-update-location}

`ibmcloud dl location "Washington 2" DEDICATED`

`ibmcloud dl loc "Washington 2" DEDICATED --output JSON`

---

## Offering speed command
{: #offering-speeds-command}

### `ibmcloud dl offering-speeds <offering_type>`
{: #offering-speeds-list}

Lists all offering speeds for an offering type.

`ibmcloud dl offering-speeds|ospeeds <offering_type> [--output JSON]`

#### Command options
{: #command-options-offering-speeds-type}

  `<offering_type>`: Specify the Direct Link offering type. Values are `Dedicated` or `Dedicated_Hosting`.

  `--output JSON`: Optional: Specify if you want the output displayed in JSON format.

#### Examples
{: #example-offering-type}

ibmcloud dl offering-speeds DEDICATED

ibmcloud dl ospeeds DEDICATED_HOSTING --output JSON

---

## Virtual connection command
{: #virtual-connection-commands}

### `ibmcloud dl virtual-connections`
{: #virtual-connections-list}

List virtual connections.

`ibmcloud dl virtual-connections|vcs [--output JSON] [--help|--h]`

#### Command options
{: #command-options-offering-speeds}

   `--output JSON`: Optional: Specify if you want the output displayed in JSON format.   

   `--help|--h` : Optional: Get help on this command.   

#### Examples
{: #example-list-details-virtual-connection}

`ibmcloud dl virtual-connections a771366f-2c8c-49f6-a23b-9d49fad035a3`

`ibmcloud dl vcs a771366f-2c8c-49f6-a23b-9d49fad035a3 --output JSON`

---

### `ibmcloud dl virtual-connection <gateway_id> <virtual_connection_id>`
{: #virtual-connection-view}

View details of a virtual connection.

`ibmcloud dl virtual-connection|vc <gateway_id> <virtual_connection_id> [--output JSON] [--help]`

#### Command options
{: #command-options-view-details-virtual-connection}

  `<gateway_id>`: Specify the ID of the gateway.

  `<virtual_connection_id>`: Specify the ID of the virtual connection.

  `--output JSON`: Optional: Specify if you want the output displayed in JSON format.   

   `--help|--h` : Optional: Get help on this command.   

#### Examples
{: #example-show-details-virtual-connection}

`ibmcloud dl virtual-connection a771366f-2c8c-49f6-a23b-9d49fad035a3 dea35ba0-7323-4d8d-9c8d-d7ecda55e23d`

`ibmcloud dl vc a771366f-2c8c-49f6-a23b-9d49fad035a3 dea35ba0-7323-4d8d-9c8d-d7ecda55e23d --output JSON`

---

### `ibmcloud dl virtual-connection-create <options>`
{: #virtual-connection-create}

Creating a virtual connection.

`ibmcloud dl virtual-connection-create|vcc [--type <type>] [--network-id <network_id>] [name <name>] [--format JSON] [--help|--h]`

#### Command options
{: #command-options-create-virtual-connection}

  `--type <type>`: Specify the type of virtual connection. Values are `classic` or `vpc`.

  `--network-id <network_id>` : Specify the ID of the network. This is not required for `classic` type.

  `name <name>`: Specify the name of the virtual connection.

  `--output JSON`: Optional: Specify if you want the output displayed in JSON format.  

  `--help|--h` : Optional: Get help on this command.   

#### Examples
{: #example-create-virtual-connection}

`ibmcloud dl virtual-connection-create fb0df64a-ef8d-4b3c-b473-dc0230593529 --type vpc --network-id crn:v1:staging:public:is:us-south:a/28e4d90ac7504be694471ee66e70d0d5::vpc:r134-b8b62f60-f152-471f-971a-376da52721e0 --name newVC`

`ibmcloud dl vcc fb0df64a-ef8d-4b3c-b473-dc0230593529 --type vpc --network-id crn:v1:staging:public:is:us-south:a/28e4d90ac7504be694471ee66e70d0d5::vpc:r134-b8b62f60-f152-471f-971a-376da52721e0 --name newVC --output JSON`

---

### `ibmcloud dl gateway-delete <gateway_id> <virtual_connection_id>`
{: #delete-virtual-connection}

Delete a virtual connection.

`ibmcloud dl virtual-connection-delete|vcd <gateway_id> <virtual_connection_id> [--help|--h] [--force|--f]`

#### Command options
{: #command-options-delete-virtual-connection}

   `<gateway_id>`: Specify the ID of the gateway.

   `<virtual_connection_id>`: Specify the ID of the virtual connection.

   `--help|--h` : Optional: Get help on this command.   

   `--force|--f`: Optional: Force the delete operation without confirmation.

#### Examples
{: #example-delete-virtual-connection}

`ibmcloud dl virtual-connection-delete fb0df64a-ef8d-4b3c-b473-dc0230593529 0b1e165c-a89c-4682-9771-dbe062e3acf7`

`ibmcloud dl vcd fb0df64a-ef8d-4b3c-b473-dc0230593529 26284b6e-78a9-416c-ba5e-2b6ec085f18b -f`

---

### `ibmcloud dl virtual-connection-update|vcu --name <name> --status <status>`
{: #example-update-virtual-connection}

Update a virtual connection.

`ibmcloud dl virtual-connection-update|vcu --name <name> --status <status> [--output JSON] [--help|--h]`

#### Command options
{: #command-options-update-virtual-connection}

   `--name <name>` : Specify the name of the virtual connection.

   `--status <status>` : Specify the virtual connection status. Values are `attached` or `rejected`.

   `--output JSON` : Optional: Specify if you want the output displayed in JSON format.

   `--help|--h` : Optional: Get help on this command.

#### Examples
{: #example-update-virtual-connection}

`ibmcloud dl virtual-connection-update fb0df64a-ef8d-4b3c-b473-dc0230593529 3d577350-9450-4fd0-94b6-2f6da21b828e --name newVCUpdated`

`ibmcloud dl vcu adaa0879-3509-4e71-b02b-0c7587ccbcfa 9b11fa61-6e74-4a8f-b978-bca1bead097f --name newVCUpdated --output JSON`

---

## Letter of Authorization (LOA) command
{: #loa-commands}

### `ibmcloud dl loa <gateway_id>`
{: #loa-download}

Download the LOA for the specified gateway in either the current, working directory or in the specified directory.

`ibmcloud dl loa <gateway_id> [--file <output_directory_path>] [--help|--h]`

#### Command options
{: #command-options-loa-download}

   `<gateway_id>` : Specify the ID of the gateway.

   `--file <output_directory_path>` : Optional: Specify the output directory path. For example, specify to download the LOA in the `/tmp` directory.

   `--help|--h` : Optional: Get help on this command.   

#### Examples
{: #example-loa-download}

`ibmcloud dl loa 5cc19d0a-792c-4595-adfc-f90fc650de01`

`ibmcloud dl loa 5cc19d0a-792c-4595-adfc-f90fc650de01 --file /tmp`

---

## Completion notice commands
{: #completion-notice-commands}

### `ibmcloud dl completion-notice|cn <gateway_id>`
{: #completion-notice-download}

Download the completion notice for the specified gateway in either the current, working directory or in a specified output directory path.

`ibmcloud dl completion-notice|cn <gateway_id> [--file <output_directory_path>][--help|--h]`

#### Command options
{: #command-options-completion-notice-download}

   `<gateway_id>` : Specify the ID of the gateway.

   `--file <output_directory_path>` : Optional: Specify the output directory path where you want to download the completion notice. For example, specify to download the completion notice in the `/tmp` directory.

   `--help|--h` : Optional: Get help on this command.   

#### Examples
{: #example-completion-notice-download}

`ibmcloud dl completion-notice 0e28b9bc-06df-44f1-b5d7-08085b9fc935`

`ibmcloud dl cn 0e28b9bc-06df-44f1-b5d7-08085b9fc935 --file /tmp`

---

## `ibmcloud dl completion-notice-update <gateway_id>`
{: #completion-notice-upload}

Upload the completion notice from either the current, working directory or a specified directory.

`ibmcloud dl completion-notice-update <gateway_id> [-i <input_directory_path>]`

#### Command options
{: #command-options-completion-notice-upload}

   `<gateway_id>` : Specify the ID of the gateway.

   `-i <input_directory_path>` : Optional: Specify the directory in which you want to upload the completion notice.

#### Examples
{: #example-completion-notice-upload}

`ibmcloud dl completion-notice-update 5cc19d0a-792c-4595-adfc-f90fc650de01`

`ibmcloud dl cnu 22f799e8-b4ab-44ca-856b-897be9b0e53d -i /tmp/`

---

## Offering type command
{: #offering-type-command}

### `ibmcloud dl locations <offering_type>`
{: #list-locations-offering-type-json}

List the locations for a specific Direct Link offering type.

`ibmcloud dl locations|locs <offering_type> [–-output JSON] [--help|--h]`

#### Command options
{: #command-options-offering_type}

   `<offering_type>`: Specify the Direct Link offering type. Values are `Dedicated` or `Dedicated_Hosting`.

   `--output JSON`: Optional: Specify if you want the output displayed in JSON format.

   `--help|--h` : Optional: Get help on this command.   

#### Examples
{: #example-offering-type1}

`ibmcloud dl locations DEDICATED`

`ibmcloud dl locs DEDICATED --output JSON`
