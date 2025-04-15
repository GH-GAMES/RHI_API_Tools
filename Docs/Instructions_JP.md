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

### プロジェクトへの統合

プラグインを購入し、プロジェクトに追加したい場合：

`Resources` フォルダーには次のファイルが含まれています：

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

> 注意事項：  
>  
> - `launch_parameter.txt` ファイルは**デフォルトでは存在しない場合があります** — これは**正常**です。このファイルには `-dx11`、`-dx12`、`-vulkan` の形式で起動パラメータが保存されます。  
> - **ファイル名は必ず `launch_parameter.txt` である必要があります**。拡張子 `.txt` を含め、正確な名前でなければなりません。名前または拡張子が間違っている場合、プラグインはそのファイルを認識できず、次回起動時に正しい名前で新しいファイルが自動的に作成されます。  
> - `RHI_API_Tools_Launcher.exe` ファイルは**任意の名前に変更できます**が、**末尾に `_Launcher.exe` を残すことを推奨します**。これにより、ユーザーが起動用ファイルとメインの `.exe` を区別しやすくなります。

起動パラメータは、`launch_parameter.txt` ファイルを手動で作成するか、`Resources` フォルダーからコピーすることで事前に設定できます。

ゲームを **Shipping モード** でパッケージ化している場合は、これらのファイルをメインの `.exe` と同じディレクトリ（ゲームのルート）に配置してください。これがプラグインを正常に動作させる唯一の方法です。

<p align="center">
  <img src="../Images/PLUGIN_EXECUTABLE.png" width="512"/> 
</p>

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
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
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
