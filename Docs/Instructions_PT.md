## 🇵🇹 Instruções para usar o plugin RHI API - Tools

Este plugin contém 9 nós diferentes, que você pode ver na imagem abaixo:

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

Este plugin foi desenvolvido e testado exclusivamente para a versão Unreal Engine 5.4

Os nós permitem que os jogadores alterem entre DirectX 11, 12 ou Vulkan diretamente do jogo. O plugin salva o parâmetro de inicialização em um arquivo de texto e permite usar um executável secundário com sufixo "*_Launcher.exe", com o mesmo ícone que aparece na seção de plugins ou na página principal deste repositório.

Se você quiser alterar o ícone do .exe que funciona como launcher, pode usar programas externos para isso.

---

### Integração no seu projeto

Se você adquiriu o plugin e deseja adicioná-lo ao seu projeto:

Na pasta `Resources`, você encontrará os seguintes arquivos:

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

> Atenção:  
>  
> - O arquivo `launch_parameter.txt` pode estar **ausente por padrão** — isso é **completamente normal**. Ele armazena o parâmetro de inicialização no formato `-dx11`, `-dx12` ou `-vulkan`.  
> - **O arquivo deve ter exatamente o nome `launch_parameter.txt`**, incluindo a extensão `.txt`. Se o nome ou a extensão estiverem incorretos, o plugin não poderá utilizá-lo — nesse caso, um novo arquivo com o nome correto será criado automaticamente na próxima execução.  
> - O arquivo `RHI_API_Tools_Launcher.exe` pode ter **qualquer nome**, mas é **recomendado** manter o sufixo `_Launcher.exe` — isso ajuda os usuários a identificar facilmente que se trata do launcher e não do executável principal.

Você pode definir previamente o parâmetro desejado criando manualmente o arquivo `launch_parameter.txt` ou copiando-o da pasta `Resources`.

Se você empacotou o jogo no modo **Shipping**, coloque ambos os arquivos no mesmo diretório do executável principal `.exe` — somente assim o plugin funcionará corretamente.

<p align="center">
  <img src="../Images/PLUGIN_EXECUTABLE.png" width="512"/> 
</p>

---

### Nós do plugin

Todos os nós estão localizados na categoria **RHI API Tools**:

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** – Permite selecionar a API gráfica desejada diretamente do editor ou no jogo empacotado.

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** – Retorna qual API gráfica está atualmente em uso (DX11, DX12, VULKAN)

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** – Retorna um array de strings com as APIs suportadas (DX11, DX12, VULKAN)

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** – Mostra quanta memória de vídeo está disponível (Float)

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** – Mostra quanta memória de vídeo está sendo usada pelo jogo (Float)

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** – Mostra a quantidade total de VRAM disponível na sua GPU (Float)

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### Informações da GPU

7. **RHI Get Current GPU Name** – Retorna o nome e fabricante da sua GPU (String)

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

8. **RHI Get GPU Driver Version** – Retorna a versão do driver da sua GPU (String). Pode ser facilmente convertida em número, se necessário.

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

9. **RHI Get GPU Vendor** – Retorna o nome do fornecedor da GPU (String)

---

### Estrutura do plugin

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. Dentro do plugin, há uma pasta `Content` que contém dois arquivos:

   - Um mapa com a interface de depuração
   - Um widget com uma demonstração visual das funções

<p align="center">
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
</p>

Esses arquivos estão acessíveis diretamente pelo editor do Unreal Engine 5.4. Se desejar, você pode copiá-los para o seu projeto.

2. A interface é simples e apresenta claramente todas as funcionalidades do plugin:

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. Dentro do widget há um gráfico adicional chamado Event Graph onde todos os nós do plugin são demonstrados:

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

Se você tiver dúvidas ou problemas com o plugin, entre no nosso canal do Discord: https://discord.gg/Yb9h4XGbWN
