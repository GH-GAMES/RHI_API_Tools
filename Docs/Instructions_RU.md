## 🇷🇺 Инструкция по использованию плагина RHI API - Tools

Данный плагин содержит в себе 9 различных нод, которые вы можете увидеть на скриншоте ниже:

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

Плагин разработан и протестирован исключительно для Unreal Engine 5.4

Эти ноды позволяют игрокам переключаться между DirectX 11, DirectX 12 и Vulkan напрямую из игры. Плагин сохраняет выбранный параметр запуска в текстовый конфиг и может использовать вторичный исполняемый файл (`*_Launcher.exe`), который действует как лаунчер — он имеет такую же иконку, как указано в разделе плагинов или на главной странице этого репозитория.

Если вы хотите изменить иконку лаунчера, вы можете использовать сторонние утилиты.

---

### Подключение к вашему проекту

Если вы приобрели плагин и хотите добавить его в свой проект:

В папке `Resources` вы найдете следующие файлы:

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

> Обратите внимание:  
>  
> - Файл `launch_parameter.txt` может отсутствовать по умолчанию — это **нормально**. Он хранит параметр запуска в формате `-dx11`, `-dx12`, `-vulkan`.  
> - **Имя файла `launch_parameter.txt` должно быть строго таким**, с расширением `.txt`. Если имя или расширение будет другим, плагин не сможет его использовать — в этом случае при следующем запуске будет создан новый файл с корректным именем.  
> - Файл `RHI_API_Tools_Launcher.exe` может называться **как угодно**, однако **рекомендуется** сохранять окончание `_Launcher.exe` — так пользователям будет проще отличить лаунчер от основного исполняемого файла.

Вы можете заранее задать нужный параметр, либо создав файл `launch_parameter.txt` вручную, либо скопировав его из `Resources`.

Если вы упаковали игру в режиме **Shipping**, разместите оба этих файла рядом с основным `.exe` в корне игры — только в этом случае плагин будет работать корректно.

<p align="center">
  <img src="../Images/PLUGIN_EXECUTABLE.png" width="512"/> 
</p>

---

### Ноды плагина

Все ноды находятся в категории **RHI API Tools**

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** — позволяет выбрать нужный RHI API прямо из редактора или в упакованной игре.

В String "Selected API" мы можем получить результат в формате `"DX11"`, `"DX12"` или `"VULKAN"`.

Boolean переменная `"Force Use Launcher"` позволяет нам принудительно заставить плагин обращаться к конфигу несмотря на то, какой у нас тип упаковки игры: Debug, Developing или Publish.

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — возвращает текущий API (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — возвращает массив строк с поддерживаемыми API (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** — возвращает количество доступной видеопамяти (`Float`).

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — возвращает количество видеопамяти, занятой игрой (`Float`).

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — возвращает общее количество поддерживаемой видеопамяти (`Float`).

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### Режим запуска приложения

7. **RHI Get Current Launch Mode** — позволяет получить данные о том, каким образом игра/проект был(а) запущены, а также указывает на режим сборки проекта.

В качестве режима запуска можно получить значения:

- `"SIMULATION"`
- `"PLAY_IN_EDITOR"`
- `"EDITOR"`
- `"DEDICATED_SERVER"`
- `"STANDALONE"`
- `"UNKNOWN"`

Режим сборки возвращает одно из следующих значений:

- `"SHIPPING"`
- `"DEVELOPMENT"`
- `"DEBUG"`
- `"UNKNOWNBUILD"`

Результат работы ноды — это объединённая строка в формате:

`PLAY_IN_EDITOR_DEVELOPMENT`, `STANDALONE_SHIPPING` и т.д.

<p align="center">
  <img src="../Images/GET_LAUNCH_MODE.png" width="512"/> 
</p>

---

### Информация о видеокарте

8. **RHI Get Current GPU Name** — возвращает строку с полным названием видеокарты и её вендора (`String`).

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

9. **RHI Get GPU Driver Version** — возвращает строку с версией драйвера видеокарты (при необходимости можно преобразовать в число).

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

10. **RHI Get GPU Vendor** — возвращает название вендора видеокарты (`String`).

<p align="center">
  <img src="../Images/GET_GPU_VENDOR.png" width="512"/> 
</p>

---

### Структура плагина

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. Внутри плагина находится папка `Content`, где хранятся:

   - Карта с примером и debug-интерфейсом
   - Виджет с демонстрацией всех функций плагина

<p align="center">
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
</p>

Эти файлы доступны напрямую в редакторе UE 5.4 через папку плагина. Вы также можете скопировать их в проект, если хотите.

2. Интерфейс плагина интуитивно понятный и показывает работу всех функций:

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. Во вкладке Event Graph в виджете размещены все ноды из плагина:

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

Если у вас возникли вопросы или сложности — присоединяйтесь к нашему Discord: https://discord.gg/Yb9h4XGbWN
