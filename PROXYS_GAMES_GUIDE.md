# NVG Terminal v2.2 - Complete Guide

Advanced custom command syntax with fullscreen iframe support for proxies, games, and content launchers.

---

## 🎮 NEW: Custom Command - `nvg-iframe` (Fullscreen)

### Purpose
Launch fullscreen iframes with hidden source attributes for proxy/game services. The iframe source is hidden in the DOM for enhanced privacy.

### Syntax
```
nvg-iframe { proxys_and_games://<service> fullscreen }
```

### Available Services

#### Rammerhead Proxy
```bash
$\:nvg:{ nvg-iframe { proxys_and_games://rammerhead fullscreen }
```
- **Service**: Rammerhead web proxy
- **URL**: `https://efly.108-181-32-77.sslip.io`
- **Use Case**: Web browsing through proxy

#### Petezah Proxy
```bash
$\:nvg:{ nvg-iframe { proxys_and_games://petezah fullscreen }
```
- **Service**: Petezah web proxy
- **URL**: `https://tubmledxeni.viar3d.com`
- **Use Case**: Anonymous web browsing

#### NextBrowser
```bash
$\:nvg:{ nvg-iframe { proxys_and_games://nextbrowser fullscreen }
```
- **Service**: NextBrowser application
- **URL**: `https://92850.vercel.app`
- **Use Case**: Browser application

#### MacVG Emulator
```bash
$\:nvg:{ nvg-iframe { proxys_and_games://macvg fullscreen }
```
- **Service**: MacVG classic Mac emulator
- **URL**: `https://kbsigmaboy67.github.io/macvg/`
- **Use Case**: Classic Macintosh emulation and games

### Features
- ✓ **Fullscreen Support** - Press F11 or use fullscreen button
- ✓ **Hidden Source** - iframe src attributes hidden from view
- ✓ **Full Permissions** - fullscreen, clipboard, autoplay, gyroscope, etc.
- ✓ **Quick Close** - Close button in terminal header
- ✓ **Dark Theme Header** - Consistent with terminal design

### Examples

#### Basic Usage
```bash
# Launch Rammerhead proxy
$\:nvg:{ nvg-iframe { proxys_and_games://rammerhead fullscreen }

# Launch Petezah proxy  
$\:nvg:{ nvg-iframe { proxys_and_games://petezah fullscreen }

# Launch NextBrowser
$\:nvg:{ nvg-iframe { proxys_and_games://nextbrowser fullscreen }

# Launch MacVG emulator
$\:nvg:{ nvg-iframe { proxys_and_games://macvg fullscreen }
```

#### With Variables
```bash
# Store favorite service
$\:nvg:{ var proxy = proxys_and_games://rammerhead

# Launch it (still need full syntax)
$\:nvg:{ nvg-iframe { proxys_and_games://rammerhead fullscreen }
```

### How It Works Technically
1. Command parser detects `nvg-iframe` syntax
2. Extracts service name from `proxys_and_games://service`
3. Plugin system resolves to actual HTTPS URL
4. Creates iframe element dynamically
5. Sets src attribute to real URL
6. Positions iframe fullscreen (fixed, top:0, left:0)
7. Adds dark header with close button
8. Sets all necessary allow attributes
9. Maintains iframe src hidden from CSS selector inspection

---

## 🚀 Existing Custom Commands

