# Best Practices

> Guidelines and best practices for writing effective prompts, instructions, and chat modes that enhance developer productivity and maintain consistency across the organization.

## 🎯 Overview

This guide provides proven strategies for creating high-quality prompts that deliver consistent, valuable results for developers using GitHub Copilot. Whether you're writing instructions, prompts, or chat modes, these practices will help you create content that is clear, effective, and maintainable.

## 📝 General Writing Principles

### Clarity and Specificity

**Be Explicit, Not Implicit**

```markdown
❌ Bad: "Write good code"
✅ Good: "Use descriptive variable names, add inline comments for complex logic, and follow the single responsibility principle"
```

**Use Active Voice**

```markdown
❌ Bad: "Errors should be handled properly"
✅ Good: "Handle errors with try-catch blocks and provide meaningful error messages"
```

**Provide Context**

```markdown
❌ Bad: "Use TypeScript interfaces"
✅ Good: "Use TypeScript interfaces for API response types to ensure type safety and better IDE support"
```

### Structure and Organization

**Use Consistent Formatting**

- Start with clear headings
- Use bullet points for lists
- Include code examples where helpful
- Maintain consistent tone and style

**Logical Information Hierarchy**

1. **What**: Clear statement of the objective
2. **Why**: Context and reasoning
3. **How**: Step-by-step instructions
4. **Examples**: Concrete illustrations
5. **Validation**: Success criteria

### Language and Tone

**Professional but Approachable**

- Use clear, direct language
- Avoid jargon unless necessary (and define it when used)
- Be helpful and instructive, not prescriptive
- Include rationale for recommendations

**Actionable Language**

```markdown
❌ Vague: "Consider using async/await"
✅ Actionable: "Replace Promise.then() chains with async/await for better readability"
```

## 📋 Instructions Best Practices

### Targeting and Scope

**Use Precise File Patterns**

```yaml
# Too broad
applyTo: '**'

# More specific
applyTo: '**/*.{js,ts,jsx,tsx}'

# Very specific
applyTo: '**/src/components/**/*.tsx'
```

**Consider Pattern Precedence**

```yaml
# Lower priority for general guidelines
applyTo: '**'
priority: 1

# Higher priority for specific file types
applyTo: '**/*.test.{js,ts}'
priority: 8
```

### Content Guidelines

**Focus on One Concept Per Instruction**

```markdown
❌ Bad: Combined instruction covering error handling, logging, and testing
✅ Good: Separate instructions for each concern
```

**Include Reasoning**

```markdown
# React Component Props Validation

## Context

Props validation helps catch bugs early and provides better developer experience with IntelliSense.

## Guidelines

- Define PropTypes or TypeScript interfaces for all props
- Mark required props explicitly
- Use specific types rather than `any` or `object`

## Why This Matters

- Reduces runtime errors
- Improves code documentation
- Enables better IDE support
```

**Provide Both Positive and Negative Examples**

````markdown
### Good Example

```typescript
interface UserProps {
  id: number;
  name: string;
  email?: string;
}
```
````

### Avoid

```typescript
interface UserProps {
  id: any;
  name: any;
  email: any;
}
```

````

### Maintenance Considerations

**Keep Instructions Current**
- Review and update regularly
- Include version information when relevant
- Remove outdated practices
- Update for new language features

**Version Control for Instructions**
```yaml
---
applyTo: '**/*.ts'
author: 'John Doe'
lastUpdated: '2025-09-01'
version: '2.1.0'
---
````

## 🤖 Prompt Best Practices

### Task Definition

**Start with Clear Objectives**

```markdown
## Objective

Generate comprehensive unit tests for React components that cover:

- All props variations
- User interaction scenarios
- Error states
- Accessibility requirements
```

**Define Success Criteria Upfront**

```markdown
## Success Criteria

- [ ] All public methods are tested
- [ ] Test coverage exceeds 90%
- [ ] Tests follow AAA pattern (Arrange, Act, Assert)
- [ ] Mock external dependencies appropriately
```

### Instruction Clarity

**Use Step-by-Step Format**

```markdown
## Instructions

### Step 1: Analyze the Component

- Identify all props and their types
- List all user interactions (clicks, form submissions, etc.)
- Note any external dependencies (APIs, stores, etc.)

### Step 2: Create Test Structure

- Set up test file with proper imports
- Create describe blocks for logical groupings
- Prepare common test utilities and mocks

### Step 3: Implement Test Cases

- Write tests for default behavior
- Test all prop variations
- Cover edge cases and error scenarios
```

**Be Specific About Expected Outcomes**

```markdown
❌ Vague: "Create good tests"
✅ Specific: "Create tests using Jest and React Testing Library that verify component renders correctly with different prop combinations and handles user interactions appropriately"
```

### Context and Constraints

**Specify Technology Constraints**

```markdown
## Technical Requirements

- Use Jest as the testing framework
- Use React Testing Library for component testing
- Follow the existing project's test file naming convention
- Import test utilities from '@testing-library/react'
```

**Include Code Style Guidelines**

```markdown
## Code Style

