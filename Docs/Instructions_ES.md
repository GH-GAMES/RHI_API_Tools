## 🇪🇸 Instrucción para usar el plugin RHI API - Tools

Este plugin contiene 9 nodos diferentes, que puedes ver en la captura de pantalla a continuación:

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

Este plugin ha sido desarrollado y probado únicamente para Unreal Engine 5.4

Estos nodos permiten a los jugadores cambiar entre DirectX 11, 12 o Vulkan directamente desde el juego. El plugin guarda el parámetro de inicio en un archivo de texto y permite usar un ejecutable secundario (Launcher) con el sufijo "*_Launcher.exe", que utiliza el mismo icono que puedes ver en la sección de plugins o en la página principal de este repositorio.

Si deseas cambiar el icono del archivo .exe del launcher, puedes utilizar programas externos.

---

### Integración en tu proyecto

Si has comprado el plugin y quieres añadirlo a tu proyecto:

En la carpeta `Resources` encontrarás los siguientes archivos:

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

> Ten en cuenta:  
>  
> - El archivo `launch_parameter.txt` puede estar **ausente por defecto** — esto es **completamente normal**. Este archivo almacena el parámetro de inicio en el formato `-dx11`, `-dx12` o `-vulkan`.  
> - **El archivo debe llamarse exactamente `launch_parameter.txt`**, incluyendo la extensión `.txt`. Si el nombre o la extensión son incorrectos, el plugin no podrá utilizarlo — en ese caso se generará automáticamente un nuevo archivo con el nombre correcto en el siguiente inicio.  
> - El archivo `RHI_API_Tools_Launcher.exe` puede tener **cualquier nombre**, pero se **recomienda** mantener el sufijo `_Launcher.exe`, ya que ayuda a los usuarios a distinguirlo fácilmente del ejecutable principal.

Puedes definir el parámetro de inicio deseado creando manualmente el archivo `launch_parameter.txt` o copiándolo desde la carpeta `Resources`.

Si has empaquetado el juego en modo **Shipping**, coloca ambos archivos junto al `.exe` principal en la carpeta raíz del juego — solo así el plugin funcionará correctamente.

<p align="center">
  <img src="../Images/PLUGIN_EXECUTABLE.png" width="512"/> 
</p>

---

### Nodos del plugin

Todos los nodos se encuentran en la categoría **RHI API Tools**:

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** – Permite seleccionar el API de renderizado deseado directamente desde el editor o en el juego empaquetado.

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** – Devuelve el API actual utilizado (DX11, DX12, VULKAN)

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** – Devuelve un array de strings con los APIs soportados (DX11, DX12, VULKAN)

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** – Muestra cuánta memoria de video está disponible (Float)

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** – Devuelve la cantidad de VRAM usada por el juego (Float)

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** – Muestra la cantidad total de memoria de video soportada por tu GPU (Float)

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### Información de GPU

7. **RHI Get Current GPU Name** – Devuelve el nombre y fabricante completo de la tarjeta gráfica (String)

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

8. **RHI Get GPU Driver Version** – Devuelve la versión del controlador de la GPU (String). Puede convertirse fácilmente en formato numérico si es necesario.

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

9. **RHI Get GPU Vendor** – Devuelve el nombre del fabricante de la GPU (String)

---

### Estructura del plugin

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. Dentro del plugin hay una carpeta llamada `Content`, que contiene dos archivos:

   - Un mapa con una interfaz de depuración
   - Un widget con una demostración visual de las funciones

<p align="center">
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
</p>

Estos archivos están disponibles directamente desde el editor de Unreal Engine 5.4. También puedes copiarlos directamente a tu proyecto si lo deseas.

2. La interfaz no es compleja y muestra claramente todas las funciones del plugin:

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. Dentro del widget, además del Event Graph principal, hay otro gráfico que contiene todos los nodos del plugin:

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

Si tienes dudas o problemas con el plugin, puedes unirte a nuestro canal de Discord: https://discord.gg/Yb9h4XGbWN
