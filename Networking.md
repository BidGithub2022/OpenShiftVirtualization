## Connecting a VM to a Linux bridge network:

https://docs.openshift.com/container-platform/4.15/virt/vm_networking/virt-networking-overview.html

Install the Kubernetes NMState Operator to configure Linux bridges, VLANs, and bondings for your secondary networks.
You can create a Linux bridge network and attach a VM to the network by performing the following steps:

*** Configure a Linux bridge network device by creating a NodeNetworkConfigurationPolicy custom resource definition (CRD).

*** Configure a Linux bridge network by creating a NetworkAttachmentDefinition CRD.

*** Connect the VM to the Linux bridge network by including the network details in the VM configuration.

https://docs.openshift.com/container-platform/4.15/virt/vm_networking/virt-connecting-vm-to-linux-bridge.html
