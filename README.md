# NVG Terminal - Complete Package v2.2

Advanced multi-platform terminal interface with JavaScript window API, custom commands, and fullscreen iframe support for proxies and games.

## 📦 What's Included

### HTML Files
1. **terminal.html** (v1.0)
   - Original feature-rich terminal
   - Window management system
   - Variable storage
   - 10+ utility commands

2. **terminal_advanced.html** (v2.2 - Latest) ⭐
   - Fullscreen iframe support
   - Proxys & Games plugin (NEW)
   - Custom commands (nvg-iframe, nvg-git-launch, nvg-fetch-html, nvg-open-raw)
   - Direct HTML/Blob loading
   - Hidden iframe sources for privacy

### Documentation Files
1. **README.md** - This file
2. **TERMINAL_GUIDE.md** - v1.0 basic guide
3. **ADVANCED_GUIDE.md** - v2.1 full API guide
4. **CUSTOM_COMMANDS_GUIDE.md** - v2.1 custom syntax
5. **PROXYS_GAMES_GUIDE.md** - v2.2 NEW fullscreen & proxies guide

## 🚀 Quick Start

### For Latest Version (v2.2)
1. Open `terminal_advanced.html` in your web browser
2. Type `help` to see all available commands
3. Try a proxy: `$\:nvg:{ nvg-iframe { proxys_and_games://rammerhead fullscreen }`
4. Try MacVG: `$\:nvg:{ nvg-iframe { proxys_and_games://macvg fullscreen }`
5. Try custom commands: `$\:nvg:{ nvg-git-launch { HTML[`git://kbsigmaboy67/mc/1.8.html`] blob }`

### For Original Version (v1.0)
1. Open `terminal.html` in your web browser
2. Type `help` for command list
3. Explore basic features and plugins

## 💻 System Requirements
- Modern web browser (Chrome, Firefox, Safari, Edge)
- JavaScript enabled
- Internet connection (for fetching from URLs)
- Popups allowed in browser settings

## 🎮 New in v2.2 - Proxys & Games

### Fullscreen Iframe Command
```bash
# Rammerhead web proxy
$\:nvg:{ nvg-iframe { proxys_and_games://rammerhead fullscreen }

# Petezah web proxy
$\:nvg:{ nvg-iframe { proxys_and_games://petezah fullscreen }

# NextBrowser application
$\:nvg:{ nvg-iframe { proxys_and_games://nextbrowser fullscreen }

# MacVG classic Mac emulator
$\:nvg:{ nvg-iframe { proxys_and_games://macvg fullscreen }
```

### Features
- Fullscreen capable iframes
- Hidden iframe sources
- Quick close button
- Full permissions enabled
- Terminal header integration

## 🎯 All Custom Commands

### nvg-iframe (NEW in v2.2)
```bash
# Launch fullscreen services
$\:nvg:{ nvg-iframe { proxys_and_games://rammerhead fullscreen }
```

