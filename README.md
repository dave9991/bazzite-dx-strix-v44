# Bazzite DX - Strix Halo Edition (F44 Base)

**⚠️ Disclaimer:** This is a quick and dirty build, barely tested. Use at your own risk.

## The Purpose
I created this fork specifically for hardware that needs bleeding-edge drivers, specifically the new AMD Strix Halo (Ryzen AI Max 300 series) APUs. 

Upstream, the Bazzite-DX variants are currently tethered to the `bazzite-deck` base image, which is delayed on an older release cycle for handheld stability. This delay means missing out on the newer Linux kernels, Mesa drivers, and ROCm updates required to make the Strix Halo architecture actually function well.

This fork simply detaches from the handheld release cycle and rebuilds the DX developer environment on top of the standard, cutting-edge Fedora 44 desktop base. 

## Transparency
Don't just trust random OS images on the internet—look at the commit history. 

The only modifications made to this fork from the upstream `ublue-os/bazzite-dx` repository are:
1. Swapping out the `cosign` cryptographic keys for my own GitHub Actions builder.
2. Modifying `image-versions.yaml` and `build.yml` to pull from the standard `bazzite` desktop base instead of `bazzite-deck`.
3. Stripping out the handheld-specific autologin cleanup scripts (since the standard desktop base doesn't have them anyway).

Everything else is standard Universal Blue infrastructure.

## Desktop Environments
Currently, this builds the **KDE Plasma** and GNOME variants.

## Installation / Rebasing Instructions

If you are already running an atomic Fedora/Universal Blue system and want to switch to this build, you need to execute a two-step rebase process to properly import the new security keys.

**Step 1: The Initial Pull (Unverified)**
Open your terminal and run this command to fetch the image and import the new public key:

rpm-ostree rebase ostree-unverified-registry:ghcr.io/dave9991/bazzite-dx:latest

Wait for the process to finish, and then reboot your system.

Step 2: Lock it Down (Signed)
Once you are booted into the new image, open your terminal again and run this command to ensure your system only accepts future updates mathematically signed by this repository's key:

rpm-ostree rebase ostree-image-signed:docker://ghcr.io/dave9991/bazzite-dx:latest

Wait for the process to finish, and reboot one final time.

Updates
Future updates can be pulled down manually via the standard atomic update command (rpm-ostree upgrade) or will happen automatically in the background via Bazzite's standard update services whenever GitHub Actions pushes a new daily build.
