## Backup & Restore

There are multiple options for backup and restore of virtual machines with OpenShift Virtualization.

OADP (OpenShift APIs for Data Protection): A Red Hat Operator which provides a storage agnostic method to back up and restore OpenShift objects, including virtual machines.- https://docs.openshift.com/container-platform/4.13/backup_and_restore/application_backup_and_restore/oadp-features-plugins.html

** Kasten K10 by Veeam - https://docs.kasten.io/latest/usage/openshift_virtualization.html

** Trilio for Kubernetes - https://docs.trilio.io/kubernetes/appendix/backup-and-restore-virtual-machine-running-on-openshift-virtualization

** Storware Backup and Recovery - https://storware.eu/solutions/containers-backup-and-recovery/red-hat-openshift-backup-restore/

Additionally, many storage partners offer the ability to protect virtual machine disks using their native technology. Be sure to check with your storage and backup vendor(s) to determine compatibility with OpenShift Virtualization.
