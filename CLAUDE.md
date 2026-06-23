# AI Instructions

Project documentation: [README.rst](README.rst)

## reStructuredText formatting

When editing the `README.rst` file:

- Preserve the existing document structure and section hierarchy.
- Do not change section levels unless explicitly requested.
- When adding a new section, determine its hierarchy level from the
  surrounding sections and reuse the existing structure consistently.
- Never skip section hierarchy levels.

Never use bold text (`**text**`) as a substitute for a section title.  If a
piece of content warrants a heading, create a proper section with overline
and underline adornments at the appropriate hierarchy level.  Bold is for
inline emphasis only.

Never use `.. rubric::` as a substitute for a section title.  A rubric
creates a visual heading that is excluded from the table of contents and
cannot be cross-referenced with `:ref:`.  If content warrants a heading,
use a proper section at the appropriate hierarchy level.

All section titles must use both overline and underline adornments.
Underline-only section titles are forbidden, even though they are valid
reStructuredText syntax.

Use the following adornment characters in descending hierarchy order:

1. `#`
2. `*`
3. `=`
4. `-`
5. `^`
6. `"`

Adornment lines must be exactly two characters longer than the section
title text.

Section titles must not contain leading or trailing spaces.

Use this exact layout:

```rst
#######
Title
#######
```

means:

* `Title` = 5 chars
* adornment = 7 chars

Vertical spacing rules for section titles:

* Exactly one empty line before the overline.
* Exactly one empty line after the underline.
* No empty lines between the overline, title text, and underline.

Example:

```rst
Some text.

***********
Section 1
***********

Another text.
```

After making any changes to a `.rst` file, verify formatting with:

```
python3 -m rstcheck <file.rst>
python3 -m doc8 <file.rst>
```

Both commands must exit with no errors before the edit is considered complete.

Do not rewrite, reflow, or rewrap unrelated documentation text.
Preserve existing indentation, directive formatting, list formatting,
and Sphinx cross-reference syntax unless modification is required for
correctness.

Do not normalize existing section title adornment widths to standard
reStructuredText conventions.  Preserve the project's custom formatting
rules exactly.
