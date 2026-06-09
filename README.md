# Bazzite DX - Strix Halo Edition (F44 Base)

🔴 **DEPRECATED - This repository is no longer maintained.**

Bazzite DX is now officially releasing based on v44, making this fork unnecessary. Please use the official upstream repository instead:

**👉 [ublue-os/bazzite](https://github.com/ublue-os/bazzite)**

## Why This Fork Is Retired

This fork was created as a temporary solution to provide a cutting-edge Bazzite DX environment for bleeding-edge hardware like the AMD Strix Halo (Ryzen AI Max 300 series) APUs, which required v44 when the official release was still based on an older cycle.

Now that upstream Bazzite DX has moved to v44, there's no need for this fork anymore. All features and improvements are available in the official repository.

## Migration Guide

If you're currently running this image, migrate to the official Bazzite DX by rebasing:

```bash
rpm-ostree rebase ostree-image-signed:docker://ghcr.io/ublue-os/bazzite-dx:latest
```

---

## Original Purpose (Archive)

This fork originally detached from the handheld release cycle and rebuilt the DX developer environment on top of the standard, cutting-edge Fedora 44 desktop base, specifically for hardware needing bleeding-edge drivers.

For historical context, the only modifications from the upstream repository were:
1. Using custom GitHub Actions builder keys instead of upstream cosign keys
2. Modifying build configuration to use standard `bazzite` desktop base instead of `bazzite-deck`
3. Removing handheld-specific autologin cleanup scripts

---

**Thank you for using this fork during the transition! 🎉**
