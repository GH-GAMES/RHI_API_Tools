## 🇪🇸 Guía de Uso del Plugin RHI API - Tools

Este plugin contiene 9 nodos diferentes, que puedes ver en la siguiente captura de pantalla:

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

El plugin ha sido desarrollado y probado exclusivamente para Unreal Engine 5.4.

Estos nodos permiten a los jugadores cambiar entre DirectX 11, DirectX 12 y Vulkan directamente desde el juego. El plugin guarda el parámetro de inicio seleccionado en un archivo de configuración de texto y puede utilizar un archivo ejecutable secundario (`*_Launcher.exe`), que actúa como lanzador — con el mismo icono que se muestra en la sección del plugin o en la página principal de este repositorio.

Si deseas cambiar el icono del lanzador, puedes usar herramientas de terceros.

---

### Integración en tu Proyecto

Si has adquirido el plugin y deseas añadirlo a tu proyecto:

- **Descarga `RHI_API_Tools_Launcher.exe`** desde el siguiente enlace:

**[RHI_API_Tools_Launcher.exe](https://github.com/GH-GAMES/RHI_API_Tools/blob/main/Launcher/RHI_API_Tools_Launcher.exe)**

- En la carpeta `Resources` encontrarás una plantilla del archivo de parámetros de inicio:

  - `launch_parameter.txt`

> Nota importante:  
>  
> - El archivo `launch_parameter.txt` puede no estar presente por defecto — esto es **normal**. Almacena el parámetro de inicio en formato `-dx11`, `-dx12`, `-vulkan`.  
> - **El nombre del archivo debe ser exactamente `launch_parameter.txt`**, con la extensión `.txt`. Si el nombre o la extensión es diferente, el plugin no podrá utilizarlo — en ese caso, se generará un nuevo archivo con el nombre correcto al siguiente inicio.  
> - El archivo `RHI_API_Tools_Launcher.exe` puede tener **cualquier nombre**, pero se **recomienda** mantener el sufijo `_Launcher.exe` para que los usuarios puedan distinguir fácilmente el lanzador del ejecutable principal.

Puedes establecer el parámetro necesario manualmente creando el archivo `launch_parameter.txt` o copiándolo desde la carpeta `Resources`.

Si has empaquetado el juego en modo **Shipping**, coloca ambos archivos junto al ejecutable principal `.exe` en la carpeta raíz del juego — solo así el plugin funcionará correctamente.

<p align="center">
  <img src="../Images/PLUGIN_EXECUTABLE.png" width="512"/> 
</p>

---

### Nodos del Plugin

Todos los nodos se encuentran en la categoría **RHI API Tools**.

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** — permite seleccionar la API RHI deseada directamente desde el editor o en el juego empaquetado.

El string "Selected API" devuelve el resultado en formato `"DX11"`, `"DX12"` o `"VULKAN"`.

La variable booleana `"Force Use Launcher"` obliga al plugin a usar la configuración sin importar el tipo de empaquetado del juego: Debug, Developing o Publish.

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — devuelve la API actual (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — devuelve un array con las APIs soportadas (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** — devuelve la cantidad de memoria de video disponible (`Float`).

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — devuelve la cantidad de VRAM utilizada por el juego (`Float`).

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — devuelve la cantidad total de VRAM soportada (`Float`).

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### Modo de Inicio de la Aplicación

7. **RHI Get Current Launch Mode** — obtiene información sobre cómo se inició el juego/proyecto, así como el modo de compilación.

Modos de inicio posibles:

- `"SIMULATION"`
- `"PLAY_IN_EDITOR"`
- `"EDITOR"`
- `"DEDICATED_SERVER"`
- `"STANDALONE"`
- `"UNKNOWN"`

Modos de compilación posibles:

- `"SHIPPING"`
- `"DEVELOPMENT"`
- `"DEBUG"`
- `"UNKNOWNBUILD"`

El resultado es una cadena combinada en formato:

`PLAY_IN_EDITOR_DEVELOPMENT`, `STANDALONE_SHIPPING`, etc.

<p align="center">
  <img src="../Images/GET_LAUNCH_MODE.png" width="512"/> 
</p>

---

### Información de la GPU

8. **RHI Get Current GPU Name** — devuelve una cadena con el nombre completo de la tarjeta gráfica y su fabricante (`String`).

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

9. **RHI Get GPU Driver Version** — devuelve la versión del driver de la GPU (se puede convertir a número si es necesario).

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

10. **RHI Get GPU Vendor** — devuelve el nombre del fabricante de la tarjeta gráfica (`String`).

<p align="center">
  <img src="../Images/GET_GPU_VENDOR.png" width="512"/> 
</p>

---

### Estructura del Plugin

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. Dentro del plugin se encuentra la carpeta `Content`, que contiene:

   - Un mapa de ejemplo con interfaz de depuración
   - Un widget que demuestra todas las funciones del plugin

<p align="center">
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
</p>

Estos archivos están disponibles directamente en el editor de UE 5.4 a través de la carpeta del plugin. También puedes copiarlos a tu proyecto si lo deseas.

2. La interfaz del plugin es intuitiva y muestra todas las funciones:

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. En la pestaña Event Graph del widget se encuentran todos los nodos del plugin:

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

Si tienes preguntas o problemas — únete a nuestro Discord: https://discord.gg/Yb9h4XGbWN
