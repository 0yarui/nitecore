# nitecore

A truly private nightcore maker. Turn any song into nightcore in your browser.

Live site: https://nitecore.pages.dev

## What it does

- Plays your file as soon as you open it and lets you set the speed from **0.50x to 2.00x** (default **1.25x**). Nightcore raises speed and pitch together.
- **Advanced** section:
  - **Pitch** (-12 to +12 semitones) on top of the speed, without changing the speed
  - **Reverb** (mix, decay, pre-delay)
  - **Bass boost**
  - Output quality: FLAC 24-bit or 16-bit, or MP3 at 320, 256, 192 or 128 kbps
- Exports **FLAC** (lossless, the default) or **MP3**. Downloads are named `<original name> (Nitecore).flac` or `.mp3`.
- Dark and light themes.

## Privacy

All processing happens locally with the Web Audio API. Your file is never uploaded, and the page makes no network requests. This is enforced by the Content-Security-Policy in `index.html` (`connect-src 'none'`), and you can check it yourself in the browser's developer tools.

## How it works

- The audio is decoded with `decodeAudioData`. Preview uses Web Audio nodes (speed through `playbackRate`, bass through a low-shelf filter, reverb through a convolver with a generated impulse response).
- For export, the speed change is applied with a windowed-sinc (Kaiser) resampler with anti-aliasing, because the browser's built-in resampler has none.
- Pitch is shifted independently with SoundTouchJS (time-stretch first, then the resampler turns the stretch into a pitch change).
- FLAC is encoded with libflac.js and MP3 with lamejs.
- If the result would clip, the whole file is lowered slightly and the page says so.

## Quality notes

The best possible quality is that of your original file. Exporting an MP3 as FLAC does not improve it; it only avoids losing more. Pitch shifting and reverb are processing, not lossless operations, and large pitch shifts can sound slightly processed.

## Project layout

- `index.html`: the whole app (HTML, CSS, JavaScript and the libraries, in one file)
- `_headers`: security headers for Cloudflare Pages
- `build/`: how to rebuild the bundled SoundTouchJS script
- `licenses/` and `THIRD-PARTY-NOTICES.md`: licenses of the included libraries

## Deploy (Cloudflare Pages)

Upload `index.html` and `_headers` together (as loose files, not inside a folder).

## Browser support

Works in current browsers that support the Web Audio API. It was developed mainly against Chromium and Firefox.

## License

MIT for the original code (see `LICENSE`). Third-party libraries keep their own licenses (see `THIRD-PARTY-NOTICES.md`).
