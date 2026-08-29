# Use WristHub Dev Builds

Dev Builds are the newest in-progress WristHub updates. They arrive before Full Releases and can include experimental features or bugs. Use the Full Release channel if you prefer the most tested version.

## Turn on automatic Dev Build updates

1. Install `Plugins/WristHubUpdater.dll` from the WristHub ZIP into `BONELAB/Plugins`.
2. Start BONELAB and open WristHub.
3. Press the **gear button** in the top-right corner.
4. Open **About**.
5. Press **Channel** until it says **Dev Builds**.
6. Confirm the updater status says **Online**.

WristHub checks the Dev Builds channel and downloads a newer signed build when one is published. If an update needs to replace a file that BONELAB is using, close and reopen BONELAB once to finish it safely.

## Return to Full Releases

Open **Gear > About > Channel** and change the channel to **Full Releases**. Full Releases are the default and receive only official stable updates.

## Troubleshooting

- **Updater offline:** confirm `WristHubUpdater.dll` is in `BONELAB/Plugins`.
- **No update found:** verify **Channel** says **Dev Builds**, then restart BONELAB once.
- **Old build still shown:** close BONELAB fully and reopen it so a pending replacement can finish.
- **Quest does not update:** confirm the updater DLL was copied into Quest's BONELAB `Plugins` folder, not the PC installation.


