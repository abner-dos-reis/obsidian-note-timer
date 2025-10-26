README
======

Obsidan Note Timer (adaptação)
-------------------------------

Este projeto é uma adaptação local do plugin "obsidian-note-timer" de davidvdev.
Base original: https://github.com/davidvdev/obsidian-note-timer

Resumo
------

O plugin adiciona um timer embutido em blocos de código Markdown com a linguagem `timer`.
Ele exibe botões para iniciar, parar e (opcionalmente) resetar o tempo, e pode manter um log
em formato de tabela dentro do próprio arquivo Markdown.

Arquivos principais
-------------------

- `main.js` — arquivo gerado/bundled com a lógica do plugin (processador do bloco de código `timer`, persistência de settings, criação de logs, etc.).
- `manifest.json` — metadados do plugin (id, versão, author, etc.).
- `styles.css` — estilos mínimos para a apresentação do bloco `timer`.

Funcionalidades
---------------

- Adiciona um processador de bloco de código para ```` ```timer ````
- Gera um UID para cada bloco `timer` e mantém o estado (running/stopped) em memória durante a sessão.
- Suporte a configuração via bloco `timer` (ex.: customizar textos dos botões, controlar se milissegundos são exibidos, etc.) e via aba de configurações do plugin.
- Se ativado, cria uma tabela de log logo abaixo do bloco timer com colunas: Start | Stop | Duration | Comments e atualiza o Total Time.

Como usar
---------

1. Instale o plugin (ver instruções abaixo).
2. No seu arquivo Markdown, adicione um bloco de código com a linguagem `timer`:

```
```timer
_timerUID:optional-id
ms: true
```

3. Ao renderizar a nota, o bloco exibirá o display do tempo e botões Start/Stop/Reset conforme configuração.
4. Se `autoLog` estiver ativado (nas configurações do plugin), ao parar o timer o tempo será adicionado na tabela de log.

Configurações suportadas (visíveis no código gerado / via plugin settings):

- autoLog: adiciona automaticamente o log na tabela
- dateFormat: formato das datas no log (ex.: YYYY-MM-DD)
- logDateLinking: `none` | `tag` | `link` — como o plugin formata as datas no log
- msDisplay: mostrar milissegundos
- startButtonText / stopButtonText / resetButtonText
- showResetButton / continueRunningOnReset

Instalação local (manualmente)
-----------------------------

1. Copie a pasta deste projeto para o diretório de plugins do Obsidian (ex.: `.obsidian/plugins/obsidian-note-timer`).
2. Reinicie o Obsidian (ou recarregue plugins) e ative "Note Timer" nas configurações de comunidade.

Observações sobre license / autoria
----------------------------------

Este repositório é uma adaptação local do trabalho de davidvdev. O código em `main.js` é a versão bundle gerada (o `source` original está no projeto upstream). Preserve a atribuição ao autor original e verifique a licença do upstream antes de redistribuir.

Instalando o GitHub CLI (`gh`) sem sudo (ambiente Flatpak / sem permissões root)
--------------------------------------------------------------------------------

Os passos abaixo baixam o binário do `gh` para Linux (amd64) e o colocam em `~/.local/bin` — não é necessário sudo.

Cole e execute no seu terminal (seu shell é `sh`):

```sh
mkdir -p "$HOME/.local/bin"
cd /tmp
url=$(curl -s https://api.github.com/repos/cli/cli/releases/latest | grep 'browser_download_url' | grep 'linux_amd64.tar.gz' | head -n1 | cut -d '"' -f4)
echo "Downloading $url"
curl -L "$url" -o gh.tar.gz
tar -xzf gh.tar.gz
mv gh_*_linux_amd64/bin/gh "$HOME/.local/bin/"
chmod +x "$HOME/.local/bin/gh"
"$HOME/.local/bin/gh" --version
```

Autenticação e criação do repositório (você autoriza via navegador)
-------------------------------------------------------------------

Após instalar `gh`, execute dentro da pasta do projeto:

```sh
cd /caminho/para/obsidian-note-timer
gh auth login --web
# siga as instruções no navegador para autorizar
gh repo create NOME_DO_REPO --public --source=. --remote=origin --confirm --push
```

Observação: `gh repo create` usará sua conta autenticada no GitHub e criará o repositório público. Substitua `NOME_DO_REPO` pelo nome desejado (por exemplo `obsidian-note-timer`).

O que eu fiz aqui
-----------------

- Li os arquivos do projeto e resumi o funcionamento.
- Adicionei este `README.md` com instruções de uso, instalação e como instalar o `gh` sem sudo.

Próximos passos sugeridos
-------------------------

- (Opcional) Incluir o código-fonte não-bundle (TypeScript/JS original) para facilitar manutenção.
- Adicionar LICENSE/NOTICE se quiser redistribuir (verificar a licença do upstream).
- Testar o fluxo `gh auth` e `gh repo create` no ambiente do usuário para confirmar permissões.

-- Fim
