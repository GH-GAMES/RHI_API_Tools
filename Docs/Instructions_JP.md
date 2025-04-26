## 🇯🇵 RHI API - Tools プラグイン使用ガイド

このプラグインには、以下のスクリーンショットに示す 9 つのノードが含まれています。

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

このプラグインは Unreal Engine 5.4 専用に開発およびテストされています。

これらのノードを使用すると、プレイヤーはゲーム内から直接、DirectX 11、DirectX 12、Vulkan を切り替えることができます。プラグインは選択した起動パラメータをテキスト構成ファイルに保存し、ランチャーとして機能する二次実行ファイル（`*_Launcher.exe`）を使用できます。このランチャーは、プラグインセクションやリポジトリのメインページに表示されているものと同じアイコンを持ちます。

ランチャーのアイコンを変更したい場合は、サードパーティ製ツールをご利用ください。

---

### プロジェクトへの導入

プラグインを購入し、プロジェクトに追加したい場合：

`Resources` フォルダに次のファイルが含まれています。

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

> 注意:  
>  
> - `launch_parameter.txt` ファイルはデフォルトで存在しない場合がありますが、これは**正常**です。このファイルには `-dx11`、`-dx12`、`-vulkan` の形式で起動パラメータが保存されます。  
> - **ファイル名は必ず `launch_parameter.txt` にしてください**。名前や拡張子が異なると、プラグインは認識できません。この場合、次回起動時に正しい名前で新しいファイルが作成されます。  
> - `RHI_API_Tools_Launcher.exe` は**任意の名前**に変更できますが、`_Launcher.exe` という接尾辞を残すことを推奨します。これにより、ユーザーがメイン実行ファイルと区別しやすくなります。

必要なパラメータを事前に設定するには、`launch_parameter.txt` を手動で作成するか、`Resources` からコピーしてください。

ゲームを**Shipping** モードでパッケージ化した場合は、これら 2 つのファイルをゲームのルートフォルダにあるメイン `.exe` の隣に配置してください。これでプラグインが正しく動作します。

<p align="center">
  <img src="../Images/PLUGIN_EXECUTABLE.png" width="512"/> 
</p>

---

### プラグインノード

すべてのノードは **RHI API Tools** カテゴリ内にあります。

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** — エディタまたはパッケージ化されたゲーム内で希望する RHI API を選択できます。

"Selected API" 文字列は `"DX11"`、`"DX12"`、`"VULKAN"` を返します。

ブール値 `"Force Use Launcher"` は、ゲームのビルドタイプ（Debug、Developing、Publish）に関係なく、設定ファイルの使用を強制します。

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — 現在使用中の API を返します（`DX11`、`DX12`、`VULKAN`）。

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — サポートされている API の配列を返します（`DX11`、`DX12`、`VULKAN`）。

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** — 使用可能なビデオメモリ容量を返します（`Float`）。

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — ゲームによって使用されているビデオメモリ容量を返します（`Float`）。

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — サポートされている総ビデオメモリ容量を返します（`Float`）。

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### アプリケーション起動モード

7. **RHI Get Current Launch Mode** — ゲーム/プロジェクトの起動方法とビルドモードに関する情報を提供します。

起動モードの例：

- `"SIMULATION"`
- `"PLAY_IN_EDITOR"`
- `"EDITOR"`
- `"DEDICATED_SERVER"`
- `"STANDALONE"`
- `"UNKNOWN"`

ビルドモードの例：

- `"SHIPPING"`
- `"DEVELOPMENT"`
- `"DEBUG"`
- `"UNKNOWNBUILD"`

結果は次のような形式の結合文字列になります：

`PLAY_IN_EDITOR_DEVELOPMENT`、`STANDALONE_SHIPPING` など。

<p align="center">
  <img src="../Images/GET_LAUNCH_MODE.png" width="512"/> 
</p>

---

### GPU情報

8. **RHI Get Current GPU Name** — GPU の正式名称とベンダー名を文字列で返します（`String`）。

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

9. **RHI Get GPU Driver Version** — GPU ドライバのバージョンを文字列で返します（必要に応じて数値に変換可能）。

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

10. **RHI Get GPU Vendor** — GPU のベンダー名を返します（`String`）。

<p align="center">
  <img src="../Images/GET_GPU_VENDOR.png" width="512"/> 
</p>

---

### プラグイン構成

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. プラグイン内の `Content` フォルダには以下が含まれています：

   - デバッグインターフェース付きのサンプルマップ
   - プラグイン機能を示すウィジェット

<p align="center">
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
</p>

これらのファイルは UE 5.4 エディタ内のプラグインフォルダから直接アクセス可能です。必要に応じてプロジェクトにコピーすることもできます。

2. プラグインのインターフェースは直感的で、すべての機能を視覚的に確認できます。

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. ウィジェットの Event Graph にはすべてのノードが配置されています。

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

ご不明な点や問題がございましたら、ぜひ Discord にご参加ください： https://discord.gg/Yb9h4XGbWN
