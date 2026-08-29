# WristHubOS SDK 3.0

The WristHubOS SDK lets a BONELAB code mod add a themed watch app without building another wrist menu. WristHub owns the VR layout, touch handling, animation, scaling, accessibility, and PC/Quest presentation. Your mod owns its values and actions.

## Quick start: build your first WristHub app

1. Install the .NET 6 SDK and create a normal BONELAB MelonLoader/LemonLoader code-mod project.
2. Copy the developer copy of `WristHub.SDK.dll` from this folder into a local `references` folder in your project.
3. Add it as a reference with `Private="false"`. This prevents your mod from shipping a second SDK DLL.
4. Implement `IWristHubAppProvider` on your normal mod class.
5. Register one permanent app ID and permanent control IDs. Never reuse an ID for a different action after release.
6. Add pages, buttons, toggles, sliders, choices, text fields, or live labels with the SDK helpers.
7. Build your project and copy only your own mod DLL into `BONELAB/Mods`. WristHub supplies the shared SDK at runtime.
8. Launch BONELAB and open **WristHub > Apps > Installed Apps**. Your app is detected automatically.
9. Test on both PCVR and Quest. Keep Unity work on the main thread and pause expensive updates while your page is hidden.
10. When publishing, declare WristHub as a dependency and do not include another `WristHub.SDK.dll` in your package.

The complete starter project is in `SampleMod`. Change its app ID, name, author, controls, and package metadata before publishing.

## Add the SDK reference

1. Reference `WristHub.SDK.dll` with `Private="false"`.
2. Implement `IWristHubAppProvider` on your normal MelonMod/LemonMod class.
3. Keep the returned `WristHubApp` and dispose it during deinitialization.
4. Declare the current WristHub package in the Thunderstore dependencies when integration is required.

```xml
<Reference Include="WristHub.SDK" HintPath="path/to/WristHub.SDK.dll" Private="false" />
```

```csharp
using WristHub.SDK;

public sealed class YourMod : MelonMod, IWristHubAppProvider
{
    private WristHubApp? _watchApp;

    public WristHubApp CreateWristHubApp()
    {
        if (_watchApp != null && !_watchApp.IsDisposed) return _watchApp;
        _watchApp = WristHubApi.RegisterApp(
            "yourname.yourmod", "Your Mod", "YourName", "1.0.0",
            "Useful controls on your wrist", "YM");

    _watchApp.PublishToCommunity(new WristHubCommunityProfile(
        WristHubCommunityCategory.Utility,
        "Quick wrist controls for Your Mod.",
        "https://your-project-page.example",
        "@YourDiscordName",
        new[] { "utility", "controls" }));

    _watchApp.PublishToStore(new WristHubStoreProfile(
        "YourTeam-YourPackage",
        WristHubCommunityCategory.Utility,
        "Quick wrist controls for Your Mod.",
        WristHubStorePlatform.All,
        "https://thunderstore.io/c/bonelab/p/YourTeam/YourPackage/",
        "@YourDiscordName"));

    _watchApp.Opened = () => StartVisibleUpdates();
    _watchApp.Closed = () => StopVisibleUpdates();

        _watchApp.Root.AddToggle("enabled", "Enabled", () => Enabled, value => Enabled = value);
        _watchApp.Root.AddSlider("power", "Power", 0, 10, 0.5, () => Power, value => Power = value);
        _watchApp.Root.AddButton("activate", "Activate", Activate);
        return _watchApp;
    }

    public override void OnDeinitializeMelon() => _watchApp?.Dispose();
}
```

Registered apps appear in **WristHubOS -> Installed Apps** and **Mod Apps**. Their controls inherit the user's theme, wrist, UI scale, haptics, Reduced Motion, and Quest performance settings.

## Drop-in installation

An SDK app is still a normal BONELAB code mod. Once its DLL is placed in the game's `Mods` folder, MelonLoader or LemonLoader loads it. WristHubOS detects any loaded mod implementing `IWristHubAppProvider`, calls `CreateWristHubApp` once, and adds the result to **Installed Apps** automatically. The user does not import an app separately inside WristHub.

Do not ship a private copy of `WristHub.SDK.dll` inside the app package. Reference it with `Private="false"` and declare WristHub as a Thunderstore dependency so every app uses the one SDK assembly supplied by WristHub.

## Community catalog

`PublishToCommunity` categorizes an app that is already installed and supplies its project and support information.

## Publish to the App Store

`PublishToStore` links the running app to its Thunderstore `Team-Package` namespace. WristHub's SDK Store only lists packages that declare the appropriate WristHub package as a dependency. Thunderstore Mod Assistant remains responsible for dependencies, installation, updates, and queued removal.

Downloaded code apps are never hot-loaded. They remain queued until BONELAB restarts, then normal Melon initialization registers the app and makes its icon launchable. `Opened` and `Closed` are optional lifecycle callbacks for pausing visible-only work.

Use `SetIcon(WristHubIconData.FromPng(bytes))` for an embedded PNG no larger than 256 x 256. Without one, WristHub uses the Thunderstore icon or the short text monogram.

## Supported controls

- Page links and nested pages
- Buttons/actions
- On/off toggles
- Number sliders
- Multiple-choice controls
- Text fields using WristHub's keyboard
- Theme-friendly colors
- Read-only live labels
- Tooltips, notification counts, and system notifications

The complete working example is in `SampleMod/ExampleWristApp.cs`.

## Runtime information

`WristHubApi.Runtime` reports host availability, Quest, Fusion, the current theme, and the API version. `WristHubApi.RuntimeChanged` reports later changes.

Use `WristHubApi.Notify` for short notifications. Use `WristHubApi.OpenApp` only after a deliberate user action; WristHub safely queues it to its main thread.

## Safety and performance

- Keep callbacks fast and move file/network work to your own background task.
- Never change Unity objects from a background thread.
- Keep visible-page getters fast and allocation-light.
- WristHub isolates and throttles app failures, but apps should still explain recoverable errors.
- WristHub does not automatically network custom actions.
- Treat app and control IDs as permanent compatibility keys.

The SDK assembly keeps a stable `1.0.0.0` identity. SDK 2 apps remain compatible with SDK 3.

