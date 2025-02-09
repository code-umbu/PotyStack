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
