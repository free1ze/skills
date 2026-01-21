---
name: markdown-style
description: Google Markdown style guide principles for creating clean, readable, and maintainable documentation.
---

# Markdown Style Guide

A skill based on Google's [Markdown Style Guide](https://google.github.io/styleguide/docguide/style.html) for creating clean, readable, and maintainable documentation.

## Core Principles

1. **Source text is readable and portable** - Plain text should be easy to read even without rendering
2. **Maintainable over time** - Consistent style across the codebase
3. **Simple and easy to remember** - Don't overcomplicate the syntax

---

## Document Structure

### Standard Layout

```markdown
# Document Title

Short introduction (1-3 sentences providing high-level overview).

[TOC]

## Topic

Content.

## See also

* https://link-to-more-info
```

### Key Components

- **H1 Title**: Use one H1 as document title (ideally matching filename)
- **Introduction**: Brief 1-3 sentence overview before TOC
- **[TOC]**: Place after introduction, before first H2
- **H2+ Sections**: All subsequent headings start from level 2
- **See Also**: Put additional resources at bottom

---

## Headings

### DO:
- Use ATX-style headings (`#` syntax)
- Add spacing after `#` and newlines before/after
- Use unique, complete names for each heading
- Use single H1 heading per document
- Follow sentence case for titles

```markdown
## Heading 2

Content here.

## Another Heading

More content.
```

### DON'T:
- Use underline-style headings (`===` or `---`)
- Omit spacing around headings
- Reuse heading names (breaks anchor links)

```markdown
Heading
=======  ❌ DON'T DO THIS
```

---

## Lists

### Numbered Lists

**For long lists** (use lazy numbering):
```markdown
1.  Foo.
1.  Bar.
    1.  Nested item.
    1.  Another nested.
1.  Baz.
```

**For short lists** (use actual numbers):
```markdown
1.  Foo.
2.  Bar.
3.  Baz.
```

### Nested Lists

Use **4-space indent** for both numbered and bulleted lists:

```markdown
*   Use 3 spaces after bullet, text indented 4 spaces.
    Wrapped text uses 4-space indent.
    1.  Use 2 spaces after number.
        Wrapped text in nested list needs 8-space indent.
    2.  Looks nice, doesn't it?
*   Back to bulleted list.
```

---

## Code

### Inline Code

Use backticks for inline code, field names, commands:

```markdown
Run `npm install` to install dependencies.
Check the `status` field in the response.
```

### Code Blocks

Always use **fenced code blocks** with language declaration:

````markdown
```python
def hello_world():
    print("Hello, World!")
```
````

**DON'T** use indented code blocks:
```markdown
    # This is harder to read  ❌
    def foo():
        pass
```

### Escape Newlines in Commands

Use backslash for long commands:

```bash
$ bazel run :target -- --flag --foo=longvalue \
  --bar=anothervalue
```

### Nest Code Blocks in Lists

Indent to match list level:

````markdown
*   Bullet point.

    ```python
    code_here = True
    ```

*   Next bullet.
````

---

## Links

### DO:
- Use explicit paths for internal links
- Write informative link titles (not "here" or "link")
- Use reference links for long URLs or repeated links
- Shorten links wherever possible

```markdown
See the [installation guide](./docs/install.md) for setup instructions.

Check the [API documentation][api-docs] for more details.

[api-docs]: https://example.com/very/long/url/to/api/documentation
```

### DON'T:
- Use relative paths with `../` unless necessary
- Use uninformative link text
- Duplicate long URLs inline

```markdown
See [here](link.md) for more info.  ❌
Click [link](http://...) to continue.  ❌
```

### Reference Links

Place reference definitions **after first use**, before next heading:

```markdown
## Section

Some text with a [reference link][ref].

More text with the same [reference link][ref].

[ref]: https://example.com/long/url

## Next Section
```

---

## Character Line Limit

### 80 Characters

Follow 80-character line limit for:
- Regular text
- List items
- Paragraphs

### Exceptions

These can exceed 80 characters:
- Links
- Tables
- Headings
- Code blocks

```markdown
*   See the
    [documentation](https://very-long-url.example.com/path/to/docs).
    and continue reading.
```

---

## Formatting Rules

### Trailing Whitespace

**DON'T** use trailing spaces for line breaks. Use backslash instead:

```markdown
For some reason I need a break here,\
though it's probably not necessary.
```

### Spacing

- Add newlines before and after headings
- Add newlines before and after code blocks
- Use consistent spacing in lists

---

## Tables

### When to Use Tables

**Use tables for:**
- Tabular data that needs quick scanning
- Many parallel items with distinct attributes
- Uniform data distribution

**DON'T use tables for:**
- Data that works better as lists
- Rambling prose content
- Few rows with many columns

### Table Best Practices

- Keep cell content short
- Use reference links to avoid long URLs
- Ensure data distribution is balanced

```markdown
Transport   | Favored by | Advantages
----------- | ---------- | --------------------------
Swallow     | Coconuts   | [Fast][speed]
Bicycle     | Cyclists   | [Weatherproof][weather]

[speed]: https://example.com/speed
[weather]: https://example.com/weather
```

---

## Best Practices Summary

### DO:
✓ Use ATX-style headings (`#` syntax)  
✓ Declare language in code blocks  
✓ Write informative link titles  
✓ Use 4-space indent for nested lists  
✓ Follow 80-character line limit  
✓ Add spacing around headings/code blocks  
✓ Use reference links for long/repeated URLs  
✓ Prefer Markdown over HTML  

### DON'T:
✗ Use underline headings (`===`)  
✗ Use indented code blocks  
✗ Write "click here" or "link" as link text  
✗ Use trailing whitespace for breaks  
✗ Exceed line limits (except links/tables)  
✗ Reuse heading names  
✗ Use tables for list-appropriate content  
✗ Add HTML when Markdown suffices  

---

## When to Apply This Skill

Use this skill when:
- Creating or editing Markdown documentation
- Writing README files
- Documenting code or APIs
- Creating technical guides or tutorials
- Maintaining documentation consistency

---

## Reference

Based on: [Google Markdown Style Guide](https://google.github.io/styleguide/docguide/style.html)

*This skill helps create documentation that is readable, maintainable, and consistent across projects.*
