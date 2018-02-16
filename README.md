# Set-Disk-Quota-Centos7
Set Disk Quota Centos7 on root

To add quota to root "/" partition with lvm, we must add a flag to the grub file **"uquota,pquota"**
vi quota /etc/fstab

GRUB_CMDLINE_LINUX="crashkernel=auto rd.lvm.lv=cl/root rd.lvm.lv=cl/swap rhgb quiet rootflags=uquota,pquota"

cp /boot/grub2/grub.cfg /boot/grub2/grub.cfg.orig

grub2-mkconfig -o /boot/grub2/grub.cfg

reboot

mount | grep ' / '

xfs_quota -x /

**xfs_quota>** state

**xfs_quota>** limit bsoft=9g bhard=10g myUser
