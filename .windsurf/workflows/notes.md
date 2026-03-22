---
description: Generate educational content for course notes based on file path and raw content
---

# Notes Command Workflow

This workflow will generate educational content for Maestro AAS course notes following the established format and style patterns.

## Usage:
Use the `/notes <file_path> <raw_content>` slash command where:
- `<file_path>` - The target file path where the content should be created
- `<raw_content>` - Raw content or topic description to work from

## Steps:

1. **Parse parameters** - Extract file path and raw content from command
2. **Create directory structure** - Ensure target directory exists
3. **Generate educational content** - Transform raw content into structured educational material following Maestro AAS format:
   - Clear learning objectives
   - Step-by-step explanations
   - Practical examples and exercises
   - Challenge problems
   - Review sections
4. **Replace file content** - Write the formatted content to the specified file path (replacing existing content if file exists)
5. **Auto-commit changes** - Commit the new content to Git

## Content Structure:
The generated notes will follow this pattern:
- **Introduction** - Clear topic overview and learning goals
- **Core Concepts** - Detailed explanations with examples
- **Practical Applications** - Real-world usage scenarios
- **Exercises** - Hands-on practice problems
- **Challenge** - Comprehensive problem to test understanding
- **Review** - Summary of key points

## Examples:
- `/notes "Term 2/CS102/Week 4 - Recursion/01 - Introduction to recursion.md" "explain recursion basics with examples"`
- `/notes "Term 1/PY101/Week 4 - File Handling/01 - Reading files.md" "how to open and read files in Python"`

## Notes:
- Automatically creates directory structure if needed
- Follows established Maestro AAS formatting conventions
- Uses markdown for proper structure and readability
- Includes practical coding examples where applicable
