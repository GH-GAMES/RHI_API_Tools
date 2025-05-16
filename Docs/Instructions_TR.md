## 🇹🇷 RHI API - Tools Eklenti Kullanım Kılavuzu

Bu eklenti, aşağıdaki ekran görüntüsünde görebileceğiniz 9 farklı düğüm (node) içermektedir:

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

Eklenti, yalnızca Unreal Engine 5.4 için geliştirilmiş ve test edilmiştir.

Bu düğümler sayesinde oyuncular, oyun içerisinden DirectX 11, DirectX 12 ve Vulkan arasında geçiş yapabilir. Eklenti, seçilen başlatma parametresini bir metin konfigürasyon dosyasına kaydeder ve başlatıcı olarak çalışan ikincil bir yürütülebilir dosya (`*_Launcher.exe`) kullanabilir. Bu dosya, eklenti bölümünde veya bu deposunun ana sayfasında belirtilen aynı simgeyi kullanır.

Başlatıcı simgesini değiştirmek isterseniz, üçüncü parti araçlar kullanabilirsiniz.

---

### Projenize Eklentiyi Ekleme

Eklentiyi satın aldıysanız ve projenize eklemek istiyorsanız:

- **`RHI_API_Tools_Launcher.exe` dosyasını buradan indirebilirsiniz:**

**[RHI_API_Tools_Launcher.exe](https://github.com/GH-GAMES/RHI_API_Tools/blob/main/Launcher/RHI_API_Tools_Launcher.exe)**

- `Resources` klasöründe başlatma parametresi için bir şablon dosya bulunur:

  - `launch_parameter.txt`

> Dikkat:  
>  
> - `launch_parameter.txt` dosyası varsayılan olarak bulunmayabilir — bu **normaldir**. Parametreyi şu formatta saklar: `-dx11`, `-dx12`, `-vulkan`.  
> - **Dosya adı kesinlikle `launch_parameter.txt` olmalıdır**, uzantısı `.txt`. Farklı bir isim veya uzantı kullanılırsa eklenti dosyayı tanımaz ve bir sonraki başlatmada doğru isimle yeni bir dosya oluşturur.  
> - `RHI_API_Tools_Launcher.exe` dosyasının adı **istediğiniz gibi** olabilir, ancak `_Launcher.exe` son ekini korumanız **tavsiye edilir**. Böylece kullanıcılar başlatıcıyı ana yürütülebilir dosyadan kolayca ayırt edebilir.

Gerekli parametreyi önceden ayarlayabilir veya `Resources` klasöründen kopyalayabilirsiniz.

Oyununuzu **Shipping** modunda paketlediyseniz, bu iki dosyayı oyunun kök dizinindeki ana `.exe` dosyasının yanına yerleştirin — eklenti yalnızca bu şekilde doğru çalışacaktır.

<p align="center">
  <img src="../Images/PLUGIN_EXECUTABLE.png" width="512"/> 
</p>

---

### Eklenti Düğümleri

Tüm düğümler **RHI API Tools** kategorisinde bulunur.

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** — İstediğiniz RHI API'yi editörden veya paketlenmiş oyundan seçmenizi sağlar.

"Selected API" string değeri `"DX11"`, `"DX12"` veya `"VULKAN"` olarak döner.

`"Force Use Launcher"` boolean değişkeni, oyun paketleme türü ne olursa olsun yapılandırma dosyasını kullanmaya zorlar: Debug, Developing veya Publish.

Önemli: Seçtiğiniz API'nin oyununuzda/projenizde uygulanabilmesi için yeniden başlatmanız gerekmektedir. Çünkü ihtiyacımız olan API yalnızca başlangıç sırasında başlatılır, Runtime modunda değil. Runtime modunda yalnızca parametreyi istediğimiz şekilde değiştirebiliriz, ancak bu değişiklik yalnızca tam bir yeniden başlatma sonrasında uygulanacaktır.

Not: UE5 editörü içinde yalnızca proje ayarlarında belirtilen API'yi göreceksiniz. Çünkü oyun/proje önizlemesi bu parametreyle başlatılır, zira API asıl başlangıçtan önce başlatılmış olur.

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — Mevcut API'yi döner (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — Desteklenen API'lerin listesini döner (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** — Kullanılabilir video belleğini döner (`Float`).

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — Oyun tarafından kullanılan video belleğini döner (`Float`).

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — Toplam desteklenen video belleğini döner (`Float`).

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### Uygulama Başlatma Modu

7. **RHI Get Current Launch Mode** — Oyun/projenin nasıl başlatıldığını ve yapı modunu belirtir.

Başlatma modları:

- `"SIMULATION"`
- `"PLAY_IN_EDITOR"`
- `"EDITOR"`
- `"DEDICATED_SERVER"`
- `"STANDALONE"`
- `"UNKNOWN"`

Yapı modları:

- `"SHIPPING"`
- `"DEVELOPMENT"`
- `"DEBUG"`
- `"UNKNOWNBUILD"`

Sonuç şu formatta döner:

`PLAY_IN_EDITOR_DEVELOPMENT`, `STANDALONE_SHIPPING` vb.

<p align="center">
  <img src="../Images/GET_LAUNCH_MODE.png" width="512"/> 
</p>

---

### GPU Bilgisi

8. **RHI Get Current GPU Name** — GPU'nun tam adını ve üreticisini döner (`String`).

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

9. **RHI Get GPU Driver Version** — GPU sürücü versiyonunu döner (gerekirse sayıya dönüştürülebilir).

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

10. **RHI Get GPU Vendor** — GPU üretici adını döner (`String`).

<p align="center">
  <img src="../Images/GET_GPU_VENDOR.png" width="512"/> 
</p>

---

### Eklenti Yapısı

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. Eklenti içinde `Content` klasörü bulunur ve burada şunlar yer alır:

   - Örnek harita ve debug arayüzü
   - Tüm eklenti işlevlerini gösteren widget

<p align="center">
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
</p>

Bu dosyalar UE 5.4 editörü üzerinden doğrudan erişilebilir. İsterseniz projeye kopyalayabilirsiniz.

2. Eklenti arayüzü sezgiseldir ve tüm işlevleri gösterir:

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. Widget'ın Event Graph bölümünde tüm düğümler bulunur:

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

Herhangi bir sorunuz veya probleminiz varsa, Discord topluluğumuza katılın: https://discord.gg/Yb9h4XGbWN
