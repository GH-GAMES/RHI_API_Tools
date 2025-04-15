## 🇯🇵 RHI API - Tools プラグイン使用ガイド（日本語）

このプラグインには、以下のスクリーンショットに示されている 9 種類のノードが含まれています：

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

このプラグインは **Unreal Engine 5.4** 専用に設計およびテストされています。

ノードを使用することで、プレイヤーはゲーム内で DirectX 11、12 または Vulkan を直接切り替えることができます。プラグインは起動パラメータをテキストファイルに保存し、「*_Launcher.exe」という名前のセカンダリ実行ファイル（ランチャー）を使用することもできます。このランチャーは、プラグインメニューやリポジトリのメインページに表示されているアイコンと同じものを使用しています。

もしランチャー .exe のアイコンを変更したい場合は、外部ツールを使用することをおすすめします。

---

### プラグインを購入してプロジェクトに導入するには：

`Resources` フォルダ内には以下のファイルが含まれています：

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

> ⚠️ `launch_parameter.txt` は初期状態では存在しない場合がありますが、それは正常です。このファイルには `-dx11`, `-dx12`, `-vulkan` などの起動パラメータが保存されます。

起動時に特定の API を選択したい場合は、このファイルをコピーして使用するか、新しく作成して希望のパラメータを書き込んでください。

ゲームが Shipping モードでパッケージ化されている場合は、これらのファイルをゲームのルートディレクトリ（.exe と同じ階層）に配置する必要があります。正しく配置されないと、プラグインは機能しません。

---

### ノード一覧

すべてのノードは **RHI API Tools** カテゴリに含まれています：

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API ノード

1. **RHI API Change** — エディタまたは Shipping ビルド内で API を選択できます。

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — 現在使用中の RHI API（DX11、DX12、VULKAN）を取得します。

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — 使用可能な RHI API を配列として返します。

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM 情報

4. **Get Available VRAM** — GPU の使用可能なメモリ量を取得します（Float）

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — ゲームによって使用されている VRAM を取得します（Float）

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — GPU の総メモリ容量を取得します（Float）

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### GPU 情報

7. **RHI Get Current GPU Name** — 使用中の GPU のモデル名とベンダー名を取得します（String）

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

8. **RHI Get GPU Driver Version** — GPU ドライバのバージョンを取得します（String）

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

9. **RHI Get GPU Vendor** — GPU のベンダー名を取得します（String）

---

### プラグイン構造について

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. プラグインの `Content` フォルダには以下の 2 つのファイルがあります：

   - デバッグ UI を起動するためのレベルマップ
   - インターフェースを視覚化したウィジェット

<p align="center">
  <img src="../Images/RHI_API_Tools__INSIDE_CONTENT.png" width="512"/> 
</p>

これらのファイルは Unreal Editor のプラグインフォルダから直接アクセスできます。必要に応じてプロジェクトへコピーまたは移動可能です。

2. UI は非常にシンプルで、すべての機能が明確に表示されます：

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. ウィジェット内には、全ノードの Blueprint 使用例が組み込まれています：

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

### ❓ サポートが必要ですか？

ご不明点があれば、Discord コミュニティへお気軽にご参加ください：  
👉 https://discord.gg/Yb9h4XGbWN
