## 🇹🇷 RHI API - Tools Eklenti Kullanım Kılavuzu

Bu eklenti, aşağıdaki ekran görüntüsünde görebileceğiniz 9 farklı node içerir:

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

Eklenti yalnızca Unreal Engine 5.4 için geliştirilmiş ve test edilmiştir.

Bu node'lar oyuncuların oyun içerisinden DirectX 11, DirectX 12 ve Vulkan arasında geçiş yapmasına olanak tanır. Eklenti, seçilen başlatma parametresini bir metin konfigürasyon dosyasına kaydeder ve bir başlatıcı olarak çalışan ikinci bir yürütülebilir dosya (`*_Launcher.exe`) kullanabilir. Bu başlatıcı, eklenti bölümünde veya bu depo sayfasında gösterilenle aynı simgeyi taşır.

Başlatıcı simgesini değiştirmek isterseniz, üçüncü taraf araçları kullanabilirsiniz.

---

### Projenize Bağlama

Eklentiyi satın aldıysanız ve projenize eklemek istiyorsanız:

`Resources` klasöründe şu dosyaları bulacaksınız:

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

> Dikkat:  
>  
> - `launch_parameter.txt` dosyası varsayılan olarak bulunmayabilir — bu **normaldir**. Başlatma parametresini `-dx11`, `-dx12`, `-vulkan` formatında saklar.  
> - **Dosya adı mutlaka `launch_parameter.txt` olmalıdır**, uzantısı dahil. Farklı bir ad veya uzantı kullanılırsa, eklenti bu dosyayı kullanamaz — bu durumda bir sonraki başlatmada doğru isimle yeni bir dosya oluşturulur.  
> - `RHI_API_Tools_Launcher.exe` dosyasının adı **istediğiniz gibi olabilir**, ancak `_Launcher.exe` ile bitmesi **önerilir**. Böylece kullanıcılar başlatıcıyı ana yürütülebilir dosyadan kolayca ayırt edebilir.

Gerekli parametreyi önceden belirlemek için `launch_parameter.txt` dosyasını manuel olarak oluşturabilir veya `Resources` klasöründen kopyalayabilirsiniz.

Oyunu **Shipping** modunda paketlediyseniz, bu iki dosyayı ana `.exe` dosyasının yanına yerleştirin — aksi takdirde eklenti düzgün çalışmaz.

<p align="center">
  <img src="../Images/PLUGIN_EXECUTABLE.png" width="512"/> 
</p>

---

### Eklenti Node'ları

Tüm node'lar **RHI API Tools** kategorisinde bulunur.

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** — İstediğiniz RHI API'yi editörden veya paketlenmiş oyundan seçmenizi sağlar.

"Selected API" string'i `"DX11"`, `"DX12"` veya `"VULKAN"` değerini döner.

"Force Use Launcher" boolean değişkeni, oyun paketleme türü ne olursa olsun eklentinin konfigürasyon dosyasını kullanmasını zorlar (Debug, Developing veya Publish).

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — Mevcut API'yi döner (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — Desteklenen API'leri dizi olarak döner (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** — Kullanılabilir video belleği miktarını döner (`Float`).

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — Oyun tarafından kullanılan video belleği miktarını döner (`Float`).

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — Toplam desteklenen video belleği miktarını döner (`Float`).

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### Uygulama Başlatma Modu

7. **RHI Get Current Launch Mode** — Oyunun/projenin nasıl başlatıldığını ve derleme modunu bildirir.

Başlatma modları:

- `"SIMULATION"`
- `"PLAY_IN_EDITOR"`
- `"EDITOR"`
- `"DEDICATED_SERVER"`
- `"STANDALONE"`
- `"UNKNOWN"`

Derleme modları:

- `"SHIPPING"`
- `"DEVELOPMENT"`
- `"DEBUG"`
- `"UNKNOWNBUILD"`

Sonuç şu formatta birleşik bir string olur:

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

9. **RHI Get GPU Driver Version** — GPU sürücü versiyonunu string olarak döner (gerekirse sayıya dönüştürülebilir).

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

1. Eklenti içinde şu dosyaların bulunduğu `Content` klasörü vardır:

   - Örnek harita ve debug arayüzü
   - Tüm işlevleri gösteren bir widget

<p align="center">
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
</p>

Bu dosyalar UE 5.4 editörü üzerinden doğrudan erişilebilir. İsterseniz projeye kopyalayabilirsiniz.

2. Eklenti arayüzü sezgiseldir ve tüm işlevleri gösterir:

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. Widget'ın Event Graph bölümünde tüm node'lar yer alır:

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

Sorularınız veya sorunlarınız varsa Discord sunucumuza katılın: https://discord.gg/Yb9h4XGbWN
