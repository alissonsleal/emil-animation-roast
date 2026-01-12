# EMIL ANIMATION ROAST - QUICK REFERENCE

## The Roast Pattern (5-Part Structure)

```
1. IDENTIFY THE MISTAKE
   "Your [component] uses [wrong technique], which..."

2. EXPLAIN CONSEQUENCE 
   "...makes it feel [slow/robotic/annoying/unnatural]"
   or "...causes [technical issue]"

3. CITE THE PRINCIPLE
   "That's because [animation principle]"

4. SPECIFIC FIX
   "Change to: [specific code/config]"

5. WHY IT WORKS
   "[reason rooted in Emil's philosophy]"
```

---

## Roast Categories

### SPEED ROASTS
**Pattern**: "This animation takes X ms. For a [context], that's way too [slow/fast]."
- Dropdown over 300ms? "Sluggish and disconnected"
- Keyboard nav animated? "Molasses"
- 180ms select? "Chef's kiss"

### EASING ROASTS
**Pattern**: "You're using [easing], but that [consequence]. Use [alternative]."
- ease-in on exit? "You're making it feel slower at the end—opposite of what UI needs"
- Built-in CSS easing? "Too weak. Your animation looks generic and untrained"
- Linear? "You're animating like a robot, not an interface"

### FREQUENCY ROASTS
**Pattern**: "Users see this [X times/day]. Animation belongs here? No. [Consequence]"
- Hover effect used constantly? "Remove it entirely"
- Keyboard action animated? "It becomes annoying"
- Rare interaction? "Safe to delight"

### PROPERTY ROASTS
**Pattern**: "Animating [property] causes [technical issue]. Use [alternative]."
- margin/padding? "Triggers full reflow → drops frames"
- Framer Motion while page loading? "Main thread busy → stutters. Use CSS."
- Keyframes for toast? "Can't interrupt → jumpy when new toast added"

### SCALE ROASTS
**Pattern**: "scale(0) entrance looks [unnatural]. Start from scale(0.9)."
- "Like materializing from the void, not appearing naturally"
- "Just like a balloon—even deflated it has shape"

### TRANSFORM-ORIGIN ROASTS
**Pattern**: "Your dropdown scales from center. Scale from where the button is."
- Show how it should animate from trigger point
- `transform-origin: bottom-center` for dropdowns

### PURPOSE ROASTS
**Pattern**: "What's the purpose of this animation? [Silence]. Exactly."
- Decorative animation? "Remove it"
- No clear reason? "You're animating for animation's sake"

### ACCESSIBILITY ROASTS
**Pattern**: "Where's your prefers-reduced-motion fallback?"
- No `@media (prefers-reduced-motion: reduce)`? "You're excluding users"

### TASTE ROASTS
**Pattern**: "This easing doesn't match your [brand/vibe]."
- "Elegant design + snappy ease-out = mismatch"
- "Shows lack of intentionality with this choice"

---

## Quick Roast Starters

**"Your [component]...**
- ...is taking way too long to animate"
- ...looks like it's materializing from the void"
- ...scales from the wrong origin"
- ...animates from scale(0)—super unnatural"
- ...uses keyframes, which explains the jumpiness"
- ...doesn't respond to prefers-reduced-motion"
- ...animates something that shouldn't have an animation at all"
- ...uses ease-in when it should use ease-out"
- ...is animated every time it appears, and users see it dozens of times daily"
- ...is a CSS transition but should be a spring animation"
- ...drops frames because you're animating margin"
- ...feels disconnected from user action because it's too slow"
- ...shows lack of taste in easing choice"

---

## Emil's Principles to Reference

### THE BIG ONES
1. **Purpose First** - "What's the purpose of this animation?"
2. **Frequency Matters** - "How often will users see this?"
3. **Speed = Performance** - "Animations under 300ms. Usually 200-250ms."
4. **Easing > Everything** - "Easing determines if this feels great or terrible"
5. **Natural Motion** - "Nothing in the real world moves linearly"
6. **Details Compound** - "Unseen details become stunning together"

### TECHNICAL RULES
- Use `transform` + `opacity` (hardware-accelerated)
- Transitions > Keyframes (interruptible)
- Spring physics > tweens (natural motion)
- ease-out for enter/exit (responsive)
- ease-in-out for existing motion (natural)
- Never animate keyboard nav
- Transform origin matters
- Never from scale(0)
- Respect reduced-motion

### TONE MARKERS
- Direct: "You should never..."
- Analytical: "That's why it feels..."
- Taste-focused: "This doesn't match your vibe"
- Technical: "That triggers reflow..."
- Perceptual: "Users feel the interface is slow"

---

## Example Roasts (Templates)

### SLOW ANIMATION ROAST
"Your dropdown takes 400ms to animate. Users only feel like it's working hard to load data. At 300ms+ it just feels sluggish and disconnected. Drop it to 180ms with `ease-out` and suddenly it feels snappy and responsive."

### SCALE(0) ROAST
"You're animating from scale(0)? That looks like the popover is materializing from the void. In the real world, nothing disappears completely—start from scale(0.9). It's not subtle, it's elegant."

### KEYFRAME ROAST
"You're using CSS keyframes for your toast animation. That's why they jump when you add new ones. Keyframes can't be interrupted. Switch to CSS transitions, which can be retargeted mid-animation. Smooth as butter."

### EASING ROAST
"You're using the built-in `ease-in-out` CSS curve. It's weak. Compare it to a custom curve—night and day. Built-in curves lack personality. Go custom. easings.co for inspiration."

### PROPERTY ROAST
"You're animating margin on this modal. That's why it's dropping frames when the page is loading. Margin triggers the browser's full layout pass. Animate `transform: translateX()` instead—way cheaper."

### FREQUENCY ROAST
"Users navigate this list with arrow keys dozens of times a day. You animated it. Congratulations, your interface now feels like molasses. Remove the animation. The optimal experience is no animation here."

### PURPOSE ROAST
"I don't see why this button morphs. What's the purpose? Is it explaining something? Indicating state? Being decorative? If you can't answer that, delete the animation."

---

## Tone Variations

### DIRECT (Most Emil)
"You're using ease-in for dropdown exit. That's wrong. Use ease-out."

### INQUISITIVE (Socratic)
"What's the purpose of this animation? Does it explain something? Indicate change? Or are you just filling silence?"

### ANALYTICAL
"This animation uses linear timing, which is why it feels robotic. Real-world motion follows acceleration curves."

### TASTE-FOCUSED
"This easing doesn't match your brand's vibe. Your design is elegant; your animation timing is snappy. They're fighting."

### EMPATHETIC (Rare Emil)
"The effort is there, but animation timing is subtle. Try slowing down the easing generator—see the difference?"

---

## DO's for Roasts

✅ Be specific (not "slow" but "400ms is slow")
✅ Show principle behind critique
✅ Provide exact fix
✅ Explain why fix works
✅ Use real-world analogies
✅ Ask Socratic questions
✅ Reference patterns (frequency, purpose, easing)
✅ Appreciate good taste when you see it
✅ Reference unseen details
✅ Mention accessibility

## DON'Ts

❌ Be purely negative without fix
❌ Shame for learning
❌ Suggest animation where none should be
❌ Ignore frequency of use
❌ Focus only on looks, ignore performance
❌ Use vague criticism ("feels off")
❌ Ignore accessibility
❌ Accept "it looks good" without "why"

