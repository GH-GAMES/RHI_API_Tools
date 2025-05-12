## 🇰🇷 RHI API - Tools 플러그인 사용 가이드

이 플러그인에는 아래 스크린샷과 같이 9개의 다양한 노드가 포함되어 있습니다.

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

이 플러그인은 Unreal Engine 5.4 전용으로 개발 및 테스트되었습니다.

플레이어는 이 노드를 통해 게임 내에서 DirectX 11, DirectX 12, Vulkan을 자유롭게 전환할 수 있습니다. 플러그인은 선택된 실행 파라미터를 텍스트 설정 파일에 저장하며, 런처 역할을 하는 보조 실행 파일(`*_Launcher.exe`)을 사용할 수 있습니다. 아이콘은 플러그인 섹션이나 저장소 메인 페이지에 표시된 것과 동일합니다.

런처 아이콘을 변경하려면 서드파티 도구를 사용하실 수 있습니다.

---

### 프로젝트에 플러그인 추가하기

플러그인을 구매하고 프로젝트에 추가하려면:

- **다음 링크에서 `RHI_API_Tools_Launcher.exe` 를 다운로드하세요:**

**[RHI_API_Tools_Launcher.exe](https://github.com/GH-GAMES/RHI_API_Tools/blob/main/Launcher/RHI_API_Tools_Launcher.exe)**

- `Resources` 폴더에는 실행 파라미터용 프리셋 파일이 포함되어 있습니다:

  - `launch_parameter.txt`

> 참고 사항:  
>  
> - `launch_parameter.txt` 파일은 기본적으로 없을 수 있으며, 이는 **정상**입니다. 이 파일은 `-dx11`, `-dx12`, `-vulkan` 형식의 실행 파라미터를 저장합니다.  
> - **파일 이름은 반드시 `launch_parameter.txt` 여야 합니다**, 확장자는 `.txt`입니다. 이름이나 확장자가 다를 경우 플러그인이 인식하지 못하며, 다음 실행 시 올바른 이름으로 새 파일이 생성됩니다.  
> - `RHI_API_Tools_Launcher.exe` 파일 이름은 **자유롭게 변경 가능**하지만, `_Launcher.exe` 접미사를 유지하는 것을 권장합니다. 이렇게 하면 메인 실행 파일과 쉽게 구분할 수 있습니다.

필요한 파라미터를 미리 설정하려면 `launch_parameter.txt` 파일을 수동으로 생성하거나 `Resources` 폴더에서 복사하세요.

게임을 **Shipping** 모드로 패키징한 경우, 두 파일을 게임 루트 폴더의 메인 `.exe` 파일 옆에 배치해야 플러그인이 제대로 작동합니다.

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

1. **RHI API Change** — 에디터나 패키지된 게임 내에서 원하는 RHI API를 선택할 수 있습니다.

"Selected API" 문자열은 `"DX11"`, `"DX12"`, `"VULKAN"` 값을 반환합니다.

불리언 `"Force Use Launcher"` 는 게임 패키징 타입(Debug, Developing, Publish)에 관계없이 설정 파일 사용을 강제합니다.

중요: 선택한 API를 게임/프로젝트에 적용하려면 재시작해야 합니다. 필요한 API는 런타임(Runtime) 모드가 아닌 시작 시점에 초기화되기 때문입니다. 런타임 모드에서는 원하는 매개변수만 변경할 수 있으며, 변경 사항은 완전한 재시작 후에만 적용됩니다.

추가: UE5 에디터 내부에서는 항상 프로젝트 설정에 지정된 API만 보입니다. 게임/프로젝트 미리보기가 이 매개변수로 시작되기 때문이며, 실제 시작 전에 이미 초기화가 완료되기 때문입니다.

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — 현재 사용 중인 API를 반환합니다 (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — 지원되는 API 목록을 반환합니다 (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** — 사용 가능한 비디오 메모리 용량을 반환합니다 (`Float`).

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — 게임이 사용 중인 비디오 메모리 용량을 반환합니다 (`Float`).

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — 총 지원 비디오 메모리 용량을 반환합니다 (`Float`).

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### 애플리케이션 실행 모드

7. **RHI Get Current Launch Mode** — 게임/프로젝트의 실행 방식과 빌드 모드를 확인할 수 있습니다.

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

결과는 다음과 같은 형식의 문자열로 반환됩니다:

`PLAY_IN_EDITOR_DEVELOPMENT`, `STANDALONE_SHIPPING` 등.

<p align="center">
  <img src="../Images/GET_LAUNCH_MODE.png" width="512"/> 
</p>

---

### GPU 정보

8. **RHI Get Current GPU Name** — GPU 전체 이름과 제조사를 반환합니다 (`String`).

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

9. **RHI Get GPU Driver Version** — GPU 드라이버 버전을 반환합니다 (필요시 숫자로 변환 가능).

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

1. 플러그인 내 `Content` 폴더에는 다음이 포함됩니다:

   - 샘플 맵과 디버그 인터페이스
   - 플러그인 기능을 보여주는 위젯

<p align="center">
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
</p>

이 파일들은 UE 5.4 에디터에서 직접 접근할 수 있으며, 필요시 프로젝트로 복사할 수 있습니다.

2. 플러그인 인터페이스는 직관적이며 모든 기능을 시각적으로 보여줍니다.

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. 위젯의 Event Graph에 모든 노드가 배치되어 있습니다.

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

질문이나 문제가 있으시면 Discord에 참여해주세요: https://discord.gg/Yb9h4XGbWN
