# NVG Terminal v2.1 - Custom Command Syntax Guide



## 🚀 Custom Command 1: `nvg-git-launch`

### Purpose
Fetch HTML directly from a Git URL and launch it in a blob or popup window without using iframe.

### Syntax
```
nvg-git-launch { HTML[`<plugin-url>`] <target1>, <target2>, ... }
```

### Parameters
- `<plugin-url>` - Any supported plugin URL (git://, github://, vercel://, etc.)
- `<target>` - Where to launch: `blob` or `popup` (defaults to popup if only one specified)

### Examples

#### Basic Git HTML to Blob
```bash
$\:nvg:{ nvg-git-launch { HTML[`git://kbsigmaboy67/mc/1.8.html`] blob }
```
Result: Fetches HTML from GitHub Pages and opens in a blob window (no iframe)

#### GitHub Pages Example
```bash
$\:nvg:{ nvg-git-launch { HTML[`git://octocat/Hello-World/index.html`] blob }
```

#### With Multiple Targets
```bash
$\:nvg:{ nvg-git-launch { HTML[`git://username/repo/page.html`] blob, popup }
```
First target takes precedence: opens in blob

#### GitHub Raw Content
```bash
$\:nvg:{ nvg-git-launch { HTML[`github://username/repo/main/index.html`] popup }
```

#### With Vercel URL
```bash
$\:nvg:{ nvg-git-launch { HTML[`vercel://myapp/file.html`] blob }
```

#### With Local Server
```bash
$\:nvg:{ nvg-git-launch { HTML[`local://localhost:3000/index.html`] popup }
```

### How It Works
1. Parses the plugin URL using pattern matching
2. Resolves plugin URL to actual HTTP/HTTPS URL
3. Fetches HTML content from the resolved URL
4. Creates a Blob from the HTML content
5. Opens blob URL in new window (if blob) or writes directly to document (if popup)

### Key Advantages
- ✓ No iframe needed - direct HTML execution
- ✓ Supports all plugins
- ✓ CORS-friendly blob approach
- ✓ Full HTML rendering without restrictions
- ✓ Direct DOM access (if popup)

---

## 🎯 Custom Command 2: `nvg-fetch-html`

### Purpose
Fetch content from any URL and open it with specific handling (HTML vs text, blob vs popup).

### Syntax
```
nvg-fetch-html { <url> <target-type> }
```

### Target Types
- `html-blob` - Fetch and open HTML in blob window
- `html-popup` - Fetch and open HTML in popup (direct write)
- `text-blob` - Fetch as text (preformatted) in blob
- `text-popup` - Fetch as text (preformatted) in popup

### Examples

#### HTML to Blob
```bash
$\:nvg:{ nvg-fetch-html { git://user/repo/index.html html-blob }
```

#### HTML to Popup
```bash
$\:nvg:{ nvg-fetch-html { github://user/repo/main/file.html html-popup }
```

#### Text File to Blob
```bash
$\:nvg:{ nvg-fetch-html { github://user/repo/main/README.md text-blob }
```

#### API Response as Text
```bash
$\:nvg:{ nvg-fetch-html { api://jsonplaceholder/posts/1 text-popup }
```

#### With Vercel
```bash
$\:nvg:{ nvg-fetch-html { vercel://myapp/api/data.json text-blob }
```

### How It Works
1. Parses the URL and target type
2. Resolves plugin URLs if needed
3. Fetches content from the URL
4. If HTML target: writes directly or creates blob
5. If text target: wraps in `<pre><code>` formatting

---

## 📦 Custom Command 3: `nvg-open-raw`

### Purpose
Load raw content with flexible options for display format and features.

### Syntax
```
nvg-open-raw { <url> <option1>, <option2>, ... }
```

### Options
- `blob` - Open in blob window (default)
- `popup` - Open in popup window
- `fullscreen` - Enable fullscreen mode
- `iframe` - Use iframe (if supported)

### Examples

#### Basic Blob Load
```bash
$\:nvg:{ nvg-open-raw { git://user/repo/page.html blob }
```

#### Popup Window
```bash
$\:nvg:{ nvg-open-raw { api://jsonplaceholder/posts popup }
```

#### Fullscreen Blob
```bash
$\:nvg:{ nvg-open-raw { local://localhost:3000/dashboard blob, fullscreen }
```

#### Multiple Options
```bash
$\:nvg:{ nvg-open-raw { vercel://app/page.html blob, fullscreen }
```

#### GitHub Raw
```bash
$\:nvg:{ nvg-open-raw { github://user/repo/main/index.html popup }
```

### How It Works
1. Parses options from comma-separated list
2. Resolves plugin URLs
3. Fetches content
4. Creates blob or popup based on options
5. Applies fullscreen if specified

---

## 🔌 Compatible Plugins

All custom commands work with these plugins:

### Git Providers
```bash
git://user/repo/path           # GitHub Pages
github://user/repo/branch/path # GitHub Raw Content
```

### Deployment Platforms
```bash
vercel://subdomain/path        # Vercel
railway://projectId/path       # Railway
netlify://siteName/path        # Netlify
```

### Local Development
```bash
local://host:port/path         # Local Server
```

### APIs
```bash
api://service/path             # API endpoints
```

---

## 📝 Variable Integration

### Using Variables with Custom Commands

```bash
# Store a URL in a variable
$\:nvg:{ var myPage = git://kbsigmaboy67/mc/1.8.html

# Use in custom command (with backticks)
$\:nvg:{ nvg-git-launch { HTML[`git://kbsigmaboy67/mc/1.8.html`] blob }

# Or store the full command
$\:nvg:{ var gitUrl = git://user/repo/index.html
```

---

## 🎯 Practical Use Cases

### Use Case 1: Launch Web App from Git
```bash
# Store your web app URL
$\:nvg:{ var myapp = git://myusername/myapp/dist/index.html

# Launch it
$\:nvg:{ nvg-git-launch { HTML[`git://myusername/myapp/dist/index.html`] blob }
```

### Use Case 2: Quick API Response Viewer
```bash
# View API response formatted
$\:nvg:{ nvg-fetch-html { api://jsonplaceholder/posts/1 text-popup }
```

### Use Case 3: Multiple File Viewer
```bash
# View README
$\:nvg:{ nvg-fetch-html { github://nodejs/node/main/README.md text-blob }

# View package.json
$\:nvg:{ nvg-fetch-html { github://nodejs/node/main/package.json text-popup }
```

### Use Case 4: Deployment Testing
```bash
# Test Vercel deployment
$\:nvg:{ nvg-git-launch { HTML[`vercel://my-app/index.html`] blob }

# Test local dev server
$\:nvg:{ nvg-open-raw { local://localhost:3000/dashboard popup, fullscreen }
```

### Use Case 5: Dashboard Launcher
```bash
# Store dashboard URLs
$\:nvg:{ var dashboard = local://localhost:3000/admin

# Launch multiple
$\:nvg:{ nvg-open-raw { local://localhost:3000/admin blob }
$\:nvg:{ nvg-open-raw { local://localhost:3000/logs popup }
$\:nvg:{ nvg-open-raw { local://localhost:3000/metrics fullscreen }
```

---

## 🔧 Technical Details

### What Makes Custom Commands Different

1. **No iframes** - Direct HTML execution in blob/popup
2. **Plugin Resolution** - Automatic URL conversion from plugin format
3. **Direct HTML** - Raw HTML content without wrapper
4. **CORS Handling** - Blob URLs bypass some CORS restrictions
5. **Full Control** - Direct document.write access in popups

### Browser Support
- Chrome/Chromium: Full support
- Firefox: Full support
- Safari: Full support (popup restrictions apply)
- Edge: Full support

### Limitations
- Popup blockers may prevent new windows
- Some browsers restrict popup sizes
- Cross-origin restrictions still apply for iframe cases
- Large files may take time to fetch

---

## 💡 Tips & Tricks

### 1. Reliable Git HTML Launching
Always use backticks around the URL:
```bash
✓ CORRECT: nvg-git-launch { HTML[`git://user/repo/file`] blob }
✗ WRONG:   nvg-git-launch { HTML[git://user/repo/file] blob }
```

### 2. Default Behaviors
- `nvg-git-launch` - Defaults to popup if only one target
- `nvg-fetch-html` - Requires explicit target type
- `nvg-open-raw` - Defaults to blob if no target specified

### 3. Testing Deployment
Compare multiple deploys:
```bash
$\:nvg:{ nvg-git-launch { HTML[`git://user/myapp/index.html`] blob }
$\:nvg:{ nvg-open-raw { vercel://myapp-prod/index.html popup }
```

### 4. File Viewing
View any file from Git:
```bash
# HTML files
$\:nvg:{ nvg-fetch-html { github://user/repo/main/index.html html-blob }

# Config files (as text)
$\:nvg:{ nvg-fetch-html { github://user/repo/main/package.json text-popup }
```

### 5. Error Handling
If a command fails:
- Check URL format matches plugin pattern
- Ensure backticks around URLs in git-launch
- Verify file exists at that path
- Check browser console for CORS errors

---

## 📋 Command Reference Table

| Command | Use For | Syntax |
|---------|---------|--------|
| `nvg-git-launch` | Direct Git HTML to blob/popup | `{ HTML[\`url\`] blob }` |
| `nvg-fetch-html` | Fetch with specific target | `{ url html-blob }` |
| `nvg-open-raw` | Raw content with options | `{ url blob, popup }` |
| `var` | Store and retrieve variables | `var name = value` |
| `echo` | Print text | `echo text` |
| `help` | Show command help | `help` |

---

## 🚀 Example Workflow

```bash
# 1. Set up your project URLs
$\:nvg:{ var project = git://kbsigmaboy67/mc/1.8.html

# 2. Launch main app
$\:nvg:{ nvg-git-launch { HTML[`git://kbsigmaboy67/mc/1.8.html`] blob }

# 3. View API data
$\:nvg:{ nvg-fetch-html { api://jsonplaceholder/posts/1 text-popup }

# 4. Check config files
$\:nvg:{ nvg-fetch-html { github://kbsigmaboy67/mc/main/config.json text-blob }

# 5. Launch local dashboard
$\:nvg:{ nvg-open-raw { local://localhost:3000/dashboard popup, fullscreen }
```

---

Generated for NVG Terminal v2.1 - Custom Command Edition
