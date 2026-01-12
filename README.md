# Emil Animation Roast

Roast your animations like [Emil Kowalski](https://twitter.com/emilkowalski_). An AI command that analyzes your codebase for animation anti-patterns and delivers constructive critiques in Emil's direct, analytical voice.

Based on Emil's [animation philosophy](https://emilkowal.ski/), [animations.dev course](https://animations.dev/), and his work on [Sonner](https://sonner.emilkowal.ski/) and [Vaul](https://vaul.emilkowal.ski/).

## Installation

### With AI

Paste this in your AI tool:

> Install the emil-roast command in `~/.config/opencode/command/emil-roast.md` from https://raw.githubusercontent.com/alissonsleal/emil-animation-roast/main/command/emil-roast.md

### Manual

#### OpenCode

```bash
curl -fsSL https://raw.githubusercontent.com/alissonsleal/emil-animation-roast/main/command/emil-roast.md -o ~/.config/opencode/command/emil-roast.md
```

#### Claude Code

```bash
curl -fsSL https://raw.githubusercontent.com/alissonsleal/emil-animation-roast/main/command/emil-roast.md -o ~/.claude/commands/emil-roast.md
```

#### Gemini CLI

```bash
curl -fsSL https://raw.githubusercontent.com/alissonsleal/emil-animation-roast/main/command/emil-roast.md -o ~/.gemini/commands/emil-roast.md
```

#### Cursor

```bash
curl -fsSL https://raw.githubusercontent.com/alissonsleal/emil-animation-roast/main/command/emil-roast.md -o .cursor/commands/emil-roast.md
```

## Usage

```bash
# Roast entire codebase
/emil-roast

# Roast specific directory
/emil-roast src/components

# Roast specific file
/emil-roast src/components/Modal.tsx
```

## What Gets Roasted

| Category | What It Catches | Example Fix |
|----------|-----------------|-------------|
| **Speed** | Animations >300ms | `duration: 0.4s` -> `duration: 0.2s` |
| **Easing** | Wrong easing curves | `ease-in` -> `ease-out` for exits |
| **Frequency** | Animating frequent actions | Remove animation from keyboard nav |
| **Properties** | Animating margin/padding | Use `transform` instead |
| **Scale** | Starting from `scale(0)` | Start from `scale(0.95)` |
| **Transform Origin** | Wrong origin point | Match origin to trigger element |
| **Purpose** | Decorative animations | Remove or justify |
| **Accessibility** | Missing reduced-motion | Add `prefers-reduced-motion` query |
| **Taste** | Mismatched easing/brand | Use custom curves |
| **Keyframes** | Non-interruptible animations | Use CSS transitions |

## Example Output

```markdown
# Animation Roast Report

Analyzed: src/components
Issues found: 3 CRITICAL, 5 SHOULD FIX, 2 POLISH

---

## CRITICAL Property: Animating margin causes jank

**File**: `src/components/Sidebar.tsx`
**Line**: 47

**The Problem**:
You're animating `margin-left` which triggers full browser reflow on every frame.

**Why It's Wrong**:
Only `transform` and `opacity` are hardware-accelerated. Everything else forces
the browser to recalculate layout, causing dropped frames under load.

**The Fix**:
```tsx
// Before
transition: margin-left 0.3s ease;
margin-left: isOpen ? 0 : -240px;

// After
transition: transform 0.25s ease-out;
transform: translateX(isOpen ? 0 : -240px);
```

**Why This Works**:
`transform` runs on the GPU compositor thread, independent of main thread work.
Your animation stays smooth even when React is re-rendering.

---

## SHOULD FIX Easing: Using ease-in for UI exit

**File**: `src/components/Modal.tsx`
**Line**: 23

**The Problem**:
Your modal exit uses `ease-in`, which accelerates at the end.

**Why It's Wrong**:
"Easing can make a bad animation feel great and a great animation feel bad."
`ease-in` makes exits feel slower because the fastest part is at the end,
when users are waiting for it to finish.

**The Fix**:
```tsx
// Before
transition: opacity 0.3s ease-in;

// After
transition: opacity 0.2s ease-out;
```

**Why This Works**:
`ease-out` front-loads the movement. The element responds instantly to user
action, then settles gracefully. Feels snappy and responsive.

---

## POLISH Scale: Starting from scale(0)

**File**: `src/components/Tooltip.tsx`
**Line**: 15

**The Problem**:
Your tooltip animates from `scale(0)`, looking like it materializes from nothing.

**Why It's Wrong**:
"Nothing in the world around us disappears or appears instantly." Even a
deflated balloon has shape. `scale(0)` is unnatural.

**The Fix**:
```tsx
// Before
initial={{ scale: 0, opacity: 0 }}

// After
initial={{ scale: 0.95, opacity: 0 }}
```

**Why This Works**:
Starting from 0.95 creates a subtle "breathing" effect. The element feels like
it's always been there, just becoming visible. Elegant, not theatrical.

---

Fix these, and your animations will feel intentional, fast, and natural.
```

## Emil's 5 Pillars

The roast is based on these core principles:

1. **Purpose-Driven** - Every animation must answer "Why does this exist?"
2. **Frequency Matters** - More daily use = less animation
3. **Speed = Performance** - Under 300ms, usually 180-250ms
4. **Easing is Everything** - `ease-out` for enter/exit, never `ease-in` for UI
5. **Natural Motion** - Spring physics over linear tweens

## Credits

- Animation philosophy by [Emil Kowalski](https://emilkowal.ski/)
- This is a fan project, not affiliated with Emil

## License

MIT