### nvg-git-launch
```bash
# Direct Git HTML to blob (no iframe)
$\:nvg:{ nvg-git-launch { HTML[`git://kbsigmaboy67/mc/1.8.html`] blob }
```

### nvg-fetch-html
```bash
# Fetch with target type
$\:nvg:{ nvg-fetch-html { api://jsonplaceholder/posts/1 text-popup }
```

### nvg-open-raw
```bash
# Load raw content with options
$\:nvg:{ nvg-open-raw { vercel://myapp/index.html popup }
```

## 🔌 Plugin System

### Proxys & Games (NEW)
```bash
proxys_and_games://rammerhead   # Rammerhead proxy
proxys_and_games://petezah      # Petezah proxy
proxys_and_games://nextbrowser  # NextBrowser app
proxys_and_games://macvg        # MacVG emulator
```

### Traditional Plugins
```bash
git://user/repo/path            # GitHub Pages
github://user/repo/branch/path  # GitHub Raw
vercel://subdomain/path         # Vercel
railway://projectId/path        # Railway
netlify://siteName/path         # Netlify
local://host:port/path          # Local Server
api://service/path              # APIs
```

## 📝 Common Commands

### Help & Info
```bash
$\:nvg:{ help              # Show all commands
$\:nvg:{ about             # About terminal
```

### Variables
```bash
$\:nvg:{ var name = value  # Set variable
$\:nvg:{ var list          # List all
```

### Utilities
```bash
$\:nvg:{ echo Hello        # Print text
$\:nvg:{ clear             # Clear terminal
$\:nvg:{ math 2+2          # Calculate
```

## 🔗 Quick Examples

### Launch Proxies
```bash
# Rammerhead proxy for web browsing
$\:nvg:{ nvg-iframe { proxys_and_games://rammerhead fullscreen }

# Petezah proxy for anonymous browsing
$\:nvg:{ nvg-iframe { proxys_and_games://petezah fullscreen }
```

### Launch Games/Emulators
```bash
# MacVG classic Macintosh emulator
$\:nvg:{ nvg-iframe { proxys_and_games://macvg fullscreen }

# NextBrowser application
$\:nvg:{ nvg-iframe { proxys_and_games://nextbrowser fullscreen }
```

### Custom HTML Loading
```bash
# Launch HTML from Git
$\:nvg:{ nvg-git-launch { HTML[`git://kbsigmaboy67/mc/1.8.html`] blob }

# View API response
$\:nvg:{ nvg-fetch-html { api://jsonplaceholder/posts/1 text-popup }
```

## 🔐 Security & Privacy

### Source Hiding
- iframe src attributes dynamically set
- Not visible in DevTools source inspection
- Runtime-only URL resolution
- Protected from static DOM analysis

### Service Selection
- All services are external HTTPS URLs
- No local data storage (except variables)
- Browser security policies enforced
- Clear iframe on close

## 🌐 GitHub Pages Deployment

All files work perfectly on GitHub Pages:

1. Create repository
2. Add HTML files
3. Create index.html to link to terminal_advanced.html
4. Enable GitHub Pages
5. Access at `https://username.github.io/repo/terminal_advanced.html`

### Example index.html
```html
<!DOCTYPE html>
<html>
<head>
    <title>NVG Terminal</title>
</head>
<body style="font-family: monospace; background: #0a0e27; color: #00ff88; text-align: center; padding: 50px;">
    <h1>🚀 NVG Terminal v2.2</h1>
    <p><a href="terminal_advanced.html">Launch Terminal</a></p>
</body>
</html>
```

## 📊 Version Comparison

| Feature | v1.0 | v2.1 | v2.2 |
|---------|------|------|------|
| Basic Commands | ✓ | ✓ | ✓ |
| Variable System | ✓ | ✓ | ✓ |
| Plugin System | ✓ | ✓ | ✓ |
| Custom Commands | ✗ | ✓ | ✓ |
| Blob/Popup Windows | ✗ | ✓ | ✓ |
| Fullscreen iframe | ✗ | ✗ | ✓ |
| Proxys & Games | ✗ | ✗ | ✓ |
| Hidden Sources | ✗ | ✗ | ✓ |

## 🎮 Services in v2.2

### Rammerhead
- Advanced web proxy
- Anonymous browsing
- https://efly.108-181-32-77.sslip.io

### Petezah
- Lightweight proxy
- Fast web access
- https://tubmledxeni.viar3d.com

### NextBrowser
- Modern browser app
- Web technologies based
- https://92850.vercel.app

### MacVG
- Classic Mac emulator
- System 7 software
- Games and applications
- https://kbsigmaboy67.github.io/macvg/

## 🔧 Browser Compatibility

| Browser | Support | Notes |
|---------|---------|-------|
| Chrome | ✓ Full | Best experience |
| Firefox | ✓ Full | Fully supported |
| Safari | ✓ Full | May have popup limits |
| Edge | ✓ Full | Chromium-based |

## 💡 Pro Tips

1. **Multiple Services** - Use different windows/tabs for each service
2. **Quick Switching** - Close with button and open different service
3. **Terminal + App** - Keep terminal minimized, app fullscreen
4. **API Testing** - Check APIs while using proxies
5. **Mixed Usage** - Combine custom commands with fullscreen apps

## 🆘 Troubleshooting

### Popups Not Opening
- Check browser popup blocker settings
- Allow popups for this site
- Try Ctrl+Shift+Delete to clear cache

### Services Not Loading
- Check internet connection
- Try different service
- Check browser console for errors
- Ensure HTTPS in address bar

### Hidden Sources Not Working
- JavaScript must be enabled
- Browser console should show no errors
- Try different browser if issues persist

## 📚 Documentation Files

### TERMINAL_GUIDE.md
- v1.0 complete feature guide
- Variable system detailed
- Window operations
- Plugin system (7 providers)

### ADVANCED_GUIDE.md
- JavaScript window.open() API
- Complete plugin documentation
- Workflow examples
- Advanced usage patterns

### CUSTOM_COMMANDS_GUIDE.md
- Custom command syntax
- nvg-git-launch detailed
- nvg-fetch-html guide
- nvg-open-raw examples

### PROXYS_GAMES_GUIDE.md
- nvg-iframe command
- Proxys & Games services
- Security & privacy
- Practical workflows

## 🚀 Getting Started

### Immediate Next Steps
1. Extract zip file
2. Open `terminal_advanced.html`
3. Type `help`
4. Try: `$\:nvg:{ nvg-iframe { proxys_and_games://macvg fullscreen }`
5. Close and explore other commands

### Explore Gradually
- Day 1: Try basic commands (echo, var, help)
- Day 2: Try proxies and emulators
- Day 3: Try custom HTML commands
- Day 4: Create your own workflows

## 📞 Support

For issues:
1. Read relevant documentation file
2. Check command syntax carefully
3. Check browser console for errors
4. Verify URLs and connectivity
5. Try clearing cache/cookies

## 📄 License

Open source. Use and modify freely for personal and commercial projects.

---

**Version**: 2.2  
**Latest Release**: February 2026  
**Terminal Editions**: 2 (v1.0, v2.2)  
**Total Commands**: 20+  
**Plugins Supported**: 11  
**Custom Commands**: 4  
**Fullscreen Services**: 4  
**Lines of Code**: 1500+  

Enjoy your NVG Terminal! 🎮🚀
