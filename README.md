<img width="920" height="430" alt="nexus-retro-horizontal-920x430" src="https://github.com/user-attachments/assets/f9945cb7-77a7-4975-a1cb-c82c7dbd935c" />

Capturas del launcher 
<img width="1917" height="1012" alt="image" src="https://github.com/user-attachments/assets/54286ecb-ba97-4492-8e40-d6ac25b0ab5b" />
<img width="1917" height="655" alt="image" src="https://github.com/user-attachments/assets/b3d5f170-9fc4-46d3-82dc-6e6ffb007106" />
<img width="1917" height="1017" alt="image" src="https://github.com/user-attachments/assets/d2591d31-d249-41a8-85bc-83303cf562c7" />
<img width="1917" height="1016" alt="image" src="https://github.com/user-attachments/assets/f7db4759-dbef-4cb0-8030-5a507aeee11d" />
<img width="1917" height="1016" alt="image" src="https://github.com/user-attachments/assets/368ed81e-df87-46ec-ae29-d8c0c0a9d652" />
<img width="1917" height="1020" alt="image" src="https://github.com/user-attachments/assets/db78b4a5-45fb-4646-9d82-4bb29072c570" />

!DISPONIBLE PARA ANDROID!
<img width="1600" height="746" alt="image" src="https://github.com/user-attachments/assets/d9b0fc86-13e5-4e54-a54e-57cba37129ee" />
<img width="1600" height="746" alt="image" src="https://github.com/user-attachments/assets/0517f4c9-4902-4c5f-bf49-a983f6beeeaa" />
<img width="1600" height="746" alt="image" src="https://github.com/user-attachments/assets/581edc55-d6f0-4ed9-be35-7bd4cc3ab455" />











Launcher universal de juegos retro para **Windows 11, Linux y Android**. Organiza tu colección, detecta sistemas automáticamente y lanza los juegos con **RetroArch**. La interfaz es original: biblioteca de estilo moderno, modo consola a pantalla completa y navegación completa con mando.

> Nexus Retro no incluye ni descarga ROMs, BIOS ni emuladores. Trabaja solo con tus propios archivos y con instalaciones oficiales de RetroArch.

## Requisitos

| Herramienta | Versión |
| --- | --- |
| Node.js | 20 o superior |
| Rust | 1.77 o superior (`rustup`) |
| Windows | Visual Studio Build Tools (C++) y WebView2 (ya incluido en Windows 11) |
| Linux | `webkit2gtk-4.1`, `libayatana-appindicator3`, `librsvg2` ([guía de Tauri](https://v2.tauri.app/start/prerequisites/)) |
| RetroArch | Cualquier versión reciente, instalada desde [retroarch.com](https://www.retroarch.com/?page=platforms), Steam o Flatpak |
| Dolphin (opcional) | Para GameCube y Wii: [dolphin-emu.org](https://dolphin-emu.org/download/) o Flatpak |
| PCSX2 (opcional) | Para PlayStation 2, versión 1.7 o posterior: [pcsx2.net](https://pcsx2.net/downloads) o Flatpak |

## Uso

```bash
npm install
npm run app:dev      # app de escritorio con recarga en caliente
npm run app:build    # instalador (.msi/.exe en Windows, .deb/.AppImage/.rpm en Linux)
npm run dev          # solo la interfaz en el navegador, con datos de demostración
```

```bash
cd src-tauri && cargo test   # tests del núcleo (escáner, base de datos, lanzador)
```

**Windows:** si la carpeta del proyecto tiene una ruta muy larga, el enlazador de MSVC falla con `LNK1104`. Usa una carpeta corta (p. ej. `C:\dev\nexus-retro`) o define `CARGO_TARGET_DIR=C:\t\nexus`.

## Primeros pasos en la app

1. **Configuración › Directorios de biblioteca › Añadir carpeta.** Se recomiendan subcarpetas por sistema (`snes/`, `megadrive/`, `psx/`…). Así los formatos ambiguos (`.bin`, `.zip`) se asignan correctamente.
2. **Emuladores › Detectar todos.** Busca RetroArch, Dolphin y PCSX2 en las rutas habituales (portable, Archivos de programa, Steam, `PATH` y Flatpak). Si alguno no aparece, usa **Seleccionar ejecutable** en su tarjeta. GameCube y Wii se abren con Dolphin, PS2 con PCSX2 y el resto con RetroArch; puedes cambiarlo en **Consolas › sistema › Emulador**.
3. Instala los núcleos desde **RetroArch › Actualizador en línea**. Nexus Retro los detecta solos.
4. Para PlayStation, copia tu propia BIOS en la carpeta `system` de RetroArch. Para PlayStation 2, cópiala en la carpeta `bios` de PCSX2 (vale cualquier nombre de archivo). **Emuladores › Validación de BIOS** comprueba que estén. GameCube y Wii no necesitan BIOS.
   Pon los juegos de GameCube, Wii y PS2 en carpetas con su nombre (`gamecube/`, `wii/`, `ps2/`): los formatos `.iso` y `.rvz` los comparten varios sistemas.
5. Abre un juego y pulsa **JUGAR**. Al cerrar el emulador, el tiempo de juego queda registrado.

**Carátulas automáticas:** al importar juegos, Nexus Retro los identifica con las bases de datos de RetroArch (por CRC, serial o nombre) y descarga su carátula y una captura del servidor oficial de libretro, igual que RetroArch. También completa el año, el género, el desarrollador y el editor. Nunca sobrescribe lo que hayas editado tú. Si tienes una imagen propia con el mismo nombre que el juego (junto a él o en `covers/`, `boxart/` o `media/covers/`), esa tiene prioridad. Desde la ficha de cada juego puedes elegir otra o volver a buscarla.

## Controles

| Mando | Teclado | Acción |
| --- | --- | --- |
| D-pad / stick izquierdo | Flechas | Navegar |
| A | Intro | Seleccionar |
| B | Esc / Retroceso | Volver |
| LB / RB | — | Sección anterior / siguiente |
| Start | F11 | Modo consola |
| Select | `/` | Buscar |

## Documentación

- [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md): módulos, flujo de datos, esquema SQLite y cómo añadir emuladores y plataformas.
- [docs/DESIGN_SYSTEM.md](docs/DESIGN_SYSTEM.md): tokens, escala, componentes y reglas de navegación.
- [docs/ROADMAP.md](docs/ROADMAP.md): fases de desarrollo.

## Licencia

GPL-3.0-or-later, compatible con RetroArch y con la mayoría de núcleos libretro. Cada núcleo mantiene su propia licencia; algunos no permiten uso comercial.
