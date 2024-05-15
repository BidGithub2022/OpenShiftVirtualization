## Expanding VM Disk:

1. See the Edit section where it says cannot edit resources that are already created.
![image](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/a347854c-6dd2-4c21-956a-c7df8c71daef)

2.  I detached the root disk(see the 60GiB) . Go to Storage, then PersistentVolumeClaims and you can see under that.
![image](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/45e6d7d1-291f-472a-8079-6adc96efe955)
 
3. Expanded to 70G using the 3 dots... you can either use that or update the YAML.
![image](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/35f00978-4f98-46a8-9108-4840e142d9c0)

4.  Attached it back to the VM by adding Disk under Configuration -> Disks section.
![image](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/dc338b79-a24c-47ac-9365-c17b7ff6f95e)


Here is the documentation: https://docs.openshift.com/container-platform/4.15/virt/virtual_machines/virtual_disks/virt-expanding-vm-disks.html
