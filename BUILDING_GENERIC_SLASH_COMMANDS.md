# Building Generic Slash Commands in Claude Code

## Overview

This guide documents the process for creating generic `/` commands in Claude Code that can be reused across different contexts. This approach allows for building flexible, parameterized commands that can adapt to various use cases.

## What Are Slash Commands?

Slash commands in Claude Code are custom prompts that start with `/` and are saved as Markdown files. They allow you to create reusable prompt templates that can be invoked quickly with arguments.

## Key Concepts

### 1. Command Structure
- Slash commands are stored as `.md` files in the Claude configuration directory
- The filename determines the command name (e.g., `compact.md` creates `/compact`)
- Commands can accept arguments that are passed when invoked

### 2. Generic Design Principles
- **Parameterization**: Use placeholders for variable content
- **Context Awareness**: Design commands to work with current file/project context
- **Flexibility**: Allow arguments to modify behavior
- **Reusability**: Create commands that work across different projects

## Implementation Steps

### Step 1: Define Command Purpose
Before creating a command, clearly define:
- What task it should accomplish
- What inputs it needs
- How it should behave in different contexts
- What outputs are expected

### Step 2: Create the Command File
Create a new `.md` file in your Claude configuration directory:

```bash
# Location varies by system, typically:
# ~/.claude/commands/ or ~/.config/claude/commands/
touch ~/.claude/commands/your-command-name.md
```

### Step 3: Write the Command Template
Structure your command with:
- Clear instructions for Claude
- Parameter placeholders
- Context-aware elements
- Expected behavior descriptions

Example template structure:
```markdown
# Command Name

## Purpose
Brief description of what this command does.

## Parameters
- `{param1}`: Description of first parameter
- `{param2}`: Description of second parameter

## Instructions
Detailed instructions for Claude on how to execute this command.

## Context Usage
How the command should use current file/project context.
```

### Step 4: Handle Arguments
Claude Code passes arguments to slash commands. Design your command to:
- Accept optional arguments
- Provide default behavior when no arguments are given
- Validate argument types and formats
- Give clear error messages for invalid arguments

### Step 5: Test and Iterate
- Test the command in different contexts
- Verify argument handling works correctly
- Ensure the command produces consistent, useful results
- Refine based on usage patterns

## Best Practices

### 1. Keep Commands Focused
- Each command should have a single, clear purpose
- Avoid trying to do too many things in one command
- Create multiple specialized commands rather than one complex one

### 2. Make Commands Context-Aware
- Use current file content when relevant
- Consider project structure and conventions
- Adapt behavior based on file type or project type

### 3. Provide Clear Instructions
- Write detailed, unambiguous instructions for Claude
- Specify expected output format
- Include examples when helpful

### 4. Handle Edge Cases
- Consider what happens with empty files
- Handle missing dependencies gracefully
- Provide fallback behavior for unexpected situations

### 5. Documentation and Naming
- Use descriptive command names
- Include clear documentation within the command file
- Maintain consistency in naming conventions

## Example: Generic Code Analysis Command

```markdown
# Analyze Code Structure

## Purpose
Analyze the current file or specified files for code structure, patterns, and potential improvements.

## Parameters
- `{target}`: Optional - specific file or directory to analyze (defaults to current file)
- `{depth}`: Optional - analysis depth level (shallow, normal, deep)

## Instructions
1. Examine the target code file(s)
2. Identify code patterns, structure, and architecture
3. Look for potential improvements or issues
4. Provide a structured analysis report including:
   - Code organization assessment
   - Potential refactoring opportunities
   - Code quality observations
   - Suggestions for improvement

## Context Usage
- If no target specified, analyze the currently open file
- Consider project context for framework-specific analysis
- Use appropriate analysis depth based on file size and complexity
```

## Advanced Techniques

### 1. Conditional Logic
Include conditional instructions based on argument values:
```markdown
If {mode} is "quick":
- Provide brief summary only
If {mode} is "detailed":
- Include comprehensive analysis with examples
```

### 2. Multi-Step Processing
Design commands that work in phases:
```markdown
1. First, analyze the current context
2. Then, based on findings, determine appropriate action
3. Finally, execute the action and report results
```

### 3. Integration with Other Tools
Commands can leverage Claude Code's tool ecosystem:
- File system operations
- Git operations
- External API calls
- Code execution

## Common Patterns

### 1. File Processing Commands
Commands that work with files in the current directory or specified paths.

### 2. Code Generation Commands
Commands that create boilerplate code based on patterns or specifications.

### 3. Analysis Commands
Commands that examine existing code and provide insights or suggestions.

### 4. Refactoring Commands
Commands that transform existing code according to specific patterns.

## Troubleshooting

### Command Not Found
- Check file location and naming
- Verify file permissions
- Ensure proper file extension (.md)

### Arguments Not Working
- Review argument parsing in command template
- Check for typos in parameter names
- Verify argument format matches expectations

### Inconsistent Results
- Add more specific instructions
- Include examples in the command template
- Consider edge cases and add handling for them

## Conclusion

Building effective generic slash commands requires careful planning, clear documentation, and iterative refinement. Focus on creating focused, well-documented commands that can adapt to different contexts while maintaining consistent, useful behavior.

The key to success is balancing flexibility with clarity—make commands generic enough to be reusable while specific enough to produce reliable results.