- Use descriptive test names that read like sentences
- Group related tests in describe blocks
- Use beforeEach for common setup
- Prefer userEvent over fireEvent for interactions
```

### Examples and Templates

**Provide Template Code**

````markdown
## Test Template

```typescript
import { render, screen, userEvent } from "@testing-library/react";
import { ComponentName } from "./ComponentName";

describe("ComponentName", () => {
  const defaultProps = {
    // Define default props here
  };

  it("should render with default props", () => {
    render(<ComponentName {...defaultProps} />);
    // Add assertions
  });

  it("should handle user interactions", async () => {
    const user = userEvent.setup();
    render(<ComponentName {...defaultProps} />);
    // Add interaction tests
  });
});
```
````

````

**Show Input/Output Examples**
```markdown
## Example

### Input Component
```typescript
interface ButtonProps {
  children: React.ReactNode;
  onClick: () => void;
  disabled?: boolean;
  variant?: 'primary' | 'secondary';
}

export const Button: React.FC<ButtonProps> = ({ children, onClick, disabled, variant = 'primary' }) => {
  return (
    <button
      onClick={onClick}
      disabled={disabled}
      className={`btn btn-${variant}`}
    >
      {children}
    </button>
  );
};
````

### Expected Test Output

```typescript
// Tests covering all props, interactions, and edge cases
// with proper mocking and assertions
```

````

## 💬 Chat Mode Best Practices

### Behavioral Definition

**Define Clear Personality Traits**
```markdown
## Behavior Guidelines

### Response Style
- Provide concise, actionable answers
- Ask clarifying questions when requirements are unclear
- Suggest best practices and alternatives
- Include relevant code examples

### Expertise Focus
- Emphasize security considerations
- Recommend performance optimizations
- Suggest testing strategies
- Consider maintainability implications
````

**Set Appropriate Boundaries**

```markdown
## Constraints

- Focus on Node.js/JavaScript ecosystem solutions
- Prioritize open-source libraries and tools
- Avoid recommending deprecated packages
- Don't provide production secrets or credentials
- Suggest code reviews for critical changes
```

### Tool Integration

**Be Selective with Tools**

```yaml
# Only include tools that are actually needed
tools: ['terminal', 'files', 'search']

# Avoid overloading with unnecessary tools
tools: ['terminal', 'files', 'search', 'browser', 'calculator', 'calendar']  # Too many
```

**Explain Tool Usage**

```markdown
## Available Tools

- **Terminal**: Execute commands for testing, building, and running applications
- **Files**: Read and write code files, configurations, and documentation
- **Search**: Find relevant code patterns and examples in the codebase

## Tool Usage Guidelines

- Use terminal for validation and testing of suggestions
- Read existing code before making recommendations
- Search for similar patterns in the codebase for consistency
```

### Conversation Flow

**Guide Natural Progressions**

```markdown
## Interaction Patterns

### Initial Questions

1. Understand the user's goal and context
2. Identify the current technology stack
3. Clarify any constraints or requirements
4. Determine the user's experience level

### Problem-Solving Flow

1. Analyze the current situation
2. Suggest multiple approaches with pros/cons
3. Help implement the chosen solution
4. Validate the implementation
5. Suggest next steps or improvements
```

**Handle Edge Cases**

```markdown
## Conversation Management

### When Information is Unclear

- Ask specific, targeted questions
- Provide examples to clarify what you need
- Suggest default approaches while waiting for clarification

### When Multiple Solutions Exist

- Present 2-3 viable options
- Explain trade-offs for each approach
- Recommend the best option based on common scenarios
- Let the user make the final decision
```

## 🔧 Technical Implementation

### File Organization

**Consistent Directory Structure**

```
prompts/
├── instructions/
│   ├── general/              # Universal guidelines
│   ├── languages/           # Language-specific rules
│   │   ├── typescript/
│   │   ├── python/
│   │   └── csharp/
│   └── frameworks/          # Framework-specific guidelines
│       ├── react/
│       ├── vue/
│       └── angular/
├── prompt/
│   ├── development/         # Core development tasks
│   ├── testing/            # Testing-related prompts
│   ├── documentation/      # Documentation generation
│   └── deployment/         # Deployment and DevOps
└── chatmode/
    ├── development/        # General development assistance
    ├── architecture/       # System design and architecture
    ├── debugging/          # Problem diagnosis and fixing
    └── review/            # Code review and analysis
```

**Naming Conventions**

```markdown
# Instructions

security-best-practices.instructions.md
react-component-guidelines.instructions.md
typescript-strict-mode.instructions.md

# Prompts

api-documentation-generator.prompt.md
unit-test-creator.prompt.md
code-refactoring-assistant.prompt.md

# Chat Modes

senior-developer-mentor.chatmode.md
security-focused-reviewer.chatmode.md
performance-optimization-expert.chatmode.md
```

### Metadata Standards

**Required Frontmatter Fields**

