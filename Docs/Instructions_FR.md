## 🇫🇷 Manuel d'utilisation du plugin RHI API - Tools

Ce plugin contient 9 nœuds différents que vous pouvez voir sur la capture d'écran ci-dessous :

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

Ce plugin a été développé et testé exclusivement pour Unreal Engine 5.4

Ces nœuds permettent aux joueurs de basculer entre DirectX 11, DirectX 12 et Vulkan directement depuis le jeu. Le plugin enregistre le paramètre de lancement dans un fichier texte et peut utiliser un exécutable secondaire (`*_Launcher.exe`) qui sert de lanceur — il possède la même icône que celle affichée dans la section des plugins ou sur la page principale de ce dépôt.

Si vous souhaitez modifier l'icône de ce lanceur, vous pouvez utiliser des outils tiers.

---

### Intégration dans votre projet

Si vous avez acheté le plugin et souhaitez l'ajouter à votre projet :

Dans le dossier `Resources`, vous trouverez les fichiers suivants :

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

> À noter :  
>  
> - Le fichier `launch_parameter.txt` peut être **absent par défaut** — c’est **tout à fait normal**. Il contient le paramètre de lancement sous la forme `-dx11`, `-dx12` ou `-vulkan`.  
> - **Le fichier doit absolument s'appeler `launch_parameter.txt`**, avec l'extension `.txt`. Si le nom ou l’extension est incorrect, le plugin ne pourra pas l’utiliser — un nouveau fichier avec le bon nom sera alors généré automatiquement au prochain lancement.  
> - Le fichier `RHI_API_Tools_Launcher.exe` peut avoir **n’importe quel nom**, mais il est **recommandé** de conserver le suffixe `_Launcher.exe` — cela permet aux utilisateurs de l’identifier facilement comme étant le launcher, et non l’exécutable principal.

Vous pouvez définir à l'avance le paramètre souhaité en créant manuellement le fichier `launch_parameter.txt`, ou en le copiant depuis le dossier `Resources`.

Si vous avez empaqueté le jeu en mode **Shipping**, placez ces deux fichiers à côté du fichier `.exe` principal, dans le répertoire racine du jeu — c’est la seule façon pour que le plugin fonctionne correctement.

<p align="center">
  <img src="../Images/PLUGIN_EXECUTABLE.png" width="512"/> 
</p>

---

### Nœuds du plugin

Tous les nœuds se trouvent dans la catégorie **RHI API Tools**

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** — Permet de choisir l'API RHI souhaitée depuis l'éditeur ou depuis un jeu empaqueté.

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — Renvoie l’API actuellement utilisée (DX11, DX12, VULKAN)

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — Renvoie une liste (String Array) des API RHI prises en charge (DX11, DX12, VULKAN)

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** — Renvoie la quantité de mémoire vidéo disponible (Float)

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — Renvoie la mémoire utilisée par le jeu (Float)

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — Renvoie la mémoire vidéo totale supportée par votre carte graphique (Float)

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### Informations GPU

7. **RHI Get Current GPU Name** — Renvoie le nom complet et le fabricant de votre carte graphique (String)

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

8. **RHI Get GPU Driver Version** — Renvoie la version du pilote de votre carte graphique sous forme de chaîne (peut être convertie en nombre)

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

9. **RHI Get GPU Vendor** — Renvoie le nom du fabricant de votre GPU (String)

---

### Structure du plugin

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. Le dossier `Content` du plugin contient deux éléments :

   - Une carte avec une interface debug
   - Un widget avec l'interface utilisateur du plugin

<p align="center">
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
</p>

Ces fichiers sont accessibles directement dans Unreal Engine 5.4 depuis la structure du plugin. Vous pouvez les copier dans votre projet si vous le souhaitez.

2. L'interface est simple et démontre visuellement chaque fonctionnalité :

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. Dans le widget, un deuxième Event Graph contient tous les nœuds du plugin :

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

Si vous avez des questions ou des difficultés, rejoignez notre serveur Discord : https://discord.gg/Yb9h4XGbWN
