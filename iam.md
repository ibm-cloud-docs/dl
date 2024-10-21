---

copyright:
  years: 2020
lastupdated: "2024-10-21"

keywords: IAM access for Direct Link, permissions for Direct Link, identity and access management for Direct Link, roles for Direct Link, actions for  Direct Link, assigning access for Direct Link

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Managing IAM access for {{site.data.keyword.dl_full_notm}}
{: #iam}

{{site.data.keyword.cloud}} Identity and Access Management (IAM) controls access to Direct Link gateways for users in your account. Every user that accesses the {{site.data.keyword.dl_short}} service in your account must be assigned an access policy with an IAM role. Review the following roles, actions, and more to help determine the best way to assign access to {{site.data.keyword.dl_short}}.
{: shortdesc}

{{site.data.keyword.dl_full}} enables connectivity between customer on-premises resources to {{site.data.keyword.cloud_notm}} resources that are hosted in classic and Virtual Private Cloud (VPC) infrastructures.
{: note}

The access policy that you assign users in your account determines what actions a user can perform within the context of the service or specific instance that you select. The direct link customizes and defines the allowable actions as operations that are allowed to be performed on the service. Each action is mapped to an IAM platform or service role that you can assign to a user.

If a specific role and its actions don't fit the use case that you're looking to address, you can [create a custom role](/docs/account?topic=account-custom-roles&interface=ui#custom-access-roles) and pick the actions to include.
{: tip}

IAM access policies enable access to be granted at different levels. Some options include:

* Access across the instance of the Direct Link service in your account
* Access to an individual service instance in your account
* Access to a specific resource within an instance

Review the following table that outlines what types of tasks each role allows for when you're working with the {{site.data.keyword.dl_short}} service. Platform management roles enable users to perform tasks on service resources at the platform level, for example, assign user access to the service, and create or delete instances.

{{site.data.keyword.dl_short}} does not have service-access roles, which enable users access to Direct Link and the ability to call the Direct Link API. For information about the exact actions that are mapped to each role, see [{{site.data.keyword.dl_short}} Connect](/docs/account?topic=account-iam-service-roles-actions#directlink.connect-roles) and [{{site.data.keyword.dl_short}} Dedicated](/docs/account?topic=account-iam-service-roles-actions#directlink.dedicated-roles).
{: note}

| Platform role | Description of actions | Example actions |
|---|---|---|
| Administrator | Allows a user to assign {{site.data.keyword.dl_short}} IAM access policies to other users. | Create gateway  \n Delete gateway  \n Edit gateway  \n Add a virtual connection to a gateway&ast;  \n Remove a virtual connection from a gateway&ast;  \n Edit a virtual connection (API only)  \n Update user access policies for the service |
| Editor | Performs all actions, including managing gateways and virtual connections. | Create gateway  \n Delete gateway  \n Edit gateway  \n Add a virtual connection to a gateway&ast;  \n Remove a virtual connection from a gateway&ast;  \n Edit a virtual connection (API only) |
| Viewer/Operator | Performs actions that don't change the state of resources. | List gateways  \n Get gateways  \n List a gateway's virtual connections  \n View a gateway's virtual connections  \n Retrieve gateway-related information (completion notice of authorization)  \n View incoming connection requests&ast; |
{: caption="IAM platform-access user role and actions" caption-side="bottom"}

&ast; To add or remove virtual connections to VPCs, or to accept or reject a connection request, the user must also have Editor or Administrator platform-access role permissions to the VPC. See [VPC: Getting started with IAM](/docs/vpc?topic=vpc-iam-getting-started) for more information.

**Notes**:

* All {{site.data.keyword.dl_short}} resources exist in a resource group. Creating a {{site.data.keyword.dl_short}} resource requires Editor access to the selected resource group.
* For information about assigning user roles in the console, see [Managing access to resources](/docs/account?topic=account-assign-access-resources).

## Assigning access to Direct Link in the console
{: #assign-access-console}
{: ui}

Common ways to assign access in the console:

* Access policies per user. You can manage access policies per user from the **Manage** > **Access (IAM)** > **Users** page in the console. For information about the steps to assign IAM access, see [Managing access to resources](/docs/account?topic=account-assign-access-resources&interface=ui#access-resources-console).
* Access groups. Access groups are used to streamline access management by assigning access to a group once, then you can add or remove users as needed from the group to control their access. You manage access groups and their access from the **Manage** > **Access (IAM)** > **Access groups** page in the console. For more information, see [Assigning access to a group in the console](/docs/account?topic=account-groups&interface=ui#access_ag).

## Authorization considerations for cross-account virtual connections
{: #xac-auth-considerations}

The following table shows the authorization changes for cross-account virtual connections.

   A cross-account virtual connection means that the gateway exists in an IBM Cloud account and a virtual connection in that gateway connects to a VPC in a different IBM Cloud account. This setup requires special authorization considerations because the objects (the direct link and the VPC) and their resource groups do not exist in both accounts.
   {: note}

| Related account | Capability | Required authorization |
|---|---|---|
| Gateway account | Any capabilities not mentioned in this table. | No authorization changes. |
| Gateway account | Create and delete a cross-account virtual connection. | `directlink.dedicated.edit` or `directlink.connect.edit`  \n No VPC authorization that is required at create or delete time. |
| Network account | View read-only gateways and virtual connections. | Service-level `directlink.dedicated.view` or `directlink.connect.view` |
| Network account | Accept and reject pending connections. | Service-level `directlink.dedicated.view` or `directlink.connect.view`  \n Update authorization on the connected VPC. |
| Network account | `DELETE` attached virtual connection. | Service-level `directlink.dedicated.view` or `directlink.connect.view`  \n  Update authorization on the connected VPC. |
{: caption="Authorization changes for cross-account virtual connections" caption-side="bottom"}

## Assigning access to Direct Link in the CLI
{: #assign-access-cli}
{: cli}

For step-by-step instructions for assigning, removing, and reviewing access, see [Assigning access resources by using the CLI](/docs/account?topic=account-assign-access-resources&interface=cli#access-resources-cli). The following example shows a command for assigning the `Editor` role to a user:

Use `directlink` for the service name. Also, use quotations around role names that are more than one word like the example here.
{: tip}

```bash
ibmcloud iam user-policy-create USER@EXAMPLE.COM --service-name directlink --roles Editor
```
{: pre}

## Assigning access to Direct Link by using the API
{: #assign-access-api}
{: api}

For step-by-step instructions for assigning, removing, and reviewing access, see [Assigning access to resources by using the API](/docs/account?topic=account-assign-access-resources&interface=api) or the [Create a policy API doc](/apidocs/iam-policy-management#create-policy). Role cloud resource names (CRN) in the following table are used to assign access with the API.

| Role name | Role CRN |
|---------------|-----------------|
| Viewer                 | `crn:v1:bluemix:public:directlink::::serviceRole:Viewer`        |
| Operator               | `crn:v1:bluemix:public:directlink::::serviceRole:Operator`      |
| Editor                 | `crn:v1:bluemix:public:directlink::::serviceRole:Editor`        |
| Administrator          | `crn:v1:bluemix:public:directlink::::serviceRole:Administrator` |
| Reader         | `crn:v1:bluemix:public:directlink::::serviceRole:Reader`        |
| Writer         | `crn:v1:bluemix:public:directlink::::serviceRole:Writer`        |
| Manager        | `crn:v1:bluemix:public:directlink::::serviceRole:Manager`       |
{: caption="Role ID values for API use" caption-side="bottom"}

Use `directlink` for the service name, and refer to the Role ID values table to make sure that you're using the correct value for the CRN.
{: tip}

The following policy assigns a user Writer role to all `serviceName=directlink` resources in the account.

```curl
curl -X POST 'https://iam.cloud.ibm.com/v1/policies' -H 'Authorization: Bearer $TOKEN' -H 'Content-Type: application/json' -d '{
  "type": "access",
  "description": "Writer role for Direct Link",
  "subjects": [
   {
    "attributes": [{
        "name": "iam_id",
        "value": "IBMid-123453user"
    }]
  }],
  "roles": [{
    "roles_id": "crn:v1:bluemix:public:directlink::::serviceRole:Writer"
   }],
  "resources": [{
    "attributes": [
    {
        "name": "accountId",
        "value": "1234567890987654321"
    },
    {
        "name": "serviceName",
        "value": "directlink"
    }]
}]
```
{: curl}
{: codeblock}

```java
SubjectAttribute subjectAttribute = new SubjectAttribute.Builder()
      .name("iam_id")
      .value("IBMid-123453user")
      .build();

PolicySubject policySubjects = new PolicySubject.Builder()
      .addAttributes(subjectAttribute)
      .build();

PolicyRole policyRoles = new PolicyRole.Builder()
      .roleId("crn:v1:bluemix:public:directlink::::serviceRole:Writer")
      .build();

ResourceAttribute accountIdResourceAttribute = new ResourceAttribute.Builder()
      .name("accountId")
      .value("ACCOUNT_ID")
      .operator("stringEquals")
      .build();

ResourceAttribute serviceNameResourceAttribute = new ResourceAttribute.Builder()
      .name("serviceName")
      .value("directlink")
      .operator("stringEquals")
      .build();

PolicyResource policyResources = new PolicyResource.Builder()
      .addAttributes(accountIdResourceAttribute)
      .addAttributes(serviceNameResourceAttribute)
      .build();

CreatePolicyOptions options = new CreatePolicyOptions.Builder()
      .type("access")
      .subjects(Arrays.asList(policySubjects))
      .roles(Arrays.asList(policyRoles))
      .resources(Arrays.asList(policyResources))
      .build();

Response<Policy> response = service.createPolicy(options).execute();
Policy policy = response.getResult();

System.out.println(policy);
```
{: java}
{: codeblock}

```python
policy_subjects = PolicySubject(
  attributes=[SubjectAttribute(name='iam_id', value='IBMid-123453user')])
policy_roles = PolicyRole(
  role_id='crn:v1:bluemix:public:directlink::::serviceRole:Writer')
account_id_resource_attribute = ResourceAttribute(
  name='accountId', value='ACCOUNT_ID')
service_name_resource_attribute = ResourceAttribute(
  name='serviceName', value='directlink')
policy_resources = PolicyResource(
  attributes=[account_id_resource_attribute,
        service_name_resource_attribute])

policy = iam_policy_management_service.create_policy(
  type='access',
  subjects=[policy_subjects],
  roles=[policy_roles],
  resources=[policy_resources]
).get_result()

print(json.dumps(policy, indent=2))
```
{: python}
{: codeblock}

```go
subjectAttribute := &iampolicymanagementv1.SubjectAttribute{
  Name:  core.StringPtr("iam_id"),
  Value: core.StringPtr("IBMid-123453user"),
}
policySubjects := &iampolicymanagementv1.PolicySubject{
  Attributes: []iampolicymanagementv1.SubjectAttribute{*subjectAttribute},
}
policyRoles := &iampolicymanagementv1.PolicyRole{
  RoleID: core.StringPtr("crn:v1:bluemix:public:directlink::::serviceRole:Writer"),
}
accountIDResourceAttribute := &iampolicymanagementv1.ResourceAttribute{
  Name:     core.StringPtr("accountId"),
  Value:    core.StringPtr("ACCOUNT_ID"),
  Operator: core.StringPtr("stringEquals"),
}
serviceNameResourceAttribute := &iampolicymanagementv1.ResourceAttribute{
  Name:     core.StringPtr("serviceName"),
  Value:    core.StringPtr("directlink"),
  Operator: core.StringPtr("stringEquals"),
}
policyResources := &iampolicymanagementv1.PolicyResource{
  Attributes: []iampolicymanagementv1.ResourceAttribute{
    *accountIDResourceAttribute, *serviceNameResourceAttribute}
}

options := iamPolicyManagementService.NewCreatePolicyOptions(
  "access",
  []iampolicymanagementv1.PolicySubject{*policySubjects},
  []iampolicymanagementv1.PolicyRole{*policyRoles},
  []iampolicymanagementv1.PolicyResource{*policyResources},
)

policy, response, err := iamPolicyManagementService.CreatePolicy(options)
if err != nil {
  panic(err)
}
b, _ := json.MarshalIndent(policy, "", "  ")
fmt.Println(string(b))
```
{: go}
{: codeblock}

```javascript
const policySubjects = [
  {
    attributes: [
      {
        name: 'iam_id',
        value: 'IBMid-123453user',
      },
    ],
  },
];
const policyRoles = [
  {
    role_id: 'crn:v1:bluemix:public:directlink::::serviceRole:Writer',
  },
];
const accountIdResourceAttribute = {
  name: 'accountId',
  value: 'ACCOUNT_ID',
  operator: 'stringEquals',
};
const serviceNameResourceAttribute = {
  name: 'serviceName',
  value: 'directlink',
  operator: 'stringEquals',
};
const policyResources = [
  {
    attributes: [accountIdResourceAttribute, serviceNameResourceAttribute]
  },
];
const params = {
  type: 'access',
  subjects: policySubjects,
  roles: policyRoles,
  resources: policyResources,
};

iamPolicyManagementService.createPolicy(params)
  .then(res => {
    examplePolicyId = res.result.id;
    console.log(JSON.stringify(res.result, null, 2));
  })
  .catch(err => {
    console.warn(err)
  });
```
{: javascript}
{: codeblock}

### Curl example 2
{: #curl-example-2}

The following policy assigns a user Writer role to all `serviceName=directlink` resources of type `dedicated` in the account.

```curl
curl -X POST 'https://iam.cloud.ibm.com/v1/policies' -H 'Authorization: Bearer $TOKEN' -H 'Content-Type: application/json' -d '{
  "type": "access",
  "description": "Writer role for Direct Link Dedicated",
  "subjects": [
  {
    "attributes": [{
        "name": "iam_id",
        "value": "IBMid-123453user"
  }]
}],
"roles": [{
    "roles_id": "crn:v1:bluemix:public:directlink::::serviceRole:Writer"
}],
"resources": [{
    "attributes": [
    {
        "name": "accountId",
        "value": "1234567890987654321"
    },
    {
        "name": "serviceName",
        "value": "directlink"
    },
    {
        "name": "dedicatedId",
        "value": "*"
    }]
}]
```
{: curl}
{: codeblock}

## Assigning access to `directlink` by using Terraform
{: #assign-access-terraform}
{: terraform}

The following example is for assigning the `Editor` role for `directlink`:

Use `directlink` for the service name.
{: tip}

```terraform
resource "ibm_iam_user_policy" "policy" {
  ibm_id = "test@example.com"
  roles  = ["Editor"]

  resources {
    service = "directlink"
  }
}
```
{: codeblock}

For more information, see [ibm_iam_user_policy](https://registry.terraform.io/providers/IBM-Cloud/ibm/latest/docs/resources/iam_user_policy){: external}.
