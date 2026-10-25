# Quiver Launcher

> 🇧🇷 **Português (BR)** · [🇺🇸 English version below](#quiver-launcher-1)

[![.NET 10](https://img.shields.io/badge/.NET-10-512BD4)](https://dotnet.microsoft.com/)
[![License](https://img.shields.io/github/license/tgeorgiadis/quiver-launcher)](https://github.com/tgeorgiadis/quiver-launcher/blob/main/LICENSE)
[![Windows](https://img.shields.io/badge/Windows-0078D4)](https://github.com/tgeorgiadis/quiver-launcher/releases/latest/download/QuiverLauncher-win-Portable.zip)
[![Linux](https://img.shields.io/badge/Linux-333333)](https://github.com/tgeorgiadis/quiver-launcher/releases/latest)
[![Android](https://img.shields.io/badge/Android-3A7D44)](https://github.com/tgeorgiadis/quiver-launcher/releases/latest/download/QuiverLauncher-android.apk)

[![Participe da comunidade no Discord](https://img.shields.io/badge/Join_the_community-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/5XRThpWHGk)
[![Apoie o Quiver no Patreon](https://img.shields.io/badge/Support_on_Patreon-B8394A?style=for-the-badge&logo=patreon&logoColor=white)](https://www.patreon.com/c/quiverlauncher)

> **Sobre** - O **Quiver Launcher** é um fork do [GithubLauncher](https://github.com/SirDiabo/GithubLauncher), ampliado com os recursos que eu queria: **filtros por tag**, **gerenciamento de biblioteca com o catálogo Quiver**, **suporte a gerenciamento de mods**, **melhorias de interface** e mais. Foi renomeado de GithubLauncher para evitar o uso da marca registrada GitHub.

![Captura de tela do Quiver Launcher](Assets/LauncherScreenshot.png)

Um launcher moderno para baixar, instalar e executar apps a partir de releases do GitHub e do GitLab. Com biblioteca pessoal, o [catálogo Quiver](https://quiverlauncher.com) e filtros flexíveis.

## Recursos

- **Filtros por tag** - Organize e filtre sua biblioteca com tags personalizadas
- **Busca na biblioteca** - Filtre a lista atual por nome, tags, repositório ou pasta
- **Apps gerenciados manualmente** - Adicione apps sem repositório no GitHub/GitLab; coloque os arquivos na pasta do app e abra-o pela biblioteca
- **Catálogo de apps** - Pesquise no catálogo do [quiverlauncher.com](https://quiverlauncher.com) por tipo de projeto, plataforma, console e uso de IA, veja como os apps rodam para outros jogadores e adicione-os à sua biblioteca
- **Releases do GitHub e GitLab** - Instale e atualize apps a partir dos assets de release do GitHub ou do gitlab.com
- **Suporte a gerenciamento de mods** - Navegue, instale e atualize mods do Thunderstore e do GameBanana
- **Atualizações automáticas** - Baixe e instale as releases mais recentes automaticamente
- **Gerenciamento de versões** - Verificação automática de versão e checagem de atualizações dentro do app
- **Melhorias de interface** - Layout refinado e controles na barra superior

## Primeiros passos

### Instalação

**Atenção se você está atualizando da versão 2.4.x ou anterior:** a atualização dentro do app não consegue migrar o Quiver Launcher 2.4.x para a versão 3.0 ou superior. Baixe uma versão 3.x nova do Quiver Launcher e copie sua biblioteca para ela. Veja [MIGRATING.md](MIGRATING.md).

**Windows**

1. Baixe o `QuiverLauncher-win-Portable.zip` em [Releases](https://github.com/tgeorgiadis/quiver-launcher/releases)
2. Extraia o arquivo
3. Execute o `QuiverLauncher.exe` a partir da pasta extraída

Sua biblioteca fica nessa mesma pasta (`apps.json`, `settings.json`, `Apps/`, `Cache/` ao lado de `current/`), então você pode mover o diretório inteiro para onde quiser.

```
QuiverLauncher/
├── QuiverLauncher.exe          # stub do launcher
├── current/            # binários do app (substituídos na atualização)
├── apps.json
├── settings.json
├── Apps/
└── Cache/
```

Para verificar a assinatura do `QuiverLauncher.exe`: clique com o botão direito → Propriedades → Assinaturas Digitais, ou rode `Get-AuthenticodeSignature .\QuiverLauncher.exe` no PowerShell.

**Linux**

1. Baixe o `QuiverLauncher-linux-x64.AppImage` ou o `QuiverLauncher-linux-arm64.AppImage` em [Releases](https://github.com/tgeorgiadis/quiver-launcher/releases)
2. Coloque o AppImage em uma pasta própria (ele cria os arquivos da biblioteca ao lado dele), marque-o como executável e rode:
   ```bash
   mkdir -p ~/QuiverLauncher
   mv QuiverLauncher*.AppImage ~/QuiverLauncher/
   cd ~/QuiverLauncher
   chmod +x QuiverLauncher*.AppImage
   ./QuiverLauncher*.AppImage
   ```
   Ou clique com o botão direito → Propriedades → Permissões → **Permitir executar o arquivo como programa**.  
   Downloads do GitHub não mantêm a permissão de execução; você precisa defini-la localmente após o download.

Os dados da biblioteca (`apps.json`, `settings.json`, `Apps/`, `Cache/`) ficam **ao lado do AppImage**, para que você possa mover a pasta inteira junto. Se o diretório do AppImage não tiver permissão de escrita (ex.: `/usr/local/bin`), o Quiver Launcher usa como alternativa `~/.local/share/QuiverLauncher/` (ou `$XDG_DATA_HOME/QuiverLauncher`).

```
MinhaPasta/
├── QuiverLauncher-linux-x64.AppImage
├── apps.json
├── settings.json
├── Apps/
└── Cache/
```

**macOS**

O suporte a macOS ainda está em desenvolvimento.

1. Baixe o pacote para macOS em [Releases](https://github.com/tgeorgiadis/quiver-launcher/releases)
2. Mantenha o `QuiverLauncher.app` em uma pasta com permissão de escrita (não apenas em `/Applications`, se você quiser dados portáteis)

Os dados da biblioteca ficam **ao lado** do `QuiverLauncher.app` nessa pasta. Se o diretório pai não tiver permissão de escrita, o Quiver Launcher usa como alternativa `~/Library/Application Support/QuiverLauncher/`.

```
MinhaPasta/
├── QuiverLauncher.app
├── apps.json
├── settings.json
├── Apps/
└── Cache/
```

### Dados da biblioteca e recuperação

O Quiver mantém snapshots verificados da biblioteca em `Backups/apps/`, ao lado do `apps.json`,
no Windows, Linux, macOS e Android. Veja [proteção e recuperação da biblioteca](docs/library-recovery.md) para saber como restaurar um snapshot caso a biblioteca seja danificada.

## Uso básico

1. Abra o aplicativo
2. Na primeira execução, abra o **Catálogo de apps** (requer internet), abra um app e escolha **Add to library** (Adicionar à biblioteca). Você também pode adicionar apps depois com **+ Add New Entry** (Adicionar nova entrada), inclusive apps **gerenciados manualmente** que não têm repositório no GitHub/GitLab. Sua biblioteca é armazenada no arquivo local [`apps.json`](apps.json)
3. Navegue pela sua biblioteca de apps na visualização Biblioteca
4. Clique no botão Download/Launch (Baixar/Executar) do app ou jogo que você quer usar

O Catálogo de apps lê o catálogo da API do [quiverlauncher.com](https://quiverlauncher.com) na primeira vez que você o abre, e novamente sempre que você pesquisa, ordena ou filtra. As avaliações são escritas no site: o botão **Write a review on the website** (Escrever uma avaliação no site) de cada app abre a página dele.

## Configuração

### Modo quiosque

**Settings → General → Kiosk mode** (Configurações → Geral → Modo quiosque) faz a próxima execução abrir em tela cheia e limitada a navegar e executar apps. Configurações, catálogo de apps e os controles de adicionar, atualizar e sair ficam ocultos. Pressione **Ctrl+Alt+K** para desbloquear a sessão atual e pressione novamente para bloquear sem reiniciar. Um PIN opcional pode ser definido nessa mesma seção; o Quiver armazena apenas um hash do PIN, e o PIN só é exigido para desbloquear.

`--kiosk` inicia uma sessão bloqueada sem alterar o `settings.json`, útil para atalhos de fliperama/cabine.

O modo quiosque não bloqueia a tecla Windows, Alt+Tab nem Ctrl+Alt+Del. Para uma máquina pública, faça do Quiver a própria sessão: Acesso Atribuído do Windows ou substituição do shell, ou uma sessão Gamescope ou cage no Linux que rode apenas o Quiver. O Modo Jogo do Steam Deck já mantém a área de trabalho fora do alcance.

### Tokens de API do GitHub / GitLab
Para evitar atingir os limites de requisições da API, você pode informar tokens de acesso pessoal em **Settings → Advanced** (Configurações → Avançado).

- **GitHub:** Crie um token clássico sem permissões especiais em GitHub Settings → Developer settings → Personal access tokens. Cole-o em **GitHub API Token**.
- **GitLab (opcional):** Crie um token de acesso pessoal com `read_api` em [GitLab personal access tokens](https://gitlab.com/-/user_settings/personal_access_tokens). Cole-o em **GitLab API Token**. Releases públicas do gitlab.com funcionam sem token.

Não compartilhe seus tokens.

### Mods (Thunderstore e GameBanana)

Os apps podem exibir um navegador de **Mods** quando `mods.path` e `mods.sources` estão definidos na entrada do catálogo (ou via **+ Add New Entry**).

`mods.layout` opcional:

| Valor | Comportamento |
|-------|----------|
| *(omitido)* / `flat` | Extrai os caminhos do arquivo compactado como estão para a pasta de mods (padrão; típico para pacotes `.nrm` do Thunderstore). |
| `folderPerMod` | Se o arquivo compactado tiver arquivos na raiz, envolve tudo em uma pasta nomeada a partir do nome do arquivo baixado (ex.: `Music-FRLG.zip` → `mods/Music-FRLG/`). Arquivos que já usam uma pasta de nível superior não são alterados. |

Use `folderPerMod` para apps que esperam cada mod em sua própria subpasta. Ative-o no JSON do catálogo ou com **Install each mod into its own folder** (Instalar cada mod em sua própria pasta) ao editar uma entrada.

**Formatos de URL de origem** (um por linha em Mod Sources):

| Provedor | Exemplos |
|----------|----------|
| Thunderstore | `https://thunderstore.io/c/banjo-recompiled/` ou o slug `banjo-recompiled` |
| GameBanana | `https://gamebanana.com/mods/games/24774`, `https://gamebanana.com/games/24774` ou apenas o id `24774` |

URLs do GameBanana são detectadas automaticamente (não é preciso o prefixo `gamebanana|`). Outros hosts ainda podem usar `provider|url`.

**Navegar e pesquisar**

- As duas fontes suportam rolagem infinita / carregar mais (mouse ou controle). A busca em múltiplas fontes mescla páginas de cada provedor.
- Mods com classificação de conteúdo / NSFW ficam **ocultos por padrão**. Use o chip **Include NSFW** para exibi-los (a escolha é salva nas configurações).
- Mods do GameBanana com vários arquivos para download mostram um seletor de arquivo ao Instalar/Atualizar. Arquivos **Zip**, **7z** e **RAR** são suportados.
- Mods do Thunderstore que listam dependências perguntam antes de instalar caso esses mods ainda não estejam instalados. **Yes** (Sim) instala as dependências que faltam (e o mod selecionado); **No** (Não) instala apenas o mod selecionado; **Cancel** (Cancelar) aborta sem instalar nada. **Update All** (Atualizar tudo) ainda baixa as dependências que faltam sem perguntar.

### Releases verificadas

Apps do catálogo Quiver seguem o que o [quiverlauncher.com](https://quiverlauncher.com) verificou:

- Atualizações, inclusive as automáticas, vão para a release que o Quiver verificou, e não simplesmente para a mais nova no GitHub ou GitLab.
- Todo download de um app do catálogo é conferido com o SHA-256 que o Quiver registrou quando a release saiu, e é recusado se tiver mudado. Os demais apps são conferidos com o checksum que o GitHub publica, quando existe.
- Instalar uma release que o Quiver ainda não verificou pede confirmação antes e explica por que ela ainda não foi verificada. Instalar uma que o Quiver bloqueou pede confirmação duas vezes. Atualizações automáticas nunca instalam nenhuma das duas.
- **Change version** (Trocar versão) marca cada release como Verified (Verificada), Unverified (Não verificada) ou Blocked (Bloqueada).

### Sua própria lista de apps

O Quiver Launcher não faz mais assinatura de listas de apps. Se você mantém sua própria lista, defina-a em **Settings → Advanced → My app list** (Configurações → Avançado → Minha lista de apps): um arquivo JSON local ou uma URL, como um link raw do GitHub. Os apps dela aparecem em **My app list** no Catálogo de apps, onde você pode adicioná-los à sua biblioteca. Uma lista adicionada em uma versão anterior é migrada automaticamente; se você tinha várias, a primeira habilitada é mantida.

A lista usa o mesmo formato do `apps.json`: um array `apps` com as entradas de app (os campos `name`, `description` e `version` de arquivos de lista antigos são ignorados).

#### Propriedades de uma entrada de app

Cada entrada de app requer as seguintes propriedades:

- **`name`** - Nome canônico do app/título (para ports, geralmente o nome do jogo). A exibição na biblioteca pode combinar isso com `project` via Settings → Library name style
- **`project`** *(opcional)* - Atribuição de projeto, equipe ou autor, exibida quando o estilo de nome da biblioteca inclui o projeto
- **`customDisplayName`** *(opcional)* - Rótulo personalizado do app na biblioteca; sempre tem prioridade sobre a combinação name/project
- **`repository`** *(obrigatório, exceto para apps gerenciados manualmente)* - O caminho do repositório no formato `usuario/repositorio` (GitHub) ou `namespace/projeto` (GitLab). O mesmo repositório pode ser usado por mais de um app desde que cada um tenha um `folderName` distinto (por exemplo, dois jogos distribuídos em uma única release do GitHub). Omita este campo para apps **gerenciados manualmente**: o Quiver cria `{Apps}/{folderName}` e você coloca os arquivos por conta própria. Não há gerenciamento de download ou atualização até que um repositório seja adicionado. Em **Edit App Entry** (Editar entrada do app), preencher um repositório promove o app para uma instalação gerenciada (os arquivos existentes são mantidos; a Atualização automática fica desligada até você atualizar). Limpar o repositório o rebaixa de volta para manual.
- **`repositorySource`** *(opcional)* - `github` (padrão quando omitido) ou `gitlab`. Ignorado para apps gerenciados manualmente. Versões antigas do Quiver Launcher ignoram este campo e tratam as entradas como somente GitHub.
- **`folderName`** - O nome da pasta dentro de Apps onde o app é instalado (prefira `Titulo-Projeto`, sem sufixos de tipo como `-Recomp`). Deve ser único. Para apps gerenciados manualmente, essa pasta é criada imediatamente como destino dos arquivos.
- **`releaseAssetFilter`** *(opcional)* - Trecho de texto (sem diferenciar maiúsculas/minúsculas) comparado com os nomes dos arquivos da release. Use quando um repositório distribui mais de um jogo, para que cada app baixe apenas seus arquivos (ex.: `EXIT1` / `EXIT2`). Ignorado para apps gerenciados manualmente.
- **`tags`** *(opcional)* - Tags livres (classificações como `recomp` / `decomp` ficam aqui, e não no título)
- **`appIconUrl`** - URL da imagem de ícone do app. Se for null, um ícone padrão será usado.

#### Exemplo de configuração

```json
{
    "apps": [
        {
            "name": "Majora's Mask",
            "project": "2 Ship 2 Harkinian",
            "repository": "HarbourMasters/2ship2harkinian",
            "folderName": "MajorasMask-2Ship2Harkinian",
            "tags": ["n64", "decomp", "harbour-masters"],
            "appIconUrl": null
        },
        {
            "name": "Example App",
            "repository": "username/example-app-repo",
            "folderName": "ExampleApp",
            "appIconUrl": null
        },
        {
            "name": "GitLab Example App",
            "repository": "namespace/example-project",
            "repositorySource": "gitlab",
            "folderName": "GitLabExampleApp",
            "appIconUrl": null
        },
        {
            "name": "Manually Managed Example",
            "project": "Itch drop",
            "folderName": "ManualExample",
            "tags": ["manual"],
            "appIconUrl": null
        }
    ]
}
```

## Suporte

Se você encontrar algum problema ou tiver dúvidas:
- [Abra uma issue](https://github.com/tgeorgiadis/quiver-launcher/issues)
- Consulte as issues existentes em busca de soluções
- Entre no [servidor do Discord](https://discord.gg/5XRThpWHGk)

## Licença

O Quiver Launcher é licenciado sob a [Licença MIT](LICENSE). Ele é baseado no
[GithubLauncher](https://github.com/SirDiabo/GithubLauncher) de SirDiabo, também licenciado sob MIT, e mantém seu aviso
de copyright.

A licença cobre o código, não o nome Quiver, o logotipo ou os ícones de apps. Veja [TRADEMARKS.md](TRADEMARKS.md) para saber como forks
e outros projetos podem usá-los.


## Para desenvolvedores: desenvolvimento local

Ao compilar e executar a partir do código-fonte, o Quiver Launcher não é uma instalação de release empacotada, então as verificações de autoatualização não fazem nada (e builds Debug sempre pulam as verificações automáticas). Defina `QuiverLauncher_SKIP_UPDATES=1` (ou `true`) para pular as verificações automáticas também em execuções locais de Release.

```powershell
# Debug: nenhuma variável de ambiente necessária
dotnet run --project QuiverLauncher.Desktop/QuiverLauncher.Desktop.csproj -c Debug

# Teste local de Release
$env:QuiverLauncher_SKIP_UPDATES = "1"
dotnet run --project QuiverLauncher.Desktop/QuiverLauncher.Desktop.csproj -c Release
```

Requer o **.NET 10 SDK**.

### Android

O Android usa um projeto principal separado (`QuiverLauncher.Android`) que instala e executa assets de release em **APK**. Binários de desktop (.exe, AppImage, Wine/Proton) não são suportados no dispositivo.

1. Instale o .NET 10 SDK e o workload do Android:
   ```powershell
   dotnet workload install android
   ```
2. Instale o Android SDK e o JDK 11+ ([configuração do Avalonia para Android](https://docs.avaloniaui.net/docs/platform-specific-guides/android/)).
3. Permita **Instalar apps desconhecidos** para o Quiver no emulador ou dispositivo.
4. Compile e implante:
   ```powershell
   dotnet build QuiverLauncher.Android/QuiverLauncher.Android.csproj -c Debug
   ```

Os dados de usuário de builds de debug não empacotadas no Windows continuam ficando ao lado da saída da build. Execuções não empacotadas no macOS/Linux (sem AppImage / pacote `.app`) usam os caminhos alternativos de suporte do SO (`~/Library/Application Support/QuiverLauncher/` ou `~/.local/share/QuiverLauncher/`).

### Testes automatizados

Execução local rápida (exclui o teste de integração de publicação, que é lento):

```powershell
dotnet test QuiverLauncher.sln -c Release --filter "Category!=Slow" --logger "console;verbosity=normal"
```

Suíte completa, incluindo o teste de integração de publicação (igual ao CI; o teste de publicação pode levar vários minutos):

```powershell
dotnet test QuiverLauncher.sln -c Release
```

Executar apenas o teste lento de empacotamento/publicação:

```powershell
dotnet test QuiverLauncher.sln -c Release --filter "Category=Slow"
```

As categorias de teste incluem segurança dos arquivos da biblioteca, adição de apps do catálogo, ida e volta do armazenamento de configurações, helpers de versão do launcher, montagem de comandos do executor no Windows, seleção de assets de download, verificação de status de jogos, helpers de ordenação/catálogo do ViewModel, comportamento de ocultar/filtrar do GameManager e testes smoke headless do Avalonia.

Colete a cobertura de código localmente com:

```powershell
dotnet test QuiverLauncher.sln -c Release --filter "Category!=Slow" --collect:"XPlat Code Coverage"
```

---

# Quiver Launcher

> 🇺🇸 **English (original)** · [🇧🇷 Versão em português acima](#quiver-launcher)

[![.NET 10](https://img.shields.io/badge/.NET-10-512BD4)](https://dotnet.microsoft.com/)
[![License](https://img.shields.io/github/license/tgeorgiadis/quiver-launcher)](https://github.com/tgeorgiadis/quiver-launcher/blob/main/LICENSE)
[![Windows](https://img.shields.io/badge/Windows-0078D4)](https://github.com/tgeorgiadis/quiver-launcher/releases/latest/download/QuiverLauncher-win-Portable.zip)
[![Linux](https://img.shields.io/badge/Linux-333333)](https://github.com/tgeorgiadis/quiver-launcher/releases/latest)
[![Android](https://img.shields.io/badge/Android-3A7D44)](https://github.com/tgeorgiadis/quiver-launcher/releases/latest/download/QuiverLauncher-android.apk)

[![Join the community on Discord](https://img.shields.io/badge/Join_the_community-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/5XRThpWHGk)
[![Support Quiver on Patreon](https://img.shields.io/badge/Support_on_Patreon-B8394A?style=for-the-badge&logo=patreon&logoColor=white)](https://www.patreon.com/c/quiverlauncher)

> **About** - **Quiver Launcher** is a fork of [GithubLauncher](https://github.com/SirDiabo/GithubLauncher), extended with the features I wanted: **tag filters**, **library management with the Quiver catalog**, **mod management support**, **UI improvements** and more. It was rebranded from GithubLauncher to avoid using the GitHub trademark.

![Quiver Launcher Screenshot](Assets/LauncherScreenshot.png)

A modern launcher for downloading, installing, and running apps from GitHub and GitLab releases. With a personal library, the [Quiver catalog](https://quiverlauncher.com), and flexible filtering.

## Features

- **Tag filters** - Organize and filter your library with custom tags
- **Library search** - Filter the current list by name, tags, repository, or folder
- **Manually managed apps** - Add apps with no GitHub/GitLab repository; drop files into the app folder and open it from the library
- **App Catalog** - Search the [quiverlauncher.com](https://quiverlauncher.com) catalog by project type, platform, console and AI use, see how apps run for other players, and add them to your library
- **GitHub & GitLab releases** - Install and update apps from GitHub or gitlab.com release assets
- **Mod Management Support** - Browse, install and update mods from Thunderstore and GameBanana
- **Automated updates** - Download and install the latest releases automatically
- **Version management** - Automatic version checking and in-app update checks
- **UI improvements** - Refined layout and top-bar controls

## Getting Started

### Installation

**Note if you are upgrading from 2.4.x or older:** the in-app update cannot migrate Quiver Launcher 2.4.x onto version 3.0 or higher. Download a fresh 3.x version of Quiver Launcher and copy your library over. See [MIGRATING.md](MIGRATING.md).

**Windows**

1. Download `QuiverLauncher-win-Portable.zip` from [Releases](https://github.com/tgeorgiadis/quiver-launcher/releases)
2. Extract it
3. Run `QuiverLauncher.exe` from the extracted folder

Your library stays in that same folder (`apps.json`, `settings.json`, `Apps/`, `Cache/` next to `current/`), so you can move the whole directory wherever you want.

```
QuiverLauncher/
├── QuiverLauncher.exe          # launcher stub
├── current/            # app binaries (replaced on update)
├── apps.json
├── settings.json
├── Apps/
└── Cache/
```

To verify a signed `QuiverLauncher.exe`: right-click → Properties → Digital Signatures, or `Get-AuthenticodeSignature .\QuiverLauncher.exe` in PowerShell.

**Linux**

1. Download `QuiverLauncher-linux-x64.AppImage` or `QuiverLauncher-linux-arm64.AppImage` from [Releases](https://github.com/tgeorgiadis/quiver-launcher/releases)
2. Put the AppImage in its own folder (it creates library files beside itself), mark it executable, then run it:
   ```bash
   mkdir -p ~/QuiverLauncher
   mv QuiverLauncher*.AppImage ~/QuiverLauncher/
   cd ~/QuiverLauncher
   chmod +x QuiverLauncher*.AppImage
   ./QuiverLauncher*.AppImage
   ```
   Or right-click → Properties → Permissions → **Allow executing file as a program**.  
   GitHub downloads do not keep the executable bit; you need to set it locally after download.

Library data (`apps.json`, `settings.json`, `Apps/`, `Cache/`) is stored **beside the AppImage** so you can move that folder together. If the AppImage’s directory is not writable (e.g. `/usr/local/bin`), Quiver Launcher falls back to `~/.local/share/QuiverLauncher/` (or `$XDG_DATA_HOME/QuiverLauncher`).

```
MyFolder/
├── QuiverLauncher-linux-x64.AppImage
├── apps.json
├── settings.json
├── Apps/
└── Cache/
```

**macOS**

Currently macOS support is a work in progress.

1. Download the macOS package from [Releases](https://github.com/tgeorgiadis/quiver-launcher/releases)
2. Keep `QuiverLauncher.app` in a writable folder (not only `/Applications` if you want portable data)

Library data lives **beside** `QuiverLauncher.app` in that folder. If the parent directory is not writable, Quiver Launcher falls back to `~/Library/Application Support/QuiverLauncher/`.

```
MyFolder/
├── QuiverLauncher.app
├── apps.json
├── settings.json
├── Apps/
└── Cache/
```

### Library data and recovery

Quiver keeps verified library snapshots in `Backups/apps/` alongside `apps.json`
on Windows, Linux, macOS, and Android. See [library protection and recovery](docs/library-recovery.md) for how to restore a snapshot if the library becomes damaged.

## Basic Usage

1. Launch the application
2. On first launch, open the **App Catalog** (internet required), open an app and choose **Add to library**. You can also add apps later with **+ Add New Entry**, including **manually managed** apps that have no GitHub/GitLab repository. Your library is stored in local [`apps.json`](apps.json)
3. Browse your app library in the Library view
4. Click the Download/Launch button on the app/game you want to use

The App Catalog reads the catalog from the [quiverlauncher.com](https://quiverlauncher.com) API the first time you open it, and again whenever you search, sort or filter. Reviews are written on the website: an app's **Write a review on the website** button opens its page.

## Configuration

### Kiosk mode

**Settings → General → Kiosk mode** keeps the next launch fullscreen and limited to browsing and launching. Settings, the app catalog, add, update, and exit controls are hidden. Press **Ctrl+Alt+K** to unlock this session, and press it again to lock it without restarting. An optional PIN can be set in that same section; Quiver stores only a hash of the PIN, and the PIN is required only to unlock.

`--kiosk` starts one locked session without changing `settings.json`, for a cabinet shortcut.

Kiosk mode does not block the Windows key, Alt+Tab, or Ctrl+Alt+Del. For a public machine, make Quiver the session: Windows Assigned Access or shell replacement, or a Linux Gamescope or cage session that only runs Quiver. Steam Deck Gaming Mode already keeps the desktop away.

### GitHub / GitLab API Tokens
To avoid hitting API rate limits, you can provide personal access tokens in **Settings → Advanced**.

- **GitHub:** Create a classic token with no special permissions at GitHub Settings → Developer settings → Personal access tokens. Paste it into **GitHub API Token**.
- **GitLab (optional):** Create a personal access token with `read_api` at [GitLab personal access tokens](https://gitlab.com/-/user_settings/personal_access_tokens). Paste it into **GitLab API Token**. Public gitlab.com releases work without a token.

Do not share your tokens.

### Mods (Thunderstore & GameBanana)

Apps can expose a **Mods** browser when `mods.path` and `mods.sources` are set in the catalog entry (or via **+ Add New Entry**).

Optional `mods.layout`:

| Value | Behavior |
|-------|----------|
| *(omitted)* / `flat` | Extract archive paths as-is into the mods folder (default; typical for Thunderstore `.nrm` packs). |
| `folderPerMod` | If the archive has payload files at its root, wrap everything in a folder named from the download filename (e.g. `Music-FRLG.zip` → `mods/Music-FRLG/`). Archives that already use a top-level folder are left unchanged. |

Use `folderPerMod` for apps that expect each mod in its own subfolder. Enable it in the catalog JSON or with **Install each mod into its own folder** when editing an entry.

**Source URL formats** (one per line in Mod Sources):

| Provider | Examples |
|----------|----------|
| Thunderstore | `https://thunderstore.io/c/banjo-recompiled/` or slug `banjo-recompiled` |
| GameBanana | `https://gamebanana.com/mods/games/24774`, `https://gamebanana.com/games/24774`, or bare id `24774` |

GameBanana URLs are detected automatically (no `gamebanana|` prefix required). Other hosts can still use `provider|url`.

**Browse & search**

- Both sources support infinite scroll / load-more (mouse or gamepad). Multi-source search merges pages from each provider.
- Content-rated / NSFW mods are **hidden by default**. Use the **Include NSFW** chip to show them (persisted in settings).
- GameBanana mods with multiple download files show a file picker on Install/Update. **Zip**, **7z**, and **RAR** archives are supported.
- Thunderstore mods that list requirements prompt before install if those mods are not already installed. **Yes** installs the missing requirements (and the selected mod); **No** installs only the selected mod; **Cancel** aborts without installing anything. **Update All** still pulls missing requirements without prompting.

### Verified releases

Apps from the Quiver catalog follow what [quiverlauncher.com](https://quiverlauncher.com) checked:

- Updates, including automatic ones, go to the release Quiver verified, not simply the newest one on GitHub or GitLab.
- Every download of a catalog app is checked against the SHA-256 Quiver saw when the release came out, and is refused if it changed. Other apps are checked against the checksum GitHub publishes, when there is one.
- Installing a release Quiver hasn't verified asks first and says why it isn't verified yet. Installing one Quiver blocked asks twice. Automatic updates never install either.
- **Change version** marks each release Verified, Unverified or Blocked.

### Your own app list

Quiver Launcher no longer subscribes to app lists. If you keep your own list, set it in **Settings → Advanced → My app list**: a local JSON file, or a URL such as a GitHub raw link. Its apps appear under **My app list** in the App Catalog, where you can add them to your library. A list you added in an earlier version is carried over automatically; if you had several, the first enabled one is kept.

The list uses the same format as `apps.json`: an `apps` array of app entries (an older list file's `name`, `description` and `version` are ignored).

#### App Entry Properties

Each app entry requires the following properties:

- **`name`** - Canonical app/title (for ports, usually the game name). Library display can compose this with `project` via Settings → Library name style
- **`project`** *(optional)* - Project, team, or author attribution shown when library name style includes project
- **`customDisplayName`** *(optional)* - Per-app library label override; always wins over name/project composition
- **`repository`** *(required unless manually managed)* - The repository path in the format `username/repository` (GitHub) or `namespace/project` (GitLab). The same repository may be used by more than one app when each has a distinct `folderName` (for example two games shipped in one GitHub release). Omit this field for **manually managed** apps: Quiver creates `{Apps}/{folderName}` and you place the files yourself. There is no download or update management until a repository is added. On **Edit App Entry**, filling in a repository promotes the app to a managed install (existing files are kept; Auto Update stays off until you update). Clearing the repository demotes it back to manual.
- **`repositorySource`** *(optional)* - `github` (default when omitted) or `gitlab`. Ignored for manually managed apps. Older Quiver Launcher versions ignore this field and treat entries as GitHub-only.
- **`folderName`** - The folder name under Apps where the app is installed (prefer `Title-Project`, without type suffixes like `-Recomp`). Must be unique. For manually managed apps this folder is created immediately as the drop target.
- **`releaseAssetFilter`** *(optional)* - Case-insensitive substring matched against release filenames. Use this when one repository ships more than one game so each app downloads only its files (e.g. `EXIT1` / `EXIT2`). Ignored for manually managed apps.
- **`tags`** *(optional)* - Freeform tags (classification such as `recomp` / `decomp` lives here, not in the title)
- **`appIconUrl`** - URL of the app's icon image. If null, a default icon will be used.

#### Example Configuration

```json
{
    "apps": [
        {
            "name": "Majora's Mask",
            "project": "2 Ship 2 Harkinian",
            "repository": "HarbourMasters/2ship2harkinian",
            "folderName": "MajorasMask-2Ship2Harkinian",
            "tags": ["n64", "decomp", "harbour-masters"],
            "appIconUrl": null
        },
        {
            "name": "Example App",
            "repository": "username/example-app-repo",
            "folderName": "ExampleApp",
            "appIconUrl": null
        },
        {
            "name": "GitLab Example App",
            "repository": "namespace/example-project",
            "repositorySource": "gitlab",
            "folderName": "GitLabExampleApp",
            "appIconUrl": null
        },
        {
            "name": "Manually Managed Example",
            "project": "Itch drop",
            "folderName": "ManualExample",
            "tags": ["manual"],
            "appIconUrl": null
        }
    ]
}
```

## Support

If you encounter any issues or have questions:
- [Open an issue](https://github.com/tgeorgiadis/quiver-launcher/issues)
- Check existing issues for solutions
- Join the [Discord server](https://discord.gg/5XRThpWHGk)

## License

Quiver Launcher is licensed under the [MIT License](LICENSE). It's based on
[GithubLauncher](https://github.com/SirDiabo/GithubLauncher) by SirDiabo, also MIT licensed, and keeps its copyright
notice.

The license covers the code, not the Quiver name, logo or app icons. See [TRADEMARKS.md](TRADEMARKS.md) for how forks
and other projects may use them.


## For Developers: Local Development

When building and running from source, Quiver Launcher is not a packaged release install, so self-update checks no-op (and Debug builds always skip automatic checks). Set `QuiverLauncher_SKIP_UPDATES=1` (or `true`) to skip automatic checks in Release local runs as well.

```powershell
# Debug: no env var needed
dotnet run --project QuiverLauncher.Desktop/QuiverLauncher.Desktop.csproj -c Debug

# Release local testing
$env:QuiverLauncher_SKIP_UPDATES = "1"
dotnet run --project QuiverLauncher.Desktop/QuiverLauncher.Desktop.csproj -c Release
```

Requires the **.NET 10 SDK**.

### Android

Android uses a separate head project (`QuiverLauncher.Android`) that installs and launches **APK** release assets. Desktop binaries (.exe, AppImage, Wine/Proton) are not supported on device.

1. Install the .NET 10 SDK and the Android workload:
   ```powershell
   dotnet workload install android
   ```
2. Install the Android SDK and JDK 11+ ([Avalonia Android setup](https://docs.avaloniaui.net/docs/platform-specific-guides/android/)).
3. Allow **Install unknown apps** for Quiver on the emulator or device.
4. Build and deploy:
   ```powershell
   dotnet build QuiverLauncher.Android/QuiverLauncher.Android.csproj -c Debug
   ```

User data for unpackaged Windows debug builds still lives beside the build output. Unpackaged macOS/Linux runs (no AppImage / `.app` package) use the OS app-support fallbacks (`~/Library/Application Support/QuiverLauncher/` or `~/.local/share/QuiverLauncher/`).

### Automated tests

Fast local run (excludes the slow publish integration test):

```powershell
dotnet test QuiverLauncher.sln -c Release --filter "Category!=Slow" --logger "console;verbosity=normal"
```

Full suite including publish integration test (matches CI; the publish test can take several minutes):

```powershell
dotnet test QuiverLauncher.sln -c Release
```

Run only the slow publish packaging test:

```powershell
dotnet test QuiverLauncher.sln -c Release --filter "Category=Slow"
```

Test categories include library file safety, adding catalog apps, settings store round-trip, launcher version helpers, Windows runner command building, download asset selection, game status checks, ViewModel sorting/catalog helpers, GameManager hide/filter behavior, and Avalonia headless smoke tests.

Collect coverage locally with:

```powershell
dotnet test QuiverLauncher.sln -c Release --filter "Category!=Slow" --collect:"XPlat Code Coverage"
```
