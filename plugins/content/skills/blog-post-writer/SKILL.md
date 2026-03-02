---
name: blog-post-writer
description: Transform brain dumps into polished blog posts in Peter Souter's voice. Use when the user says "write a blog post," "draft a post," "write about [topic]," "turn my notes into a blog post," or provides scattered ideas, talking points, or conclusions that need shaping into a cohesive narrative.
---

# Peter Souter Blog Writer

Transform unstructured brain dumps into polished blog posts that sound like Peter Souter.

## Process

### 1. Receive the Brain Dump

Accept whatever the user provides:

- Scattered thoughts and ideas
- Technical points to cover
- Code examples or commands
- Conclusions or takeaways
- Links to reference
- Random observations

Don't require organization. The mess is the input.

**Clarify constraints** (if not provided, ask about):

- Target length (see `references/post-template.md` for word count ranges)
- Target audience (if different from general developer peers)
- Whether this is a first draft or revision of existing content
- Any specific sections, topics, or angles to include or exclude

### 2. Read Voice and Tone

Load `references/voice-tone.md` as the baseline voice guide.

**Then calibrate against recent writing:**

1. Fetch `https://petersouter.xyz/archives/` to find the 2-3 most recent posts
2. Fetch and read those posts
3. Note any patterns that extend or differ from the static reference — new phrases, tone shifts, topic-specific voice adjustments

The static reference captures established patterns. The live fetch catches evolution. When they conflict, prefer the recent posts — voice is a living thing. If the site cannot be fetched, rely on the static voice guide alone.

Key characteristics (read the full reference for details and examples):

- Conversational yet substantive
- Vulnerable and authentic
- Journey-based narrative
- Mix of short and long sentences
- Specific examples and real details
- Self-aware humor

### 3. Choose a Narrative Framework

Match the content to the best framework. Read the corresponding reference file before writing.

**Quick-match shortcuts** (covers ~80% of posts):

- Personal journey → **Story Circle** (`references/story-circle.md`)
- Teaching a concept → **Progressive Disclosure** (`references/progressive-disclosure.md`)
- Bug fix story → **PAS** (`references/problem-agitation-solution.md`)
- Tool comparison → **Compare & Contrast** (`references/compare-contrast.md`)
- Something broke → **Post-mortem** (`references/post-mortem.md`)
- Technical decision → **SCQA** (`references/scqa.md`)
- Contrarian take → **The Sparkline** (`references/the-sparkline.md`)
- Absurd complexity → **Kafkaesque Labyrinth** (`references/kafkaesque-labyrinth.md`)

**Category decision tree** (for the other 20%):

- "I changed through this" → **Journey & Transformation**
- "The structure IS the story" → **Structural Techniques**
- "There's a surprise or tension" → **Tension & Contrast**
- "Making a logical case" → **Analytical & Persuasive**
- "Mood/feeling drives the piece" → **Atmospheric & Experimental**

#### Journey & Transformation

| Framework | Reference | One-liner |
|---|---|---|
| Story Circle | `references/story-circle.md` | 8-step hero's journey for personal transformation arcs |
| Three-Act | `references/three-act.md` | Classic setup/confrontation/resolution narrative spine |
| Freytag's Pyramid | `references/freytags-pyramid.md` | 5-phase dramatic arc with explicit climax mapping |
| The Metamorphosis | `references/the-metamorphosis.md` | Identity-level change — the author becomes someone different |
| Existential Awakening | `references/existential-awakening.md` | Profound realization that shifts relationship to work |

#### Structural Techniques

| Framework | Reference | One-liner |
|---|---|---|
| In Medias Res | `references/in-medias-res.md` | Start in the middle of the action, backfill context |
| Reverse Chronology | `references/reverse-chronology.md` | Tell it backwards — outcome first, origin last |
| Nested Loops | `references/nested-loops.md` | Layer stories inside each other like Russian dolls |
| The Spiral | `references/the-spiral.md` | Revisit the same concept with deeper understanding each pass |
| The Petal | `references/the-petal.md` | Multiple stories radiating from a central theme |

#### Tension & Contrast

| Framework | Reference | One-liner |
|---|---|---|
| Kishōtenketsu | `references/kishotenketsu.md` | 4-act twist without conflict — recontextualize, don't confront |
| The Sparkline | `references/the-sparkline.md` | Oscillate between "what is" and "what could be" |
| The False Start | `references/the-false-start.md` | Begin with the wrong story, then restart with truth |
| Converging Ideas | `references/converging-ideas.md` | Unrelated threads that connect to a single insight |
| Catch-22 | `references/catch-22.md` | Paradox where the rules create an impossible situation |
| The Rashomon | `references/the-rashomon.md` | Same event from multiple contradictory perspectives |

#### Analytical & Persuasive

