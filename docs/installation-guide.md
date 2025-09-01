# Installation Guide

> Step-by-step instructions for installing and configuring the Logient-Nventive Shared Prompt Bank system.

## 🎯 Overview

This guide covers everything you need to get started with the Logient-Nventive Shared Prompt Bank, from initial setup to advanced configuration options.

## 📋 Prerequisites

Before installing, ensure you have:

### Required Software

- **VS Code**: Version 1.70.0 or higher
- **Git**: For repository access and version control
- **Node.js**: Version 16+ (only if building from source)

### Access Requirements

- **GitHub Account**: With access to the `prompts-logient-nventive` repository
- **Repository Permissions**: Read access to the prompt repository
- **Network Access**: Internet connection for syncing prompts

### System Requirements

- **Operating System**: macOS, Windows 10+, or Linux
- **Disk Space**: ~50MB for extension and prompts
- **Memory**: Minimal impact on VS Code performance

## 🚀 Quick Installation

### Option 1: Install Pre-built Extension (Recommended)

1. **Download the Extension**

   - Navigate to the `tools/vscode-extension/` directory in the repository
   - Download the latest `prompts-sync-extension-{version}.vsix` file

2. **Install in VS Code**

   ```
   1. Open VS Code
   2. Press Ctrl+Shift+P (Cmd+Shift+P on macOS)
   3. Type "Extensions: Install from VSIX"
   4. Select the downloaded .vsix file
   5. Click "Install"
   6. Restart VS Code when prompted
   ```

3. **Verify Installation**
   - Look for "Prompts Sync" in the Extensions panel
   - Check for a sync status indicator in the status bar
   - Open Settings and search for "Prompts Sync" to see configuration options

### Option 2: Build and Install from Source

1. **Clone the Repository**

   ```bash
   git clone https://github.com/MounirAbdousNventive/prompts-logient-nventive.git
   cd prompts-logient-nventive/tools/vscode-extension
   ```

2. **Install Dependencies**

   ```bash
   npm install
   ```

3. **Build the Extension**

   ```bash
   npm run compile
   npm run package
   ```

4. **Install the Built Extension**
   ```bash
   code --install-extension prompts-sync-extension-*.vsix
   ```

## ⚙️ Initial Configuration

### Automatic Setup (Default)

The extension works out-of-the-box with these default settings:

- **Repository**: `https://github.com/MounirAbdousNventive/prompts-logient-nventive`
- **Branch**: `master`
- **Sync Frequency**: Daily
- **Sync on Startup**: Enabled
- **Notifications**: Enabled

### Manual Configuration

If you need to customize settings:

1. **Open VS Code Settings**

   ```
   File > Preferences > Settings (Ctrl+,)
   Or: Cmd+, on macOS
   ```

2. **Search for "Prompts Sync"**

