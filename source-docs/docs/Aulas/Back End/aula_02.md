# Aula 02 - Preparando o ambiente de desenvolvimento

Agora que temos um ambiente WSL configurado, vamos começar a preparar o ambiente de desenvolvimento.

Para isso vamos instalar uma serie de ferramentas que vão nos ajudar a desenvolver nosso projeto.



## Instalando ferramentas do Python

### Instalando o Python 3.13.4

#### Conhecendo o `pyenv` e instalando o Python 3.13.1

O `pyenv` é uma ferramenta que permite instalar e gerenciar diferentes versões do Python em um mesmo ambiente.

Vamos dar uma olhada nas opções disponíveis:

```bash
pyenv install --list # (1)!
```

1. :man_raising_hand: Entendendo o comando:
    - `pyenv`: Comando para gerenciar versões do Python.
    - `install`: Comando para instalar uma versão do Python.
    - `--list`: flag para listar todas as versões disponíveis para instalação.

O resultado será uma lista de versões disponíveis para instalação. Como você pode ver é uma lista bem grande. Mas como podemos procurar por uma versão específica?

```bash
pyenv install --list | grep 3.13.1 # (1)! 

# 3.13.1
# 3.13.1t
```

1. :man_raising_hand: Entendendo o comando:
    - `pyenv install --list`: Lista todas as versões disponíveis para instalação.
    - `|`: Pipe, redireciona a saída do comando anterior para o próximo comando.
    - `grep 3.13.1`: Filtra a lista para exibir apenas as versões que contém `3.13.1`.

Vamos instalar a versão `3.13.1`: 

```bash
pyenv install 3.13.1 # (1)!
```

1. :man_raising_hand: Entendendo o comando:
    - `pyenv`: Comando para gerenciar versões do Python.
    - `install`: Comando para instalar uma versão do Python.
    - `3.13.1`: Versão do Python que queremos instalar.

Esse processo pode demorar um pouco, então aproveite para tomar um café ou fazer um alongamento.

???+ warning "O que está acontecendo aqui?"
    O comando `pyenv install 3.13.1` está baixando e instalando a versão `3.13.1` do Python. O processo de instalação do Python é algo um pouco complexo, pois ele precisa ser compilado e configurado para funcionar corretamente no seu ambiente. Por isso, é normal que esse processo demore um pouco e pode apresentar alguns erros. Por isso é importante prestar atenção nas mensagens que aparecem no terminal e buscar por soluções caso algo dê errado. O `pyenv` sempre gera um arquivo de log da instalação na pasta `/tmp` e especifica o nome do arquivo durante as mensagens de instalação, então se algo der errado, você pode verificar esse arquivo para entender o que aconteceu.

##### Verificando a instalação

Para verificar se a instalação foi bem sucedida, podemos usar o comando:

```bash
pyenv versions # (1)!
```

1. :man_raising_hand: Entendendo o comando:
    - `pyenv`: Comando para gerenciar versões do Python.
    - `versions`: Comando para listar todas as versões do Python instaladas.

O resultado deve ser algo parecido com isso:

```bash
  system (set by /home/runner/.pyenv/version)
* 3.13.1 (set by /home/runner/.python-version)
```
### Montando o ambiente

A primeira coisa que vamos fazer é informar para o `pyenv` que queremos usar a versão `3.13.1` do Python que acabamos de instalar. Para isso, vamos usar o comando:

```bash
pyenv global 3.13.1 # (1)!
```

1. :man_raising_hand: Entendendo o comando:
    - `pyenv`: Comando para gerenciar versões do Python.
    - `global`: Comando para definir a versão global do Python.
    - `3.13.1`: Versão do Python que queremos definir como global.

O resultado deve ser algo assim:

```bash
Python 3.13.1
```

O problema é que sua sessão do terminal ainda não sabe que você mudou a versão do Python. Para isso, você precisa reiniciar o terminal ou executar o comando:

```bash
source ~/.bashrc
```

Pronto agora você tem o Python 3.13.1 instalado e configurado no seu ambiente e podemos instalar mais algumas ferramentas globais que vamos usar no python.

