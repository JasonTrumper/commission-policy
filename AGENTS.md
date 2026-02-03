# Agent Instructions

This project contains commission policy documentation for Achieve Test Prep.

## Project Structure

```
commission-policy/
├── README.md                    # Project overview
├── AGENTS.md                    # This file
├── COMMISSION_POLICY_FLOWCHART.md   # Full policy visualized
├── SIMPLIFIED_COMMISSION_POLICY_PROPOSAL.md  # Proposed simplified version
├── Commission Policy.txt         # Source document
├── Commission Logic.txt          # Source document
└── links.txt                    # Reference links
```

## Common Tasks

### 1. Add New Policy Section

Follow the existing Mermaid pattern:

```mermaid
flowchart TB
    subgraph SECTION ["X: Section Title"]
        direction TB
        
        START["Starting point"]
        DECISION{"Decision?"]
        
        YES_PATH["Yes outcome"]
        NO_PATH["No outcome"]
        
        START --> DECISION
        DECISION -->|Yes| YES_PATH
        DECISION -->|No| NO_PATH
    end
```

### 2. Fix Mermaid Syntax Errors

Common issues:
- `{` closed with `]` instead of `}`
- Parentheses in edge labels: `|No (No Show)|` → `|No Show|`
- Special characters in node IDs

Always use:
- `{}` for diamonds (decisions)
- `[]` for rectangles (process steps)
- `()` for parentheses in edge labels

### 3. Update Simplified Proposal

When editing `SIMPLIFIED_COMMISSION_POLICY_PROPOSAL.md`:
- Keep the same Mermaid patterns
- Update the comparison table when making changes
- Update the "Key Numbers Summary Card"

### 4. Add New Diagram

1. Use `flowchart TB` (top-down)
2. Use subgraphs for logical grouping
3. Label edges clearly (`|Yes|`, `|No|`)
4. Include a legend or table for rates

### 5. Review Checklist

Before committing changes:
- [ ] All Mermaid diagrams render without errors
- [ ] No `{...]` bracket mismatches
- [ ] No parentheses in edge labels
- [ ] Consistent naming convention (CAPS_SNAKE for IDs)
- [ ] README.md updated if needed

## Diagram Style Guide

### Node Types

| Shape | Type | Example |
|-------|------|---------|
| Rectangle | Process | `START["Process step"]` |
| Diamond | Decision | `DECISION{"Yes or No?"}` |
| Subgraph | Group | `subgraph NAME ["Title"]` |

### Edge Labels

- Use `|Yes|` and `|No|` for decisions
- Use `|Text description|` for other paths
- Avoid parentheses in labels

### Naming Conventions

- Use `CAPS_SNAKE` for node IDs
- Use `Pascal Case` for subgraph names
- Keep IDs short but descriptive

## Policy Sections Reference

| Section | Topic | Complexity |
|---------|-------|------------|
| 1-2 | Eligibility, Commission Types | Low |
| 3 | Self-Generated Leads | Medium |
| 4 | Earned Conditions | Low |
| 5.1-5.9 | Adjustments | High |
| 6 | Draw | Low |
| 7 | Booker Commissions | Medium |
| 8 | Payment Timing | Low |
| 9 | Sharing | Low |
| 10 | Legal | Low |

## Troubleshooting

### Diagram Won't Render

1. Check for bracket mismatches: `{...]` should be `{}`
2. Remove parentheses from edge labels
3. Verify all backticks are balanced
4. Check for unclosed quotes

### GitHub/GitLab Rendering Issues

Some Mermaid features work in editors but not GitHub:
- Complex styling may not render
- Theme settings may be ignored
- Test in GitHub preview before committing

## Resources

- [Mermaid Syntax](https://mermaid.js.org/intro/)
- [GitHub Mermaid Support](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams)
