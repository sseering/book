# Instalando Nu

Atualmente, as melhores maneira de instalar o Nu são a partir do [crates.io](https://crates.io), fazer o download dos binários da nossa [página de releasea](https://github.com/nushell/nushell/releases), fazer o build a partir dos fontes ou baixar um container pré-construído com o Docker.

## Binários

Você pode baixar o Nu da [página de releases](https://github.com/nushell/nushell/releases). Alternativamente, se você usa o [Homebrew](https://brew.sh/) para macOS, pode instalar o binário executando o comando `brew install nushell`.

## Containers Docker

Se quiser baixar um container pronto, você pode navegar nas tags da [organização nushell](https://quay.io/organization/nushell) no Quay.io. Baixar um container se resume a:

```bash
$ docker pull quay.io/nushell/nu
$ docker pull quay.io/nushell/nu-base
```

Tanto "nu-base" como "nu" fornecem o binário `nu`, mas o nu-base também inclui o código fonte no container em `/code`, bem como todas as  dependências.

Opcionalmente, você pode fazer o build dos containers localmente usando os [dockerfiles fornecidos](https://github.com/nushell/nushell/tree/master/docker):

Para fazer o build da imagem base:

```bash
$ docker build -f docker/Dockerfile.nu-base -t nushell/nu-base .
``` 

E então, para fazer o build do container menor (usando o build Multiestágios):

```bash
$ docker build -f docker/Dockerfile -t nushell/nu .
``` 

De qualquer modo, você pode rodar qualquer um dos containers assim:

```bash
$ docker run -it nushell/nu-base
$ docker run -it nushell/nu
/> exit
```

O segundo container é um pouco menor, se o tamanho for importante para você.

## Preparando

Antes de poder instalar o Nu, precisamos nos certificar de que nosso sistema tem os requisitos necessários. Atualmente, isso significa ter certeza de que temos tanto o conjunto de ferramentas do Rust como as dependências locais instaladas.

### Instalando o Rust

Se ainda não tivermos o Rust instalado no sistema, a melhor maneira de instalar é via [rustup](https://rustup.rs/). Rustup é um gerenciador de instalações de Rust, inclusive para usar versões diferentes de Rust.

O Nu atualmente requer a versão **nightly** do Rust. Quando você abrir o "rustup" pela primeira vez, ele vai perguntar qual versão do Rust você quer instalar:

```
Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

Selecione a opção #2 para customizar a instalação,

```
Default host triple?
```

Aperte enter aqui para selecionar o default.

```
Default toolchain? (stable/beta/nightly/none)
```

Certifique-se de digitar "nightly" aqui e pressionar enter. Isso vai levar à configuração seguinte:

```
Modify PATH variable? (y/n)
```

Você pode opcionalmente atualizar o seu *path*. Normalmente é uma boa ideia, pois torna os passos seguintes mais fáceis.

```
Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: nightly
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

Você pode ver que o conjunto de ferramentas agora mudou para a versão nightly. Se isso lhe parece um pouco arriscado, não se preocupe. O compilador do Rust passa por uma bateria completa de testes. O compilador nightly é praticamente tão confiável quanto a versão estável.

Quando estiver pronto, aperte 1 e enter. Depois desse ponto, podemos seguir as instruções que o "rustup" nos der e teremos um compilador Rust funcionando no nosso sistema.

Se você preferir não instalar o Rust via "rustup", você pode também instalar por outros métodos (por exemplo, a partir de um pacote em uma distribuição Linux). Apenas se certifique de instalar uma versão nightly recente.

## Dependências

### Debian/Ubuntu

Você vai precisar instalar os pacotes "pkg-config" e "libssl-dev":

```
apt install pkg-config libssl-dev
```

Usuários Linux que quiserem usar as funcionalidades opcionais `rawkey` ou `clipboard` precisarão instalar os pacotes "libx11-dev" and "libxcb-composite0-dev":

```
apt install libxcb-composite0-dev libx11-dev
```

### macOS

Ao usar o [Homebrew](https://brew.sh/), você precisará instalar o "openssl" e o "cmake" usando: 

```
brew install openssl cmake
```

## Instalando a partir do [crates.io](https://crates.io)

Quando tivermos todas as dependências de que o Nu precisa, podemos instalá-lo usando o comando `cargo` que vem com o compilador Rust.

```
> cargo +nightly install nu
```

É isso! A ferramenta cargo fará o download do Nu e das dependências do fonte, o build, e a instalação no caminho bin do cargo de forma que possamos rodá-lo.

Se quiser instalar todas as funcionalidades, inclusive algumas opcionais divertidas, você pode usar:

```
> cargo +nightly install nu --all-features
```

Para isso funcionar, certifique-se de ter todas as dependências (mostradas acima) instaladas no seu sistema.

Uma vez instalado, podemos rodar o Nu usando o comando `nu`:

```
$ nu
/home/jonathan/Source> 
```

## Fazendo o Build a partir dos fontes

Também podemos fazer o build do código fonte diretamente do GitHub. Isso nos dá acesso imediato às últimas funcionalidades e correções do Nu.

```
> git clone https://github.com/nushell/nushell.git
```

O Git vai clonar para nós o repositório principal do nushell. Daí, podemos fazer o build e rodar o Nu:

```
> cd nushell
nushell> cargo build --all-features && cargo run --all-features
```

Você também pode fazer o build e rodar o Nu em modo release:

```
nushell> cargo build --release && cargo run --release
```

Pessoas mais acostumadas com Rust podem se perguntar por que fazemos tanto o "build" como o "run" se o "run" já faz o build por padrão. Isso serve para contornar uma falha da nova opção `default-run` no Cargo e assegurar que será feito o build de todos os plugins, embora isso possa não ser necessário no futuro.
