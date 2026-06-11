# 🎓 Guia Completo: Como Executar o Wokwi Simulator no VS Code

Passo a Passo de como instalar e executar projetos Wokwi no VS code. Siga o passo a passo abaixo com atenção!

---

## Método 1: Tudo do 0

---

## 🛠️ Passo 1: Baixar e Instalar o VS Code

Se você ainda não tem o VS code instalado:

1. Acesse o site oficial: [code.visualstudio.com](https://code.visualstudio.com/).
2. Baixe a versão correspondente ao seu sistema operacional (Windows, macOS ou Linux).
3. Execute o instalador e siga as instruções na tela (pode deixar as opções padrão).

## 🔌 Passo 2: Instalar a Extensão do Wokwi Simulator

Com o VS Code aberto:

1. Vá até a aba de **Extensões** na barra lateral esquerda (ou aperte `Ctrl+Shift+X`).
2. Na barra de pesquisa, digite **Wokwi Simulator**.
3. Clique em **Install** (Instalar) na extensão oficial desenvolvida pelo Wokwi.

## 🔑 Passo 3: Pegar a Licença do Wokwi e Ativar no VS Code

Para usar a extensão no VS Code, você precisa de uma licença (existe uma versão gratuita).

1. Aperte `Ctrl+Shift+P` (ou `Cmd+Shift+P` no Mac) no VS Code para abrir a Paleta de Comandos.
2. Digite e selecione: `Wokwi: Request a New License`.
3. Seu navegador vai abrir pedindo para você fazer login na sua conta Wokwi.
4. Após o login, a licença será gerada e o navegador pedirá para abrir o VS Code novamente. Aceite.
5. Uma mensagem de sucesso aparecerá no canto inferior direito do VS Code confirmando a ativação!

## 🐝 Passo 4: Baixar o PlatformIO, Criar o Projeto e Linkar Firmwares

O PlatformIO (PIO) gerencia nossas placas, bibliotecas e compilação.

### Instalando o PlatformIO

1. Volte na aba de **Extensões** (`Ctrl+Shift+X`).
2. Pesquise por **PlatformIO IDE** e instale. (Pode demorar alguns minutos, ele instala dependências do Python no fundo. Aguarde a mensagem de que a instalação foi concluída e reinicie o VS Code).

### Criando o Projeto

1. Clique no ícone de "Formiga" (ou alienígena) do PlatformIO na barra lateral.
2. Clique em **PIO Home > Open**.
3. Clique em **New Project**.
4. Dê um nome ao projeto, selecione a placa que deseja usar (ex: *Arduino Uno* ou * Para ESP32: DOIT ESP32 DEVKIT V1*) e o framework (geralmente *Arduino*).
5. Escolha a pasta onde quer salvar e clique em **Finish**.

### Configurando o arquivo `platformio.ini`

Para que o Wokwi saiba onde está o firmware compilado pelo PlatformIO, você precisa criar ou editar o arquivo `wokwi.toml` na raiz do seu projeto. Ele deve apontar para os arquivos gerados pelo PIO.

Exemplo de conteúdo para o `wokwi.toml`:

```toml
[wokwi]
version = 1
firmware = ".pio/build/NOME_DA_SUA_PLACA/firmware.elf"
elf = ".pio/build/NOME_DA_SUA_PLACA/firmware.elf"

```

*(Lembre-se de trocar `NOME_DA_SUA_PLACA` pelo ambiente criado no seu `platformio.ini`, como `uno` ou `esp32doit-devkit-v1`).*

---

## Método 2: Usando o Template do Repositório

---

## 🛠️ Passo 1. Preparando o Terreno (Baixando o Template)
Escolha UMA das opções abaixo para baixar o projeto para o seu computador:

## Opção A: Para quem NÃO tem o Git instalado (Mais Fácil)

1. Role esta página para cima e clique no botão verde "<> Code".
2. Clique em "Download ZIP".
3. Extraia (descompacte) a pasta ZIP em um local de fácil acesso (ex: Documentos ou Área de Trabalho).

## Opção B: Para quem tem o Git instalado (Recomendado)

1. Abra o seu terminal (Prompt de Comando ou PowerShell) ou crie uma pasta, abra ela no VS code e acesse o terminal do VS code.
2. Navegue até a pasta desejada e digite o comando:
```bash
git clone [https://github.com/glhrmlud/Wokwi-Simulator-Tutorial.git]
```

## 🧩 Passo 2. Abrindo no VS Code e Instalando Extensões
Abra o VS Code.

1. Vá em File > Open Folder... (Arquivo > Abrir Pasta...) e selecione a pasta do projeto que você baixou/clonou.
2. Certifique-se de ter as duas extensões instaladas (procure no menu lateral de Extensões Ctrl+Shift+X):

## PlatformIO IDE:
  * Aguarde a instalação concluir se for a primeira vez).

