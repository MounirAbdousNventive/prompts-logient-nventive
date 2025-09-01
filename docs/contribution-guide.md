# Contribution Guide

> Guidelines for contributing prompts, instructions, and chat modes to the Logient-Nventive Shared Prompt Bank.

## 🎯 Overview

We welcome contributions that help improve developer productivity across our organization. This guide covers everything you need to know about contributing high-quality prompts, instructions, and chat modes.

## 🚀 Getting Started

### Prerequisites

Before contributing, ensure you have:

- Access to the [prompts-logient-nventive](https://github.com/MounirAbdousNventive/prompts-logient-nventive) repository
- Basic understanding of Markdown
- Familiarity with GitHub Copilot and VS Code
- Understanding of your team's coding standards and practices

### Setup for Contributors

1. **Fork the repository** or create a feature branch:

   ```bash
   git clone https://github.com/MounirAbdousNventive/prompts-logient-nventive.git
   cd prompts-logient-nventive
   git checkout -b feature/your-prompt-name
   ```

2. **Install development tools** (optional, for VS Code extension work):

   ```bash
   cd tools/vscode-extension
   npm install
   ```

3. **Test your changes locally** before submitting

## 📝 Contribution Types

### 1. Adding New Prompts

**When to add a new prompt:**

- You have a reusable task that others would benefit from
- The prompt follows a specific pattern that should be standardized
- It addresses a common development scenario in your team

**What makes a good prompt:**

- Clear, specific instructions
- Reusable across different projects
- Follows company/team standards
- Includes success criteria

### 2. Improving Existing Prompts

**When to improve existing prompts:**

- You find ambiguous or unclear instructions
- The prompt produces inconsistent results
- You have additional context that would help
- The prompt needs updates for new tools or practices

### 3. Adding Documentation

**When to add documentation:**

- You discover gaps in existing documentation
- You have insights from using the prompt bank
- You want to share best practices
- You've solved common problems

## 📁 File Structure and Naming

### Directory Structure

```
prompts/
├── instructions/           # Global coding guidelines
│   ├── general/           # General development practices
│   ├── security/          # Security-focused instructions
│   ├── frameworks/        # Framework-specific guidelines
│   └── languages/         # Language-specific standards
├── prompt/                # Task-specific prompts
│   ├── development/       # Development tasks
│   ├── testing/          # Testing-related prompts
│   ├── documentation/    # Documentation prompts
│   └── review/           # Code review prompts
└── chatmode/             # Custom chat behaviors
    ├── development/      # Development-focused modes
    ├── architecture/     # Architecture planning modes
    └── debugging/       # Debugging assistance modes
```

### Naming Conventions

**File Naming:**

- Use descriptive, kebab-case names
- Include the prompt type in the extension
- Examples:
  - `react-component-guidelines.instructions.md`
  - `api-endpoint-testing.prompt.md`
  - `code-review-assistant.chatmode.md`

**Directory Organization:**

- Group related prompts in subdirectories
- Use clear, descriptive directory names
- Maintain consistent categorization

## 📋 Prompt Format Templates

### Instructions Template

````markdown
---
applyTo: "**/*.{js,ts,jsx,tsx}" # File pattern (use '**' for all files)
priority: 1 # Optional: 1-10, higher = more important
author: "Your Name" # Optional: For tracking and questions
lastUpdated: "2025-09-01" # Optional: Maintenance tracking
---

# Brief Title of the Instruction

## Context

Explain when and why this instruction should be applied.

## Guidelines

### Specific Area 1

- Clear, actionable guideline
- Specific example or pattern to follow
- What to avoid and why

### Specific Area 2

- Another clear guideline
- Code example if applicable
- Expected outcome

## Examples

### Good Example

```javascript
// Show good code that follows the instruction
```
````

### Avoid

```javascript
// Show what not to do
```

## Exceptions

- When this instruction might not apply
- Alternative approaches for special cases

````

### Prompt Template

```markdown
---
mode: agent                      # Always 'agent' for prompts
category: 'development'          # Category for organization
difficulty: 'intermediate'       # beginner|intermediate|advanced
author: 'Your Name'              # Optional: For tracking and questions
lastUpdated: '2025-09-01'        # Optional: Maintenance tracking
tags: ['testing', 'react']      # Optional: For searchability
---

# Brief Title of the Task

## Objective
Clear statement of what this prompt accomplishes.

## Context
- When to use this prompt
- Prerequisites or setup needed
- Relevant technologies or frameworks

## Instructions

### Step 1: [Action]
Detailed instruction for the first step.

### Step 2: [Action]
Detailed instruction for the second step.

### Step 3: [Validation]
How to verify the task was completed successfully.

## Success Criteria
- [ ] Specific measurable outcome 1
- [ ] Specific measurable outcome 2
- [ ] Specific measurable outcome 3

## Example

### Input
````

Show what kind of input this prompt expects

```

### Expected Output
```

Show what the result should look like

```

## Tips
- Additional helpful information
- Common pitfalls to avoid
- Best practices specific to this task
```

### Chat Mode Template

```markdown
---
description: "Brief description of this chat mode behavior"
category: "development" # Category for organization
tools: ["terminal", "files"] # Available tools for this mode
author: "Your Name" # Optional: For tracking and questions
lastUpdated: "2025-09-01" # Optional: Maintenance tracking
---

# Chat Mode Name

## Purpose

Clear explanation of what this chat mode is designed to do.

## Behavior Guidelines

### Response Style

- How the AI should communicate (formal/casual, brief/detailed, etc.)
- Tone and personality traits
- Preferred format for responses

### Focus Areas

- Primary topics this mode should emphasize
- Relevant technologies, frameworks, or domains
- Specific expertise areas

### Interaction Patterns

- How conversations should flow
- When to ask clarifying questions
- How to handle ambiguous requests

## Available Tools

List and explain the tools available in this mode:

- **Tool Name**: What it's used for and when to use it
- **Another Tool**: Purpose and usage guidelines

## Constraints

- What this mode should avoid doing
- Limitations or boundaries
- When to suggest switching to a different mode

## Example Conversations

### Scenario 1: [Common Use Case]

**User**: Example question or request
**Assistant**: Example response following this mode's guidelines

### Scenario 2: [Another Use Case]

**User**: Another example question
**Assistant**: Another example response

## Success Indicators

- How to measure if this mode is working effectively
- User satisfaction signals
- Task completion criteria
```

## ✅ Quality Standards

### Content Requirements

**All Prompts Must:**

- Have clear, unambiguous instructions
- Include proper frontmatter with required fields
- Use correct Markdown formatting
- Be tested before submission
- Follow naming conventions

**Instructions Must:**

- Apply to specific file patterns when possible
- Avoid conflicting with existing instructions
- Include concrete examples
- Explain the reasoning behind guidelines

**Prompts Must:**

- Have clear success criteria
- Be reusable across different projects
- Include example inputs and outputs
- Have step-by-step instructions

**Chat Modes Must:**

- Define clear behavioral guidelines
- Specify appropriate tools and constraints
- Include example conversations
- Have specific use cases

### Testing Requirements

Before submitting, test your contribution:

1. **Format Validation:**

   - Frontmatter is valid YAML
   - Markdown renders correctly
   - File follows naming conventions

2. **Functional Testing:**

   - Instruction produces expected coding behavior
   - Prompt generates desired outputs
   - Chat mode behaves as intended

3. **Integration Testing:**
   - Works with existing prompts
   - Doesn't conflict with other instructions
   - Syncs properly with the VS Code extension

## 🔄 Submission Process

### 1. Prepare Your Contribution

1. **Create your prompt file(s)** following the templates above
2. **Test thoroughly** in your local environment
3. **Add documentation** if needed (README updates, new guides)
4. **Follow the file naming and organization conventions**

### 2. Submit for Review

1. **Commit your changes:**

   ```bash
   git add .
   git commit -m "feat: add [brief description of your contribution]"
   ```

2. **Push your branch:**

   ```bash
   git push origin feature/your-prompt-name
   ```

3. **Create a Pull Request:**
   - Use a clear, descriptive title
   - Fill out the PR template completely
   - Link any related issues
   - Add appropriate labels

### 3. Review Process

**Review Criteria:**

- Code quality and clarity
- Adherence to guidelines
- Usefulness to the team
- Integration with existing prompts
- Documentation completeness

**Review Timeline:**

- Initial review within 2 business days
- Final approval within 1 week
- Feedback provided for changes needed

**Reviewers Look For:**

- Clarity and usefulness
- Proper formatting and structure
- No conflicts with existing content
- Security and best practice compliance
- Appropriate categorization

## 🛠️ Advanced Contributions

### Contributing to the VS Code Extension

If you want to improve the extension itself:

1. **Development Setup:**

   ```bash
   cd tools/vscode-extension
   npm install
   npm run compile
   ```

2. **Testing Changes:**

   ```bash
   # Run in development mode
   npm run watch

   # Package for testing
   npm run package
   ```

3. **Key Areas for Contribution:**
   - Sync reliability improvements
   - New configuration options
   - Better error handling
   - UI/UX enhancements

### Adding New Prompt Categories

To add a new category:

1. **Create directory structure:**

   ```bash
   mkdir -p prompts/prompt/your-category
   mkdir -p prompts/instructions/your-category
   mkdir -p prompts/chatmode/your-category
   ```

2. **Add category documentation** explaining its purpose and scope

3. **Create initial prompts** to populate the category

4. **Update relevant documentation** (this guide, README, etc.)

## 📊 Measuring Impact

### Success Metrics

Track the effectiveness of your contributions:

- **Usage frequency**: How often is your prompt used?
- **User feedback**: Are users finding it helpful?
- **Issue reports**: Are there problems with your prompt?
- **Iteration count**: How often has it needed updates?

### Feedback Collection

- **GitHub Issues**: Users can report problems or suggestions
- **Pull Request Comments**: Direct feedback during review
- **Team Feedback**: Regular team retrospectives on prompt effectiveness
- **Usage Analytics**: Extension usage data (when available)

## 🎯 Best Practices for Contributors

### Writing Effective Instructions

1. **Be Specific**: Avoid vague terms like "good" or "clean"
2. **Provide Context**: Explain why the instruction matters
3. **Include Examples**: Show both good and bad examples
4. **Consider Edge Cases**: Address common exceptions
5. **Stay Current**: Update for new language features or frameworks

### Creating Useful Prompts

1. **Start with User Stories**: "As a developer, I want to..."
2. **Break Down Complex Tasks**: Use step-by-step instructions
3. **Define Success Clearly**: What does "done" look like?
4. **Make It Reusable**: Avoid project-specific details
5. **Test Thoroughly**: Try it on different codebases

### Designing Chat Modes

1. **Define Purpose Clearly**: What specific problem does this solve?
2. **Set Appropriate Boundaries**: What should this mode NOT do?
3. **Choose Tools Wisely**: Only include tools that are actually needed
4. **Consider User Experience**: How does this improve developer workflow?
5. **Plan for Evolution**: How might this mode need to change over time?

## 🚫 Common Mistakes to Avoid

### Content Issues

- **Too Vague**: Instructions that could be interpreted multiple ways
- **Too Specific**: Prompts that only work for one project
- **Conflicting Guidelines**: Instructions that contradict existing ones
- **Missing Context**: Not explaining when or why to use something
- **Poor Examples**: Examples that don't clearly illustrate the point

### Technical Issues

- **Invalid Frontmatter**: YAML syntax errors or missing required fields
- **Wrong File Extensions**: Using incorrect file naming conventions
- **Poor Organization**: Files in the wrong directories
- **Broken Markdown**: Syntax errors that prevent proper rendering
- **Missing Testing**: Submitting untested content

### Process Issues

- **Inadequate Description**: PR descriptions that don't explain the contribution
- **Missing Documentation**: Not updating relevant docs when needed
- **Ignoring Feedback**: Not addressing review comments
- **Rushing Submission**: Not taking time to polish and test
- **Poor Commit Messages**: Vague or unhelpful commit descriptions

## 🔗 Resources and References

### Documentation

- [Usage Guide](usage-guide.md) - How to use the prompt bank
- [Best Practices](best-practices.md) - Writing effective prompts
- [Technical Architecture](technical-architecture.md) - System implementation
- [Templates](templates/) - Standardized formats

### Tools

- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [VS Code Extension Development](https://code.visualstudio.com/api)
- [Markdown Guide](https://www.markdownguide.org/)
- [YAML Syntax Reference](https://yaml.org/spec/1.2/spec.html)

### Community

- **Repository Issues**: For bug reports and feature requests
- **Pull Request Discussions**: For contribution feedback
- **Team Channels**: Internal communication for questions
- **DevOps Team**: For technical support and guidance

## 📞 Getting Help

### Before Asking for Help

1. **Check existing documentation** in this repository
2. **Search through existing issues** for similar problems
3. **Review similar prompts** for patterns and examples
4. **Test your contribution** thoroughly

### How to Ask for Help

1. **Choose the Right Channel:**

   - GitHub Issues for bugs or feature requests
   - Pull Request comments for feedback on contributions
   - Team channels for general questions

2. **Provide Context:**

   - What you're trying to accomplish
   - What you've already tried
   - Specific error messages or unexpected behavior
   - Your environment (OS, VS Code version, etc.)

3. **Be Specific:**
   - Include relevant code snippets
   - Describe expected vs. actual behavior
   - Provide steps to reproduce issues

### Escalation Path

1. **Community Support**: GitHub issues and PR discussions
2. **Team Lead**: Your immediate team lead for project-specific questions
3. **DevOps Team**: For technical issues with the extension or repository
4. **Architecture Team**: For questions about prompt design and standards

---

**Thank you for contributing to the Logient-Nventive Shared Prompt Bank! Your contributions help improve productivity across our entire development organization.**