O que precisamos fazer agora é atualiza o `pip`. Para isso vamos usar o comando:

```bash
pip install --upgrade pip # (1)!
```

1. :man_raising_hand: Entendendo o comando:
    - `pip`: Comando para gerenciar pacotes Python.
    - `install`: Comando para instalar um pacote Python.
    - `--upgrade`: flag para atualizar um pacote Python.
    - `pip`: Pacote Python que queremos atualizar.

Como resultado irá aparecer uma mensagem informando que o `pip` foi atualizado.

### Instalando o Pipx

O [`pipx`](https://pipx.pypa.io/stable/) é uma ferramenta que permite instalar e gerenciar pacotes Python de forma global. Vamos instalar o `pipx`:

```bash
pip install pipx # (1)!
```

1. :man_raising_hand: Entendendo o comando:
    - `pip`: Comando para gerenciar pacotes Python.
    - `install`: Comando para instalar um pacote Python.
    - `pipx`: Pacote Python que queremos instalar.

Se o processo ocorrer sem erros, uma mensagem `Successfully installed ...` será exibida.

### Instalando o Poetry

O [`Poetry`](https://python-poetry.org/) é uma ferramenta de gerenciamento de dependências e empacotamento de aplicações Python. Vamos instalar o `Poetry`:

```bash
pipx install poetry # (1)!
```

1. :man_raising_hand: Entendendo o comando:
    - `pipx`: Comando para gerenciar pacotes Python de forma global.
    - `install`: Comando para instalar um pacote Python.
    - `poetry`: Pacote Python que queremos instalar.

Para facilitar um pouco o nosso trabalho, vamos instalar um plugin do `Poetry` que permite ativemos o uso de ambientes virtuais do `Poetry` mais facilmente. Para isso vamos usar o comando:

```bash
pipx inject poetry poetry-plugin-shell # (1)!
```

1. :man_raising_hand: Entendendo o comando:
    - `pipx`: Comando para gerenciar pacotes Python de forma global.
    - `inject`: Comando para injetar um pacote Python em outro pacote Python.
    - `poetry`: Pacote Python onde vamos injetar.
    - `poetry-plugin-shell`: Pacote Python que queremos injetar.


## Criando o projeto

Um projeto de software, de uma forma bem simplificada, nada mais é que um conjuto de arquivos e pastas que juntos formam uma aplicação.

Precisamos organizar esses arquivos e pastas de uma forma que seja fácil de entender e de manter. Para isso vamos criar algumas pastas.

Primeiro vamos perceber onde você está no seu terminal. Para isso vamos usar o comando:

```bash
pwd
```

Como resultado você deve receber uma saída parecida com essa `/home/<<nome do seu usuário>>`. No linux essa é uma pasta especial e tem um apelido, que é o `~`. Então se você estiver nessa pasta, você pode usar o comando:

```bash
cd ~
```

Isso vai te levar para a pasta do seu usuário. Agora vamos criar uma pasta para que você possa organizar seus projetos. Para isso vamos usar o comando:

```bash
mkdir projects
```

Agora vamos entrar nessa pasta:

```bash
cd projects
```

Agora vamos criar uma pasta para o nosso projeto:

```bash
mkdir tamo_junto
```

!!! note "Por que `tamo_junto` e não `tamo-junto`?"
    Vamos evitar de usar hífens (`-`) em nomes de pastas e arquivos. Isso porque o hífen é um caractere especial e pode causar problemas em alguns sistemas operacionais e ambientes de desenvolvimento. Por isso, é uma boa prática evitar o uso de hífens em nomes de pastas e arquivos.

Agora vamos entrar nessa pasta:

```bash
cd tamo_junto
```

Dentro dessa pasta vamos iniciar o nosso repositorio local do git. Para isso vamos usar o comando:

```bash
git init
```



Vamos criar mais uma pasta onde vamos colocar o código da parte de back-end do nosso projeto:

```bash
mkdir backend
```

E vamos entrar nessa pasta:

```bash
cd backend
```

Agora que criamos esse estrutura de pastas, vamos 



