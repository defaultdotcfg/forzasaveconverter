# Forza Save Converter

Forza Save Converter é uma ferramenta de conversão de saves dos jogos da série Forza, baixados pela ferramenta XBsync no PC, para funcionar nos ports para PC (Azimuth e RaceOneHub). A ferramenta estrutura a pasta corretamente para o save ser reconhecido nesses ports sem modficar nenhum arquivo.

Ferramenta criada com Claude e Manus.

## Recursos

- Lê a pasta da save ou o arquivo em `.zip`.
- Verifica os arquivos esperados de cada jogo salvo: `BinarySaveState`, `PlayerDatabase`, `ProfileData`, `SaveState` e `VersionFlags`.
- Cria uma nova revisão para o port selecionado.
- Pode adicionar a revisão a um usuário existente ou criar uma nova estrutura.
- Inclui simulação sem gravação, análise da origem e ferramenta para verificar revisões existentes.
- Disponível em Português (Brasil), English e Español.

## Compatibilidade

- Forza Horizon 2 (Azimuth Launcher)
- Forza Motorsport 5 (RaceOneHub)

## Requisitos

- Windows 10/11 para executar o BAT e gerar o `.exe`.
- Python 3.10 ou superior.
- Para a interface gráfica: Python instalado com Tcl/Tk (opção “tcl/tk and IDLE” no instalador oficial do Windows).
- Conexão à internet na primeira compilação para instalar o PyInstaller.

O conversor usa somente a biblioteca padrão do Python; nenhuma dependência adicional é necessária para executar o script.

## Caminhos das saves

Forza Horizon 2
- Pasta do Azimuth\data\titles\1A96545B\saves

Forza Motorsport 5
- %USERPROFILE%\Saved Games\Race One Hub\RaceOne5\data\titles\7B35D917\saves

## Agradecimentos

XBSync - https://github.com/D3FEKT/XBsync

RaceOneHub (FM5) - https://github.com/LoZazaMastro/RaceOneHub

Azimuth (FH2) - https://almost-there-games.itch.io/azimuth
