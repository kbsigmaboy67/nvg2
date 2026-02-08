# NVG Terminal - Complete Feature Guide

## 🎯 Overview
Advanced terminal interface with variable system, window management, and multi-platform support.

---

## 📦 Variable System (Like JavaScript/CSS)

### Basic Variable Operations
```bash
# Set a variable
$\:nvg:{ var myUrl = https://example.com
$\:nvg:{ var apiKey = sk-1234567890
$\:nvg:{ var htmlCode = <h1>Hello</h1>

# Get a variable
$\:nvg:{ var myUrl

# List all variables
$\:nvg:{ var list

# Delete a variable
$\:nvg:{ var delete myUrl

# Clear all variables
$\:nvg:{ var clear
```

### Using Variables in Commands
```bash
# Store a URL and use it later
$\:nvg:{ var site = https://google.com
$\:nvg:{ open $site

# Store HTML and create window with it
$\:nvg:{ var page = <html><body><h1>Hello</h1></body></html>
$\:nvg:{ open window html $page
```

---

## 🪟 Window Management System

### Opening Windows - Different Types

#### 1. **Popup/Blank Window**
```bash
# Basic popup (empty)
$\:nvg:{ open window popup

# Popup with text content
$\:nvg:{ open window popup Hello from terminal!

# Popup with HTML
$\:nvg:{ open window popup <h1>This is HTML</h1>
```

#### 2. **HTML Window** (Write custom HTML)
```bash
# Custom HTML document
$\:nvg:{ open window html <html><head><title>Test</title></head><body><h1>Custom Page</h1></body></html>

# Store HTML in variable first
$\:nvg:{ var myHtml = <html><body style="background:black;color:lime"><h1>Matrix Mode</h1></body></html>
$\:nvg:{ open window html $myHtml
```

#### 3. **Blob Window** (Binary Large Object)
```bash
# Create window from blob data
$\:nvg:{ open window blob Some text content here
```

#### 4. **Frame Window** (FULLSCREEN SUPPORT!) ⭐
```bash
# Open URL in fullscreen-capable frame
$\:nvg:{ open window frame https://example.com

# The frame has a fullscreen button to go fullscreen!
```

### Opening URLs Directly

```bash
# Open URL in popup window
$\:nvg:{ open https://example.com

# Open URL in frame (with fullscreen button!)
$\:nvg:{ open https://example.com frame

# Use variable as URL
$\:nvg:{ var url = https://github.com
$\:nvg:{ open $url frame
```

### Window Management

```bash
# List all open windows
$\:nvg:{ windows list

# Close specific window
$\:nvg:{ windows close win_0
$\:nvg:{ windows close url_frame_1

# Close all windows at once
$\:nvg:{ windows closeall

# Focus a specific window
$\:nvg:{ window focus win_0
```

---

## 🔧 Utility Commands

### Math Operations
```bash
$\:nvg:{ math 2+2
$\:nvg:{ math 100*5
$\:nvg:{ math (50+25)/3
$\:nvg:{ math Math.pow(2,8)
$\:nvg:{ math Math.sqrt(16)
```

### Base64 Encoding/Decoding
```bash
# Encode to base64
$\:nvg:{ base64 encode Hello World
$\:nvg:{ base64 encode your-secret-key

# Decode from base64
$\:nvg:{ base64 decode SGVsbG8gV29ybGQ=
```

### Random Numbers
```bash
# Random decimal (0-1)
$\:nvg:{ random

# Random integer in range
$\:nvg:{ random 1 100
$\:nvg:{ random 1 10
```

### System Information
```bash
# Show current time
$\:nvg:{ time

# Show current date and time
$\:nvg:{ date

# Show connection info
$\:nvg:{ ip

# Show current user
$\:nvg:{ whoami
```

---

## 🔌 Plugin System (Fetch from Multiple Platforms)

### GitHub Pages
```bash
$\:nvg:{ get git://username/repository/path/to/file.html
```

### Vercel
```bash
$\:nvg:{ get vercel://mysite/api/data
```

### Railway
```bash
$\:nvg:{ get railway://my-project-id/status
```

### Bolt
```bash
$\:nvg:{ get bolt://project-id/endpoint
```

### Netlify
```bash
$\:nvg:{ get netlify://site-name/page.html
```

### Local Server
```bash
$\:nvg:{ get local://localhost:3000/api/data
```

