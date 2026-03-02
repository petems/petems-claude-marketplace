# Blog Post Output Template

## File Format

Posts are written in Markdown (`.md`).

## Frontmatter

Every post must include YAML frontmatter at the top:

```yaml
---
title: "Post Title Here"
date: YYYY-MM-DD
description: "A 1-2 sentence summary for SEO and social sharing."
categories:
  - category1
tags:
  - tag1
  - tag2
---
```

### Required Fields

- **title** (string): The post title
- **date** (date): Publication date in `YYYY-MM-DD` format
- **tags** (string[]): Array of topic tags

### Optional Fields

- **description** (string): 1-2 sentence summary for SEO and social cards
- **categories** (string[]): Array of category names (e.g., `DevOps`, `Puppet`, `Career`)
- **slug** (string): Custom URL slug (defaults to filename if omitted)
- **draft** (boolean): Set `true` to hide from published listings
- **thumbnailImage** (string): Path or URL to thumbnail image
- **coverImage** (string): Path or URL to cover/hero image
- **metaAlignment** (string): Alignment of post meta info (e.g., `center`)

For a typical post, use `title`, `date`, `tags`, and `description`. Add other fields only when relevant.

## Target Word Counts

- **Short post**: 500-800 words (quick takes, single insights)
- **Standard post**: 1000-1500 words (most posts)
- **Long-form**: 2000+ words (deep dives, tutorials, narratives)

Default to standard unless the user specifies otherwise.

## Structural Skeleton

```markdown
---
title: ""
date: YYYY-MM-DD
description: ""
categories: []
tags: []
---

# Opening Hook

[1-2 paragraphs: Set up tension, question, or current position]

## Section 1: Context/Setup

[Establish the situation, background, or problem]

## Section 2: Journey/Discovery

[Show the process, experimentation, or narrative middle]

## Section 3: Resolution/Insight

[Present the breakthrough, solution, or realization]

## Closing

[Tie back to opening, forward-looking perspective, actionable takeaway]
```

Section headers should be descriptive and specific to the content — the names above are structural placeholders, not literal headers.
