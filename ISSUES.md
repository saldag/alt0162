# Alt0162 - Known Issues

## 1. Clicking inside the cent sign should register
**Status:** FIXED
**Description:** Previously, clicking directly on the cent character didn't trigger decorations or sounds due to a check that prevented this.

**Fix applied:** Removed the `if (e.target === fullscreenCent) return;` check so clicks anywhere in the fullscreen overlay (including on the cent sign itself) now create decorations and play sounds.

## 2. Safari initialization issue on Mac
**Status:** FIXED
**Description:** There was an initialization problem when running the page in Safari on Mac.

**Fix applied:** The AudioContext resume code added on fullscreen entry (checking `audioContext.state === 'suspended'` and calling `audioContext.resume()`) resolved Safari's stricter autoplay policies. Safari now properly initializes audio on user interaction.