### Direct HTTP/HTTPS Fetch
```bash
$\:nvg:{ fetch https://api.example.com/data
```

---

## 💡 Practical Examples

### Example 1: Store and Open Custom Dashboard
```bash
$\:nvg:{ var dashboard = <html><body style="background:#0a0e27;color:#00ff88;font-family:monospace;padding:20px"><h1>📊 Dashboard</h1><p>Welcome to your dashboard!</p></body></html>

$\:nvg:{ open window html $dashboard
```

### Example 2: Store API Endpoint and Fetch
```bash
$\:nvg:{ var api = https://jsonplaceholder.typicode.com/posts/1

$\:nvg:{ fetch $api
```

### Example 3: Build HTML Page Dynamically and Display
```bash
$\:nvg:{ var pageContent = <html><head><style>body{background:black;color:lime;font-family:monospace;padding:20px}</style></head><body><h1>Generated Page</h1><p>This was created dynamically!</p></body></html>

$\:nvg:{ open window html $pageContent
```

### Example 4: Create Fullscreen Embedder
```bash
$\:nvg:{ var site = https://www.youtube.com

$\:nvg:{ open $site frame
# Then click the fullscreen button in the frame!
```

### Example 5: Random Password Generator
```bash
$\:nvg:{ random 10000000 99999999
$\:nvg:{ base64 encode password-above
```

---

## ⌨️ Command Syntax

All commands start with:
```
$\:nvg:{
```

Structure:
```
$\:nvg:{ <command> [arguments]
```

Arguments with spaces:
```bash
$\:nvg:{ var message = This is a long message
$\:nvg:{ echo This will all be printed
```

---

## 🎯 Quick Tips

1. **Variables persist** - Set once, use multiple times
2. **Frames support fullscreen** - Click the fullscreen button in the frame header
3. **Use variables for complex URLs** - Store them first, reference with `$name`
4. **Combine operations** - Store HTML in variable, then open in window
5. **Window IDs** - Check with `windows list` to see all open windows
6. **CORS limitation** - Direct fetch may be blocked by same-origin policy
7. **Plugin URLs** - Don't need http://, they convert automatically

---

## 🚀 Advanced Usage

### Multi-Step Workflow
```bash
# Step 1: Set up your workspace
$\:nvg:{ var project = my-awesome-project
$\:nvg:{ var baseUrl = https://my-awesome-project.vercel.app

# Step 2: Store custom interface
$\:nvg:{ var dashboard = <html><body style="background:#000;color:#0f0"><h2>$project Dashboard</h2></body></html>

# Step 3: Open dashboard
$\:nvg:{ open window html $dashboard

# Step 4: Open API in frame
$\:nvg:{ open $baseUrl/api frame
```

### Window Management Workflow
```bash
# Open multiple resources
$\:nvg:{ open https://example.com frame
$\:nvg:{ open https://github.com frame
$\:nvg:{ open window html <h1>Notes</h1>

# List what's open
$\:nvg:{ windows list

# Close the one you don't need
$\:nvg:{ windows close url_frame_0

# Close everything when done
$\:nvg:{ windows closeall
```

---

## 📋 All Available Commands

| Category | Command | Purpose |
|----------|---------|---------|
| **Variables** | `var <n> = <v>` | Set variable |
| | `var <n>` | Get variable |
| | `var list` | List all variables |
| | `var delete <n>` | Delete variable |
| | `var clear` | Clear all variables |
| **Windows** | `open window <type> [data]` | Create window |
| | `open <url> [frame]` | Open URL |
| | `windows list` | List windows |
| | `windows close <id>` | Close window |
| | `windows closeall` | Close all windows |
| | `window focus <id>` | Focus window |
| **Math** | `math <expr>` | Calculate expression |
| **Encoding** | `base64 encode <text>` | Encode to base64 |
| | `base64 decode <text>` | Decode from base64 |
| **Random** | `random [min max]` | Random number |
| **System** | `time` | Current time |
| | `date` | Current date/time |
| | `ip` | Connection info |
| | `whoami` | Current user |
| **Network** | `fetch <url>` | Fetch URL |
| | `get <protocol>` | Plugin fetch |
| **Utility** | `echo <text>` | Print text |
| | `clear` | Clear terminal |
| | `help` | Show help |
| | `plugins` | List plugins |

---

Generated for NVG Terminal v1.0
