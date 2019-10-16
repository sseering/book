# Instalando Nu

La mejor manera actualmente para poner en marcha Nu es instalándolo a través de [crates.io](https://crates.io), descargando desde [nuestra página](https://github.com/nushell/nushell/releases), compilarlo desde la fuente, o jalando un contenedor preconstruido con Docker.

## Binarios

Puedes descargar Nu compilado desde [nuestra página](https://github.com/nushell/nushell/releases). Alternativamente, si usas [Homebrew](https://brew.sh/) para macOS, puedes instalar el binario ejecutando `brew install nushell`.

## Contenedores de Docker preconstruidos

Si deseas jalar un contenedor preconstruido, puedes navegar las etiquetas de la [organización nushell](https://quay.io/organization/nushell)
en Quay.io. Jalar un contenedor se reduce a:

```bash
$ docker pull quay.io/nushell/nu
$ docker pull quay.io/nushell/nu-base
```

Tanto "nu-base" y "nu" proporciona el binario `nu`, sin embargo nu-base también incluye el código fuente en `/code` en el contenedor y todas las dependencias.

Opcionalmente, también puedes construir los contenedores localmente utilizando los [dockerfiles proporcionados](https://github.com/nushell/nushell/tree/master/docker):
Para construir la imagen base:

```bash
$ docker build -f docker/Dockerfile.nu-base -t nushell/nu-base .
``` 

y luego para construir el contenedor más pequeño (usando una construcción de varias etapas):

```bash
$ docker build -f docker/Dockerfile -t nushell/nu .
``` 

De cualquier manera, se puede ejecutar cualquier contenedor de la siguiente manera:

```bash
$ docker run -it nushell/nu-base
$ docker run -it nushell/nu
/> exit
```

El segundo contenedor es un poco más pequeño, si tamaño es importante para ti.

## Preparación

Antes de que podamos instalar Nu, necesitamos asegurarnos de que nuestro sistema tenga los requerimientos necesarios. Actualmente significa que debemos verificar tener instalado tanto el Rust toolchain así como las dependencias locales.

### Instalando Rust

En el caso de que no dispongamos de Rust en nuestro sistema la mejor manera de instalarlo es mediante [rustup](https://rustup.rs/). Rustup es una manera de manejar instalaciones de Rust incluyendo distintas versiones de Rust.

Nu actualmente requiere la versión **beta** de Rust. La mejor manera de `rustup` inferir la versión correcta para ti. En el momento de abrir `rustup` te solicitará qué versión de Rust deseas instalar:

```
Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

Una vez que estamos listos, presionamos 1 y luego enter. Después de este punto, podemos seguir las instrucciones que `rustup` proporciona y deberíamos tener un compilador de Rust listo en el sistema. La versión correcta del compilador se obtendrá en el momento que realices la compilación.

Si prefieres no instalar Rust mediante `rustup`, también puedes instalar a través de otros métodos (Ej. un paquete en alguna distribución de Linux). Solo asegúrate de instalar una versión correspondiente del toolchain (puedes encontrarla en el archivo `rust-toolchain`)

## Dependencias

### Debian/Ubuntu

Vas a necesitar instalar "pkg-config" y "libssl-dev":

```
apt install pkg-config libssl-dev
```

Usuarios de Linux que desean usar las funcionalidades opcionales `rawkey` o `clipboard` necesitarán instalar los paquetes "libx11-dev" y "libxcb-composite0-dev":

```
apt install libxcb-composite0-dev libx11-dev
```

### macOS

Usando [homebrew](https://brew.sh/), vas a necesitar instalar la fórmula "openssl":

```
brew install openssl cmake
```

## Instalando desde [crates.io](https://crates.io)

Una vez instaladas las depependencias que Nu necesita, podemos instalarla usando el comando `cargo` que viene con el compilador Rust.

```
> cargo +beta install nu
```

¡Eso es todo! Cargo hará el trabajo de descarga Nu junto con sus dependencias, construirla e instalarla en el bin path de cargo para que podamos arrancarlo.

Si deseas instalar todas las funciones, incluyendo algunas opcionales divertidas, puedes hacer:

```
> cargo +beta install nu --all-features
```

Para que esto funcione, asegúrate de tener todas las dependencias instaladas (que se muestran arriba) en el sistema.

Finalizada la instalación podemos ejecutar Nu usando el comando `nu`:

```
$ nu
/home/jonathan/Source> 
```

## Construyendo desde la fuente

También podemos contruir nuestro propio Nu directamente desde github. Esto nos da acceso inmediato a las últimas funcionalidades y corrección de bugs.

```
> git clone https://github.com/nushell/nushell.git
```

Git nos clonará el repositorio principal de Nu. Partiendo de ahí podemos contruir y arrancar Nu si estamos usando `rustup` con:

```
> cd nushell
nushell> cargo build --all-features && cargo run --all-features
```

También puedes construir y arrancar Nu en modo release:

```
nushell> cargo build --release && cargo run --release
```
Gente familiarizada con Rust se preguntará la razón por la que hacemos un paso "build" y otro paso "run" si "run" construye por defecto. Esto es para evitar una deficiencia de la nueva opción `default-run` en Cargo y asegurar que todos los plugins se construyan aunque puede que esto no sea necesario en el futuro.

**Nota:** Si te encuentras trabajando tanto en modo debug y release, asegúrate de ejecutar `cargo clean` cuando cambies entre ellas. Nu buscará plugins en los directorios tanto de debug así como release y puede suceder que cargue versiones de un plugin que no tienes intenciones de usar.

## Establecer como shell de inicio de sesión

{% hint style="warning" %} Nu todavía está en desarrollo y puede no ser estable para uso diario. {% endhint %}

Para configurar la shell de inicio de sesión, puedes usra el comando [`chsh`](https://linux.die.net/man/1/chsh).
En algunas distribuciones de Linux se encuentra una lista válida de shells en `/etc/shells` y no permitirá cambiar la shell hasta que Nu esté en la lista blanca. Es posible que vea un error similar al siguiente si no ha actualizado el archivo `shells`:

```
chsh: /home/username/.cargo/bin/nu is an invalid shell
```

Puedes agregar Nu a la lista de shells válidas añadiendo el binario al archivo `shells`. La ruta para agregar puedes encontrarla con el comando `which nu`, usualmente es `$HOME/.cargo/bin/nu`.