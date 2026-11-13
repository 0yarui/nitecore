# Third-party notices

`index.html` contains the following third-party software, each in its own `<script>` block (or inline SVG), so any of them can be replaced independently. The original code of this project is under the MIT License (see `LICENSE`).

| Component | Version | License | Used for | Source |
|---|---|---|---|---|
| lamejs | 1.2.1 | LGPL-3.0 | MP3 encoding | https://github.com/zhuker/lamejs |
| SoundTouchJS | 0.3.0 | LGPL-2.1 | Pitch shifting without changing speed | https://github.com/cutterbl/SoundTouchJS |
| libflac.js (on libFLAC) | 5.6.0 | MIT (libFLAC: BSD-3-Clause) | FLAC encoding | https://github.com/mmig/libflac.js |
| Lucide icons | 1.71.0 | ISC (some icons derived from Feather, MIT) | Interface icons (inline SVG) | https://lucide.dev |
| Octicons (GitHub mark) | 19 | MIT | GitHub icon in the header (inline SVG). The GitHub logo itself is a trademark of GitHub, Inc. | https://primer.style/octicons |

Full license texts are in the `licenses/` folder:

- `licenses/LGPL-3.0.txt` (lamejs; the LGPL-3.0 incorporates the GPL-3.0, included as `licenses/GPL-3.0.txt`)
- `licenses/lamejs-LAME-notice.txt` (the license notice shipped inside the lamejs package, about the underlying LAME encoder)
- `licenses/soundtouchjs-LGPL-2.1.txt`
- `licenses/libflacjs-MIT.txt`
- `licenses/lucide-ISC.txt`
- `licenses/octicons-MIT.txt`

## Notes on the LGPL components

- **lamejs** is used unmodified (the published `lame.min.js` from npm, version 1.2.1) and is a JavaScript port of the LAME MP3 encoder.
- **SoundTouchJS** 0.3.0 is bundled unmodified into a single minified script with esbuild. The bundle entry file is `build/st-entry.js`; see the README for how to rebuild it. To use a different version, rebuild the bundle and replace the corresponding `<script>` block in `index.html`.
- Because these libraries are separate script blocks in a readable HTML file, anyone can replace them with a modified version.

The LGPL-3.0 and GPL-3.0 texts come from the SPDX license list (formatting normalized); the authoritative versions are at https://www.gnu.org/licenses/.

Last checked: 2026-11-13. If you reuse this project, verify the licenses and versions against the upstream sources.
