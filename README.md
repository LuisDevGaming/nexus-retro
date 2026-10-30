# Nexus Retro
<img width="920" height="430" alt="nexus-retro-horizontal-920x430" src="https://github.com/user-attachments/assets/0a06692f-cd9a-479d-b5dc-b1498e0a7e9b" />

Launcher universal de juegos retro para **Windows 11 y Linux**. Organiza tu colección, detecta sistemas automáticamente y lanza los juegos con **RetroArch**. La interfaz es original: biblioteca de estilo moderno, modo consola a pantalla completa y navegación completa con mando.




> Nexus Retro no incluye ni descarga ROMs, BIOS ni emuladores. Trabaja solo con tus propios archivos y con instalaciones oficiales de RetroArch.
<img width="1600" height="826" alt="image" src="https://github.com/user-attachments/assets/14b9711c-a2e3-43b3-ad6a-2ac21d00a77c" />
<img width="1917" height="1017" alt="image" src="https://github.com/user-attachments/assets/3c0b9907-5aab-49ae-8001-e89fc0a06a90" />
<img width="1917" height="1016" alt="image" src="https://github.com/user-attachments/assets/651edc39-f4b9-4894-8e1c-693c3dfd462a" />
<img width="1857" height="622" alt="image" src="https://github.com/user-attachments/assets/415ff145-0a35-4e4d-888e-01130dc2921a" />

!Ya está disponible para android! y es compatible con RetroArchievements
<img width="1600" height="746" alt="image" src="https://github.com/user-attachments/assets/24b16c73-d5ad-4227-b692-bbf6ffc845c8" />
<img width="1600" height="746" alt="image" src="https://github.com/user-attachments/assets/2aa284e9-7654-4287-ba73-970dfcd16e56" />
<img width="1600" height="746" alt="image" src="https://github.com/user-attachments/assets/b677724b-b4cf-4371-9000-ac4dc20f4ab0" />
<img width="1600" height="746" alt="image" src="https://github.com/user-attachments/assets/4e9ea0a5-566f-4147-a339-fdf6ed1dab7f" />





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
