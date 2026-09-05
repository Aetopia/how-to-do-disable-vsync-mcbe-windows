# How to disable V-Sync in Minecraft: Bedrock Edition (Windows)?
The definitive guide to disabling V-Sync for Minecraft: Bedrock Edition (Windows).

> [!IMPORTANT]
> This guide was made since there numerous methods of disabling V-Sync since:
> 
> - Configuring `gfx_vsync` isn't enough to disable V-Sync & is quite broken.
>
> - Not all hardware configurations react the same to said methods of disable V-Sync.

## Why is `gfx_vsync` shouldn't be used?
Most online recommend the following to disable V-Sync:
- Find `options.txt` in the game's data folder.
- Find `gfx_vsync` and set its `0` to disable V-Sync.

Pretty straight forward but `gfx_vsync` or the game's V-Sync Off implementation is quite broken.
- Essentially, it doesn't work as expected and behaves differently depending on the hardware.

Various bug reports have been documented that showcase this:
- https://bugs.mojang.com/browse/MCPE-110006
- https://bugs.mojang.com/browse/MCPE-166745

Additionally, here is a video showcase of the issues:
- https://youtube.com/watch?v=aLcjJbHO-tY

TLDR, the game's V-Sync Off implementation is broken since:
- The game can cap double the monitor's refresh rate.
- The game uncaps in windowed mode only not fullscreen.
- The game doesn't uncap its framerate on iGPU + dGPU laptops.

The exact reason for being broken can be seen here:
- https://learn.microsoft.com/windows/win32/direct3ddxgi/variable-refresh-rate-displays

The game doesn't explicitly add "screen tearing support" hence causing V-Sync Off to not work correctly.

## How to actually disable V-Sync?

> [!TIP]
> Try out each method & see what works for you!

### Disabling V-Sync at the driver level.

> [!CAUTION]
> - This method may not work if your device is a laptop & has a iGPU + dGPU.
> - This may not work if your GPU configuration software doesn't expose controls for V-Sync.

You may consider disabling V-Sync at the driver for Intel, AMD & NVIDIA GPUs.

- Open your GPU's configuration software i.e NVIDIA App, AMD Software or Intel Arc Control.

- Find the configuration page for V-Sync.
 
- You disable V-Sync globally or for Minecraft: Bedrock Edition specifically.

### Using clients to disable V-Sync.

If you are using a client then consider availing their 'V-Sync Off' feature.

- Launch your preferred client via their launcher.

- Go into client's settings or configuration section.

- Find the relevant option for disabling V-Sync.

> [!CAUTION]
> - Sometimes, clients might not be able to disable V-Sync correctly.
> - Consider disabling V-Sync via [your GPU's configuration software](#disabling-v-sync-at-the-driver-level).


### Using a dedicated mod for disabling V-Sync.

> [!CAUTION]
> Consider this as a last reliable resort which will work regardless of hardware.

> [!NOTE]
> - This mod can be used to fix [buggy V-Sync Off implementations in clients](#using-clients-to-disable-v-sync) also.

MCBE DirectX VSync Fixer is a standalone mod that fixes the game's V-Sync implementation.

This is done by adding "screen tearing support" as per [Microsoft's documentation](https://learn.microsoft.com/windows/win32/direct3ddxgi/variable-refresh-rate-displays).

- Follow the install instructions as [mentioned here](https://github.com/Aetopia/MCBE.DirectX.VSync.Fixer).

- Disable `gfx_vsync` by editing all instances of `options.txt` in the game's data folder.
    - The mod uses this to control V-Sync hence the user remains in control.