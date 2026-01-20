# Simple Execution Rule

## Description

A lightweight rule for straightforward task execution. Use this when you need the AI to perform simple, well-defined tasks quickly without the overhead of a multi-phase protocol.

## When to Use

Use this skill when:
- Tasks are simple and well-defined
- Changes are localized and low-risk
- Quick iteration is more valuable than extensive planning
- The user explicitly requests fast execution
- Working on small bug fixes, formatting changes, or minor refactors

## When NOT to Use

Avoid this skill when:
- Making changes to critical systems
- Working on complex multi-file refactors
- Changes require careful planning and review
- The scope of work is unclear or ambiguous

---

## Core Principles

### 1. Understand First, Then Act

Before executing any task:
- Read and understand the relevant code
- Identify the scope of changes needed
- Confirm your understanding with the user if unclear

### 2. Make Minimal Changes

- Only modify what is necessary to complete the task
- Avoid "improving" unrelated code
- Keep changes focused and reversible

### 3. Verify After Execution

- Confirm the change works as expected
- Check for obvious errors or regressions
- Report completion status clearly

---

## Execution Flow

```
1. UNDERSTAND → Read task requirements and relevant code
2. CONFIRM → Brief confirmation of approach (optional for trivial tasks)
3. EXECUTE → Make the necessary changes
4. VERIFY → Check results and report status
```

---

## Response Format

### For Simple Tasks

```
✓ Task: [Brief description of what was done]
  Files modified: [file1.ts, file2.ts]
  Changes: [Brief summary]
```

### For Tasks Requiring Confirmation

```
Understanding: [What you understand the task to be]
Approach: [How you plan to accomplish it]
Proceed? [Yes/No or await user confirmation]
```

---

## Guidelines

### DO:
- Execute quickly for well-defined tasks
- Ask for clarification when requirements are ambiguous
- Report any unexpected issues encountered
- Keep the user informed of progress

### DON'T:
- Make assumptions about unclear requirements
- Add features not explicitly requested
- Refactor working code without permission
- Skip verification of changes

---

## Command Shortcuts

The user can use these shortcuts to control execution:

| Command | Effect |
|---------|--------|
| `just do it` | Execute immediately without confirmation |
| `explain first` | Explain approach before executing |
| `dry run` | Show what would be changed without making changes |
| `rollback` | Revert the last change if possible |

---

## Error Handling

If an error occurs during execution:

1. **Stop** - Don't continue making changes
2. **Report** - Clearly describe what went wrong
3. **Suggest** - Offer potential solutions
4. **Wait** - Get user approval before proceeding

---

## Examples

### Example 1: Simple Rename

**User**: Rename `getUserData` to `fetchUserProfile` in `user.ts`

**Response**:
```
✓ Task: Renamed function getUserData → fetchUserProfile
  Files modified: user.ts
  Changes: 
  - Renamed function definition
  - Updated all internal references (3 occurrences)
```

### Example 2: Bug Fix

**User**: Fix the null check in `parseConfig`

**Response**:
```
Understanding: The parseConfig function is missing a null check 
that causes a crash when config is undefined.

Approach: Add early return with default value when config is null/undefined.

Proceed?
```

### Example 3: Format Change

**User**: Convert tabs to spaces in `main.py`

**Response**:
```
✓ Task: Converted indentation tabs → 4 spaces
  Files modified: main.py
  Changes: Replaced all tab characters with 4-space indentation (47 lines affected)
```

---

## Integration with Other Rules

This rule can be combined with other rules:
- Use **RIPER-5** for complex tasks requiring planning
- Use **Simple Execution** for quick, low-risk changes
- The user can switch between them as needed

---

*This rule prioritizes speed and simplicity for straightforward tasks while maintaining code quality and user control.*
