# Video Rotation Duck

A static, browser based video rotator that can be hosted on GitHub Pages. It accepts local video files up to 6 GB, previews quarter-turn rotation and horizontal/vertical flips, and exports WebM, MP4, MOV, or AVI at source, HD (1080p), or HD Ultra (up to 4K) resolution. Video stays on the user's device.

## Publish with GitHub Pages

1. Add `index.html` and this `README.md` to the root of a GitHub repository, or place them in a `/docs` folder.
2. In the repository, open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select the branch and folder containing `index.html`, then save.

The app has no build step or server requirement. GitHub Pages serves the files over HTTPS.

## Notes

- WebM export uses the browser's `MediaRecorder` in real time. MP4, MOV, and AVI are converted locally with FFmpeg.wasm, which is loaded from jsDelivr when needed. Keep the page open while exporting.
- FFmpeg.wasm has a documented 2 GB input-file limit. The app accepts files up to 6 GB, but for files above 2 GB choose WebM; non-WebM conversion is blocked. Large exports also need substantial device memory and processing time.
- Browser codec support varies. Input playback depends on the codecs in the uploaded video. The first MP4/MOV/AVI export downloads the conversion engine from jsDelivr.
- The 6 GB limit is checked locally in the page. No video upload is made to GitHub or another server.
