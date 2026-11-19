# Video Rotation Duck

A static, browser based video rotator that can be hosted on GitHub Pages. It selects local video files up to 6 GB, previews quarter-turn rotation and horizontal/vertical flips, and exports WebM, MP4, MOV, or AVI at source, HD (1080p), or HD Ultra (up to 4K) resolution. Video stays on the user's device; GitHub Pages does not receive or store the video.

## Publish with GitHub Pages

1. Add `index.html` and this `README.md` to the root of a GitHub repository, or place them in a `/docs` folder.
2. In the repository, open **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select the branch and folder containing `index.html`, then save.

The app has no build step or server requirement. GitHub Pages serves the files over HTTPS.

## Notes

- Video selection accepts files through 6 GB, including videos with generic/empty MIME labels when their filename has a common video extension. Export decodes and rotates the video in the browser; the source file is not uploaded to a server.
- WebM export uses the browser's `MediaRecorder` in real time. The default **Compress export to stay under 2 GB** option sets a conservative bitrate from the video duration and targets about 1.6 GiB to leave headroom below 2 GiB. Browser encoders vary, so the final size is not an absolute guarantee.
- If supported, MP4 is recorded directly by the browser. Chrome supports the File System Access save picker, so the app can write recording chunks to a device location as they are produced. Other browsers show a manual download link after export.
- MOV and AVI conversion uses FFmpeg.wasm, which has a documented 2 GB input-file limit. Large source files can still be exported as MP4 if the browser supports MP4 recording, or as WebM. Large exports need substantial device memory and processing time.
- Browser codec support varies. Input playback depends on the codecs in the uploaded video. The first MP4/MOV/AVI export downloads the conversion engine from jsDelivr.
- The 6 GB limit is checked locally in the page. No video upload is made to GitHub or another server.
