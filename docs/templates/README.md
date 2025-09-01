# Template Files

> Standardized templates for creating consistent, high-quality prompts, instructions, and chat modes.

## 📋 Overview

These templates provide standardized formats for all prompt types in the Logient-Nventive Shared Prompt Bank. Using these templates ensures consistency, completeness, and maintainability across all contributions.

## 📁 Available Templates

### Quick Links

- [Instructions Template](#instructions-template) - For global coding guidelines
- [Prompt Template](#prompt-template) - For task-specific agent prompts
- [Chat Mode Template](#chat-mode-template) - For custom chat behaviors
- [Documentation Template](#documentation-template) - For project documentation

---

## 📋 Instructions Template

**File naming**: `{topic-name}.instructions.md`  
**Location**: `prompts/instructions/{category}/`

````markdown
---
applyTo: "**/*.{js,ts,jsx,tsx}" # Required: Glob pattern for file targeting
priority: 5 # Optional: 1-10, higher = more important
author: "Your Name" # Optional: For tracking and questions
lastUpdated: "2025-09-01" # Optional: Maintenance tracking (ISO date)
version: "1.0.0" # Optional: Semantic versioning
tags: ["react", "components"] # Optional: For searchability
---

# Brief Title of the Instruction

## Context

Explain when and why this instruction should be applied. Provide background on the problem this instruction solves and the benefits of following it.

## Guidelines

### Specific Area 1

- Clear, actionable guideline with specific details
- Concrete example or pattern to follow
- What to avoid and why (include reasoning)

### Specific Area 2

- Another clear guideline with specific implementation details
- Code example if applicable (use proper syntax highlighting)
- Expected outcome or benefit

### Specific Area 3

- Additional guidelines as needed
- Keep each area focused on a single concept
- Maintain consistent formatting and depth

## Examples

### ✅ Good Example

```javascript
// Show good code that follows the instruction
// Include comments explaining why this is good
const UserComponent = ({ user, onUpdate }) => {
  // Clear, descriptive variable names
  const isUserActive = user.status === "active";

  return (
    <div className="user-card">
      <h3>{user.name}</h3>
      {isUserActive && <span className="status-active">Active</span>}
    </div>
  );
};
```
````

### ❌ Avoid

```javascript
// Show what not to do with explanation
// Explain why this should be avoided
const UserComponent = ({ u, onUpd }) => {
  // Unclear variable names and logic
  const x = u.status === "active";

  return (
    <div>
      <h3>{u.name}</h3>
      {x && <span>Active</span>}
    </div>
  );
};
```

## Exceptions

- When this instruction might not apply
- Alternative approaches for special cases
- How to handle conflicts with other instructions

## Related Guidelines

- Link to related instructions or documentation
- Reference external style guides or standards
- Point to team-specific conventions

## Validation

How to verify that the instruction is being followed:

- [ ] Specific checkpoint 1
- [ ] Specific checkpoint 2
- [ ] Specific checkpoint 3

````

---

## 🤖 Prompt Template

**File naming**: `{task-name}.prompt.md`
**Location**: `prompts/prompt/{category}/`

```markdown
---
mode: agent                      # Required: Always 'agent' for prompts
category: 'development'          # Optional: development|testing|documentation|deployment
difficulty: 'intermediate'       # Optional: beginner|intermediate|advanced
author: 'Your Name'              # Optional: For tracking and questions
lastUpdated: '2025-09-01'        # Optional: Maintenance tracking (ISO date)
version: '1.0.0'                 # Optional: Semantic versioning
tags: ['testing', 'react', 'unit'] # Optional: For searchability
estimatedTime: '15-30 minutes'   # Optional: Expected completion time
---

# Brief Title of the Task

## Objective
Clear, one-sentence statement of what this prompt accomplishes and the expected outcome.

## Context
- When to use this prompt (specific scenarios)
- Prerequisites or setup needed before starting
- Relevant technologies, frameworks, or tools involved
- Assumptions about the codebase or environment

## Requirements

### Technical Requirements
- Specific tools, frameworks, or libraries to use
- Code style and formatting guidelines
- Performance or quality standards to meet
- Integration requirements with existing systems

### Functional Requirements
- Specific features or behaviors to implement
- User experience considerations
- Error handling and edge case requirements
- Accessibility or security considerations

## Instructions

### Step 1: Analysis and Planning
Detailed instruction for the first step, including:
- What to analyze or review
- How to identify key requirements
- Planning considerations or decisions to make

### Step 2: Implementation Setup
Clear setup instructions:
- Files to create or modify
- Dependencies to install or configure
- Initial code structure or boilerplate

### Step 3: Core Implementation
Main implementation guidance:
- Specific coding patterns to follow
- Key algorithms or logic to implement
- Integration points with existing code

### Step 4: Testing and Validation
How to verify the implementation:
- Types of tests to write or run
- Manual testing procedures
- Performance or quality checks

### Step 5: Documentation and Cleanup
Final steps:
- Documentation to create or update
- Code cleanup or refactoring
- Deployment or integration steps

## Success Criteria
- [ ] Specific, measurable outcome 1 (with clear validation method)
- [ ] Specific, measurable outcome 2 (with clear validation method)
- [ ] Specific, measurable outcome 3 (with clear validation method)
- [ ] All tests pass and code meets quality standards
- [ ] Documentation is complete and accurate

## Example

### Input Scenario
````

Describe a typical input scenario or starting condition.
Include sample code, configuration, or data as relevant.

```

### Expected Output
```

Show what the result should look like after completing the prompt.
Include code examples, file structures, or other concrete outputs.

````

### Sample Implementation
```typescript
// Provide a concrete example of the expected implementation
// Include relevant imports, types, and structure
interface ExampleInterface {
  id: string;
  name: string;
  // ... other properties
}

export const exampleFunction = (input: ExampleInterface): OutputType => {
  // Implementation that follows the prompt guidelines
  return processedOutput;
};
````

## Tips and Best Practices

- Additional helpful information specific to this task
- Common pitfalls to avoid and how to prevent them
- Performance considerations or optimization opportunities
- Debugging tips for common issues

## Troubleshooting

Common issues and their solutions:

**Issue**: Description of a common problem
**Solution**: Specific steps to resolve the issue

**Issue**: Another common problem  
**Solution**: Another specific solution

## Related Resources

- Links to relevant documentation
- Related prompts or instructions
- External tools or libraries that might be helpful
- Team-specific resources or standards

````

---

## 💬 Chat Mode Template

**File naming**: `{mode-name}.chatmode.md`
**Location**: `prompts/chatmode/{category}/`

```markdown
---
description: 'Brief, clear description of this chat mode behavior and purpose'
category: 'development'          # Optional: development|architecture|debugging|review
tools: ['terminal', 'files']     # Optional: Available tools for this mode
author: 'Your Name'              # Optional: For tracking and questions
lastUpdated: '2025-09-01'        # Optional: Maintenance tracking (ISO date)
version: '1.0.0'                 # Optional: Semantic versioning
expertise: ['javascript', 'react'] # Optional: Primary expertise areas
---

# Chat Mode Name

## Purpose
Clear, detailed explanation of what this chat mode is designed to accomplish and when it should be used.

## Behavior Guidelines

### Response Style
- How the AI should communicate (formal/casual, brief/detailed, etc.)
- Tone and personality traits to adopt
- Preferred format for responses (bullet points, code examples, step-by-step, etc.)
- Level of technical depth appropriate for responses

### Communication Patterns
- How to structure responses for maximum clarity
- When to ask clarifying questions vs. making assumptions
- How to handle ambiguous or incomplete requests
- Balance between being helpful and being directive

### Expertise Focus
- Primary technical domains and technologies to emphasize
- Specific areas of knowledge to draw from
- Types of problems this mode is optimized to solve
- Depth of technical detail to provide

### Problem-Solving Approach
- Methodology for analyzing and solving problems
- How to break down complex issues
- When to suggest alternatives or multiple approaches
- How to prioritize different considerations (performance, maintainability, etc.)

## Interaction Patterns

### Initial Engagement
How to start conversations and gather context:
1. Understand the user's goal and current situation
2. Identify relevant constraints or requirements
3. Clarify the scope and expected outcomes
4. Determine the user's experience level with relevant technologies

### Ongoing Conversation Flow
How to maintain productive conversations:
1. **Listen actively** - Pay attention to both explicit and implicit needs
2. **Ask targeted questions** - When clarification is needed
3. **Provide structured responses** - Use clear formatting and organization
4. **Follow up appropriately** - Check understanding and offer next steps

### Problem Resolution
How to guide users through problem-solving:
1. **Analyze the situation** - Break down the problem systematically
2. **Present options** - Show multiple approaches with trade-offs
3. **Guide implementation** - Provide step-by-step assistance
4. **Validate results** - Help verify that solutions work as expected

## Available Tools

### Tool Usage Guidelines
Explain each available tool and when to use it:

- **Terminal**: Execute commands for testing, building, installing packages, or running diagnostics
  - Use for: Verification of suggestions, running tests, checking system status
  - Avoid: Destructive operations without explicit user consent

- **Files**: Read existing code and write new files or modifications
  - Use for: Understanding current codebase, implementing suggested changes
  - Avoid: Modifying files without explaining the changes

- **Search**: Find relevant patterns, examples, or information in the codebase
  - Use for: Understanding existing patterns, finding similar implementations
  - Avoid: Searching without a specific purpose or context

### Tool Integration Strategy
How to combine tools effectively:
- **Read before writing** - Understand existing code before suggesting changes
- **Test suggestions** - Validate recommendations with appropriate tools
- **Explain tool usage** - Let users know what you're doing and why

## Constraints and Boundaries

### What This Mode Should Do
- Specific types of assistance and guidance to provide
- Topics and technologies to focus on
- Level of hands-on help to offer

### What This Mode Should Avoid
- Types of requests to redirect elsewhere
- Limitations or boundaries to maintain
- When to suggest alternative approaches or modes

### Escalation Guidelines
When and how to suggest users seek additional help:
- Complex architectural decisions requiring team input
- Security-sensitive implementations needing review
- Performance-critical code requiring specialized expertise

## Example Conversations

### Scenario 1: [Common Use Case Name]
**Context**: Brief description of the scenario

**User**: "Example question or request that would be typical for this mode"

**Assistant**: Example response following this mode's guidelines, demonstrating:
- Appropriate tone and style
- Use of available tools
- Problem-solving approach
- Level of technical detail

**User**: "Follow-up question"

**Assistant**: Example follow-up response showing:
- How to build on previous context
- Appropriate level of detail
- When to use tools or ask clarifying questions

### Scenario 2: [Another Common Use Case]
**Context**: Description of a different typical scenario

**User**: "Different type of question or request"

**Assistant**: Response demonstrating:
- Flexibility in approach while maintaining mode characteristics
- How to handle different types of requests
- Appropriate tool usage for the scenario

## Success Indicators

### Conversation Quality Metrics
How to measure if this mode is working effectively:
- User questions are answered completely and accurately
- Conversations progress toward clear, actionable outcomes
- Users express satisfaction with the level of help provided
- Technical solutions are appropriate and well-explained

### Technical Outcomes
What successful use of this mode should produce:
- Code that follows best practices and team standards
- Solutions that are maintainable and well-documented
- Proper use of tools and technologies
- Improvements to user knowledge and capabilities

### User Experience Goals
How users should feel after interacting with this mode:
- Confident in the solutions provided
- Better understanding of the underlying concepts
- Equipped to handle similar problems independently
- Satisfied with the level of support received

## Customization Notes

### Team-Specific Adaptations
Areas where this mode can be customized for specific teams or projects:
- Technology stack preferences
- Code style and standards
- Security or compliance requirements
- Performance or scalability considerations

### Environment Considerations
How this mode should adapt to different environments:
- Development vs. production contexts
- Different project types or scales
- Varying team experience levels
- Specific organizational constraints

## Related Resources
- Links to relevant team documentation
- Related chat modes for different scenarios
- External documentation or standards
- Training materials or best practice guides
````

---

## 📚 Documentation Template

**File naming**: `{document-name}.md`  
**Location**: `docs/`

````markdown
# Document Title

> Brief, compelling description of what this document covers and who it's for.

## 🎯 Overview

Clear explanation of the document's purpose, scope, and intended audience. Include what readers will learn and how it fits into the larger documentation ecosystem.

## 📋 Prerequisites

What readers need to know or have before using this document:

- Required knowledge or experience
- Software or tools that should be installed
- Access permissions or accounts needed
- Related documents that should be read first

## 🚀 Quick Start (if applicable)

For procedural documents, provide a rapid getting-started section:

1. **First essential step** with brief explanation
2. **Second essential step** with brief explanation
3. **Third essential step** with brief explanation
4. **Verification step** - how to confirm success

## 📖 Main Content

### Section 1: [Descriptive Name]

Detailed information about the first major topic. Use clear headings, bullet points, and code examples where appropriate.

#### Subsection 1.1: [Specific Topic]

More detailed information about specific aspects.

```bash
# Include relevant code examples
npm install package-name
```
````

#### Subsection 1.2: [Another Specific Topic]

Additional detailed information.

### Section 2: [Another Major Topic]

Continue with logical organization and clear structure.

## 🔧 Advanced Topics (if applicable)

More complex information for advanced users:

- Advanced configuration options
- Troubleshooting complex scenarios
- Integration with other systems
- Customization and extension points

## 📊 Examples and Use Cases

### Example 1: [Common Scenario]

```markdown
Provide concrete examples that readers can follow along with.
Include both code and explanatory text.
```

### Example 2: [Another Scenario]

Additional examples covering different use cases or approaches.

## 🚨 Troubleshooting

### Common Issues

#### Issue: [Problem Description]

**Symptoms**: What users will see when this problem occurs
**Cause**: Why this problem happens
**Solution**: Step-by-step resolution

```bash
# Include any commands or code needed
```

#### Issue: [Another Problem]

**Symptoms**: Observable signs of this issue
**Cause**: Root cause explanation
**Solution**: Clear resolution steps

## ❓ FAQ

**Q: Common question that users ask?**
A: Clear, complete answer with examples if needed.

**Q: Another frequently asked question?**  
A: Another helpful answer.

## 🔗 Related Resources

- [Related Document 1](link) - Brief description of relevance
- [Related Document 2](link) - Brief description of relevance
- [External Resource](link) - Brief description of relevance

## 📞 Support and Feedback

Information about how to get help or provide feedback:

- How to report issues or bugs
- Where to ask questions
- How to suggest improvements
- Contact information for urgent issues

---

**Document Information**

- **Last Updated**: 2025-09-01
- **Version**: 1.0.0
- **Maintainer**: Team/Individual Name
- **Review Schedule**: Quarterly/Semi-annually/Annually

```

---

## 🎯 Template Usage Guidelines

### Choosing the Right Template

**Use Instructions Template when:**
- Creating coding guidelines that apply automatically
- Establishing team standards for specific file types
- Providing context-aware guidance for GitHub Copilot

**Use Prompt Template when:**
- Creating task-specific workflows
- Building reusable procedures for common development tasks
- Providing step-by-step guidance for complex operations

**Use Chat Mode Template when:**
- Defining AI personality and behavior for specific domains
- Creating specialized assistants for particular workflows
- Establishing consistent interaction patterns

**Use Documentation Template when:**
- Writing user guides or technical documentation
- Creating reference materials
- Documenting processes or procedures

### Customization Guidelines

**Required Elements:**
- All fields marked as "Required" in the frontmatter
- Core sections that provide essential information
- Examples that illustrate the concepts clearly

**Optional Elements:**
- Additional metadata fields for better organization
- Extra sections that add value for your specific use case
- Team-specific customizations or standards

**Adaptation Tips:**
- Modify language and tone to match your team's communication style
- Add or remove sections based on your specific needs
- Include team-specific tools, frameworks, or standards
- Adjust complexity level for your audience

### Quality Checklist

Before submitting content based on these templates:

**Content Quality:**
- [ ] Information is accurate and up-to-date
- [ ] Examples are relevant and working
- [ ] Language is clear and appropriate for the audience
- [ ] All required sections are complete

**Technical Quality:**
- [ ] YAML frontmatter is valid
- [ ] Markdown formatting is correct
- [ ] File naming follows conventions
- [ ] Code examples use proper syntax highlighting

**Usability Quality:**
- [ ] Content is well-organized and easy to follow
- [ ] Instructions are actionable and specific
- [ ] Success criteria are clear and measurable
- [ ] Troubleshooting guidance is helpful

## 📝 Template Maintenance

These templates are living documents that should be updated as:
- New best practices emerge
- Team standards evolve
- Tool capabilities change
- User feedback suggests improvements

To suggest template improvements:
1. Review the current template and identify areas for enhancement
2. Create an issue describing the proposed changes and rationale
3. Submit a pull request with the updated template
4. Work with maintainers to refine and approve changes

---

**Questions about using these templates? Check the [Contribution Guide](../contribution-guide.md) or create an issue for assistance.**
```