3. **Configure Options** (see [Configuration Reference](#configuration-reference) below)

### GitHub Authentication Setup

The extension uses VS Code's built-in GitHub authentication:

1. **Sign in to GitHub in VS Code**

   ```
   1. Press Ctrl+Shift+P (Cmd+Shift+P)
   2. Type "GitHub: Sign In"
   3. Follow the authentication flow
   4. Grant necessary permissions
   ```

2. **Verify Repository Access**
   - The extension will automatically test repository access on first sync
   - Check the Output panel for any authentication errors

## 📁 Understanding Prompt Locations

### Default Prompt Directories

The extension automatically detects your OS-specific prompts directory:

**macOS:**

```
~/Library/Application Support/Code/User/prompts/
```

**Windows:**

```
%APPDATA%\Code\User\prompts\
```

**Linux:**

```
~/.config/Code/User/prompts/
```

### Directory Structure After Sync

Once synced, your prompts directory will contain:

```
prompts/
├── instructions/          # Global coding guidelines
│   ├── general/
│   ├── frameworks/
│   └── languages/
├── prompt/               # Task-specific prompts
│   ├── development/
│   ├── testing/
│   └── documentation/
└── chatmode/            # Custom chat behaviors
    ├── development/
    ├── architecture/
    └── debugging/
```

### Custom Prompt Directory

To use a custom location:

1. **Open Extension Settings**
2. **Find "Custom Path" setting**
3. **Enter your preferred absolute path**
   ```
   Example: /Users/yourname/custom-prompts
   ```
4. **Save and restart VS Code**

## 🔧 Configuration Reference

### Core Settings

| Setting                         | Type    | Default   | Description                              |
| ------------------------------- | ------- | --------- | ---------------------------------------- |
| `promptsSync.enabled`           | boolean | `true`    | Enable/disable automatic synchronization |
| `promptsSync.frequency`         | string  | `"daily"` | How often to sync prompts                |
| `promptsSync.syncOnStartup`     | boolean | `true`    | Sync when VS Code starts                 |
| `promptsSync.showNotifications` | boolean | `true`    | Show sync status notifications           |

### Advanced Settings

| Setting                  | Type    | Default        | Description                    |
| ------------------------ | ------- | -------------- | ------------------------------ |
| `promptsSync.customPath` | string  | `""`           | Custom prompts directory path  |
| `promptsSync.repository` | string  | Repository URL | Source repository for prompts  |
| `promptsSync.branch`     | string  | `"master"`     | Repository branch to sync from |
| `promptsSync.debug`      | boolean | `false`        | Enable detailed logging        |

### Sync Frequency Options

- **`"startup"`**: Only sync when VS Code starts
- **`"hourly"`**: Sync every hour while VS Code is running
- **`"daily"`**: Sync once per day (recommended for most users)
- **`"weekly"`**: Sync once per week
- **`"manual"`**: Only sync when manually triggered

### JSON Configuration

You can also configure via VS Code's `settings.json`:

```json
{
  "promptsSync.enabled": true,
  "promptsSync.frequency": "daily",
  "promptsSync.syncOnStartup": true,
  "promptsSync.showNotifications": true,
  "promptsSync.customPath": "",
  "promptsSync.repository": "https://github.com/MounirAbdousNventive/prompts-logient-nventive",
  "promptsSync.branch": "master",
  "promptsSync.debug": false
}
```

## 🔍 Verification and Testing

### Verify Installation Success

1. **Check Extension Status**

   ```
   1. Open Extensions panel (Ctrl+Shift+X)
   2. Search for "Prompts Sync"
   3. Verify it shows as "Enabled"
   ```

2. **Check Status Bar**

   - Look for sync status indicator in bottom status bar
   - Should show checkmark (✅) if sync is successful
   - Hover to see last sync time

3. **Check Prompts Directory**

   ```bash
   # macOS/Linux
   ls -la ~/Library/Application\ Support/Code/User/prompts/

   # Windows (PowerShell)
   ls $env:APPDATA\Code\User\prompts\
   ```

### Test Manual Sync

1. **Trigger Manual Sync**

   ```
   1. Press Ctrl+Shift+P (Cmd+Shift+P)
   2. Type "Prompts Sync: Sync Now"
   3. Press Enter
   ```

2. **Monitor Sync Progress**
   - Watch status bar for progress indicator
   - Check for completion notification
   - Review any error messages

### Test Prompt Functionality

1. **Open a Code File**
2. **Start GitHub Copilot Chat**
3. **Verify Prompts Available**
   - Instructions should automatically apply
   - Prompts should be available in prompt picker
   - Chat modes should be selectable

## 🛠️ Advanced Installation Options

### Enterprise Deployment

For enterprise-wide deployment:

1. **Package the Extension**

   ```bash
   cd tools/vscode-extension
   npm run package
   ```

2. **Distribute via Group Policy or Management Tool**

   ```bash
   code --install-extension prompts-sync-extension-{version}.vsix
   ```

3. **Pre-configure Settings**
   ```json
   // Default settings.json for all users
   {
     "promptsSync.enabled": true,
     "promptsSync.frequency": "daily",
     "promptsSync.repository": "https://your-internal-repo.com/prompts"
   }
   ```

### Custom Repository Setup

To use a different repository:

1. **Fork or Clone the Original**

   ```bash
   git clone https://github.com/MounirAbdousNventive/prompts-logient-nventive.git
   cd prompts-logient-nventive

   # Add your remote
   git remote add origin https://your-company.com/your-prompts-repo.git
   git push -u origin master
   ```

2. **Update Extension Settings**
   ```json
   {
     "promptsSync.repository": "https://your-company.com/your-prompts-repo.git",
     "promptsSync.branch": "main"
   }
   ```

### Development Environment Setup

For contributors and developers:

1. **Clone Repository**

   ```bash
   git clone https://github.com/MounirAbdousNventive/prompts-logient-nventive.git
   cd prompts-logient-nventive
   ```

2. **Install Development Dependencies**

   ```bash
   cd tools/vscode-extension
   npm install
   npm install -g @vscode/vsce  # For packaging
   ```

3. **Development Commands**

   ```bash
   npm run compile     # Build TypeScript
   npm run watch      # Watch mode for development
   npm run lint       # Code linting
   npm run test       # Run tests
   npm run package    # Create VSIX package
   ```

4. **Debug in VS Code**
   ```
   1. Open the extension folder in VS Code
   2. Press F5 to start debugging
   3. This opens a new Extension Development Host window
   4. Test your changes in the development window
   ```

## 🚨 Troubleshooting Installation

### Common Installation Issues

#### Extension Installation Fails

**Problem**: "Failed to install extension" error

**Solutions**:

1. **Check VS Code Version**

   ```
   Help > About
   Ensure version is 1.70.0 or higher
   ```

2. **Verify File Integrity**

   ```bash
   # Check VSIX file isn't corrupted
   file prompts-sync-extension-*.vsix
   ```

3. **Install via Command Line**

   ```bash
   code --install-extension path/to/extension.vsix --force
   ```

4. **Clear Extension Cache**
   ```bash
   # Remove extension cache and reinstall
   rm -rf ~/.vscode/extensions/logient-nventive.prompts-sync-extension-*
   ```

#### GitHub Authentication Issues

**Problem**: "Authentication failed" or "Repository access denied"

**Solutions**:

1. **Re-authenticate with GitHub**

   ```
   1. Command Palette: "GitHub: Sign Out"
   2. Command Palette: "GitHub: Sign In"
   3. Complete authentication flow
   ```

2. **Check Repository Permissions**

   - Verify you have read access to the repository
   - Contact your admin if access is denied

3. **Clear Authentication Cache**
   ```
   1. Command Palette: "Developer: Reload Window"
   2. Try authentication again
   ```

#### Sync Directory Issues

**Problem**: "Cannot create prompts directory" or "Permission denied"

**Solutions**:

1. **Check Directory Permissions**

   ```bash
   # macOS/Linux
   ls -la ~/Library/Application\ Support/Code/User/

   # Windows
   icacls %APPDATA%\Code\User
   ```

2. **Create Directory Manually**

   ```bash
   # macOS
   mkdir -p ~/Library/Application\ Support/Code/User/prompts

   # Linux
   mkdir -p ~/.config/Code/User/prompts

   # Windows (PowerShell)
   New-Item -ItemType Directory -Path "$env:APPDATA\Code\User\prompts" -Force
   ```

3. **Use Custom Directory**
   - Set `promptsSync.customPath` to a directory you have write access to

### Network and Connectivity Issues

#### Sync Fails with Network Error

**Problem**: "Network error" or "Connection timeout"

**Solutions**:

1. **Check Internet Connection**
2. **Verify Repository URL**
   ```bash
   git ls-remote https://github.com/MounirAbdousNventive/prompts-logient-nventive.git
   ```
3. **Check Corporate Firewall**
   - Ensure GitHub.com is accessible
   - Verify HTTPS traffic is allowed
4. **Try Manual Sync**
   - Use "Prompts Sync: Sync Now" command for detailed error information

### Performance Issues

#### Extension Slows Down VS Code

**Problem**: VS Code becomes slow after installing extension

**Solutions**:

1. **Adjust Sync Frequency**

   ```json
   {
     "promptsSync.frequency": "weekly"
   }
   ```

2. **Disable Sync on Startup**

   ```json
   {
     "promptsSync.syncOnStartup": false
   }
   ```

3. **Enable Debug Mode**
   ```json
   {
     "promptsSync.debug": true
   }
   ```
   Check Output panel for performance bottlenecks

## 📊 Post-Installation Validation

### Validation Checklist

- [ ] Extension appears in Extensions panel as "Enabled"
- [ ] Status bar shows sync indicator
- [ ] GitHub authentication is working
- [ ] Prompts directory exists and contains files
- [ ] Manual sync completes successfully
- [ ] Prompts are available in GitHub Copilot
- [ ] No error messages in Output panel
- [ ] Extension settings are configurable

### Performance Validation

- [ ] VS Code startup time is not significantly impacted
- [ ] Sync operations complete within reasonable time (< 30 seconds)
- [ ] No memory leaks or excessive resource usage
- [ ] Extension works properly after VS Code restart

### Integration Validation

- [ ] Instructions apply to code files as expected
- [ ] Prompts are accessible through prompt picker
- [ ] Chat modes function correctly
- [ ] No conflicts with other extensions
- [ ] Proper cleanup when extension is disabled

## 🔗 Next Steps

After successful installation:

1. **Read the [Usage Guide](usage-guide.md)** to learn how to use prompts effectively
2. **Review [Best Practices](best-practices.md)** for writing and using prompts
3. **Check out the [Contribution Guide](contribution-guide.md)** if you want to add your own prompts
4. **Explore the [Technical Architecture](technical-architecture.md)** for advanced customization

## 📞 Installation Support

If you encounter issues not covered in this guide:

1. **Check the [Troubleshooting section](#-troubleshooting-installation) above**
2. **Search existing [GitHub Issues](https://github.com/MounirAbdousNventive/prompts-logient-nventive/issues)**
3. **Create a new issue** with:
   - Your operating system and version
   - VS Code version
   - Extension version
   - Detailed error messages
   - Steps to reproduce the problem
4. **Contact your DevOps team** for urgent installation issues

---

**Welcome to the Logient-Nventive Shared Prompt Bank! Your installation is complete and you're ready to enhance your coding productivity with shared prompts.**
