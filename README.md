# FH2 Save Converter

Ferramenta para converter saves de console do **Forza Horizon 2** para a estrutura de revisões utilizada pelo emulador Azimuth. Inclui interface gráfica multilíngue e linha de comando.

## Recursos

- Lê uma pasta de save ou um arquivo `.zip`.
- Verifica os cinco arquivos esperados: `BinarySaveState`, `PlayerDatabase`, `ProfileData`, `SaveState` e `VersionFlags`.
- Cria uma nova revisão Azimuth e valida o `commit` gerado usando tamanho e hash SHA-256 dos arquivos.
- Pode adicionar a revisão a um usuário Azimuth existente ou criar uma nova estrutura.
- Permite usar o `ProfileData` da save do console ou, quando há uma revisão existente, o `ProfileData` do emulador.
- Inclui simulação sem gravação, análise da origem e ferramenta para verificar revisões existentes.
- A interface está disponível em Português (Brasil), English e Español.

## Requisitos

- Windows 10/11 para executar o BAT e gerar o `.exe`.
- Python 3.10 ou superior.
- Para a interface gráfica: Python instalado com Tcl/Tk (opção “tcl/tk and IDLE” no instalador oficial do Windows).
- Conexão à internet na primeira compilação para instalar o PyInstaller.

O conversor usa somente a biblioteca padrão do Python; nenhuma dependência adicional é necessária para executar o script.

## Arquivos

```text
.
├── fh2_to_azimuth.py
└── fh2_to_azimuth_build.bat
```

Mantenha o script Python e o BAT na mesma pasta.

## Compilar para `.exe` no Windows

Execute:

```text
fh2_to_azimuth_build.bat
```

O BAT instala/atualiza o PyInstaller e gera:

```text
dist\FH2 Save Converter.exe
```

## Uso da interface gráfica

Execute o script sem argumentos:

```bash
python fh2_to_azimuth.py
```

1. Selecione a pasta da save do console ou um `.zip` que a contenha.
2. Escolha o destino Azimuth.
3. Selecione o modo de destino e a origem de `ProfileData`, se necessário.
4. Opcionalmente, use **Simular** para conferir a operação sem gravar nada.
5. Clique em **Converter**. Uma nova revisão será criada e verificada.

### Modos de destino

- **Usuário existente (`existing`)**: adiciona uma revisão em uma estrutura existente do emulador, normalmente `saves/player-1` ou uma pasta `User_*`.
- **Estrutura nova (`new`)**: cria `User_9000000000000/revisions/<revisão>/...` na pasta selecionada. A pasta `User_9000000000000` é usada para compatibilidade com o Azimuth.

O conversor não altera a save de console original nem sobrescreve revisões existentes: ele acrescenta uma revisão no destino escolhido. Ainda assim, mantenha uma cópia de segurança dos arquivos importantes.

## Linha de comando

Ajuda e opções disponíveis:

```bash
python fh2_to_azimuth.py --help
```

Analisar uma pasta ou ZIP:

```bash
python fh2_to_azimuth.py info "C:\caminho\para\a\save"
```

Converter para um usuário existente:

```bash
python fh2_to_azimuth.py convert "C:\caminho\para\a\save" "C:\Azimuth\saves\player-1" --layout existing
```

Criar uma estrutura nova:

```bash
python fh2_to_azimuth.py convert "C:\caminho\para\a\save" "C:\caminho\de\saida" --layout new
```

Simular sem escrever arquivos:

```bash
python fh2_to_azimuth.py convert "C:\caminho\para\a\save" "C:\caminho\de\saida" --layout new --dry-run
```

Verificar revisões e hashes:

```bash
python fh2_to_azimuth.py verify "C:\Azimuth\saves\player-1"
```

Se a origem contiver várias saves, use `--pick TEXTO`; se houver vários usuários no destino, escolha com `--user User_...`. Consulte `--help` para as demais opções, inclusive seleção de `ProfileData` e `--force` (ignorar validação).

## Limitações e aviso

O conversor espera a estrutura e os arquivos de save do Forza Horizon 2 listados acima. `--force` ignora falhas de validação e deve ser usado somente quando você entende o motivo do aviso ou erro.

Projeto independente e não oficial, sem afiliação com Microsoft, Turn 10, Forza ou Azimuth.

**Licença:** ainda não definida. Adicione um arquivo `LICENSE` antes de redistribuir o código sob uma licença específica.