### `nvg-git-launch` - Direct Git HTML to Blob/Popup
```bash
$\:nvg:{ nvg-git-launch { HTML[`git://kbsigmaboy67/mc/1.8.html`] blob }
```
- Fetches HTML directly from Git URLs
- No iframe wrapper
- Full HTML execution

### `nvg-fetch-html` - Fetch with Target Type
```bash
$\:nvg:{ nvg-fetch-html { git://user/repo/file.html html-blob }
$\:nvg:{ nvg-fetch-html { api://jsonplaceholder/posts/1 text-popup }
```
- `html-blob` / `html-popup` - For HTML content
- `text-blob` / `text-popup` - For formatted text

### `nvg-open-raw` - Raw Content Loading
```bash
$\:nvg:{ nvg-open-raw { api://jsonplaceholder/posts/1 popup }
```
- Flexible content loading with options
- Supports blob, popup, fullscreen modes

---

## 🔌 Plugin System

### Proxys & Games Plugin (NEW)
```
proxys_and_games://rammerhead      # Rammerhead proxy
proxys_and_games://petezah         # Petezah proxy
proxys_and_games://nextbrowser     # NextBrowser app
proxys_and_games://macvg           # MacVG emulator
```

### Traditional Plugins
```
git://user/repo/path               # GitHub Pages
github://user/repo/branch/path     # GitHub Raw
vercel://subdomain/path            # Vercel
railway://projectId/path           # Railway
netlify://siteName/path            # Netlify
local://host:port/path             # Local Server
api://service/path                 # APIs
```

---

## 📝 Practical Examples

### Example 1: Quick Access Proxy Launcher
```bash
# Rammerhead for web browsing
$\:nvg:{ nvg-iframe { proxys_and_games://rammerhead fullscreen }

# Petezah for anonymous browsing
$\:nvg:{ nvg-iframe { proxys_and_games://petezah fullscreen }
```

### Example 2: Retro Gaming with MacVG
```bash
# Launch classic Mac emulator with games
$\:nvg:{ nvg-iframe { proxys_and_games://macvg fullscreen }
```

### Example 3: NextBrowser Launcher
```bash
# Launch NextBrowser application
$\:nvg:{ nvg-iframe { proxys_and_games://nextbrowser fullscreen }
```

### Example 4: Mixed Workflow
```bash
# Get API data in text viewer
$\:nvg:{ nvg-fetch-html { api://jsonplaceholder/posts/1 text-popup }

# Launch proxy in fullscreen
$\:nvg:{ nvg-iframe { proxys_and_games://rammerhead fullscreen }

# View GitHub source in blob
$\:nvg:{ nvg-fetch-html { github://user/repo/main/README.md text-blob }
```

---

## 🎯 Common Workflows

### Workflow 1: Proxy Browsing Session
```bash
# Open terminal in one tab
# Launch proxy in fullscreen in another window
$\:nvg:{ nvg-iframe { proxys_and_games://rammerhead fullscreen }

# Use proxy for web access
# Close with button and return to terminal
```

### Workflow 2: Retro Gaming + Terminal
```bash
# Keep terminal open
$\:nvg:{ nvg-iframe { proxys_and_games://macvg fullscreen }

# Play games
# Close and check API data
$\:nvg:{ nvg-fetch-html { api://jsonplaceholder/posts text-popup }
```

### Workflow 3: Content Testing
```bash
# View GitHub source
$\:nvg:{ nvg-fetch-html { github://user/repo/main/index.html html-blob }

# Test in MacVG environment
$\:nvg:{ nvg-iframe { proxys_and_games://macvg fullscreen }

# Check in NextBrowser
$\:nvg:{ nvg-iframe { proxys_and_games://nextbrowser fullscreen }
```

---

## 🔧 Technical Details

### How Hidden Sources Work
The iframe src attribute is dynamically set using JavaScript rather than hardcoded in HTML. This makes it:
1. Less visible in static source inspection
2. Hidden from basic CSS selectors
3. Dynamic and runtime-dependent
4. Protected from DOM scraping tools

### Browser Support
- Chrome/Chromium: Full support ✓
- Firefox: Full support ✓
- Safari: Full support (popup restrictions may apply) ✓
- Edge: Full support ✓

### Permissions Set on iframes
```
fullscreen              # Fullscreen capability
picture-in-picture      # PiP support
accelerometer           # Motion sensors
autoplay                # Auto-play media
clipboard-write         # Clipboard access
encrypted-media         # Media encryption
gyroscope              # Gyroscope sensor
payment                # Payment APIs
usb                    # USB access
xr-spatial-tracking    # XR support
```

---

## 🔒 Security & Privacy

### Source Hiding
- iframe src is not visible in DevTools
- Dynamic insertion prevents static analysis
- Runtime-only URL resolution

### Service Selection
- All services are external URLs
- No data stored locally except variables
- All communication is HTTPS
- Browser security policies enforced

### Recommendations
- Use over HTTPS connections
- Trust the services you're proxying through
- Close iframes when not in use
- Clear browser data if desired

---

## 📋 Command Reference

| Command | Purpose | Example |
|---------|---------|---------|
| `nvg-iframe` | Fullscreen iframe | `nvg-iframe { proxys_and_games://rammerhead fullscreen }` |
| `nvg-git-launch` | Git HTML blob | `nvg-git-launch { HTML[\`git://user/repo/file\`] blob }` |
| `nvg-fetch-html` | Fetch with target | `nvg-fetch-html { git://user/repo/file html-blob }` |
| `nvg-open-raw` | Raw content | `nvg-open-raw { api://service/path popup }` |
| `var` | Variables | `var name = value` |
| `help` | Command help | `help` |
| `about` | About terminal | `about` |

---

## 💡 Pro Tips

1. **Multiple Services** - Open different proxies in different windows
2. **Quick Switching** - Close and open different services quickly
3. **Mixed Usage** - Alternate between terminal and fullscreen apps
4. **API Testing** - Check APIs while using proxies/emulators
5. **Gaming + Work** - Keep terminal minimized, game in fullscreen

---

## 🎮 Service Descriptions

### Rammerhead
Advanced web proxy service for anonymous browsing and accessing restricted content.

### Petezah
Lightweight proxy solution for fast web browsing through intermediary.

### NextBrowser
Modern browser application built with web technologies.

### MacVG
Authentic classic Macintosh (68k/PPC) emulator running System 7 software and classic games.

---

## 🚀 Getting Started

### First Time Setup
1. Open `terminal_advanced.html` in browser
2. Type `help` to see commands
3. Try: `$\:nvg:{ nvg-iframe { proxys_and_games://macvg fullscreen }`
4. Explore the emulator
5. Close with button to return

### Recommended First Commands
```bash
# View available commands
$\:nvg:{ help

# About the terminal
$\:nvg:{ about

# Launch MacVG emulator
$\:nvg:{ nvg-iframe { proxys_and_games://macvg fullscreen }

# Try a proxy
$\:nvg:{ nvg-iframe { proxys_and_games://rammerhead fullscreen }
```

---

## ❓ FAQ

**Q: How do I close the fullscreen iframe?**
A: Click the "✕ Close" button in the dark header at the top, or press Escape in some browsers.

**Q: Can I use variables with proxys_and_games?**
A: Yes, you can store the full command but you'll need the complete syntax to execute it.

**Q: Are these services safe?**
A: These are external services. Use trusted proxies and be aware of security implications.

**Q: Can I run multiple iframes at once?**
A: Only one fullscreen iframe at a time. Open new windows/tabs for multiple services.

**Q: How is the source hidden?**
A: JavaScript dynamically sets the iframe src attribute instead of hardcoding it in HTML.

---

Generated for NVG Terminal v2.2 - Proxys & Games Edition
