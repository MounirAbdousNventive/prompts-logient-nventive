# Logient-Nventive Shared Prompt Bank

> A centralized repository for Copilot instructions, prompts, and templates to enhance developer productivity across the organization.

## 🎯 Overview

This repository serves as the single source of truth for all GitHub Copilot instructions, coding prompts, and development templates used by our development teams. It provides automatic synchronization with VS Code global settings and ensures all developers have access to the latest, peer-reviewed prompts.

## ✨ Features

- **Centralized Storage**: All prompts, Copilot instructions, and coding guidelines in one place
- **Global Accessibility**: Automatically available in every VS Code project
- **Auto-Sync**: Keeps your local prompts up-to-date with the latest versions
- **Version Control**: Track changes and improvements over time
- **Peer Review**: Quality assurance through collaborative review process
- **Categorized Organization**: Easy to find prompts by framework, language, or use case
- **Language Guidelines**: Consistent coding standards and best practices across languages

## 🚀 Quick Start

### For Users

1. **Install the VS Code Extension**

   - Download the latest `prompts-sync-extension-{version}.vsix` from `tools/vscode-extension/`
   - Install via VS Code: `Ctrl+Shift+P` → "Extensions: Install from VSIX"
   - Restart VS Code when prompted

2. **Verify Installation**

   - Check for sync status indicator in the status bar
   - Your prompts will automatically sync and be available in all projects

3. **Start Using Prompts**
   - Instructions automatically apply to your code
   - Access prompts through GitHub Copilot's prompt picker
   - Use custom chat modes for specialized assistance

👉 **[Complete Installation Guide](docs/installation-guide.md)**

### For Contributors

1. **Read the Documentation**

   - Review the [Contribution Guide](docs/contribution-guide.md)
   - Check [Best Practices](docs/best-practices.md) for writing effective prompts
   - Use the provided [Templates](docs/templates/) for consistency

2. **Set Up Development Environment**

   ```bash
   git clone https://github.com/MounirAbdousNventive/prompts-logient-nventive.git
   cd prompts-logient-nventive
   ```

3. **Add Your Prompts**
   - Create new prompt files following the [template formats](docs/templates/)
   - Test your prompts locally
   - Submit a pull request for review

👉 **[Complete Contribution Guide](docs/contribution-guide.md)**

## 📁 Repository Structure

```
├── copilot-instructions/    # Copilot instruction files
│   ├── general/            # General coding instructions
│   ├── frameworks/         # Framework-specific instructions
│   └── languages/          # Language-specific instructions
├── prompts/                # Reusable prompt templates
│   ├── development/        # Development-related prompts
│   ├── documentation/      # Documentation prompts
│   ├── testing/           # Testing prompts
│   └── templates/         # Code templates
├── language-guidelines/    # Language-specific coding standards
│   ├── general/           # Universal coding principles
│   ├── typescript/        # TypeScript style guides and best practices
│   ├── javascript/        # JavaScript style guides and best practices
│   ├── python/           # Python style guides and best practices
│   └── csharp/           # C# style guides and best practices
├── scripts/               # Installation and sync scripts
├── tools/                 # VS Code extension and utilities
└── docs/                  # Documentation and guides
```

## 📖 Documentation

### User Guides

- [Installation Guide](docs/installation-guide.md) - Complete setup and installation instructions
- [Usage Guide](docs/usage-guide.md) - How to use the prompt bank effectively
- [Best Practices](docs/best-practices.md) - Guidelines for writing and using effective prompts

### Developer Resources

- [Contribution Guide](docs/contribution-guide.md) - How to contribute new prompts and improvements
- [Technical Architecture](docs/technical-architecture.md) - System design and implementation details
- [API Reference](docs/api-reference.md) - Complete API documentation for the VS Code extension

### Templates and Standards

- [Templates](docs/templates/) - Standardized formats for all prompt types
- [Prompt Format Specification](docs/technical-architecture.md#-prompt-file-format-specification) - Technical format requirements

## 🤝 Contributing

We welcome contributions from all team members! Please see our [Contribution Guide](docs/contribution-guide.md) for details on:

- How to add new prompts
- Prompt quality standards
- Review process
- Template usage

## 📊 Current Status

- **Phase**: Foundation Setup
- **Contributors**: Development Team
- **Last Updated**: August 30, 2025
- **Version**: 1.0.0

## 📄 License

Internal use only - Logient/Nventive Development Team
