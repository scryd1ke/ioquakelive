# Fork de scryd1ke

> Este es un **fork** de [foressssst/ioquakelive](https://github.com/foressssst/ioquakelive) que se usa para **proponer arreglos** al proyecto original. Para jugar, descarga la versión oficial desde [Releases](https://github.com/foressssst/ioquakelive/releases) del proyecto original.

Cada arreglo va en **su propia rama**, sale de la versión más reciente de `main` del proyecto original y se envía con su propio pull request. Así cada cambio se puede revisar, aceptar o rechazar por separado.

## Ramas de este fork

| Rama | Para quién | Qué arregla | Pull request |
|---|---|---|---|
| [`fix/browser-columnas`](https://github.com/scryd1ke/ioquakelive/tree/fix/browser-columnas) | Todos los que usan el Match Browser | Las columnas **Players** y **Ping** ya no se salen del recuadro cuando un servidor tiene muchos tags. Agrega un botón **Stop** para detener el escaneo de servidores sin esperar a que termine. | [#11](https://github.com/foressssst/ioquakelive/pull/11) ✅ aceptado en [v2.0.1](https://github.com/foressssst/ioquakelive/releases/tag/v2.0.1) |
| [`fix/steam-connect-juego-abierto`](https://github.com/scryd1ke/ioquakelive/tree/fix/steam-connect-juego-abierto) | Quienes entran a servidores desde **[ql.syncore.org](https://ql.syncore.org)** o con "Unirse a la partida" de Steam | Con el juego **ya abierto**, los enlaces `steam://connect/IP:puerto` no hacían nada. Ahora el juego recibe el aviso de Steam (`GameServerChangeRequested`) y se conecta al servidor, como el Quake Live original. | [#12](https://github.com/foressssst/ioquakelive/pull/12) ✅ aceptado en [v2.0.1](https://github.com/foressssst/ioquakelive/releases/tag/v2.0.1) |
| [`fix/icono-conexion-picmip`](https://github.com/scryd1ke/ioquakelive/tree/fix/icono-conexion-picmip) | Quienes juegan con `r_picmip` alto (lo normal en competitivo) | El ícono de pérdida de conexión (abajo a la derecha) se veía como un **cuadro azul liso**. Ahora se carga sin `r_picmip`, como los demás íconos del HUD, y se ve el cable de red. | [#13](https://github.com/foressssst/ioquakelive/pull/13) ✅ aceptado en [v2.0.1](https://github.com/foressssst/ioquakelive/releases/tag/v2.0.1) |

## Cómo se trabaja en este fork

1. La rama nueva sale de `main` del proyecto original, nunca de otra rama de arreglo.
2. Cada rama lleva un commit por cambio, con el problema, la causa y el arreglo explicados en el mensaje.
3. Antes de enviarse, se compila en Windows x64 y x86 y se prueba en el juego.
4. Se envía con un pull request a [foressssst/ioquakelive](https://github.com/foressssst/ioquakelive). La decisión de incluirlo es del proyecto original.

---

*Abajo sigue el README original del proyecto.*

# ioquakelive

Una implementación de código abierto de Quake Live, desarrollada por el equipo de [Quake Club](https://quakeclub.com). Reproduce la última versión original del juego (1069) sobre el motor [ioquake3](https://ioquake3.org/), incorporando mejoras propias y manteniendo la compatibilidad con el juego original.

El proyecto toma como punto de partida el trabajo de [Thomas Jones](https://github.com/tjone270/ioquakelive), cuya implementación sirvió de base e inspiración para continuar su desarrollo.

## Cómo jugar

Necesitarás una copia legítima de [Quake Live en Steam](https://store.steampowered.com/app/282440/Quake_Live/), ya que ioquakelive no incluye los archivos originales del juego, por lo que utiliza los de tu propia instalación.

1. Descarga la última versión desde [Releases](https://github.com/foressssst/ioquakelive/releases).
2. Extrae los archivos en la carpeta que prefieras.
3. Ejecuta `ioquakelive.x86_64.exe` para utilizar la version OpenGL o `ioquakelive-vulkan.x86_64.exe` si prefieres Vulkan.

En Windows, el juego detecta automáticamente tu instalación de Quake Live y copia el archivo `pak00.pk3`. Si la detección automática no funciona, puedes copiarlo manualmente a la carpeta `baseq3`.

## Características

- Compatibilidad con OpenGL, OpenGL 2 y Vulkan, incluyendo soporte para NVIDIA Reflex y AMD Anti-Lag 2 en Vulkan.
- Carga de recursos en varios hilos y FPS desbloqueados.
- Reproductor de demos mejorado, con soporte para `cg_xray` (wallhack) durante la reproducción de demos y al espectear. Esta función no está disponible durante las partidas.
- Integración con Quake Club.
- Nuevos comandos de consola: `help <comando o cvar>` y `searchconsole`.

## Compilación

Antes de compilar, inicializa los submódulos del proyecto:

```bash
git submodule update --init --recursive
```

- **Windows:** requiere Visual Studio 2026 con el toolset v145. Para compilar, ejecuta:

  ```bash
  MSBuild misc\msvc\ioquakelive.sln -p:Configuration=Release -p:Platform=x64
  ```

- **Linux y macOS:** ejecuta `make release`. Se requiere tener SDL3 instalado.

## Créditos y licencia

Este proyecto también se basa en el trabajo de otros desarrolladores y proyectos de código abierto:

- [Thomas Jones — ioquakelive](https://github.com/tjone270/ioquakelive)
- [ioquake3](https://github.com/ioquake/ioq3)
- [Quake3e](https://github.com/ec-/Quake3e)
- [CPMA](https://playmorepromode.com/)

Quake Live y sus recursos pertenecen a id Software. El código fuente de este proyecto se distribuye bajo la licencia GPL v2.
