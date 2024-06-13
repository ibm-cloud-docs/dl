---

copyright:
  years: 2024
lastupdated: "2024-01-08"

keywords:

subcollection: dl

---

{{site.data.keyword.attribute-definition-list}}

# Learning about Direct Link architecture and workload isolation
{: #compute-isolation}

Review the following sample architecture for Direct Link, and learn more about different isolation levels so that you can choose the solution that best meets the requirements of the workloads that you want to run in the cloud.
{: shortdesc}

## Direct Link architecture
{: #architecture}

_Review the following example: https://cloud.ibm.com/docs/containers?topic=containers-service-arch. Review the System Architecture Guide: https://pages.github.ibm.com/CloudEngineering/system_architecture/services/multitenancy.html. Provide an architectural overview diagram identifying what runs within the IBM Service Account and what runs in the customer's account._

## Direct Link workload isolation
{: #workload-isolation}

Document how customer workloads are isolated from each other by plan. Do customer workloads run within the customer account?  Are customer workloads isolated within Kubernetes namespaces? Do customer workloads run on dedicated compute? Check out the example from Kubernetes: https://cloud.ibm.com/docs/containers?topic=containers-service-arch#worker-components
