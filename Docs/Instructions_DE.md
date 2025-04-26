## 🇩🇪 Anleitung zur Verwendung des Plugins RHI API - Tools

Dieses Plugin enthält 9 verschiedene Nodes, die Sie auf dem Screenshot unten sehen können:

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

Das Plugin wurde ausschließlich für Unreal Engine 5.4 entwickelt und getestet.

Diese Nodes ermöglichen es den Spielern, direkt im Spiel zwischen DirectX 11, DirectX 12 und Vulkan zu wechseln. Das Plugin speichert den ausgewählten Startparameter in einer Textkonfigurationsdatei und kann eine sekundäre ausführbare Datei (`*_Launcher.exe`) verwenden, die als Launcher fungiert — sie hat das gleiche Symbol wie im Plugin-Bereich oder auf der Hauptseite dieses Repositories angegeben.

Wenn Sie das Symbol des Launchers ändern möchten, können Sie Drittanbieter-Tools verwenden.

---

### Integration in Ihr Projekt

Wenn Sie das Plugin erworben haben und es zu Ihrem Projekt hinzufügen möchten:

Im Ordner `Resources` finden Sie folgende Dateien:

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

> Hinweis:  
>  
> - Die Datei `launch_parameter.txt` kann standardmäßig fehlen — das ist **normal**. Sie speichert den Startparameter im Format `-dx11`, `-dx12`, `-vulkan`.  
> - **Der Dateiname `launch_parameter.txt` muss exakt so bleiben**, inklusive der Erweiterung `.txt`. Bei Abweichungen kann das Plugin die Datei nicht verwenden — in diesem Fall wird beim nächsten Start eine neue Datei mit dem korrekten Namen erstellt.  
> - Die Datei `RHI_API_Tools_Launcher.exe` kann **beliebig benannt** werden, jedoch wird empfohlen, das Suffix `_Launcher.exe` beizubehalten, damit Nutzer den Launcher leichter vom Hauptprogramm unterscheiden können.

Sie können den gewünschten Parameter im Voraus festlegen, indem Sie die Datei `launch_parameter.txt` manuell erstellen oder aus dem Ordner `Resources` kopieren.

Wenn Sie das Spiel im **Shipping**-Modus gepackt haben, legen Sie beide Dateien neben die Haupt-`.exe` im Stammverzeichnis des Spiels — nur so funktioniert das Plugin korrekt.

<p align="center">
  <img src="../Images/PLUGIN_EXECUTABLE.png" width="512"/> 
</p>

---

### Plugin-Nodes

Alle Nodes befinden sich in der Kategorie **RHI API Tools**

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** — ermöglicht die Auswahl des gewünschten RHI API direkt im Editor oder im gepackten Spiel.

Im String "Selected API" erhalten Sie das Ergebnis im Format `"DX11"`, `"DX12"` oder `"VULKAN"`.

Die Boolean-Variable `"Force Use Launcher"` zwingt das Plugin, auf die Konfigurationsdatei zuzugreifen, unabhängig vom Spiel-Build-Typ: Debug, Developing oder Publish.

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — gibt das aktuell verwendete API zurück (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — gibt ein Array mit den unterstützten APIs zurück (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** — gibt die verfügbare Menge an Videospeicher zurück (`Float`).

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — gibt die vom Spiel belegte Menge an Videospeicher zurück (`Float`).

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — gibt die gesamte unterstützte Menge an Videospeicher zurück (`Float`).

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### Startmodus der Anwendung

7. **RHI Get Current Launch Mode** — liefert Informationen darüber, wie das Spiel/Projekt gestartet wurde, sowie den Build-Modus des Projekts.

Mögliche Startmodi:

- `"SIMULATION"`
- `"PLAY_IN_EDITOR"`
- `"EDITOR"`
- `"DEDICATED_SERVER"`
- `"STANDALONE"`
- `"UNKNOWN"`

Der Build-Modus kann folgende Werte haben:

- `"SHIPPING"`
- `"DEVELOPMENT"`
- `"DEBUG"`
- `"UNKNOWNBUILD"`

Das Ergebnis ist ein kombinierter String im Format:

`PLAY_IN_EDITOR_DEVELOPMENT`, `STANDALONE_SHIPPING` usw.

<p align="center">
  <img src="../Images/GET_LAUNCH_MODE.png" width="512"/> 
</p>

---

### GPU-Informationen

8. **RHI Get Current GPU Name** — gibt den vollständigen Namen der Grafikkarte und des Herstellers zurück (`String`).

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

9. **RHI Get GPU Driver Version** — gibt die Treiberversion der Grafikkarte als String zurück (bei Bedarf in eine Zahl umwandelbar).

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

10. **RHI Get GPU Vendor** — gibt den Namen des GPU-Herstellers zurück (`String`).

<p align="center">
  <img src="../Images/GET_GPU_VENDOR.png" width="512"/> 
</p>

---

### Plugin-Struktur

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. Im Plugin befindet sich der Ordner `Content`, welcher Folgendes enthält:

   - Eine Beispielkarte mit Debug-Interface
   - Ein Widget zur Demonstration aller Plugin-Funktionen

<p align="center">
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
</p>

Diese Dateien sind direkt im UE 5.4 Editor über den Plugin-Ordner zugänglich. Sie können sie auch in Ihr Projekt kopieren, wenn gewünscht.

2. Das Plugin-Interface ist intuitiv und zeigt alle Funktionen in Aktion:

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. Im Event Graph des Widgets sind alle Nodes des Plugins platziert:

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

Wenn Sie Fragen oder Probleme haben — treten Sie unserem Discord bei: https://discord.gg/Yb9h4XGbWN
