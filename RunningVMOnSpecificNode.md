# Running VM On Specific Node


1. It was running on worker1 before.
   ![image](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/12d71b62-761a-48c0-9e91-358a26a8c68d)


2. Used the nodeSelector method : added a label to the worker2 node as "node=test" and used that in the nodeSelector for the VM.
   ![image](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/bb619dbe-7282-4ff2-a640-4af47f5bc579)

   ![image](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/ec3a7161-99c0-4185-bd4f-6da3fe35d34d)

   ![image](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/8c892bb8-38db-4ce4-8561-5d57dfcdcca2)

https://docs.openshift.com/container-platform/4.15/virt/virtual_machines/advanced_vm_management/virt-specifying-nodes-for-vms.html#virt-about-node-placement-vms_virt-specifying-nodes-for-vms is the documentation on that.
