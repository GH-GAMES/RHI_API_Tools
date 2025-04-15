## 🇺🇸 Instruction for using the RHI API - Tools plugin in English:

This plugin contains 9 different nodes, which you can see in the screenshot below:

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

This plugin was developed and tested exclusively for Unreal Engine 5.4

These nodes allow players to switch between DirectX 11, DirectX 12, or Vulkan directly from the game. The plugin saves the selected launch parameter in a text config and also allows using a secondary executable acting as a launcher — it has the suffix "*_Launcher.exe" and the same icon you see in the plugin section or on the main page of this repository.

If you want to change the icon of the .exe that serves as a launcher, you can use third-party programs for such tasks.

If you have purchased the plugin and want to connect it to your project:

In the plugin folder under `Resources`, you will find files such as:

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

Note that `launch_parameter.txt` may not be present initially, and that’s completely fine — it only stores the launch parameter like (-dx11, -dx12, -vulkan).

So if you want to specify the launch parameter in advance, you can either copy this file from `Resources` or create it yourself and write the desired launch parameter in it.

If your game is packaged in Shipping mode, you must place these files next to the game’s main .exe file, in the root folder of the game. Only then will the plugin work correctly.

---

### About the Nodes:

All nodes are located in the **RHI API Tools** category.

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** — lets you choose the desired API directly from the editor or in a Shipping build.

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — returns the currently used RHI API (DX11, DX12, VULKAN)

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — returns a string array of all supported APIs (DX11, DX12, VULKAN)

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** — shows the amount of available GPU memory (Float)

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — shows how much VRAM is currently used by the game (Float)

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — shows the total amount of memory supported by your GPU (Float)

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### GPU Info

7. **RHI Get Current GPU Name** — returns your full GPU model name and vendor (String)

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

8. **RHI Get GPU Driver Version** — returns the GPU driver version (String). You can easily convert this into a number format if needed.

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

9. **RHI Get GPU Vendor** — returns the name of your GPU vendor (String)

---

### Plugin Structure

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. Inside the plugin you will find a `Content` folder that includes:
   - A map where you can run a debug interface
   - A UI widget that clearly shows all plugin features

<p align="center">
  <img src="../Images/RHI_API_Tools__INSIDE_CONTENT.png" width="512"/> 
</p>

These files are accessible directly from the Unreal Engine 5.4 editor through the plugin folder. You may also copy or move them to your own project if desired.

2. The interface itself is quite simple and demonstrates each function of the plugin:

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. Inside the widget, there is not only the main logic for the interface and plugin functions, but also a separate Event Graph where all the plugin nodes are placed:

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

If you encounter any issues or have questions, feel free to join our Discord channel: https://discord.gg/Yb9h4XGbWN
