# Código fuente de ffmpeg.wasm (@ffmpeg/core 0.12.10) y Liberation Sans 1.07.4

Release `ffmpeg-core-0.12.10`. Código fuente correspondiente de los componentes con licencia GPL que
sirve [PDFcadabra](https://pdfcadabra.com) a tu navegador, sin modificar:

- **ffmpeg.wasm** (`@ffmpeg/core` 0.12.10), el motor de **Vídeo a MP3**. Su licencia es la
  GPL-2.0 o posterior y lo distribuimos bajo los términos de la **GPL-3.0** (texto en `LICENSE`).
- **Liberation Sans 1.07.4**, las fuentes estándar de pdf.js 6.3.289 (para
  mostrar los PDF que no incrustan su fuente y en el informe de Comparar PDF). Su licencia es la
  GPL-2.0 con una excepción para fuentes (texto en `LICENSE_LIBERATION`).

Más información en <https://pdfcadabra.com/licencias>.

## Contenido

Todos los archivos están en un solo nivel (los de una release de GitHub no admiten carpetas): el
prefijo `fuente-` marca el código fuente y `binario-` lo que servimos.

- `fuente-ffmpeg.wasm-v12.15.tar.gz`: [ffmpeg.wasm](https://github.com/ffmpegwasm/ffmpeg.wasm) en el commit
  `71aa99d37c02a7b4c435275ca9ef50e612f6efa1` (etiqueta `v12.15`, «RELEASE: @ffmpeg/core and @ffmpeg/core-mt
  v0.12.10»): el `Dockerfile`, los scripts `build/*.sh`, el `Makefile` y el código de
  `src/bind` y `src/fftools` que se compila con FFmpeg. Ojo: la etiqueta `v0.12.10` de ese
  repositorio es la de `@ffmpeg/ffmpeg` 0.12.10 (que lleva `@ffmpeg/core` 0.12.6), no esta.
- `fuente-<componente>-<versión>.tar.gz`: cada componente que esa compilación incluye, en el
  commit exacto (tabla de abajo y `COMPONENTES.tsv`), **Emscripten incluido**. Cada archivo es
  `git archive` de ese commit, comprimido con `gzip -n`.
- `fuente-liberation-fonts-1.07.4.tar.gz`: el código fuente de las Liberation 1.x (ver más abajo).
- `binario-ffmpeg-core-0.12.10.tgz`: el paquete de npm que servimos, para cotejarlo
  (`integrity` sha512-dzNplnn2Nxle2c2i2rrDhqcB19q9cglCkWnoMTDN9Q9l3PvdjZWd1HfSPjCNWc/p8Q3CT+Es9fWOR0UhAeYQZA==).
- `binario-LiberationSans-{Regular,Bold,Italic,BoldItalic}.ttf`: las cuatro TTF de Liberation
  Sans 1.07.4 que trae `pdfjs-dist` 6.3.289 y que servimos, con su nombre
  original tras el prefijo, y `LICENSE_LIBERATION`, su licencia.
- `SHA256SUMS`: `sha256sum -c SHA256SUMS`, en la carpeta con todos los archivos descargados,
  los comprueba todos.

## Componentes de ffmpeg.wasm

| Componente | Versión | Commit | Licencia | Papel |
| --- | --- | --- | --- | --- |
| [FFmpeg](https://github.com/FFmpeg/FFmpeg) | n5.1.4 | `4729204c17f756e186d622060088371d10b34f7e` | GPL-2.0-or-later (compilado con --enable-gpl) | libavcodec, libavformat, libavfilter, libavutil, libswresample, libswscale, libpostproc, libavdevice |
| [x264](https://github.com/ffmpegwasm/x264) | 4-cores | `33cac6b77d5b9259c552156013a817ab23119612` | GPL-2.0-or-later | codificador H.264 (-lx264) |
| [x265](https://github.com/ffmpegwasm/x265) | 3.4 | `2bb5520e9596f361bf0ed81b3b8da0d7fd999069` | GPL-2.0-or-later | codificador H.265 (-lx265) |
| [libvpx](https://github.com/ffmpegwasm/libvpx) | v1.13.1 | `10b9492dcf05b652e2e4b370e205bd605d421972` | BSD-3-Clause | VP8/VP9 (-lvpx) |
| [lame](https://github.com/ffmpegwasm/lame) | 3.100 | `2badea1974ae36cb8312afe99cff1e6b3b5decee` | LGPL-2.0-or-later | codificador MP3 (-lmp3lame) |
| [ogg](https://github.com/ffmpegwasm/Ogg) | v1.3.4 | `bada45718453ac27b56773ae663f7e65112f6a6e` | BSD-3-Clause | contenedor Ogg (-logg) |
| [theora](https://github.com/ffmpegwasm/theora) | v1.1.1 | `7ffd8b2ecfc2d93ae5e16028e7528e609266bfbf` | BSD-3-Clause | Theora (-ltheora) |
| [opus](https://github.com/ffmpegwasm/opus) | v1.3.1 | `e85ed7726db5d677c9c0677298ea0cb9c65bdd23` | BSD-3-Clause | Opus (-lopus) |
| [vorbis](https://github.com/ffmpegwasm/vorbis) | v1.3.3 | `7798164043197d7e33f02de4353ce2aa5b248225` | BSD-3-Clause | Vorbis (-lvorbis -lvorbisenc -lvorbisfile) |
| [zlib](https://github.com/ffmpegwasm/zlib) | v1.2.11 | `cacf7f1d4e3d44d871b605da3b647f07d718623f` | Zlib | compresión (-lz) |
| [libwebp](https://github.com/ffmpegwasm/libwebp) | v1.3.2 | `ca332209cb5567c9b249c86788cb2dbf8847e760` | BSD-3-Clause | WebP (-lwebpmux -lwebp -lsharpyuv) |
| [freetype2](https://github.com/ffmpegwasm/freetype2) | VER-2-10-4 | `6a2b3e4007e794bfc6c91030d0ed987f925164a8` | FTL OR GPL-2.0-or-later | tipografías (-lfreetype) |
| [fribidi](https://github.com/fribidi/fribidi) | v1.0.9 | `f9e8e71a6fbf4a4619481284c9f484d10e559995` | LGPL-2.1-or-later | texto bidireccional (-lfribidi) |
| [harfbuzz](https://github.com/harfbuzz/harfbuzz) | 5.2.0 | `4a1d891c6317d2c83e5f3c2607ec5f5ccedffcde` | MIT («Old MIT») | composición de texto (-lharfbuzz) |
| [libass](https://github.com/libass/libass) | 0.15.0 | `d149636f502f5774ae1a8fb4c554b122674393b2` | ISC | subtítulos ASS/SSA (-lass) |
| [zimg](https://github.com/sekrit-twc/zimg) | release-3.0.5 | `e5b0de6bebbcbc66732ed5afaafef6b2c7dfef87` | WTFPL | escalado (-lzimg) |
| [SDL2](https://github.com/libsdl-org/SDL) | release-2.24.2 | `55b03c7493a7abed33cf803d1380a40fa8af903f` | Zlib | puerto de Emscripten enlazado con -sUSE_SDL=2 |
| [emscripten](https://github.com/emscripten-core/emscripten) | 3.1.40 | `5c27e79dd0a9c4e27ef2326841698cdd4f6b5784` | MIT OR NCSA | compilador (imagen emscripten/emsdk:3.1.40): libc, libc++ y el JavaScript de arranque |

La lista sale del `Dockerfile` de ffmpeg.wasm v12.15 (cada `ADD` o `git clone` con su
`ENV *_BRANCH` o `FFMPEG_VERSION`, y la imagen `emscripten/emsdk`), más SDL2, que el enlazado
pide con `-sUSE_SDL=2` y Emscripten descarga como puerto (`tools/ports/sdl2.py`). Emscripten
3.1.40 (el compilador de la imagen `emscripten/emsdk`) va incluido: aporta la libc, la
libc++ y el JavaScript de arranque que acaban en el binario. No se incluyen `build/aom.sh` ni
`build/wavpack.sh`, que el `Dockerfile` no usa, ni el submódulo `googletest` de zimg, que solo
sirve para sus pruebas.

### Límites conocidos

- **x264 y lame no tienen etiqueta**: el `Dockerfile` los toma de la punta de una rama (x264
  `4-cores`, lame `master`). Aquí van en el commit que es esa punta, sin cambios desde
  2022-08-22 (x264) y 2020-10-29 (lame), anteriores a la publicación de `@ffmpeg/core`
  0.12.10 (2025-01-07); salvo que esas ramas se hubieran reescrito, es el que usó su
  compilación.
- **No se ha comprobado que el binario se reproduzca byte a byte**: no hemos recompilado
  `ffmpeg-core.wasm` para compararlo con el de npm. Lo que se garantiza es que estos son los
  commits que fijan el `Dockerfile` y los scripts de la versión publicada.

## Cómo se compila

Con Docker y BuildKit, desde `ffmpeg.wasm-v12.15`: `make prd` (la receta de producción
del `Makefile`: `FFMPEG_ST=yes` y `EXTRA_CFLAGS="-O3 -msimd128"`) deja `ffmpeg-core.js` y
`ffmpeg-core.wasm` en `packages/core/dist/`. Los `ADD` del `Dockerfile` descargan los
componentes de la tabla; para compilar sin red, sustituye cada uno por el contenido del archivo
`fuente-*.tar.gz` correspondiente.

## Liberation Sans 1.07.4

`fuente-liberation-fonts-1.07.4.tar.gz` es [liberation-1.7-fonts](https://github.com/liberationfonts/liberation-1.7-fonts) (el repositorio de las
Liberation 1.x de Red Hat) en el commit `819661898cf7b177602210b019821e98e4d901b3`, el último con la versión
1.07.4 (2014-05-09): los `.sfd` de FontForge de `src/`, los scripts de `scripts/`, el
`Makefile`, `License.txt` y `COPYING`. El repositorio no tiene etiqueta 1.07.4; que es
el código de las TTF que servimos se comprueba así: cada `LiberationSans-*.ttf` dice «Version
1.07.4» y la fecha de modificación de su tabla `head` es, al segundo, el
`ModificationTime` de su `.sfd` en este commit. El SHA-256 del `tar` de `git archive` de este
commit (prefijo `liberation-fonts-1.07.4/`, antes de comprimirlo) es `9163e1d4e4123b8eb19a8073aaaa125437ae6323cc403bcd45ca339018129345`.
Se compila con FontForge: `make` en esa carpeta.

---

# Source code of ffmpeg.wasm (@ffmpeg/core 0.12.10) and Liberation Sans 1.07.4

Release `ffmpeg-core-0.12.10`. Corresponding source code of the GPL components that PDFcadabra serves
to your browser, unmodified: **ffmpeg.wasm** (`@ffmpeg/core` 0.12.10), the **Video to MP3**
engine, licensed under GPL-2.0 or later and distributed by us under the terms of the **GPL-3.0**
(see `LICENSE`); and **Liberation Sans 1.07.4**, the pdf.js standard fonts, licensed under
GPL-2.0 with a font exception (see `LICENSE_LIBERATION`). All files sit at a single level:
`fuente-*.tar.gz` hold ffmpeg.wasm at the commit that released `@ffmpeg/core` 0.12.10 and
every component its build includes, Emscripten included, at the exact commit (table above,
`COMPONENTES.tsv`), plus the Liberation 1.x sources at commit `819661898cf7b177602210b019821e98e4d901b3`; `binario-*`
are the npm package and the font files we serve; `sha256sum -c SHA256SUMS`, run in the folder
holding all the downloaded files, verifies everything. x264 and lame are pinned at the tip of a branch
(unchanged since 2022 and 2020), and we have not checked that the binary is reproducible byte for
byte. Build with `make prd` (Docker BuildKit) and the fonts with FontForge (`make`).
