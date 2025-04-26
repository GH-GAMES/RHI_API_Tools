## 🇵🇹 Guia de Uso do Plugin RHI API - Tools

Este plugin contém 9 diferentes nodes, que você pode ver na captura de tela abaixo:

<p align="center">
  <img src="../Images/RHI_API_Tools_Nodes_List.png" alt="RHI API Tools V.1.0" width="900"/> 
</p>

<h1 align="center">RHI API Tools</h1>

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN.png" width="900"/> 
</p>

O plugin foi desenvolvido e testado exclusivamente para Unreal Engine 5.4.

Esses nodes permitem que os jogadores alternem entre DirectX 11, DirectX 12 e Vulkan diretamente do jogo. O plugin salva o parâmetro de inicialização selecionado em um arquivo de configuração de texto e pode usar um executável secundário (`*_Launcher.exe`), que atua como um launcher — com o mesmo ícone mostrado na seção de plugins ou na página principal deste repositório.

Se você quiser alterar o ícone do launcher, pode usar ferramentas de terceiros.

---

### Conectando ao seu Projeto

Se você comprou o plugin e deseja adicioná-lo ao seu projeto:

Na pasta `Resources` você encontrará os seguintes arquivos:

- `RHI_API_Tools_Launcher.exe`
- `launch_parameter.txt`

> Atenção:  
>  
> - O arquivo `launch_parameter.txt` pode não estar presente por padrão — isso é **normal**. Ele armazena o parâmetro de inicialização no formato `-dx11`, `-dx12`, `-vulkan`.  
> - **O nome do arquivo deve ser exatamente `launch_parameter.txt`**, com a extensão `.txt`. Se o nome ou a extensão forem diferentes, o plugin não conseguirá utilizá-lo — nesse caso, um novo arquivo com o nome correto será criado na próxima execução.  
> - O arquivo `RHI_API_Tools_Launcher.exe` pode ter **qualquer nome**, porém é **recomendado** manter o sufixo `_Launcher.exe` para facilitar a identificação do launcher em relação ao executável principal.

Você pode definir o parâmetro antecipadamente criando o arquivo `launch_parameter.txt` manualmente ou copiando da pasta `Resources`.

Se você empacotar o jogo no modo **Shipping**, coloque ambos os arquivos ao lado do `.exe` principal na raiz do jogo — só assim o plugin funcionará corretamente.

<p align="center">
  <img src="../Images/PLUGIN_EXECUTABLE.png" width="512"/> 
</p>

---

### Nodes do Plugin

Todos os nodes estão na categoria **RHI API Tools**.

<p align="center">
  <img src="../Images/RHI_API_Tools_Category.png" width="512"/> 
</p>

---

### API

1. **RHI API Change** — permite selecionar a API RHI desejada diretamente no editor ou no jogo empacotado.

A string "Selected API" retorna `"DX11"`, `"DX12"` ou `"VULKAN"`.

A variável booleana `"Force Use Launcher"` força o plugin a usar o arquivo de configuração independentemente do tipo de build: Debug, Developing ou Publish.

<p align="center">
  <img src="../Images/API_CHANGE.png" width="512"/> 
</p>

2. **Get Current API** — retorna a API atual (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/CURRENT_API.png" width="512"/> 
</p>

3. **Get Supported RHI API** — retorna uma lista com as APIs suportadas (`DX11`, `DX12`, `VULKAN`).

<p align="center">
  <img src="../Images/GET_SUPPORTED_API.png" width="512"/> 
</p>

---

### VRAM

4. **Get Available VRAM** — retorna a quantidade de memória de vídeo disponível (`Float`).

<p align="center">
  <img src="../Images/AVAILABLE_VRAM.png" width="512"/> 
</p>

5. **Get Reserved VRAM by Game** — retorna a quantidade de VRAM usada pelo jogo (`Float`).

<p align="center">
  <img src="../Images/RESERVED_VRAM_BY_GAME.png" width="512"/> 
</p>

6. **Get Total VRAM** — retorna a quantidade total de VRAM suportada (`Float`).

<p align="center">
  <img src="../Images/TOTAL_VRAM.png" width="512"/> 
</p>

---

### Modo de Inicialização da Aplicação

7. **RHI Get Current Launch Mode** — fornece informações sobre como o jogo/projeto foi iniciado e o modo de build.

Modos de inicialização possíveis:

- `"SIMULATION"`
- `"PLAY_IN_EDITOR"`
- `"EDITOR"`
- `"DEDICATED_SERVER"`
- `"STANDALONE"`
- `"UNKNOWN"`

Modos de build:

- `"SHIPPING"`
- `"DEVELOPMENT"`
- `"DEBUG"`
- `"UNKNOWNBUILD"`

O resultado é uma string combinada no formato:

`PLAY_IN_EDITOR_DEVELOPMENT`, `STANDALONE_SHIPPING`, etc.

<p align="center">
  <img src="../Images/GET_LAUNCH_MODE.png" width="512"/> 
</p>

---

### Informações da GPU

8. **RHI Get Current GPU Name** — retorna o nome completo da placa de vídeo e seu fabricante (`String`).

<p align="center">
  <img src="../Images/GET_CURRENT_GPU_NAME.png" width="512"/> 
</p>

9. **RHI Get GPU Driver Version** — retorna a versão do driver da GPU como string (pode ser convertida para número, se necessário).

<p align="center">
  <img src="../Images/GET_GPU_DRIVER_VERSION.png" width="512"/> 
</p>

10. **RHI Get GPU Vendor** — retorna o nome do fabricante da GPU (`String`).

<p align="center">
  <img src="../Images/GET_GPU_VENDOR.png" width="512"/> 
</p>

---

### Estrutura do Plugin

<p align="center">
  <img src="../Images/RHI_API_Tools_PLUGIN_CONTENT.png" width="512"/> 
</p>

1. Dentro do plugin há uma pasta `Content` que contém:

   - Mapa de exemplo com interface de debug
   - Widget demonstrando todas as funções do plugin

<p align="center">
  <img src="../Images/RHI_API_Tools_INSIDE_CONTENT.png" width="512"/> 
</p>

Esses arquivos estão disponíveis diretamente no editor UE 5.4 através da pasta do plugin. Você também pode copiá-los para o seu projeto, se desejar.

2. A interface do plugin é intuitiva e mostra todas as funcionalidades em ação:

<p align="center">
  <img src="../Images/INTERFACE_EXAMPLE.png" width="900"/> 
</p>

3. Todos os nodes do plugin estão organizados no Event Graph do widget:

<p align="center">
  <img src="../Images/BLUEPRINT_EXAMPLES.png" width="512"/> 
</p>

---

Se você tiver dúvidas ou problemas — junte-se ao nosso Discord: https://discord.gg/Yb9h4XGbWN
