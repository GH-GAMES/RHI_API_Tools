## 🇩🇪 Anleitung zur Verwendung des Plugins RHI API - Tools

Dieses Plugin enthält 9 verschiedene Nodes, die du im Screenshot unten sehen kannst:

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

Dieses Plugin wurde ausschließlich für Unreal Engine 5.4 entwickelt und getestet.

Die Nodes ermöglichen es Spielern, direkt im Spiel zwischen DirectX 11, 12 oder Vulkan zu wechseln. Das Plugin speichert den Startparameter in einer Textdatei und ermöglicht die Verwendung einer sekundären .exe-Datei (Launcher), die mit dem Suffix `*_Launcher.exe` benannt ist und dasselbe Symbol wie im Plugin-Fenster oder auf der Hauptseite dieses Repositories verwendet.

Wenn du das Symbol des Launchers ändern möchtest, kannst du dafür externe Tools nutzen.

---

### Plugin zu deinem Projekt hinzufügen

Wenn du das Plugin gekauft hast und es in dein Projekt einbinden möchtest:

Im Plugin-Ordner `Resources` findest du folgende Dateien:

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

> Hinweis: Die Datei `launch_parameter.txt` ist möglicherweise nicht vorhanden – das ist normal. Sie enthält nur den Startparameter im Format `-dx11`, `-dx12` oder `-vulkan`.

Du kannst den Parameter direkt setzen, indem du diese Datei erstellst oder aus dem `Resources`-Ordner kopierst und den gewünschten Startparameter hineinschreibst.

Wenn dein Spiel im **Shipping**-Modus gepackt wurde, musst du diese Dateien in das Hauptverzeichnis des Spiels neben die .exe-Datei legen. Nur dann funktioniert das Plugin korrekt.

---

### Plugin-Nodes

Alle Nodes befinden sich in der Kategorie **RHI API Tools**:

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** – Damit kannst du die gewünschte RHI-API direkt im Editor oder im Shipping-Build auswählen.

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** – Gibt die aktuell verwendete RHI API zurück (DX11, DX12, VULKAN)

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** – Gibt ein String-Array mit den unterstützten RHI-APIs zurück (DX11, DX12, VULKAN)

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** – Zeigt an, wie viel Videospeicher verfügbar ist (Float)

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** – Gibt den vom Spiel belegten Videospeicher zurück (Float)

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** – Zeigt den gesamten von deiner GPU unterstützten Videospeicher an (Float)

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### GPU-Informationen

7. **RHI Get Current GPU Name** – Gibt den vollständigen Namen und Hersteller deiner GPU zurück (String)

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

8. **RHI Get GPU Driver Version** – Gibt die Treiberversion deiner GPU zurück (String, kann in eine Zahl konvertiert werden)

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

9. **RHI Get GPU Vendor** – Gibt den Namen des GPU-Herstellers zurück (String)

---

### Plugin-Struktur

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. Im Plugin befindet sich der Ordner `Content`, der zwei Dateien enthält:

   - Eine Karte mit Debug-Interface
   - Ein Widget mit der Benutzeroberfläche

<p align="center">
  <img src="../Images/RHI_API_Tools__INSIDE_CONTENT.png" width="512"/> 
</p>

Diese Dateien sind direkt im Unreal Engine 5.4 Editor über das Plugin sichtbar. Du kannst sie auch in dein Projekt kopieren, wenn du möchtest.

2. Die Benutzeroberfläche ist einfach gehalten und zeigt jede Funktion des Plugins visuell:

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. Im Widget gibt es neben dem Hauptlogik-Graph auch einen Event Graph, in dem alle Nodes des Plugins platziert sind:

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

Wenn du Fragen oder Probleme hast, tritt unserem Discord-Server bei: https://discord.gg/Yb9h4XGbWN
