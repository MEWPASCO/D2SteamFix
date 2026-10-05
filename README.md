# D2SteamFix

**D2SteamFix** is a launch wrapper for *Destiny 2* designed to help alleviate frame pacing and stuttering issues for Steam users. Before starting the game, it temporarily denies execute access to Steam's overlay renderer DLLs, then restores the original permissions after exiting.

> [!NOTE]
> Blocking the Steam Overlay DLLs can affect overlay-dependent features such as Steam Input, notifications, Game Recording, and Remote Play. This program temporarily changes only the ACL metadata of the overlay DLLs; it does not alter their contents, inject code, inspect process memory, modify game files, change Steam configuration, or bypass BattlEye.

---

## Installation

1. Download [steamfix.exe](https://pkg.d2checkpoint.com/D2SteamFix/steamfix.exe) and place it directly in your *Destiny 2* game directory.
2. Open *Destiny 2*'s launch options in Steam:
   * Right-click **Destiny 2** in your Steam library and select **Properties**.
   * Find the **Launch Options** field under the **General** tab.
3. Paste the following command (adjusting the path to match your actual installation directory):

```text
"C:\Program Files (x86)\Steam\steamapps\common\Destiny 2\steamfix.exe" %command%
```

<img width="842" height="601" alt="image" src="https://github.com/user-attachments/assets/3a0f7f0c-7f28-459d-80e8-197a4955f9ce" />

---

## Troubleshooting

### Windows Defender False Positive

The published binary may occasionally be flagged as a false positive by Windows Defender. Microsoft has confirmed this is a false positive and removed the detection signature. 

If your system still reports the old detection, follow the instructions in the [Windows Defender Guide](docs/WINDOWS_DEFENDER.md) to clear cached detections and update malware definitions.

### Steam Overlay Broken in Other Games

If the overlay stops working for other games after closing *Destiny 2*:
1. Completely close Steam, running games, and `SteamFix`.
2. Delete `GameOverlayRenderer64.dll` and `GameOverlayRenderer.dll` from your main Steam installation folder.
3. Restart Steam.

<img width="1123" height="633" alt="image" src="https://github.com/user-attachments/assets/0ddc6143-b12b-45b0-b79b-6e337d39bc7e" />

### Error: "The requested operation requires elevation"

1. Completely close Steam, running games, and `steamfix`.
2. Right-click `destiny2.exe` and `destiny2launcher.exe` and open their **Properties**.
3. Under the Compatibility tab, toggle **Run this program as an administrator** to **OFF** for both files.

<img width="405" height="548" alt="image" src="https://github.com/user-attachments/assets/fb797581-ab4c-46f0-8581-0d0b8cfb7da6" /> <img width="405" height="548" alt="image" src="https://github.com/user-attachments/assets/06e68c4e-d6b4-47ce-9ed0-6b2ed17946fb" />

### Error: "D2SteamFix failed during ACL recovery"

1. Completely close Steam, running games, and `steamfix`.
2. Delete `steamfix.dat` and/or `steamfix.dat.old` from your *Destiny 2* game folder (whichever files are currently present).

_No image present currently_

---

## Building from Source

### Prerequisites

Building D2SteamFix requires Windows and the Microsoft Visual C++ toolchain. Install either Visual Studio or Visual Studio Build Tools with the **Desktop development with C++** workload selected (ensure the MSVC compiler and Windows SDK are included).

### Build Commands

Run the following commands from a Visual Studio Developer Command Prompt:

```batch
make.cmd configure
make.cmd build
```
