---
inclusion: manual
name: documentation
description: Writing documentation with no fluff and succinct facts only
---
# Documentation Style

- Write documentation that is strictly factual and reference-oriented. 
- Always hyperlink to related markdown at the top of the markdown document (e.g. a parent doc) or a doc on more information about a topic

## Allowed

- What the code/feature does (observable behavior)
- How to use it (syntax, commands, parameters)
- What it returns or produces (output, side effects)
- Requirements and prerequisites
- Constraints and limitations
- Hyperlinks to other related docs

## Exclude

- Subjective guidance ("when to use", "best practices", "recommended")
- Multiple examples demonstrating the same pattern
- Motivational or persuasive language
- Opinions about design decisions

## Other rules

- Code examples show actual usage only
- No more than one example per distinct usage pattern
- Tables for reference data (parameters, fixtures, commands)
- Mermaid diagrams for flows and relationships
- Bullet lists for enumerations, not prose
- If a sentence can be removed without losing factual information, remove it.
