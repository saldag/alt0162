# Alt0162 - Cent Sign Clicker - TODO

> For known issues and bug tracking, see [ISSUES.md](ISSUES.md)

---

## Element Catalog

### Main View Elements
| Element | Class | Selectable | Interactive | Notes |
|---------|-------|-----------|-------------|-------|
| Page header | `h1` | Yes | No | Standard text |
| Info box | `.info` | Yes | No | Displays character info |
| Font samples | `.font-sample` | Yes | No | Grid containers |
| Cent displays | `.cent-display` | No (via `.no-select`) | Yes (clickable) | Triggers fullscreen |
| Font names | `.font-name` | Yes | No | Labels |

### Fullscreen Overlay Elements
| Element | Class | Selectable | Interactive | Notes |
|---------|-------|-----------|-------------|-------|
| Fullscreen overlay | `.fullscreen-overlay` | No (parent) | Yes (clickable) | Container - all children non-selectable by default |
| Main cent sign | `.fullscreen-cent` | No (inherits) | No | Display only, color changes in night mode |
| Random decorations | `.random-decoration` | No (inherits) | No | Spawned symbols/ASCII art, lighter in night mode |
| Initial ring | `.initial-ring` | No (inherits) | No | First 8 decorations - black in day, white in night |
| ESC hint | `.close-hint` | No (inherits) | No | Instruction text, inverted in night mode |
| Night mode toggle | `.night-mode-toggle` | Yes (via `.selectable`) | Yes (clickable) | Toggles night mode, text updates |

### Selection Strategy
- **Global utility:** `.no-select` - Apply anywhere to disable selection
- **Fullscreen default:** Everything non-selectable via `.fullscreen-overlay`
- **Interactive override:** Add `.selectable` class to elements that need user interaction in fullscreen
- **Future controls:** Simply add `.selectable` class to make them interactive

---

## Night Mode

### Implementation
Night mode uses a dark background rather than simple color inversion:
- Background: `#1a1a1a` - solid dark gray (fully opaque)
- Cent sign: Light gray (`#e0e0e0`)
- Decorations: Light gray (`#cccccc`)
- Initial ring (first 8): White (`#ffffff`) instead of black
- Toggle button: Top-left corner, updates text to "Day Mode" when active
- ESC hint: Inverted colors for visibility

### Auto-Detection

**Main/Index Page:**
- Uses CSS `@media (prefers-color-scheme: dark)` media query
- Automatically applies dark theme based on OS preference
- Updates in real-time when OS setting changes
- No JavaScript required - pure CSS solution

**Fullscreen Overlay:**
- Automatically detects system dark mode preference on fullscreen entry
- Uses JavaScript `window.matchMedia('(prefers-color-scheme: dark)')`
- Respects OS-level dark mode setting
- Allows manual override (see below)

### Manual Override (Fullscreen Only)
- Click "Night Mode" / "Day Mode" button in top-left of fullscreen
- Manual toggle overrides system preference during current fullscreen session
- Resets to system preference when re-entering fullscreen
- Smooth transitions between modes
- Button is selectable (uses `.selectable` class)

**Note:** Main page follows OS preference only (no manual toggle)

---

## Layout

### Bottom-Anchored Design
The main page uses a bottom-anchored layout with auto-scroll:
- Content sits at the bottom of the viewport
- Uses flexbox: `display: flex; flex-direction: column; justify-content: flex-end`
- `min-height: 100vh` ensures full viewport coverage
- Content grows upward as more elements are added
- Horizontally centered with `max-width` and `margin: 0 auto`
- **Auto-scrolls to bottom on page load** using `window.scrollTo()` to ensure viewport starts at bottom

---

## Future Enhancements
- Consider adding more sound variations
- Possibly integrate actual retro sound files (ICQ, AOL, etc.)
- Additional visual effects or animations
- localStorage persistence for manual night mode override preference
- User controls/options in fullscreen mode (will use `.selectable` class)
- Randomization options (sound order, position rules, ASCII pattern probability)
