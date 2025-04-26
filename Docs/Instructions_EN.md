## 🇬🇧 RHI API - Tools Plugin User Guide

This plugin contains 9 different nodes, which you can see in the screenshot below:

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

The plugin is developed and tested exclusively for Unreal Engine 5.4.

These nodes allow players to switch between DirectX 11, DirectX 12, and Vulkan directly from the game. The plugin saves the selected launch parameter in a text config file and can use a secondary executable (`*_Launcher.exe`), which acts as a launcher — it shares the same icon as shown in the plugin section or on the main page of this repository.

If you want to change the launcher icon, you can use third-party tools.

---

### Integration into Your Project

If you purchased the plugin and want to add it to your project:

In the `Resources` folder, you will find the following files:

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

> Note:  
>  
> - The `launch_parameter.txt` file may be missing by default — this is **normal**. It stores the launch parameter in the format `-dx11`, `-dx12`, `-vulkan`.  
> - **The file name must be exactly `launch_parameter.txt`**, with the `.txt` extension. If the name or extension differs, the plugin will not be able to use it — in this case, a new file with the correct name will be created on the next launch.  
> - The `RHI_API_Tools_Launcher.exe` file can be named **anything**, but it is **recommended** to keep the `_Launcher.exe` suffix to make it easier for users to distinguish the launcher from the main executable.

You can predefine the desired parameter by creating the `launch_parameter.txt` manually or copying it from `Resources`.

If you packaged your game in **Shipping** mode, place both files next to the main `.exe` in the root folder — only then will the plugin function correctly.

<p align="center">
  <img src="../Images/PLUGIN_EXECUTABLE.png" width="512"/> 
</p>

---

### Plugin Nodes

All nodes are located in the **RHI API Tools** category.

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** — allows you to select the desired RHI API directly from the editor or in the packaged game.

The "Selected API" string returns `"DX11"`, `"DX12"` or `"VULKAN"`.

The boolean `"Force Use Launcher"` forces the plugin to use the config file regardless of the game's packaging type: Debug, Developing, or Publish.

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — returns the current API (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — returns an array of supported APIs (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** — returns the amount of available video memory (`Float`).

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — returns the amount of video memory used by the game (`Float`).

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — returns the total supported video memory (`Float`).

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### Application Launch Mode

7. **RHI Get Current Launch Mode** — provides information on how the game/project was launched and indicates the project's build mode.

Possible launch modes:

- `"SIMULATION"`
- `"PLAY_IN_EDITOR"`
- `"EDITOR"`
- `"DEDICATED_SERVER"`
- `"STANDALONE"`
- `"UNKNOWN"`

Build modes:

- `"SHIPPING"`
- `"DEVELOPMENT"`
- `"DEBUG"`
- `"UNKNOWNBUILD"`

The node returns a combined string in the format:

`PLAY_IN_EDITOR_DEVELOPMENT`, `STANDALONE_SHIPPING`, etc.

<p align="center">
  <img src="../Images/GET_LAUNCH_MODE.png" width="512"/> 
</p>

---

### GPU Information

8. **RHI Get Current GPU Name** — returns a string with the full name of the GPU and its vendor (`String`).

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

9. **RHI Get GPU Driver Version** — returns the GPU driver version as a string (can be converted to a number if needed).

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

10. **RHI Get GPU Vendor** — returns the GPU vendor name (`String`).

<p align="center">
  <img src="../Images/GET_GPU_VENDOR.png" width="512"/> 
</p>

---

### Plugin Structure

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. Inside the plugin, there is a `Content` folder containing:

   - A sample map with a debug interface
   - A widget demonstrating all plugin functions

<p align="center">
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
</p>

These files are accessible directly in the UE 5.4 editor via the plugin folder. You can also copy them into your project if desired.

2. The plugin interface is intuitive and showcases all features:

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. All plugin nodes are placed in the widget's Event Graph:

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

If you have any questions or issues — join our Discord: https://discord.gg/Yb9h4XGbWN
