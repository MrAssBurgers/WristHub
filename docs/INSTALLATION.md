# Install WristHub

WristHub uses one universal download for PCVR and standalone Quest. Do not install separate platform editions together.

## Files to install

| File in the ZIP | Put it here |
| --- | --- |
| `Mods/WristHub.dll` | `BONELAB/Mods` |
| `Mods/WristHub.Core.dll` | `BONELAB/Mods` |
| `Mods/WristHub.SDK.dll` | `BONELAB/Mods` |
| `Plugins/WristHubUpdater.dll` | `BONELAB/Plugins` |

The `Docs` and `SDK` folders are reference material. Regular players do not copy them into BONELAB.

## PCVR

1. Close BONELAB.
2. Open the BONELAB installation folder.
3. Copy all three DLLs from the ZIP's `Mods` folder into `BONELAB/Mods`.
4. Copy `WristHubUpdater.dll` from the ZIP's `Plugins` folder into `BONELAB/Plugins`.
5. Replace older WristHub files when Windows asks.
6. Start BONELAB and wait for the green **WristHub Updater is online** message.

## Standalone Quest

1. Close BONELAB completely.
2. Using a file manager or a connected PC, open BONELAB's game files.
3. Copy all three DLLs from the ZIP's `Mods` folder into BONELAB's `Mods` folder.
4. Copy `WristHubUpdater.dll` from the ZIP's `Plugins` folder into BONELAB's `Plugins` folder.
5. Replace older WristHub files, then launch BONELAB.
6. Wait for the green **WristHub Updater is online** message.

## If the updater says Offline

- Confirm `WristHubUpdater.dll` is in `Plugins`, not `Mods`.
- Remove duplicate or renamed copies of WristHub DLLs.
- Make sure BONELAB was closed while replacing files.
- Restart BONELAB once after installing a newer updater version.
- Check that the headset or PC can reach GitHub.


