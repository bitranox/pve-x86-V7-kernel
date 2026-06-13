# pve-x86-V7-kernel

Proxmox VE x86_64 kernel source, 7.0.x ("V7") series, Proxmox-patched.

- `linux-7.0.0` : the shared Ubuntu 7.0.0 kernel base (unpatched).
- `7.0.X-Y-pve` : the proxmox-patched source for that released point release,
  committed on top of `linux-7.0.0` so the whole series dedups against the base.

Each `7.0.X-Y-pve` branch is the Ubuntu base that release pins plus the matching
`patches/kernel/*.patch` from pve-kernel at that version, the tree the shipped PVE
kernel is built from, so an in-tree module built here matches the running ABI.

## Build the in-tree KVM modules
```
git checkout 7.0.6-2-pve
cp /boot/config-7.0.6-2-pve .config
cp /usr/src/linux-headers-7.0.6-2-pve/Module.symvers .
make olddefconfig && make modules_prepare && make M=arch/x86/kvm
```
Released versions only; release candidates are omitted.
