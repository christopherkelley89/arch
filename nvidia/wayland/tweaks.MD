# Wayland Tweaks

## Drivers 
- currently using nvidia-open-dkms 570 branch with Linux 614 custom TKG eevdf kernel 
- Prior was on zen kernel and have used nvidia open 
- Need to test with propietary driver to see if it reduces random monitor freezes in KDE Wayland sessions
This document outlines the key environment variables and settings required to improve the interaction between NVIDIA drivers and Wayland compositors, specifically under KDE. Th>
---

## Environment Variables

Add the following environment variables to your `~/.zshrc` file to improve NVIDIA + Wayland compatibility:

```bash
# Enable V-Sync and smooth GPU operation
export __GL_YIELD="USLEEP"
export __GL_SYNC_TO_VBLANK="1"
```

These settings achieve the following:

- **`__GL_YIELD="USLEEP"`**: Reduces latency and minimizes stuttering by forcing the GPU to yield to V-Sync.
- **`__GL_SYNC_TO_VBLANK="1"`**: Forces synchronization with the vertical blanking interval, which prevents screen tearing and improves frame pacing.

### Notes
- These tweaks are specifically for users running NVIDIA open drivers (570+ versions) with Wayland compositors like KDE.
- Make sure to add these variables to your session environment or Wayland compositor's configuration.
