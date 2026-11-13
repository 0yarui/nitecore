# Rebuilding the SoundTouchJS bundle

`index.html` includes SoundTouchJS 0.3.0 bundled into one script. To rebuild it:

```bash
npm init -y
npm install soundtouchjs@0.3.0 esbuild
npx esbuild build/st-entry.js --bundle --format=iife --minify --legal-comments=none --outfile=st.bundle.js
```

Then put the contents of `st.bundle.js` in the `<script>` block of `index.html` that defines `NiteSoundTouch`.
