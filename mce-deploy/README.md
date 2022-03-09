# MCE Deploy Instructions quick guide

This guide explains the intended purpose of the pipeline and a brief overview of how to run the pipeline.

This Pipeline is intended to help enablement of development alongside MCE/HyperShift by providing a means to quickly get a cluster configured with them installed on demand.

Currently this Pipeline is installed onto the `Collective` cluster, in the `managed-services` namespace.

It is recommended to read the [HyperShift getting started](https://hypershift-docs.netlify.app/getting-started/) before using this Pipeline.

The Pipeline currently takes into account the following parameters - 

ii1. **ClusterPoolNamespace**: On the cluster the pipeline is installed in, this is the name of the namespace of the clusterpool to use.
2. **ClusterPoolName**: On the cluster the pipeline is installed in, this is hte name of the clusterpool to use.
3. **ClusterClaimName**: The name to use when creating the clusterClaim.
4. **ClusterClaimLifetime**: The length of the lifetime of the clusterClaim. Must be in 'h'
5. **Namespace**: This will be the namespace that MCE and the HyperShift Deployment Controller are deployed into when installed onto the clusterClaim.
6. **Snapshot**: This is the upstream snapshot tag to use to deploy MCE. This is intended to allow for developer builds to be installed alongside HyperShift. Tags are retrieable from this [quay repo](https://quay.io/repository/stolostron/cmb-custom-registry?tab=tags).
7. **ImagePullSecret**: The imagePullSecret used to pull the MCE images. Must exist in clusterPoolNamespace. Must have pull access to `quay.io/stolostron`. Must be formatted like shown [here](prereqs/pull-secret.yaml).
8. **AWSCredsSecret**: The name of the AWS Credentials Secret used to deploy HyperShift. Must exist in clusterPoolNamespace. Must be formatted like shown [here](prereqs/aws-creds.yaml).
9. **OCPPullSecret**: The name of the secret containing the OCP pull secret used to deploy a HyperShift HostedCluster. Can be retrieved from [here](https://console.redhat.com/openshift/install/aws/installer-provisioned). Must be stored formatted like shown [here](prereqs/ocp-pull-secret.yaml).
10. **S3BucketName**: The name of the AWS S3 bucket used to Install HyperShift and provision a HostedCluster. Must be public. See guide [here](https://hypershift-docs.netlify.app/getting-started/) for instructions.
11. **Region**: The AWS region the S3 bucket exists in
12. **HostedClusterName**: The name to use when creating the HyperShift Hosted Cluster on the targeted cluster.
13. **BaseDomain**: The basedomain to use for DNS records when deploying the HyperShift HostedCluster.
