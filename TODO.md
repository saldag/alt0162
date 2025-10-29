# Alt0162 - Cent Sign Clicker - TODO

## Known Issues

### 1. Clicking inside the cent sign should register
**Status:** ✅ Fixed
**Description:** Previously, clicking directly on the cent character didn't trigger decorations or sounds due to a check that prevented this.

**Fix applied:** Removed the `if (e.target === fullscreenCent) return;` check so clicks anywhere in the fullscreen overlay (including on the cent sign itself) now create decorations and play sounds.

### 2. Safari initialization issue on Mac
**Status:** Under investigation
**Description:** There's an initialization problem when running the page in Safari on Mac. Details TBD.

**Possible causes:**
- AudioContext not starting until user interaction
- Safari's stricter autoplay policies
- Timing issues with audio initialization
- Need to explicitly resume AudioContext after user gesture

**Code location:** Around line 283-286 in index.html where AudioContext is resumed

---

## Future Enhancements
- Consider adding more sound variations
- Possibly integrate actual retro sound files (ICQ, AOL, etc.)
- Additional visual effects or animations