| Framework | Reference | One-liner |
|---|---|---|
| SCQA | `references/scqa.md` | Situation-Complication-Question-Answer for logical problem-solving |
| Progressive Disclosure | `references/progressive-disclosure.md` | Simple-to-complex layering for teaching concepts |
| Compare & Contrast | `references/compare-contrast.md` | Structured evaluation of trade-offs between options |
| PAS | `references/problem-agitation-solution.md` | Punchy problem→pain→fix for short optimization stories |
| Post-mortem | `references/post-mortem.md` | Incident retrospective with timeline and lessons |
| Socratic Path | `references/socratic-path.md` | Chain of questions leading to self-discovered conclusions |

#### Atmospheric & Experimental

| Framework | Reference | One-liner |
|---|---|---|
| Comedian's Set | `references/comedians-set.md` | Setup→punchline structure for myth-busting and reframes |
| Kafkaesque Labyrinth | `references/kafkaesque-labyrinth.md` | Systemic absurdity where the villain is the system itself |
| Sisyphean Arc | `references/sisyphean-arc.md` | Find meaning in repetitive work that never ends |
| Stranger's Report | `references/strangers-report.md` | Fresh-eyes outsider perspective on normalized strangeness |
| The Waiting | `references/the-waiting.md` | Something promised that never arrives — meaning from anticipation |

Not every post maps cleanly to one framework. Hybrid approaches are fine — each framework's reference includes Combination Notes for pairing. Use a framework as a starting structure, not a straitjacket.

`voice-tone.md` and `post-template.md` are always loaded. Load only one framework reference in addition — do not preload all twenty-seven.

### 4. Outline the Post

Apply the chosen framework to the brain dump material:

- Map the user's points to the framework's steps/sections
- Identify gaps — what's missing that the framework needs?
- Decide section headers (descriptive and specific, not generic placeholders)
- Determine where code examples and specific details will land

If the content doesn't fit the framework cleanly, adapt — the framework is scaffolding, not a cage.

### 5. Write in Peter's Voice

Apply voice characteristics:

**Opening:**

- Hook with current position or recent event
- Set up tension or question
- Be direct and honest

**Body:**

- Vary paragraph length
- Use short paragraphs for emphasis
- Include specific details (tool names, commands, numbers)
- Show vulnerability where appropriate
- Use inline code formatting naturally
- Break up text with headers

**Technical content:**

- Assume reader knowledge but explain when needed
- Show actual commands and examples
- Be honest about limitations
- Use casual tool references

**Tone modulation:**

- Technical sections: clear, instructional
- Personal sections: vulnerable, reflective
- Be conversational throughout

**Ending:**

- Tie back to opening
- Forward-looking perspective
- Actionable advice
- Optimistic or thought-provoking

### 6. Review and Refine

Check the post:

- Does it sound conversational?
- Is there a clear narrative arc?
- Are technical details specific and accurate?
- Does it show vulnerability appropriately?
- Are paragraphs varied in length?
- Is humor self-aware, not forced?
- Does it end with momentum?

**AI slop check:**

1. Load `references/ai-slop-checklist.md` for the curated guidance and Peter-specific nuances
2. Fetch the current "words to watch" from Wikipedia by calling:
   ```
   https://en.wikipedia.org/w/api.php?action=parse&page=Wikipedia:Signs_of_AI_writing&prop=wikitext&format=json
   ```
   Extract the `{{tmbox}}` "Words to watch" lists and the AI vocabulary word list from the response. These evolve as AI writing patterns change — newer models drop old tells and develop new ones.
3. Scan the draft for vocabulary clusters, formulaic transitions, superficial -ing phrases, and structural tells. One hit is normal; a pattern means the LLM was writing on autopilot instead of in Peter's voice.

If the API fetch fails, fall back to the static checklist alone.

Show the post to the user for feedback and iterate.

**Revision strategy:**

- Re-read `references/voice-tone.md` before revising to recalibrate
- Focus changes on the specific feedback — don't rewrite unrelated sections
- Preserve the overall narrative structure unless the user explicitly requests restructuring
- If feedback is vague ("make it better"), ask what specifically feels off

## Output Format

Format posts using `references/post-template.md` as the structural template. This defines the frontmatter schema and file format for Peter's site.

For detailed voice do's and don'ts, see `references/voice-tone.md`.

## Example Patterns

### Opening hooks:

```markdown
One thing you should know about me is I love tinkering.
```

```markdown
One of the more fiddly parts I found when using a custom provider is how to
use it with the rest of your Terraform code.
```

```markdown
I've had to setup 3 different macbooks from scratch recently.
```

### Emphasis through structure:

```markdown
All good right? Wrong!
```

```markdown
Boom, one deadline down.
```

### Vulnerability:

```markdown
Honestly, I'm not a golang developer, I just like it for CLI apps...
```

