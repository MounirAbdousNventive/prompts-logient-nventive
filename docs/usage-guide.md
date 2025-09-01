# Usage Guide

> Complete guide to using the Logient-Nventive Shared Prompt Bank and VS Code extension.

## 🎯 Overview

The Logient-Nventive Shared Prompt Bank provides three types of prompts to enhance your GitHub Copilot experience:

- **Instructions** (`.instructions.md`): Global coding guidelines applied to all files
- **Prompts** (`.prompt.md`): Task-specific prompts for agent mode interactions
- **Chat Modes** (`.chatmode.md`): Custom chat behaviors with specific tools and focus areas

## 🚀 Getting Started

### 1. Install the VS Code Extension

1. Download the latest `prompts-sync-extension-{version}.vsix` from the `tools/vscode-extension/` directory
2. In VS Code, open the Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P`)
3. Type "Extensions: Install from VSIX" and select it
4. Browse to the downloaded `.vsix` file and install
5. Restart VS Code when prompted

### 2. Verify Installation

After installation, you should see:

- A status bar item showing sync status (bottom of VS Code)
- Prompts automatically synced to your local prompts directory
- Extension settings available in VS Code Settings

### 3. Check Sync Status

- **Status Bar**: Look for the sync indicator in the bottom status bar
- **Manual Check**: Use `Ctrl+Shift+P` → "Prompts Sync: Show Status"
- **Force Sync**: Use `Ctrl+Shift+P` → "Prompts Sync: Sync Now"

## 📁 Understanding Prompt Types

### Instructions (`.instructions.md`)

Instructions provide global coding guidelines that apply to all files in your projects.

**Format:**

```markdown
---
applyTo: "**" # Glob pattern for file targeting
---

Your coding guidelines and instructions here.
```

**Example Use Cases:**

- Company coding standards
- Security guidelines
- Framework-specific conventions
- Architecture patterns

**How to Use:**

1. Instructions are automatically applied when you interact with Copilot
2. They influence code generation, suggestions, and responses
3. Use specific `applyTo` patterns to target certain file types

### Prompts (`.prompt.md`)

Prompts are task-specific templates for agent mode interactions.

**Format:**

```markdown
---
mode: agent # Specifies this is for agent mode
---

Define your specific task, requirements, and success criteria here.
```

**Example Use Cases:**

- Code review checklists
- Testing strategies
- Documentation generation
- Refactoring guidelines

**How to Use:**

1. Access through VS Code's prompt picker
2. Select the appropriate prompt for your task
3. Customize the prompt content as needed
4. Execute with GitHub Copilot agent mode

### Chat Modes (`.chatmode.md`)

Chat modes define custom AI behaviors with specific tools and focus areas.

**Format:**

```markdown
---
description: "Brief description of this chat mode"
tools: ["tool1", "tool2"] # Available tools for this mode
---

