## 🇰🇷 RHI API - Tools 플러그인 사용 가이드

이 플러그인에는 아래 스크린샷에서 볼 수 있는 9개의 노드가 포함되어 있습니다.

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

이 플러그인은 Unreal Engine 5.4 전용으로 개발 및 테스트되었습니다.

이 노드를 통해 플레이어는 게임 내에서 DirectX 11, DirectX 12, Vulkan을 자유롭게 전환할 수 있습니다. 플러그인은 선택한 실행 파라미터를 텍스트 설정 파일에 저장하며, 런처 역할을 하는 보조 실행 파일(`*_Launcher.exe`)을 사용할 수 있습니다. 이 런처는 플러그인 섹션이나 리포지토리 메인 페이지에 표시된 것과 동일한 아이콘을 사용합니다.

런처 아이콘을 변경하려면 서드파티 툴을 사용하실 수 있습니다.

---

### 프로젝트에 플러그인 추가하기

플러그인을 구매하고 프로젝트에 추가하려면:

`Resources` 폴더에서 다음 파일을 찾을 수 있습니다:

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

> 참고:  
>  
> - `launch_parameter.txt` 파일이 기본적으로 없을 수 있습니다 — 이는 **정상**입니다. 해당 파일은 `-dx11`, `-dx12`, `-vulkan` 형식으로 실행 파라미터를 저장합니다.  
> - **파일 이름은 반드시 `launch_parameter.txt` 이어야 합니다**, 확장자 포함. 이름이나 확장자가 다르면 플러그인이 인식하지 못합니다. 이 경우, 다음 실행 시 올바른 이름으로 새 파일이 생성됩니다.  
> - `RHI_API_Tools_Launcher.exe` 파일은 **자유롭게 이름 변경 가능**하지만, `_Launcher.exe`로 끝나는 것을 **권장**합니다. 이렇게 하면 사용자들이 메인 실행 파일과 쉽게 구분할 수 있습니다.

필요한 파라미터를 미리 설정하려면 `launch_parameter.txt` 파일을 수동으로 생성하거나 `Resources` 폴더에서 복사하십시오.

게임을 **Shipping** 모드로 패키징한 경우, 두 파일을 게임 루트 폴더의 메인 `.exe` 옆에 배치해야 플러그인이 정상 작동합니다.

<p align="center">
  <img src="../Images/PLUGIN_EXECUTABLE.png" width="512"/> 
</p>

---

### 플러그인 노드

모든 노드는 **RHI API Tools** 카테고리에 위치합니다.

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** — 에디터 또는 패키지된 게임에서 원하는 RHI API를 선택할 수 있습니다.

"Selected API" 문자열은 `"DX11"`, `"DX12"`, `"VULKAN"` 값을 반환합니다.

Boolean 변수 `"Force Use Launcher"`는 게임 빌드 타입과 상관없이 설정 파일 사용을 강제합니다 (Debug, Developing, Publish).

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — 현재 사용 중인 API를 반환합니다 (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — 지원되는 API 목록을 배열로 반환합니다 (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** — 사용 가능한 비디오 메모리 용량을 반환합니다 (`Float`).

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — 게임이 사용하는 비디오 메모리 용량을 반환합니다 (`Float`).

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — 총 지원 비디오 메모리 용량을 반환합니다 (`Float`).

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### 애플리케이션 실행 모드

7. **RHI Get Current Launch Mode** — 게임/프로젝트가 어떻게 실행되었는지와 빌드 모드 정보를 제공합니다.

실행 모드:

- `"SIMULATION"`
- `"PLAY_IN_EDITOR"`
- `"EDITOR"`
- `"DEDICATED_SERVER"`
- `"STANDALONE"`
- `"UNKNOWN"`

빌드 모드:

- `"SHIPPING"`
- `"DEVELOPMENT"`
- `"DEBUG"`
- `"UNKNOWNBUILD"`

결과는 다음과 같은 형식의 결합 문자열입니다:

`PLAY_IN_EDITOR_DEVELOPMENT`, `STANDALONE_SHIPPING` 등.

<p align="center">
  <img src="../Images/GET_LAUNCH_MODE.png" width="512"/> 
</p>

---

### GPU 정보

8. **RHI Get Current GPU Name** — GPU의 전체 이름과 제조사를 문자열로 반환합니다 (`String`).

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

9. **RHI Get GPU Driver Version** — GPU 드라이버 버전을 문자열로 반환합니다 (필요시 숫자로 변환 가능).

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

10. **RHI Get GPU Vendor** — GPU 제조사 이름을 반환합니다 (`String`).

<p align="center">
  <img src="../Images/GET_GPU_VENDOR.png" width="512"/> 
</p>

---

### 플러그인 구조

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. 플러그인 내 `Content` 폴더에는 다음이 포함되어 있습니다:

   - 디버그 인터페이스가 포함된 샘플 맵
   - 모든 기능을 보여주는 위젯

<p align="center">
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
</p>

이 파일들은 UE 5.4 에디터의 플러그인 폴더에서 바로 사용할 수 있으며, 필요시 프로젝트로 복사할 수 있습니다.

2. 플러그인 인터페이스는 직관적이며 모든 기능을 시각적으로 보여줍니다.

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. 위젯의 Event Graph에 모든 노드가 배치되어 있습니다.

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

질문이나 문제가 있으시면 Discord에 참여해 주세요: https://discord.gg/Yb9h4XGbWN