## Wokwi Simulator:
  * Para usar a extensão no VS Code, você precisa de uma licença (existe uma versão gratuita).
  * 1. Aperte `Ctrl+Shift+P` (ou `Cmd+Shift+P` no Mac) no VS Code para abrir a Paleta de Comandos.
  * 2. Digite e selecione: `Wokwi: Request a New License`.
  * 3. Seu navegador vai abrir pedindo para você fazer login na sua conta Wokwi.
  * 4. Após o login, a licença será gerada e o navegador pedirá para abrir o VS Code novamente. Aceite.
  * 5. Uma mensagem de sucesso aparecerá no canto inferior direito do VS Code confirmando a ativação!

---

## Exportar e Executar Projetos Wokwi

---

## 📦 Passo 1: Exportar o Projeto do Wokwi Web para o VS Code

Se você já tem um projeto pronto no navegador e quer trazer para o VS Code:

1. Abra o seu projeto no Wokwi Web.
2. No VS Code, certifique-se de ter os arquivos `diagram.json` (que descreve o circuito) e `wokwi.toml` na raiz do seu projeto PlatformIO.
3. Copie o conteúdo da aba `diagram.json` do site do Wokwi e cole dentro do arquivo `diagram.json` no seu VS Code.
4. O seu código fonte (C/C++) deve ser copiado do site e colado dentro da pasta `src/` no arquivo `main.cpp` do seu projeto PlatformIO.
5. Compile o projeto no PlatformIO (ícone de "✔" na barra inferior).
6. Abra o arquivo `diagram.json` no VS Code e clique no botão **Play** (ou no aviso superior) para iniciar a simulação.

---

## ✏️ Passo 2: Como Alterar o Circuito (Para quem tem Licença Gratuita)

O editor visual de circuitos no VS Code é um recurso pago. Porém, quem usa a licença **gratuita** pode alterar o circuito facilmente usando uma ponte entre o VS Code e a versão Web!

**Cenário A: O circuito já está no Wokwi Web**

1. Abra o seu projeto no site do Wokwi.
2. Adicione os componentes, fios e faça todas as alterações visuais que precisar.
3. Vá na aba de código e procure pelo arquivo `diagram.json`.
4. Copie todo o texto desse arquivo.
5. Volte para o VS Code, abra o seu arquivo `diagram.json` e **cole** (substituindo o texto anterior). Salve o arquivo.

**Cenário B: O circuito ainda NÃO está no Wokwi Web (Só no VS Code)**

1. No VS Code, abra o arquivo `diagram.json` e **copie** todo o conteúdo.
2. Abra um projeto em branco (da mesma placa) no site oficial do Wokwi.
3. No site, vá até a aba do `diagram.json` e **cole** o conteúdo que você copiou do VS Code.
4. O circuito vai aparecer na tela! Faça suas alterações visuais (adicione LEDs, sensores, etc.).
5. Após terminar de montar o circuito, **copie novamente** o conteúdo atualizado do `diagram.json` do site.
6. Volte para o VS Code, **cole** as novidades no seu arquivo `diagram.json` e salve.

---

## Baixar Bibliotecas

---

## Forma 1: Pelo arquivo de texto

1. Abra o arquivo platformio.ini na raiz do seu projeto.
2. Procure pela linha lib_deps = (se não existir, você pode digitar ela no final do arquivo).
3. Pule uma linha, dê um espaço (Tab) e digite o nome da biblioteca que você quer. Exemplo:
```platformio.ini
lib_deps =
    marcoschwartz/LiquidCrystal_I2C @ ^1.1.2
```
4. Salve o arquivo (Ctrl + S). Pronto! Na próxima vez que você clicar no Build (✔), o PlatformIO baixa ela automaticamente.

## Forma 2: Pela interface visual do PlatformIO

1. Clique no ícone do PlatformIO (a formiguinha) na barra lateral esquerda do VS Code.
2. Clique em PIO Home > Open para abrir a tela inicial do gerenciador.
**3. Para Repositório Baixado/Clonado:**
  Na tela que abriu, clique no botão Open Project (Abrir Projeto), navegue até a pasta do template que você baixou/clonou e selecione ela. Isso garante que o PlatformIO reconheça o projeto ativo.
4. Agora, no menu esquerdo dessa mesma tela do PIO Home, clique em Libraries (ícone de livro).
5. Na barra de pesquisa, digite o nome da biblioteca que você quer (ex: LiquidCrystal I2C) e aperte Enter.
6. Clique na biblioteca desejada e depois no botão azul Add to Project.
7. Selecione o seu projeto na lista e clique em Add. O próprio PlatformIO vai configurar tudo para você!

---

## ✒️ Autor

* **Guilherme Eliúde** - [GitHub](https://github.com/glhrmlud)
