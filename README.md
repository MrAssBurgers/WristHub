<p align="center">
  <img src="assets/wristhub-banner.svg" alt="WristHub — the all-in-one BONELAB wrist menu for PCVR and Quest" width="100%">
</p>

<p align="center">
  <a href="https://github.com/MrAssBurgers/WristHub/releases/latest"><img alt="Download Full Release" src="https://img.shields.io/badge/DOWNLOAD-FULL%20RELEASE-2ea44f?style=for-the-badge&logo=github"></a>
  <a href="https://github.com/MrAssBurgers/WristHub/releases?q=wristhub-dev"><img alt="Browse Dev Builds" src="https://img.shields.io/badge/TRY-DEV%20BUILDS-009fe3?style=for-the-badge&logo=github"></a>
  <a href="docs/SDK-DEVELOPMENT.md"><img alt="Build a WristHub app" src="https://img.shields.io/badge/BUILD-WRISTHUB%20APPS-00c9aa?style=for-the-badge&logo=dotnet"></a>
</p>

<p align="center">
  <img alt="Universal build" src="https://img.shields.io/badge/BUILD-UNIVERSAL-ff9d42?style=flat-square">
  <img alt="PCVR and Quest" src="https://img.shields.io/badge/PLATFORM-PCVR%20%2B%20QUEST-23d5c9?style=flat-square">
  <img alt="BONELAB Fusion" src="https://img.shields.io/badge/BONELAB-FUSION-8a5cf5?style=flat-square">
  <img alt="Automatic updates" src="https://img.shields.io/badge/UPDATES-AUTOMATIC-2ea44f?style=flat-square">
</p>

<h1 align="center">WristHub</h1>

<p align="center">
  A universal all-in-one wrist menu for <strong>BONELAB</strong>, built for both <strong>PCVR</strong> and <strong>standalone Quest</strong>.
  Browse content, manage Fusion, use social tools, customize your avatar, and control your experience without leaving VR.
</p>

---

## Download WristHub

| Channel | Best for | Download |
|---|---|---|
| **Full Release** | Most players. Tested, stable, and updated less often. | **[Download the latest Full Release](https://github.com/MrAssBurgers/WristHub/releases/latest)** |
| **Dev Builds** | Beta testers who want the upcoming version and newest fixes immediately. Builds may contain unfinished features. | **[Open the Dev Builds section](https://github.com/MrAssBurgers/WristHub/releases?q=wristhub-dev)** |

> **New users should choose Full Release.** Dev Builds are for testing and can update frequently.

Every release ZIP contains the newest universal WristHub runtime, the standalone automatic updater, the public SDK DLL, a complete sample app, and player/developer tutorials.

### Guides

- **[Install WristHub on PCVR or Quest](docs/INSTALLATION.md)**
- **[Enable automatic Dev Build updates](docs/DEV-BUILDS.md)**
- **[Build your own WristHub app with the SDK](docs/SDK-DEVELOPMENT.md)**

## What WristHub includes

| Feature | What it does |
|---|---|
| **Avatar Hub** | Browse, search, install, preview, scan, equip, and manage avatars; access stats and cosmetics from your wrist. |
| **Spawner** | Search spawnables, view textured 3D previews, use recents and favorites, scan objects, and spawn by hand, float, front, or raycast. |
| **Fusion Browser** | Browse and join Fusion lobbies, view lobby information, switch servers, and manage your current lobby. |
| **Friends** | Add players by code, nearby detection, or WristHub-to-WristHub interaction; see online friends, requests, invites, chats, and groups. |
| **Calls** | Cross-lobby voice and video calling with a movable camera, POV options, mute, volume, speaker, and hang-up controls. |
| **Party Portals** | Open visible Fusion-synced portals that other WristHub users can enter, including two-way and remote portal controls. |
| **Soundboard** | Community and custom sounds, folders, search, local monitoring, and Fusion playback on PCVR and Quest. |
| **Voicemod** | PCVR control for supported Voicemod voices, sounds, monitoring, shortcuts, and microphone controls. |
| **Abilities** | Configurable ESP, phase, teleportation, fullbright, strength, health, jump, agility, density, finger guns, and shortcuts. |
| **Utilities** | Useful wrist tools, cosmetics and holster controls, display options, ray interaction, performance controls, and diagnostics. |
| **Themes** | Multiple visual styles, including the MrAssBurgers Edition, plus watch and interface customization. |
| **Automatic Updates** | Signed release channels for Full Release and Dev Builds with verified downloads and automatic fallback. |
| **Log Center** | Version-aware WristHub diagnostics that help identify PCVR and Quest problems without duplicate error spam. |

Some features depend on the installed platform, BONELAB/Fusion version, network availability, and required dependencies.

## Universal build

There is only **one WristHub package**. It detects whether the player is using PCVR or Quest and loads the correct platform support automatically.

- No separate PCVR package
- No separate Quest package
- One version number
- One update channel selection
- One download for everybody

## Installation

1. Download a WristHub release ZIP and close BONELAB.
2. Copy all three DLLs from `Mods` into `BONELAB/Mods`.
3. Copy `Plugins/WristHubUpdater.dll` into `BONELAB/Plugins`.
4. Launch BONELAB and confirm the green **WristHub Updater is online** startup message.

The `Docs` and `SDK` folders are reference material and do not need to be copied into BONELAB. See the **[complete PCVR and Quest installation guide](docs/INSTALLATION.md)** for exact paths and troubleshooting.

## Update channels

Full Releases are selected by default. To receive each new Dev Build automatically:

1. Open WristHub.
2. Press the **gear button** in the top-right.
3. Open **About**.
4. Press **Channel** until it says **Dev Builds**.
5. Confirm the updater says **Online**.

See the **[Dev Builds tutorial](docs/DEV-BUILDS.md)** for how updates finish and how to return to Full Releases.

## WristHub SDK

The release ZIP includes `SDK/WristHub.SDK.dll`, a complete sample mod, and a step-by-step guide. Regular players do not install the developer SDK folder. Mod creators can start with the **[WristHub SDK developer guide](docs/SDK-DEVELOPMENT.md)**.

## Safe automatic updates

WristHub downloads through this GitHub repository first, then uses the signed WristHub service as a fallback. Every archive must match its signed file size and SHA-256 hash before installation, so a failed or incomplete mirror cannot silently install.

## Repository purpose

This is WristHub's official public download and update repository. Releases are mirrored automatically so PCVR and Quest users receive the same verified package while keeping update delivery fast and inexpensive.

<p align="center">
  Made with care for the BONELAB community by <strong>MrAssBurgers</strong>.
</p>
