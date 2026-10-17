# Forza Save Converter

Forza Save Converter é uma ferramenta de conversão de saves dos jogos da série Forza, baixados pela ferramenta XBsync no PC, para funcionar nos ports para PC (Azimuth e RaceOneHub). A ferramenta estrutura a pasta corretamente para o save ser reconhecido nesses ports sem modficar nenhum arquivo.

Ferramenta criada com Claude e Manus.

## Recursos

- Lê a pasta da save ou o arquivo em `.zip`.
- Verifica os cinco arquivos esperados: `BinarySaveState`, `PlayerDatabase`, `ProfileData`, `SaveState` e `VersionFlags`.
- Cria uma nova revisão para o port selecionado e valida o `commit` gerado usando tamanho e hash SHA-256 dos arquivos.
- Pode adicionar a revisão a um usuário Azimuth existente ou criar uma nova estrutura.
- Inclui simulação sem gravação, análise da origem e ferramenta para verificar revisões existentes.
- Interface disponível em Português (Brasil), English e Español.

## Compatibilidade

- Forza Horizon 2 (Azimuth Launcher)
- Forza Motorsport 5 (WIP)

## Requisitos

- Windows 10/11 para executar o BAT e gerar o `.exe`.
- Python 3.10 ou superior.
- Para a interface gráfica: Python instalado com Tcl/Tk (opção “tcl/tk and IDLE” no instalador oficial do Windows).
- Conexão à internet na primeira compilação para instalar o PyInstaller.

O conversor usa somente a biblioteca padrão do Python; nenhuma dependência adicional é necessária para executar o script.

### Modos de destino

- **Usuário existente (`existing`)**: adiciona uma revisão em uma estrutura existente do emulador, normalmente `saves/player-1` ou uma pasta `User_*`.
- **Estrutura nova (`new`)**: cria `User_9000000000000/revisions/<revisão>/...` na pasta selecionada. A pasta `User_9000000000000` é usada para compatibilidade com o Azimuth.

O conversor não altera a save de console original nem sobrescreve revisões existentes: ele acrescenta uma revisão no destino escolhido. Ainda assim, mantenha uma cópia de segurança dos arquivos importantes.

## Limitações e aviso

O conversor espera a estrutura e os arquivos de save do Forza Horizon 2 listados acima. `--force` ignora falhas de validação e deve ser usado somente quando você entende o motivo do aviso ou erro.

Projeto independente e não oficial, sem afiliação com Microsoft, Turn 10, Forza ou Azimuth.

## Agradecimentos

XBSync - https://github.com/D3FEKT/XBsync

RaceOneHub (FM5) - https://github.com/LoZazaMastro/RaceOneHub

Azimuth (FH2) - https://almost-there-games.itch.io/azimuth
