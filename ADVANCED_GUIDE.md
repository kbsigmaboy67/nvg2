# NVG Terminal v2.0 - Advanced Documentation

## Overview
A powerful terminal interface with full JavaScript `window.open()` API compatibility and a comprehensive plugin system for seamless integration with multiple platforms.

---

## 🪟 Window API (JavaScript Compatible)

### Basic Window.open() Syntax
```bash
# Simple open (like window.open)
$\:nvg:{ open https://example.com

# With name
$\:nvg:{ open https://example.com myWindow

# With name and specs
$\:nvg:{ open https://example.com myWindow width=1024,height=768
```

### Window Specifications
Supported window specs (comma-separated):
- `width=800` - Window width in pixels
- `height=600` - Window height in pixels
- `left=100` - Position from left
- `top=100` - Position from top
- `resizable=1` - Allow resizing (1 or 0)
- `fullscreen=1` - Enable fullscreen button
- `scrollbars=1` - Show scrollbars
- `toolbar=1` - Show toolbar
- `menubar=1` - Show menu bar

### Examples
```bash
# Standard size window
$\:nvg:{ open https://example.com newWin width=1024,height=768

# Fullscreen-capable window
$\:nvg:{ open https://example.com fullWin width=1280,height=960,fullscreen=1

# Named window (reuses if opened again)
$\:nvg:{ open https://google.com search width=800,height=600

# Minimal popup
$\:nvg:{ open https://example.com mini width=400,height=300
```

### Window Control Commands

```bash
# List all open windows
$\:nvg:{ windows list

# Focus/bring window to front
$\:nvg:{ focus nvg_window_0

# Minimize window
$\:nvg:{ minimize nvg_window_1

# Maximize/fullscreen
$\:nvg:{ maximize nvg_window_1

# Restore to original size
$\:nvg:{ restore nvg_window_1

# Close specific window
$\:nvg:{ close nvg_window_0
```

---

## 🔌 Plugin System (10+ Providers)

### 1. GitHub Pages
```bash
# Format: git://user/repo/path
$\:nvg:{ open git://octocat/Hello-World/index.html

# In a window with specs
$\:nvg:{ open git://username/myrepo/page.html myApp width=1024,height=768

# Variable reference
$\:nvg:{ var gh_page = git://octocat/Hello-World/index.html
$\:nvg:{ open $gh_page
```

### 2. GitHub Raw Content
```bash
# Format: github://user/repo/branch/path
$\:nvg:{ open github://torvalds/linux/master/README.md

# Fetch without opening
$\:nvg:{ get github://nodejs/node/main/README.md
```

### 3. Vercel
```bash
# Format: vercel://subdomain/path
$\:nvg:{ open vercel://my-app/dashboard

# With window specs
$\:nvg:{ open vercel://nextjs-app/api/status myDash width=1024,height=768
```

### 4. Railway
```bash
# Format: railway://projectId/path
$\:nvg:{ open railway://my-project-123/api/health
```

### 5. Bolt
```bash
# Format: bolt://projectId/path
$\:nvg:{ open bolt://my-bolt-app/editor
```

### 6. Netlify
```bash
# Format: netlify://siteName/path
$\:nvg:{ open netlify://my-site/admin
```

### 7. Heroku
```bash
# Format: heroku://appName/path
$\:nvg:{ open heroku://my-app-12345/dashboard
```

### 8. Local Server
```bash
# Format: local://host:port/path
$\:nvg:{ open local://localhost:3000/dashboard

$\:nvg:{ open local://localhost:8080/api/users

# With window specs
$\:nvg:{ open local://127.0.0.1:5000/admin admin width=1200,height=800
```

### 9. CDN
```bash
# Format: cdn://provider/path
# Providers: jsdelivr, unpkg, cdnjs, skypack

$\:nvg:{ open cdn://jsdelivr/npm/lodash@4.17.21/lodash.min.js

$\:nvg:{ open cdn://unpkg/react@18/umd/react.production.min.js

$\:nvg:{ open cdn://cdnjs/ajax/libs/jquery/3.6.0/jquery.min.js

$\:nvg:{ open cdn://skypack/lodash@4
```

### 10. API Gateway
```bash
# Format: api://service/path
# Services: jsonplaceholder, pokeapi, restcountries, weather

# JSONPlaceholder
$\:nvg:{ open api://jsonplaceholder/posts/1

# PokéAPI
$\:nvg:{ open api://pokeapi/pokemon/pikachu

# REST Countries
$\:nvg:{ open api://restcountries/all

# OpenMeteo Weather
$\:nvg:{ open api://weather/forecast
```

