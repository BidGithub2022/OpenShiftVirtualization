# OpenShift Virtualization

## Contents

- [Defining File System Configurations for VM](#Defining-File-System-Configurations-for-VM)
- [Windows VM](#Windows-VM)
___

## Defining File System Configurations for VM:

## Create the rhel9 guest image:

![Screenshot 2024-04-03 at 6 12 32 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/2ce13dc4-329a-4c89-9c59-a427b6365fb4)

![Screenshot 2024-04-03 at 6 15 34 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/c5c2a972-8064-4db7-8616-370904efb8b6)

![Screenshot 2024-04-03 at 6 18 08 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/9ef8cc72-cc22-4244-8e00-3d55818016f8)

![Screenshot 2024-04-03 at 6 18 59 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/cd225b1e-e8af-45f5-bc10-af7284fbc6f4)

![Screenshot 2024-04-03 at 6 29 29 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/b0bbafd7-b237-4f02-94ea-16e6487acddf)


## Download the qcow2 image to your local system once ready:

![Screenshot 2024-04-03 at 6 34 24 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/6444d663-18e9-46e0-8da3-a36562d3ce94)


## Copy the image to your working server

![Screenshot 2024-04-03 at 6 37 31 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/ae4d5505-9041-4819-aa75-53d6f65896c0)


## Compress the qcow2 image for faster performance:

![Screenshot 2024-04-03 at 6 41 04 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/f3f95472-498b-491e-8bfe-f17af5c2c884)


## Login to OCP cli:

![Screenshot 2024-04-03 at 6 47 16 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/4bd659c6-86ed-4833-9581-e63bb6a67a23)

## Use below command to upload the image:

virtctl image-upload dv rhel9-with-fs --size=30Gi --image-path=/home/bsahu/composer-api-37841dfb-f81c-4a11-be2f-e463f59dcf29-disk.qcow2.gz --force-bind --storage-class=lvms-vg1 --access-mode=ReadWriteOnce --insecure

![Screenshot 2024-04-03 at 6 58 59 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/faba85f3-6566-4db9-8a15-a1a53acdf04e)

*** I was using 4.15 OCP and topolvm.io as my storage class and was getting "Data Volume failed to initiate upload" while doing through the OCP console.
Checked with experts and got to know that "since TopoLVM is WaitForFIrstConsumer, I suspect the issue is that there is no consumer and thus the volume won't bind and the pod won't start". The suggestion was to use "--force-bind" flag.

## You will see PVC , PV and cdi-upload pod status on OCP console:

![Screenshot 2024-04-03 at 8 05 25 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/94fb13de-6fe1-4f48-b9db-ce3cdf8f9505)

![Screenshot 2024-04-03 at 8 05 37 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/0635429c-c599-4558-b902-f63c1c742f8c)

![Screenshot 2024-04-03 at 8 05 46 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/7f9eba62-dc04-4fbf-9ead-eab69951910d)

## Create a VM:

Virtualization -> VirtualMachines -> Create from Template -> Select rhel9 -> Customize VM -> Select Disk -> Edit rootdisk -> Use existing PVC -> Create VM

Go to Scripts and update the cloud-init data to initialize with your specific username.
 
![Screenshot 2024-04-03 at 7 00 36 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/c55f0650-ce6f-4991-ae30-9c8b4023ca03)

![Screenshot 2024-04-03 at 7 11 12 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/5d54199d-f633-4a90-b5c9-e470dc332aed)

## You will see PVC , PV and virt-launcher pod status on OCP console:

![Screenshot 2024-04-03 at 7 12 40 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/ada8da38-81b6-42ce-81be-a119c0d823d6)

![Screenshot 2024-04-03 at 7 13 02 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/b4370ab5-0074-4ffd-a098-0082d6a6598a)

![Screenshot 2024-04-03 at 7 13 11 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/d99cd1ab-f2e3-4b24-9513-60e30608a1b6)


## You will see VM is running.

![Screenshot 2024-04-03 at 7 13 59 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/1dc8851d-873e-46b0-9822-b94fd9570e7f)

## Login to console and check the rhel version and file system:

![Screenshot 2024-04-03 at 7 16 01 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/359fc28a-93a3-489b-89ab-cbf1e54a910d)

## File system on console:

![Screenshot 2024-04-03 at 7 17 28 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/848f6689-3e7e-4928-b7cb-a7322add821a)

## Resource usage of VM:

![Screenshot 2024-04-03 at 8 07 59 PM](https://github.com/BidGithub2022/OpenShiftVirtualization/assets/113651761/d8f92155-affd-48f2-b3a0-d059dce7f3d7)


### Links to refer:

https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/creating_customized_images_by_using_insights_image_builder/index#proc_creating-a-customized-rhel-guest-system-image-using-image-builder_assembly_creating-a-customized-rhel-guest-image-using-red-hat-image-builder

https://docs.openshift.com/container-platform/4.15/virt/getting_started/virt-using-the-cli-tools.html

https://docs.openshift.com/container-platform/4.15/cli_reference/openshift_cli/getting-started-cli.html

https://docs.openshift.com/container-platform/4.15/virt/virtual_machines/creating_vms_custom/virt-creating-vms-uploading-images.html


## Windows VM
This is a 3 mins video which will walk you through creating an windows VM: https://youtu.be/Kty3hUBwk54
Supported and Certified guests: https://access.redhat.com/articles/973163#thirdpartyguests

   
