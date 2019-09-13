# Instalando Nu

La mejor manera actualmente para poner en marcha Nu es instalándolo a través de [crates.io](https://crates.io), descargando desde [nuestra página](https://github.com/nushell/nushell/releases), o compilarlo desde la fuente.

## Binarios

Puedes descargar Nu compilado desde [nuestra página](https://github.com/nushell/nushell/releases). Alternativamente, si usas [Homebrew](https://brew.sh/) para macOS, puedes instalar el binario ejecutando `brew install nushell`.

## Preparación

Antes de que podamos instalar Nu, necesitamos asegurarnos de que nuestro sistema tenga los requerimientos necesarios. Actualmente significa que debemos verificar tener instalado tanto el Rust toolchain así como las dependencias locales.

### Instalando Rust

En el caso de que no dispongamos de Rust en nuestro sistema la mejor manera de instalarlo es mediante [rustup](https://rustup.rs/). Rustup es una manera de manejar instalaciones de Rust incluyendo distintas versiones de Rust.

Nu actualmente requiere la versión **nightly** de Rust. En el momento de abrir "rustup" te solicitará qué versión de Rust deseas instalar:

```
Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

Selecciona la opción #2 para personalizar la instalación, 

```
Default host triple?
```

Presiona enter aquí para seleccionar el predeterminado.

```
Default toolchain? (stable/beta/nightly/none)
```

Asegúrate de ingresar "nightly" aquí y presiona enter. Esto debe darte esta configuración:

```
Modify PATH variable? (y/n)
```

Opcionalmente puedes actualizar el path. Esto es generalmente una buena idea debido a que los próximos pasos serán más fáciles.


```
Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: nightly
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

Puedes observar el toolchain predeterminado ahora cambió a la versión nightly. No te preocupes si esto suena un poco arriesgado. El compilador Rust se ejecuta a través de una batería llena de pruebas. La versión nightly del compilador suele ser tan confiable como la versión stable.

Una vez que estamos listos presionamos 1 y luego enter. Posterior a este paso podemos seguir las instrucciones que "rustup" nos proporciona y deberíamos tener un compilador Rust funcionando en nuestro sistema.

Si prefieres no instalar Rust mediante "rustup", también puedes instalar a través de otros métodos (Ej. un paquete en alguna distro de Linux). Solo asegúrate de instalar una versión nightly reciente del toolchain.

## Dependencias

### Debian/Ubuntu

Vas a necesitar instalar "pkg-config" y "libssl-dev":

```
apt install pkg-config libssl-dev
```

Usuarios de Linux que desean usar las funcionalidades opcionales `rawkey` o `clipboard` necesitarán instalar los paquetes "libx11-dev" y "libxcb-composite0-dev":

```
apt install libx11-dev libxcb-composite0-dev 
```

### macOS

Usando [homebrew](https://brew.sh/), vas a necesitar instalar la fórmula "openssl":

```
brew install openssl
```

## Instalando desde [crates.io](https://crates.io)

Una vez instaladas las depependencias que Nu necesita, podemos instalarla usando el comando `cargo` que viene con el compilador Rust.

```
> cargo install nu
```

¡Eso es todo! Cargo hará el trabajo de descarga Nu junto con sus dependencias, construirla e instalarla en el bin path de cargo para que podamos arrancarlo.

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

Git nos clonará el repositorio principal de Nu. Partiendo de ahí podemos contruir y arrancar Nu:

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