### Fetching with Plugins
```bash
# Get content and display in terminal
$\:nvg:{ get git://user/repo/file.json

$\:nvg:{ get api://jsonplaceholder/posts/1

$\:nvg:{ get github://nodejs/node/main/README.md
```

---

## 🪟 Custom Window Types

### Popup Window
```bash
$\:nvg:{ open window popup

$\:nvg:{ open window popup This is a popup message

$\:nvg:{ var msg = Important notification
$\:nvg:{ open window popup $msg
```

### HTML Window
```bash
$\:nvg:{ open window html <h1>Hello World</h1>

$\:nvg:{ open window html <html><body><h1>Custom Page</h1></body></html>

# Complex HTML
$\:nvg:{ var myPage = <html><head><style>body{background:#000;color:#0f0}</style></head><body><h1>Matrix Mode</h1></body></html>
$\:nvg:{ open window html $myPage
```

### Blob Window
```bash
$\:nvg:{ open window blob Some data content

$\:nvg:{ var data = {"name":"John","age":30}
$\:nvg:{ open window blob $data
```

### Text Window
```bash
$\:nvg:{ open window text My text content

$\:nvg:{ open window text Line 1 / Line 2 / Line 3
```

### Iframe Window
```bash
$\:nvg:{ open window iframe https://example.com

$\:nvg:{ open window iframe local://localhost:3000/dashboard
```

---

## 📦 Variables System

### Setting Variables
```bash
# Simple variable
$\:nvg:{ var username = john

# URL variable
$\:nvg:{ var api = https://api.example.com/v1

# Plugin URL variable
$\:nvg:{ var myapp = vercel://my-app/dashboard

# Long content
$\:nvg:{ var description = This is a long description that spans multiple words

# HTML content
$\:nvg:{ var template = <div><h1>Hello</h1><p>Welcome</p></div>
```

### Using Variables
```bash
# Reference with $
$\:nvg:{ open $myapp

$\:nvg:{ fetch $api/users

# In custom windows
$\:nvg:{ open window html $template

# In plugins
$\:nvg:{ var endpoint = api://jsonplaceholder/posts/1
$\:nvg:{ open $endpoint
```

### Managing Variables
```bash
# List all variables
$\:nvg:{ var list

# Get single variable
$\:nvg:{ var username

# Update variable
$\:nvg:{ var username = jane

# Delete variable
$\:nvg:{ var delete username

# Clear all variables
$\:nvg:{ var clear
```

---

## 💻 Utility Commands

### Math Operations
```bash
$\:nvg:{ math 2+2

$\:nvg:{ math 100*5-25

$\:nvg:{ math Math.pow(2,8)

$\:nvg:{ math Math.sqrt(16)

$\:nvg:{ math (50+30)/2
```

### Base64 Encoding
```bash
# Encode
$\:nvg:{ base64 encode Hello World

$\:nvg:{ base64 encode my-secret-key

# Decode
$\:nvg:{ base64 decode SGVsbG8gV29ybGQ=
```

### Random Numbers
```bash
# Random 0-1
$\:nvg:{ random

# Random in range
$\:nvg:{ random 1 100

$\:nvg:{ random 1 1000000
```

### System Information
```bash
# Current time
$\:nvg:{ time

# Full date/time
$\:nvg:{ date

# Current user/connection info
$\:nvg:{ whoami

# Connection details
$\:nvg:{ ip
```

### Fetch Operations
```bash
# Direct HTTP fetch
$\:nvg:{ fetch https://api.github.com/users/octocat

# Fetch with plugin resolution
$\:nvg:{ get api://jsonplaceholder/posts/1

$\:nvg:{ get git://user/repo/data.json
```

### Terminal Operations
```bash
# Print text
$\:nvg:{ echo Hello from terminal

# Clear terminal
$\:nvg:{ clear

# Show help
$\:nvg:{ help

# Show about
$\:nvg:{ about

# List plugins
$\:nvg:{ plugins
```

---

## 🎯 Practical Workflows

### Workflow 1: Multi-Window Dashboard
```bash
# Set up your workspace
$\:nvg:{ var api_server = local://localhost:3000

# Open multiple windows
$\:nvg:{ open $api_server/dashboard dashboard width=1024,height=768

$\:nvg:{ open $api_server/users users width=800,height=600

$\:nvg:{ open $api_server/analytics analytics width=900,height=700

# Manage windows
$\:nvg:{ windows list

$\:nvg:{ focus nvg_dashboard_0

$\:nvg:{ maximize nvg_dashboard_0
```

