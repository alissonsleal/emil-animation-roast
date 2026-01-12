# Emil Animation Roast - AI Command + Research Repo

## OVERVIEW

AI command (slash command) that roasts animations using Emil Kowalski's philosophy. Pure markdown—no code, no build, no deps.

## STRUCTURE

```
emil-animation-roast/
├── command/
│   └── emil-roast.md      # THE COMMAND - copy to AI tool config dir
├── research/
│   ├── EMIL_PHILOSOPHY.md # 5 pillars, technical rules, voice patterns
│   ├── PRINCIPLES_MAP.md  # Decision trees, quality checklist
│   ├── ROAST_GUIDE.md     # Quick reference, roast templates
│   └── RESEARCH_COMPLETE.md
├── README.md              # Installation + usage
└── LICENSE
```

## WHERE TO LOOK

| Task | Location | Notes |
|------|----------|-------|
| Install command | `command/emil-roast.md` | Copy to `~/.config/opencode/command/`, `~/.claude/commands/`, etc. |
| Understand philosophy | `research/EMIL_PHILOSOPHY.md` | 5 pillars, 15 common mistakes, voice traits |
| Quick roast patterns | `research/ROAST_GUIDE.md` | Templates for 10 roast categories |
| Decision logic | `research/PRINCIPLES_MAP.md` | Visual decision trees |
| Add new AI tool | `README.md` | Add install section with toggle |

## CONVENTIONS

- **Markdown only** — no code files, no package.json
- **YAML frontmatter** in command file: `description:` field required
- **Research → Command pipeline**: philosophy docs inform command design
- **Installation dual-path**: "Let AI do it" prompt + manual curl

## ANTI-PATTERNS (THIS PROJECT)

- Never add code/build tooling — this is pure documentation
- Don't edit `command/emil-roast.md` without understanding `research/` context
- README install sections use `<details>` toggles — keep consistent

## UNIQUE STYLES

- **Emil's voice**: Direct, Socratic, taste-focused, never vague
- **5-part roast structure**: Identify → Explain → Cite → Fix → Why
- **Severity levels**: CRITICAL, SHOULD FIX, POLISH

## NOTES

- No tests, no CI, no build — just copy the command file
- Remote: `github.com/alissonsleal/emil-animation-roast`
- Command works with: OpenCode, Claude Code, Gemini CLI, Cursor, Codex
