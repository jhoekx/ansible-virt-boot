Ansible virt_boot module
========================

This repository contains an Ansible module to configure the boot order of
libvirt virtual machines.

Example usage:

```
  - name: direct kernel boot
    action: virt_boot domain=${inventory_hostname} bootmenu=yes kernel=$storage/${inventory_hostname}/kernel-${inventory_hostname} initrd=$storage/${inventory_hostname}/initramfs-${inventory_hostname}.img cmdline="root=/dev/ram0 vga=normal rw"
    delegate_to: vmhost
  - ...
  - name: restore normal boot order
    action: virt_boot domain=${inventory_hostname} bootmenu=yes boot=cdrom,hd
    delegate_to: vmhost
```

This has only been tested on qemu+kvm..