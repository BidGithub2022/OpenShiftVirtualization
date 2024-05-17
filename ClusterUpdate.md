## Cluster Update:

### Introduction to OpenShift updates: https://docs.openshift.com/container-platform/4.15/updating/understanding_updates/intro-to-updates.html

- With OpenShift Container Platform 4, you can update an OpenShift Container Platform cluster with a single operation: 

     - **Administration → Cluster Settings** in the web console.
  
     - **oc adm upgrade** OpenShift CLI (oc) command.

- Red Hat hosts a public **OpenShift Update Service (OSUS)** graph of update possibilities based on the OpenShift Container Platform release images in the official registry

- When updating the cluster to a new version, the CVO applies manifests in separate stages called **Runlevels**. 

- The CVO monitors the state of each applied resource and the states reported by all cluster Operators. **The CVO only proceeds with the update when all manifests and cluster Operators in the active Runlevel reach a stable condition**. 
- After the CVO updates the entire control plane through this process, **the Machine Config Operator (MCO)** updates the operating system and configuration of every node in the cluster.

- Update Channels:
  - A new release is initially added to the **candidate** channel.
  
  - After successful final testing, a release on the candidate channel is promoted to the **fast** channel, an errata is published, and the release is now fully supported.
  
  - After a delay, a release on the fast channel is finally promoted to the **stable** channel. This delay represents the only difference between the fast and stable channels.
  
  - Releases promoted to the stable channel are simultaneously promoted to the **eus** channel. The primary purpose of the eus channel is to serve as a convenience for clusters performing an EUS-to-EUS update.


### Red Hat OpenShift Container Platform Life Cycle Policy: https://access.redhat.com/support/policy/updates/openshift

- Red Hat OpenShift container platform v4 provides a time-delineated, phased life cycle, where in at least 4 minor versions can be supported at any time. The time period of support is fixed from the point of minor version release and offers varying levels of support and maintenance. **Red Hat aims to forecast releases at a 4 month cadence**, providing customers ample opportunity to plan.

- Life Cycle Phases:
   - Full Support
  
   - Maintenance Support
  
   - Extended Update Support
  
   - Extended Update Support Term 2
  
   - Extended Life Phase