### Workflow 2: API Testing
```bash
# Set API endpoint
$\:nvg:{ var api = api://jsonplaceholder

# Open different endpoints in windows
$\:nvg:{ open $api/posts/1 post1 width=600,height=400

$\:nvg:{ open $api/users/1 user1 width=600,height=400

$\:nvg:{ open $api/comments/1 comment1 width=600,height=400

# Fetch specific data
$\:nvg:{ fetch https://jsonplaceholder.typicode.com/posts/1
```

### Workflow 3: Development Environment
```bash
# Local dev server
$\:nvg:{ var dev = local://localhost:3000

# Frontend
$\:nvg:{ open $dev frontend width=1024,height=768

# Backend API
$\:nvg:{ open local://localhost:8000/api backend width=800,height=600

# Database viewer
$\:nvg:{ open local://localhost:4000/admin admin width=600,height=500

# Monitor all
$\:nvg:{ windows list
```

### Workflow 4: Multi-Provider Testing
```bash
# Test across platforms
$\:nvg:{ open git://octocat/Hello-World/index.html gh

$\:nvg:{ open vercel://my-app/home vercel

$\:nvg:{ open netlify://my-site/admin netlify

$\:nvg:{ open railway://my-app/status railway

# Compare windows side by side
$\:nvg:{ windows list
```

### Workflow 5: Custom Dashboard
```bash
# Create custom HTML dashboard
$\:nvg:{ var dashboard = <html><head><style>body{background:#0a0e27;color:#00ff88;font-family:monospace;padding:20px}h1{text-shadow:0 0 10px #00ff88}</style></head><body><h1>📊 Dashboard</h1><p>Welcome to your workspace</p></body></html>

# Display it
$\:nvg:{ open window html $dashboard
```

---

## ⌨️ Quick Reference

### Command Syntax
```
$\:nvg:{ <command> [args...]
```

### Window Operations
| Command | Purpose |
|---------|---------|
| `open <url> [name] [specs]` | Open URL in window |
| `open window <type> [data]` | Create custom window |
| `close <id>` | Close window |
| `focus <id>` | Focus window |
| `minimize <id>` | Minimize |
| `maximize <id>` | Maximize |
| `restore <id>` | Restore |
| `windows list` | List all windows |

### Plugins Available
| Protocol | Format | Example |
|----------|--------|---------|
| GitHub Pages | `git://user/repo/path` | `git://octocat/Hello-World/index.html` |
| GitHub Raw | `github://user/repo/branch/path` | `github://nodejs/node/main/README.md` |
| Vercel | `vercel://subdomain/path` | `vercel://my-app/api/status` |
| Railway | `railway://projectId/path` | `railway://my-app-123/health` |
| Bolt | `bolt://projectId/path` | `bolt://my-app/editor` |
| Netlify | `netlify://siteName/path` | `netlify://my-site/admin` |
| Heroku | `heroku://appName/path` | `heroku://my-app/dashboard` |
| Local | `local://host:port/path` | `local://localhost:3000/api` |
| CDN | `cdn://provider/path` | `cdn://unpkg/react@18/umd/react.js` |
| API | `api://service/path` | `api://jsonplaceholder/posts/1` |

---

## 🚀 Advanced Tips

1. **Window Reuse** - Using same window name will reuse/focus that window
2. **Variable Chaining** - Store URLs, paths, and data in variables for reuse
3. **Plugin Flexibility** - Mix plugins with direct URLs
4. **Window Management** - Use `windows list` to track all open windows
5. **Specs Combination** - Combine multiple specs for custom layout
6. **API Testing** - Use api:// plugin for quick API endpoint testing
7. **Local Development** - Use local:// to test local servers

---

## 🔧 Browser Compatibility

- Chrome/Chromium: Full support
- Firefox: Full support
- Safari: Full support (some popup restrictions)
- Edge: Full support

Note: Some browsers may restrict popup windows. Allow popups in settings if windows don't open.

---

## 📝 Example Scripts

### Multi-Window Monitoring
```bash
$\:nvg:{ var app = local://localhost:3000
$\:nvg:{ open $app/metrics metrics width=1024,height=768
$\:nvg:{ open $app/logs logs width=800,height=600
$\:nvg:{ open $app/health health width=600,height=400
```

### Cross-Platform Comparison
```bash
$\:nvg:{ open git://user/repo/page
$\:nvg:{ open vercel://same-app/page
$\:nvg:{ open netlify://same-app/page
```

### Content Viewing
```bash
$\:nvg:{ get github://user/repo/branch/README.md
$\:nvg:{ fetch https://raw.githubusercontent.com/user/repo/main/file.json
$\:nvg:{ open window html <h1>Readme</h1>
```

---

Generated for NVG Terminal v2.0 - Advanced Window API Edition
