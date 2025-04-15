## 🇰🇷 RHI API - Tools 플러그인 사용 설명서 (한국어)

이 플러그인에는 다음 스크린샷에 표시된 9개의 다양한 노드가 포함되어 있습니다:

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

이 플러그인은 **Unreal Engine 5.4** 버전에서만 개발되고 테스트되었습니다.

이 노드를 통해 플레이어는 게임 내에서 DirectX 11, 12 또는 Vulkan을 직접 전환할 수 있습니다. 플러그인은 시작 파라미터를 텍스트 파일로 저장할 수 있으며, "*_Launcher.exe" 접미사를 가진 별도의 실행 파일(런처)을 사용할 수 있습니다. 이 런처는 플러그인 메뉴 또는 이 저장소의 메인 페이지에서 볼 수 있는 아이콘을 그대로 사용합니다.

런처로 사용하는 .exe 파일의 아이콘을 변경하고 싶다면 외부 유틸리티를 사용할 수 있습니다.

---

### 플러그인을 구매하고 프로젝트에 통합하려면:

`Resources` 폴더에는 다음 파일이 포함되어 있습니다:

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

> ⚠️ `launch_parameter.txt` 파일은 기본적으로 존재하지 않을 수 있으며, 이는 정상입니다. 해당 파일은 `-dx11`, `-dx12`, `-vulkan`과 같은 실행 파라미터를 저장합니다.

시작 시 특정 API를 설정하려면 이 파일을 복사하거나 직접 작성하여 원하는 파라미터를 입력하면 됩니다.

게임이 Shipping 빌드로 패키징되었다면, 이 파일들을 게임의 루트 폴더(.exe가 있는 위치)에 배치해야 플러그인이 제대로 작동합니다.

---

### 노드 목록

모든 노드는 **RHI API Tools** 카테고리 내에 있습니다:

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API 노드

1. **RHI API Change** — 에디터 또는 Shipping 빌드에서 직접 API를 전환할 수 있습니다.

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — 현재 활성화된 RHI API(DX11, DX12, VULKAN)를 반환합니다.

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — 사용 가능한 RHI API 목록을 문자열 배열로 반환합니다.

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM 정보

4. **Get Available VRAM** — 사용 가능한 VRAM 용량을 반환합니다 (Float)

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — 현재 게임에서 사용하는 VRAM 용량을 반환합니다 (Float)

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — GPU가 지원하는 총 VRAM 용량을 반환합니다 (Float)

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### GPU 정보

7. **RHI Get Current GPU Name** — GPU의 전체 모델명 및 제조사를 문자열로 반환합니다

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

8. **RHI Get GPU Driver Version** — GPU 드라이버의 버전을 문자열로 반환합니다

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

9. **RHI Get GPU Vendor** — GPU 제조사의 이름을 문자열로 반환합니다

<p align="center">
  <img src="../Images/GET_GPU_VENDOR.png" width="512"/> 
</p>

---

### 플러그인 구조

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. 플러그인의 `Content` 폴더에는 다음 2개의 파일이 포함되어 있습니다:

   - 디버그 UI를 테스트할 수 있는 레벨 맵
   - 플러그인의 기능을 시각적으로 확인할 수 있는 위젯

<p align="center">
  <img src="../Images/RHI_API_Tools__INSIDE_CONTENT.png" width="512"/> 
</p>

이 파일들은 Unreal Editor의 플러그인 패널에서 직접 사용할 수 있으며, 프로젝트로 복사하여 사용할 수도 있습니다.

2. UI는 매우 직관적으로 구성되어 있으며 모든 기능이 명확하게 표시됩니다:

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. 위젯에는 플러그인의 모든 노드를 예시로 배치한 별도의 Event Graph 도 포함되어 있습니다:

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

### ❓ 도움이 필요하신가요?

문제가 발생했거나 질문이 있다면 Discord 커뮤니티에 참여해 주세요:  
👉 https://discord.gg/Yb9h4XGbWN