```markdown
maybe I'm out-of-step
```

### Technical details:

```markdown
It's actually pretty important because by default Go's HTTP Client has an
unlimited timeout if not specified.
```

```markdown
After getting frustrated with the official GitHub MCP for its size for what
I was doing... I found myself making a basic one for my specific use case.
```

### Conclusions:

```markdown
Hopefully you enjoyed this walk down memory lane...hopefully you've seen
the advantages.
```

```markdown
This is an ambitious list I'll admit, and I'm sure it'll evolve throughout
the year.
```

## Bundled Resources

### References

- `references/voice-tone.md` - Complete voice and tone guide. Read this first to capture Peter's style.
- `references/post-template.md` - Output format template with frontmatter schema and structural skeleton.
- `references/ai-slop-checklist.md` - AI writing tells to scan for during review. Adapted from Wikipedia's field guide.

**Narrative frameworks** (read the one that matches the content — do not preload all twenty-seven):

Journey & Transformation:
- `references/story-circle.md` - 8-step hero's journey for personal transformation arcs
- `references/three-act.md` - Classic setup/confrontation/resolution narrative spine
- `references/freytags-pyramid.md` - 5-phase dramatic arc with explicit climax mapping
- `references/the-metamorphosis.md` - Identity-level change — the author becomes someone different
- `references/existential-awakening.md` - Profound realization that shifts relationship to work

Structural Techniques:
- `references/in-medias-res.md` - Start in the middle of the action, backfill context
- `references/reverse-chronology.md` - Tell it backwards — outcome first, origin last
- `references/nested-loops.md` - Layer stories inside each other like Russian dolls
- `references/the-spiral.md` - Revisit the same concept with deeper understanding each pass
- `references/the-petal.md` - Multiple stories radiating from a central theme

Tension & Contrast:
- `references/kishotenketsu.md` - 4-act twist without conflict — recontextualize, don't confront
- `references/the-sparkline.md` - Oscillate between "what is" and "what could be"
- `references/the-false-start.md` - Begin with the wrong story, then restart with truth
- `references/converging-ideas.md` - Unrelated threads that connect to a single insight
- `references/catch-22.md` - Paradox where the rules create an impossible situation
- `references/the-rashomon.md` - Same event from multiple contradictory perspectives

Analytical & Persuasive:
- `references/scqa.md` - Situation-Complication-Question-Answer for logical problem-solving
- `references/progressive-disclosure.md` - Simple-to-complex layering for teaching concepts
- `references/compare-contrast.md` - Structured evaluation of trade-offs between options
- `references/problem-agitation-solution.md` - Punchy problem→pain→fix for short optimization stories
- `references/post-mortem.md` - Incident retrospective with timeline and lessons
- `references/socratic-path.md` - Chain of questions leading to self-discovered conclusions

Atmospheric & Experimental:
- `references/comedians-set.md` - Setup→punchline structure for myth-busting and reframes
- `references/kafkaesque-labyrinth.md` - Systemic absurdity where the villain is the system itself
- `references/sisyphean-arc.md` - Find meaning in repetitive work that never ends
- `references/strangers-report.md` - Fresh-eyes outsider perspective on normalized strangeness
- `references/the-waiting.md` - Something promised that never arrives — meaning from anticipation

## Workflow Example

User provides brain dump:

```
thoughts on using cursor vs claude code
- cursor is in IDE, feels familiar
- but claude code is in terminal, my natural environment
- tried cursor first, felt weird leaving vim
- claude code met me where I was
- not about which is better, about workflow fit
- some devs love IDE integration
- I need terminal access
- conclusion: use what fits YOUR workflow
```

Process:

1. Read voice-tone.md
2. Choose framework — this is a personal journey, so **Compare & Contrast** with Story Circle elements
3. Outline: Current tools → Trying Cursor → Finding Claude Code → Realization
4. Write opening hook about tool debates
5. Show vulnerability about trying new things
6. Include specific terminal commands naturally
7. Conclude with "meet yourself where you are" message
8. Review for conversational tone and specific details

Sample output (opening paragraphs):

```markdown
"Which AI coding tool should I use?"

I must get asked that question weekly at this point. And honestly? I tried to answer it
the wrong way for months.

When Cursor started blowing up, I did what any curious developer would do — I installed
it and gave it a shot. It's impressive. The inline completions, the chat panel, the way
it weaves right into VS Code. I get why people love it.

But here's the thing: I'm not a VS Code person. I live in the terminal. Vim, tmux,
`rg` piped into `fzf` — that's my happy place. And every time I opened Cursor, I felt
like I was visiting someone else's apartment. Nice place, but not *mine*.

Then I found Claude Code.
```

Notice: conversational hook, specific tool names, vulnerability about trying something new, short paragraph for emphasis at the end.
