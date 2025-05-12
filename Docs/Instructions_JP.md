## 🇯🇵 RHI API - Tools プラグイン使用ガイド

このプラグインには、以下のスクリーンショットに示す9つの異なるノードが含まれています。

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

このプラグインは Unreal Engine 5.4 専用に開発・テストされています。

これらのノードを使用すると、プレイヤーはゲーム内から直接、DirectX 11、DirectX 12、Vulkan を切り替えることができます。プラグインは選択された起動パラメータをテキスト設定ファイルに保存し、ランチャーとして機能する二次実行ファイル（`*_Launcher.exe`）を使用できます。アイコンはプラグインセクションやリポジトリのメインページに表示されるものと同じです。

ランチャーのアイコンを変更したい場合は、サードパーティ製ツールをご利用ください。

---

### プロジェクトへの導入方法

プラグインを購入し、プロジェクトに追加したい場合：

- **こちらから `RHI_API_Tools_Launcher.exe` をダウンロードしてください：**

**[RHI_API_Tools_Launcher.exe](https://github.com/GH-GAMES/RHI_API_Tools/blob/main/Launcher/RHI_API_Tools_Launcher.exe)**

- `Resources` フォルダには起動パラメータ用のプリセットファイルが含まれています：

  - `launch_parameter.txt`

> 注意事項:  
>  
> - `launch_parameter.txt` ファイルはデフォルトで存在しない場合がありますが、これは **正常** です。パラメータは `-dx11`、`-dx12`、`-vulkan` の形式で保存されます。  
> - **ファイル名は必ず `launch_parameter.txt` にする必要があります**。拡張子は `.txt` です。異なる場合、プラグインは認識できず、次回起動時に正しい名前のファイルが自動生成されます。  
> - `RHI_API_Tools_Launcher.exe` の名前は **自由** に変更できますが、識別しやすくするために `_Launcher.exe` を末尾に付けることを推奨します。

必要なパラメータは手動で作成するか、`Resources` フォルダからコピーして設定できます。

ゲームを **Shipping** モードでパッケージ化した場合、これら2つのファイルをゲームのルートディレクトリにあるメイン `.exe` の隣に配置してください。これによりプラグインが正常に動作します。

<p align="center">
  <img src="../Images/PLUGIN_EXECUTABLE.png" width="512"/> 
</p>

---

### プラグインノード

すべてのノードは **RHI API Tools** カテゴリにあります。

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** — エディタまたはパッケージ化されたゲーム内で、使用するRHI APIを選択できます。

"Selected API" 文字列は `"DX11"`、`"DX12"`、`"VULKAN"` のいずれかを返します。

ブール値 `"Force Use Launcher"` は、ゲームのパッケージタイプに関係なく、設定ファイルの使用を強制します（Debug、Developing、Publish）。

重要: 選択したAPIをゲーム/プロジェクトに適用するには、再起動が必要です。必要なAPIは起動時に初期化されるため、Runtimeモードでは初期化されません。Runtimeモードではパラメータを変更することは可能ですが、完全な再起動後にのみ適用されます。

追記: UE5エディタ内では、プロジェクト設定で指定されたAPIのみが表示されます。これは、ゲーム/プロジェクトのプレビューがこのパラメータで起動するためです。実際の起動前に初期化が行われるからです。

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — 現在使用中のAPIを返します (`DX11`, `DX12`, `VULKAN`)。

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — サポートされているAPIのリストを返します (`DX11`, `DX12`, `VULKAN`)。

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** — 利用可能なビデオメモリ量を返します (`Float`)。

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — ゲームによって使用されているVRAM量を返します (`Float`)。

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — サポートされている総ビデオメモリ容量を返します (`Float`)。

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### アプリケーション起動モード

7. **RHI Get Current Launch Mode** — ゲーム/プロジェクトの起動方法とビルドモードを取得します。

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

結果は以下の形式で返されます：

`PLAY_IN_EDITOR_DEVELOPMENT`、`STANDALONE_SHIPPING` など。

<p align="center">
  <img src="../Images/GET_LAUNCH_MODE.png" width="512"/> 
</p>

---

### GPU情報

8. **RHI Get Current GPU Name** — GPUのフルネームとベンダー名を返します (`String`)。

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

9. **RHI Get GPU Driver Version** — GPUドライバーのバージョンを返します（必要に応じて数値に変換可能）。

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

10. **RHI Get GPU Vendor** — GPUベンダー名を返します (`String`)。

<p align="center">
  <img src="../Images/GET_GPU_VENDOR.png" width="512"/> 
</p>

---

### プラグイン構成

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. プラグイン内の `Content` フォルダには以下が含まれています：

   - サンプルマップとデバッグインターフェース
   - プラグイン機能を示すウィジェット

<p align="center">
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
</p>

これらのファイルはUE5.4エディタ内で直接アクセスできます。必要に応じてプロジェクトにコピーすることも可能です。

2. プラグインのインターフェースは直感的で、すべての機能を表示します。

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. ウィジェットのEvent Graphにすべてのノードが配置されています。

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

ご不明な点や問題がある場合は、ぜひDiscordに参加してください： https://discord.gg/Yb9h4XGbWN
