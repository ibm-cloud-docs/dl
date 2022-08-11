---

copyright:
  years: 2022
lastupdated: "2022-08-11"
keywords: api

subcollection: dl


---

{{site.data.keyword.attribute-definition-list}}

# Setting up your API environment
{: #set-up-environment}

Before you can use the Direct Link (2.0) API, you must set up your environment.
{: shortdesc}

## General prerequisites
{: #general-prerequisites}

Set up your account to access the direct link. Make sure that your account is [upgraded to a paid account](/docs/account?topic=account-accountfaqs#changeacct){: external}.

## API prerequisites
{: #api-prerequisites-setup}

Before you can use the API to interact with a direct link, you must get an IAM token, store the endpoint as a variable, and verify that you have access to the IBM Cloud Direct Link API service.

The following examples use the `directlink.cloud.ibm.com` global endpoint.
{: note}

### Step 1: Store your API key as a variable
{: #store-api-key-variable}

Run the following command to store the API key for your account in an environment variable. If you don't have an API key, see [Creating an API key](/docs/account?topic=account-userapikey#create_user_key){: external}.

```sh
apikey="<YOUR_API_KEY>"
```

### Step 2: Get an IBM Identity and Access Management (IAM) token
{: #get-iam-token}

Run the following command to get and parse an IAM token by using the JSON processing utility [jq](https://stedolan.github.io/jq/){: external}. You can modify the command to use another parsing tool, or you can remove the last part of the command if you prefer to manually parse the token.

```sh
iam_token=`curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=$apikey" \
  "https://iam.cloud.ibm.com/identity/token"  |jq -r '(.token_type + " " + .access_token)'`
```

To view the IAM token, run ``echo $IAM_TOKEN``. The result should look like this:

```text
Bearer <your_token>
```
{: screen}

The Authorization header expects the token to begin with `Bearer`. If the result doesn't include `Bearer`, update the `iam_token` variable to include it. These examples assume that `Bearer` is included in the `iam_token`.

Because the IAM token expires, you must repeat the preceding step to refresh your token every hour.
{: important}

### Step 3: Store the API endpoint as a variable
{: #store-api-endpoint-variable}

Run the following command to store the API endpoint in a variable so that it can be reused later in your session.  

Public endpoint:

```sh
directlink_api_endpoint="https://directlink.cloud.ibm.com"
```

Virtual private endpoint:

```sh
directlink_api_endpoint="https://private.directlink.cloud.ibm.com"
```

To verify that the variable was saved, run `echo $directlink_api_endpoint` and ensure that the response is not empty.

### Step 4: Store the API version as a variable
{: #store-api-version-variable}

Every API request must include the `version` parameter, in the format `YYYY-MM-DD`. Run the following command to store the version date in a variable so that it can be reused in your session. For more information about setting the `version` parameter, see **Versioning** in the [Direct Link API](/apidocs/direct_link#versioning).

```sh
api_version="2020-03-31"
```

To verify that this variable was saved, run ``echo $api_version`` and make sure that the response is not empty.

### Step 5: Verify that you have API access
{: #verify-api-access}

If you run into unexpected results, add the `--verbose` (debug) flag after the `curl` command to obtain detailed logging information.
{: tip}

* Call the [List Available Locations API](/apidocs/direct_link#list-offering-type-locations) to see the locations available for your direct link, in JSON format. At least one object should return. 
   
   This example lists the locations available for a Direct Link Dedicated gateway. For Direct Link Connect, simply substitute `connect` for `dedicated`.
   {: note}

    ```sh
    curl -X GET "$directlink_api_endpoint/v1/offering_types/dedicated/locations?version=$api_version"   -H "Authorization: Bearer $IAM_TOKEN"
    ```

* Call the [List gateways](/apidocs/direct_link#list-gateways) API to see any direct links that you already created under your account, in JSON format.

    ```sh
    curl -X GET "$directlink_api_endpoint/v1/gateways?version=$api_version"   -H "Authorization: Bearer $IAM_TOKEN"
    ```
