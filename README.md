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

1. Install the Logient Prompt Bank VS Code extension
2. Your prompts will automatically sync and be available in all projects

### For Contributors

1. Read the [Contribution Guide](docs/contribution-guide.md)
2. Fork the repository or create a feature branch
3. Add your prompts following our [templates](docs/templates/)
4. Submit a pull request for review

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

- [Usage Guide](docs/usage-guide.md) - How to use the prompt bank
- [Contribution Guide](docs/contribution-guide.md) - How to contribute new prompts
- [Best Practices](docs/best-practices.md) - Guidelines for writing effective prompts
- [Implementation Plan](docs/implementation-plan.md) - Detailed project plan
- [Technical Architecture](docs/technical-architecture.md) - Technical implementation details

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