Define the AI behavior, response style, and interaction patterns.
```

**Example Use Cases:**

- Code review focused conversations
- Architecture planning sessions
- Debugging assistance
- Documentation writing

**How to Use:**

1. Select from available chat modes in Copilot Chat
2. The AI will adopt the specified behavior and focus
3. Use the defined tools and constraints for the session

## ⚙️ Configuration

### Extension Settings

Access via `File > Preferences > Settings` → Search "Prompts Sync":

| Setting                         | Default   | Description                                                          |
| ------------------------------- | --------- | -------------------------------------------------------------------- |
| `promptsSync.enabled`           | `true`    | Enable/disable automatic syncing                                     |
| `promptsSync.frequency`         | `"daily"` | How often to sync (`startup`, `hourly`, `daily`, `weekly`, `manual`) |
| `promptsSync.syncOnStartup`     | `true`    | Sync when VS Code starts                                             |
| `promptsSync.showNotifications` | `true`    | Show sync status notifications                                       |
| `promptsSync.customPath`        | `""`      | Custom prompts directory (leave empty for default)                   |

### Default Prompt Locations

The extension syncs prompts to your OS-specific VS Code user directory:

- **macOS**: `~/Library/Application Support/Code/User/prompts/`
- **Windows**: `%APPDATA%\Code\User\prompts\`
- **Linux**: `~/.config/Code/User/prompts/`

### Sync Frequencies

- **`startup`**: Only when VS Code starts
- **`hourly`**: Every hour while VS Code is running
- **`daily`**: Once per day (recommended)
- **`weekly`**: Once per week
- **`manual`**: Only when manually triggered

## 🎮 Using Prompts in Practice

### Scenario 1: Code Review

1. Open a pull request or code file
2. Open Copilot Chat
3. Select the "Code Review" prompt
4. The AI will follow the code review guidelines defined in the prompt

### Scenario 2: Writing Tests

1. Select the code you want to test
2. Use the "Test Generation" prompt
3. The AI will generate tests following your organization's testing patterns

### Scenario 3: Documentation

1. Open the file you want to document
2. Use the "Documentation" chat mode
3. The AI will focus on creating comprehensive, standardized documentation

### Scenario 4: Architecture Planning

1. Start a new project or feature
2. Use the "Architecture" chat mode
3. The AI will help plan the technical architecture using company patterns

## 🔧 Troubleshooting

### Common Issues

#### Prompts Not Syncing

**Symptoms**: No new prompts appear, status shows error
**Solutions**:

1. Check GitHub authentication in VS Code
2. Verify repository access permissions
3. Try manual sync: `Ctrl+Shift+P` → "Prompts Sync: Sync Now"
4. Check the output panel for detailed error messages

#### Prompts Not Available in Copilot

**Symptoms**: Prompts synced but not appearing in Copilot
**Solutions**:

1. Restart VS Code to refresh Copilot's prompt cache
2. Verify prompts are in the correct format with proper frontmatter
3. Check that the prompt files are in the correct directories

#### Extension Not Loading

**Symptoms**: Extension not appearing in VS Code
**Solutions**:

1. Verify the extension is installed: `View > Extensions`
2. Check if the extension is enabled
3. Look for errors in the Developer Console: `Help > Toggle Developer Tools`

#### Sync Takes Too Long

**Symptoms**: Sync operation appears stuck
**Solutions**:

1. Check internet connection
2. Verify repository availability
3. Try with a smaller sync frequency
4. Enable debug mode for detailed logging

### Debug Mode

Enable detailed logging:

1. Open VS Code Settings
2. Search for "promptsSync.debug"
3. Enable debug mode
4. Open Output panel (`View > Output`)
5. Select "Prompts Sync" from the dropdown
6. Review detailed sync logs

### Manual Prompt Management

If automatic sync isn't working, you can manually manage prompts:

1. **Find your prompts directory** (see locations above)
2. **Clone the repository manually**:
   ```bash
   git clone https://github.com/MounirAbdousNventive/prompts-logient-nventive.git temp-repo
   cp -r temp-repo/prompts/* /path/to/your/prompts/directory/
   rm -rf temp-repo
   ```
3. **Update manually** by repeating the clone and copy process

## 📊 Monitoring Usage

### Status Indicators

The extension provides several ways to monitor sync status:

- **Status Bar**: Shows current sync state with icons

  - ✅ Successfully synced
  - 🔄 Sync in progress
  - ❌ Sync error
  - ⏸️ Sync disabled

- **Last Sync Time**: Hover over status bar to see last successful sync

- **Detailed Status**: Use "Prompts Sync: Show Status" command for full details

### Sync History

The extension maintains a local sync history showing:

- Sync timestamps
- Success/failure status
- Error messages
- Number of files updated

## 🎯 Best Practices

### For Users

1. **Keep Extension Updated**: Regularly update to get new features and bug fixes
2. **Monitor Sync Status**: Check that prompts are syncing regularly
3. **Restart After Major Updates**: Restart VS Code after significant prompt updates
4. **Report Issues**: Submit issues for broken or unclear prompts

### For Organizations

1. **Set Consistent Frequency**: Use daily sync for active development teams
2. **Monitor Usage**: Track which prompts are most effective
3. **Provide Training**: Ensure teams understand how to use different prompt types
4. **Encourage Feedback**: Create channels for prompt improvement suggestions

## 🔗 Related Resources

- [Contribution Guide](contribution-guide.md) - How to add new prompts
- [Best Practices](best-practices.md) - Writing effective prompts
- [Technical Architecture](technical-architecture.md) - Implementation details
- [Templates](templates/) - Prompt format templates

## 📞 Support

For help with using the prompt bank:

1. **Check this guide** for common solutions
2. **Review troubleshooting** section above
3. **Check existing issues** in the repository
4. **Create a new issue** with detailed information about your problem
5. **Contact the DevOps team** for urgent issues

---

**Questions or suggestions for improving this guide? Please create an issue or submit a pull request.**