```yaml
# Instructions
---
applyTo: "**/*.{js,ts}" # Required: File pattern
priority: 5 # Optional: 1-10 scale
author: "Team/Individual" # Optional: For maintenance
lastUpdated: "2025-09-01" # Optional: ISO date
version: "1.2.0" # Optional: Semantic versioning
---
# Prompts
---
mode: agent # Required: Always 'agent'
category: "development" # Optional: For organization
difficulty: "intermediate" # Optional: beginner|intermediate|advanced
tags: ["react", "testing"] # Optional: For searchability
author: "Team/Individual" # Optional: For maintenance
lastUpdated: "2025-09-01" # Optional: ISO date
---
# Chat Modes
---
description: "Brief purpose" # Required: Mode description
tools: ["terminal", "files"] # Optional: Available tools
category: "development" # Optional: For organization
author: "Team/Individual" # Optional: For maintenance
lastUpdated: "2025-09-01" # Optional: ISO date
---
```

### Validation and Testing

**Content Validation Checklist**

- [ ] YAML frontmatter is valid
- [ ] Required fields are present
- [ ] File follows naming conventions
- [ ] Content is clear and actionable
- [ ] Examples are correct and relevant
- [ ] No conflicting instructions
- [ ] Proper markdown formatting

**Functional Testing**

```markdown
## Testing Your Prompts

### Instructions Testing

1. Apply instruction to sample code files
2. Verify GitHub Copilot behavior changes appropriately
3. Check for conflicts with existing instructions
4. Test with different file types in the target pattern

### Prompt Testing

1. Use the prompt with various input scenarios
2. Verify outputs meet success criteria
3. Test edge cases and error conditions
4. Confirm reusability across different projects

### Chat Mode Testing

1. Test different conversation flows
2. Verify tool usage works as expected
3. Check boundary conditions and constraints
4. Validate personality and response style
```

## 📊 Quality Metrics

### Effectiveness Indicators

**Instruction Quality**

- Reduces ambiguity in Copilot suggestions
- Improves code consistency across team
- Decreases code review feedback on covered topics
- Increases developer confidence in generated code

**Prompt Quality**

- Produces reliable, consistent outputs
- Saves significant time on repetitive tasks
- Generates code that requires minimal modification
- Can be used successfully by different team members

**Chat Mode Quality**

- Provides helpful, relevant responses
- Maintains consistent personality and focus
- Uses tools appropriately and effectively
- Guides conversations toward productive outcomes

### Success Criteria

**Quantitative Measures**

- Usage frequency and adoption rates
- User satisfaction scores
- Time saved on development tasks
- Reduction in code review iterations

**Qualitative Measures**

- Clarity and usefulness of generated content
- Consistency with team standards and practices
- Appropriateness for target audience
- Maintainability and updateability

## 🔄 Continuous Improvement

### Feedback Collection

**User Feedback Mechanisms**

- GitHub issues for bug reports and suggestions
- Regular team retrospectives on prompt effectiveness
- Usage analytics from the VS Code extension
- Direct feedback through team communication channels

**Iterative Improvement Process**

1. **Monitor Usage**: Track which prompts are used most/least
2. **Collect Feedback**: Gather user experiences and pain points
3. **Analyze Patterns**: Identify common issues or improvement opportunities
4. **Update Content**: Revise prompts based on feedback and new best practices
5. **Test Changes**: Validate improvements before deployment
6. **Communicate Updates**: Inform users of significant changes

### Version Management

**Semantic Versioning for Prompts**

```yaml
version: "1.2.3"
# 1 = Major version (breaking changes)
# 2 = Minor version (new features, backwards compatible)
# 3 = Patch version (bug fixes, improvements)
```

**Change Documentation**

```markdown
## Changelog

### Version 2.1.0 (2025-09-01)

- Added support for React 18 features
- Updated testing examples to use React Testing Library v13
- Improved error handling guidance

### Version 2.0.0 (2025-08-15)

- BREAKING: Changed file pattern from `**/*.js` to `**/*.{js,ts}`
- Removed deprecated jQuery examples
- Added TypeScript-specific guidelines
```

### Community Contribution

**Encouraging Contributions**

- Make the contribution process clear and simple
- Provide templates and examples for new contributors
- Recognize and celebrate valuable contributions
- Maintain responsive review and feedback processes

**Knowledge Sharing**

- Document lessons learned from prompt usage
- Share successful patterns and anti-patterns
- Create case studies of effective prompt implementations
- Host regular sessions on prompt writing best practices

## 🔗 Related Resources

- [Usage Guide](usage-guide.md) - How to use prompts effectively
- [Contribution Guide](contribution-guide.md) - How to contribute new prompts
- [Technical Architecture](technical-architecture.md) - System implementation details
- [Installation Guide](installation-guide.md) - Setup and configuration

## 📞 Questions and Support

For questions about best practices or help with writing effective prompts:

1. **Review existing examples** in the repository
2. **Check the [Contribution Guide](contribution-guide.md)** for templates and processes
3. **Create an issue** for specific questions or suggestions
4. **Contact the DevOps team** for guidance on complex scenarios

---

**Remember: The best prompts are those that genuinely help developers be more productive while maintaining code quality and consistency. Focus on solving real problems that your team faces regularly.**
