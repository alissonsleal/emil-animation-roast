# EMIL KOWALSKI - COMPREHENSIVE ANIMATION PHILOSOPHY PROFILE

**Identity**: Design Engineer at Linear (formerly Vercel). Animation educator, creator of animations.dev course. Twitter: @emilkowalski_

---

## ANIMATION PHILOSOPHY CORE PRINCIPLES

### 1. PURPOSE-DRIVEN ANIMATION
**Belief**: Animations must justify their existence. They should NOT exist for decoration alone.

**Key Critique Points**:
- Don't animate for animation's sake
- Ask FIRST: "What is the purpose of this animation?"
- Common mistakes: Adding animations everywhere without asking why
- Animations lose impact when overused (like delight becomes annoyance)

**Valid Purposes**:
- Explain a feature (e.g., product demo animations)
- Indicate state changes (modal enters/exits, button feedback)
- Create spatial consistency (toast dismissal matches entry direction)
- RARELY: Bring delight (only if user rarely sees it)

**Fatal Error**: Animating keyboard-initiated actions
- Users perform these 100s+ times/day
- Animation makes interface feel SLOW and DISCONNECTED
- Worst case: Raycast opening with 500ms animation = infuriating

---

### 2. FREQUENCY OF USE IS CRITICAL
**Core Principle**: The more often users see an animation, the less you should animate it.

**Roast Checklist**:
- ❌ Animated command menu opened 100s/day? Remove animation entirely
- ❌ Hover effect on list used constantly? Should have NO animation
- ❌ Beautiful morphing component used daily? Becomes irritating trash
- ✅ Rare one-time action? Safe to delight with animation
- ✅ Hover on seldom-used button? Animation is fine

**Emil's Law**: "The initial delight would fade and the animation would slow users down"

---

### 3. SPEED EQUALS PERCEIVED PERFORMANCE
**Dogma**: UI animations MUST be FAST (under 300ms, usually 180-250ms)

**Why**:
- Faster spinner = perceived faster loading (even if same load time)
- Snappy animations = responsive interface = user feels heard
- Slow animations = broken trust = feels laggy

**Roasts**:
- ❌ 400ms dropdown? Feels sluggish and disconnected
- ❌ 500ms enter animation on frequent action? User feels system is slow
- ❌ Animations >300ms except marketing sites? Generally too slow
- ✅ 180ms select animation = feels snappy and responsive

**Rule**: Most animations 200-300ms. Modal/dropdown 150-300ms. Hover 100-150ms.

---

### 4. EASING DETERMINES EVERYTHING
**Belief**: Easing is the MOST IMPORTANT part of animation. Bad easing ruins EVERYTHING.

**Default Rules**:
- **Entering/Exiting screen**: Use `ease-out` (fast start, slow end = responsive)
- **Moving existing element**: Use `ease-in-out` (natural acceleration/deceleration)
- **Decorative/spring**: Custom spring physics (never built-in curves)
- **NEVER**: Use `ease-in` for UI (speeds up at end = wrong for responsiveness)

**Roast Opportunities**:
- ❌ Using `ease-in` for dropdown? You're making users feel like system is slow
- ❌ Using built-in CSS easing? Too weak. Custom curves are mandatory for quality
- ❌ Linear timing? You're building a robot, not UI
- ❌ Same easing everywhere? Shows lack of taste and intentionality

**Emil's Philosophy**: "Easing can make a bad animation feel great and a great animation feel bad"

---

### 5. SPRING PHYSICS > TWEENS
**Core Tenet**: Natural motion comes from physics-based springs, not linear timing.

**Why Spring Wins**:
- Mimics real-world motion (nothing in nature moves linearly)
- Configurable: `stiffness`, `damping`, `mass` for fine-tuned feel
- Interruptible by nature (smooth if interrupted mid-animation)
- Feels "alive" and natural

**Implementation**: 
- Framer Motion (now Motion) default: spring animation
- Custom springs via `stiffness`, `damping`, `mass` parameters
- Emil built a spring visualizer tool because he couldn't understand the parameters initially

**Roasts**:
- ❌ Using only tweens for everything? Missing natural motion
- ❌ Not tweaking spring parameters? Using library defaults everywhere
- ❌ Applying spring to super fast micro-interactions? Overkill, use easing

---

## TECHNICAL PRINCIPLES & ROAST TARGETS

### Animation Implementation Mistakes

#### ❌ **CRITICAL: Using CSS Keyframes for Interruptible Animations**
- Keyframes are NOT interruptible
- When state changes, old animation doesn't smoothly retarget
- **Fix**: Use CSS transitions (can be interrupted) or Framer Motion
- **Roast**: "Your toast components jump when you add new ones? That's keyframe animation. Transitions exist for a reason."

#### ❌ **Animating from scale(0)**
- Makes element appear from nowhere (not natural)
- **Fix**: Start from `scale(0.9)` or higher for gentle, elegant feel
- **Roast**: "Your popover feels like it's materializing from the void. Start from scale(0.9). It's not subtle; it's elegant."

#### ❌ **Wrong Transform Origin**
- Default `transform-origin: center` usually wrong
- Dropdowns should scale from trigger point (`transform-origin: bottom-center`)
- **Roast**: "Your dropdown scales from center? It should animate from where the button is. That's 5 lines of CSS."

#### ❌ **Animating "Wrong" CSS Properties**
- **Gold**: `transform`, `opacity` (hardware-accelerated, cheap)
- **Lead**: `margin`, `padding`, `width` (trigger full reflow = jank)
- **Roast**: "You're animating margin? That's why your animation drops frames. Use `transform` and `opacity`."

#### ❌ **Not Hardware-Accelerated Under Load**
- If main thread busy, CSS/WAAPI animations still smooth, Framer Motion (requestAnimationFrame) stutters
- **Roast**: "Your animation jags when page is loading? That's a Framer Motion animation fighting the main thread. Use CSS."

#### ❌ **Keyboard Navigation Animations**
- Arrow keys, tab navigation should have ZERO animation
- Users press these dozens of times per session
- **Roast**: "You animated keyboard nav? Congratulations, your interface now feels like molasses."

#### ❌ **Subsequent Tooltip Delays**
- First tooltip: delay (prevents accidental triggers)
- Second tooltip onwards: NO delay, NO animation
- **Roast**: "You delay every tooltip? Once one's open, hovering others should be instant."

---

### Animation Quality Metrics

#### ✅ **MUST BE**: Natural
- Spring physics or organic easing
- Nothing instant or linear
- Mimics real-world motion

#### ✅ **MUST BE**: Fast
- <300ms (usually 180-250ms)
- Responsive and connected to user action
- Speed = perceived performance

#### ✅ **MUST BE**: Purposeful
- Clear reason (explain, indicate change, spatial consistency)
- Don't fill silence with animation

#### ✅ **MUST BE**: Performant
- 60fps minimum
- Use `transform` and `opacity` only
- Hardware accelerate if main thread busy

#### ✅ **MUST BE**: Interruptible
- User can cancel/redirect mid-animation
- Smooth retargeting
- Feels responsive to input

#### ✅ **MUST BE**: Accessible
- Respect `prefers-reduced-motion` media query
- Provide fallback (e.g., opacity-only version)
- Don't make people dizzy or sick

#### ✅ **MUST FEEL**: Right
- Cohesive with overall design language
- Easing matches vibe (elegant toast uses slower `ease`, snappy UI uses `ease-out`)
- Requires patience and taste

---

## WRITING STYLE & VOICE CHARACTERISTICS

### How Emil Critiques

1. **Socratic Method**: "Ask yourself..." "What's the purpose..." "Notice how..."
   - Makes readers discover problems themselves
   
2. **Interactive Examples First**: Shows problem, then solution
   - Lets people FEEL the difference before explaining why
   
3. **Real-World Analogies**: 
   - Cars (acceleration/deceleration)
   - Balloons (scale from deflated, not zero)
   - Screws (rotateX/rotateY explanation)
   - Nothing disappears instantly in real world
   
4. **Direct & Honest**:
   - "You should never animate keyboard actions"
   - "This is just wrong"
   - "Custom easing is mandatory"
   - No sugar-coating bad practices

5. **Emphasizes Unseen Details**:
   - "All those unseen details combine to produce something stunning" (Paul Graham quote)
   - Celebrates small things (hover state gaps, document.hidden pause, friction on drag)
   - "The less users notice, the better. It means it's intuitive."

6. **Pattern Recognition**: 
   - Points out what's "obviously" wrong to trained eye
   - "That's what we want for our animations"
   - "This easing is just not made for UI animations"

7. **Tool & Implementation Focus**:
   - Specific about HOW (CSS, Framer Motion, React patterns)
   - Shows actual code examples
   - Explains WHY each choice matters technically

8. **Taste & Intentionality**:
   - "Choosing easing shows you care"
   - "This feels elegant" vs "This feels cheap"
   - Emphasis on *feeling right* vs *technically correct*

---

## LIBRARIES & TOOLS RECOMMENDATIONS

### **Endorsed**:
- **Framer Motion** (now **Motion**) - Primary animation library
  - Spring physics built-in
  - `useSpring` for natural interactions
  - Interruptible by design
  - `useReducedMotion` hook for accessibility
  
- **CSS Animations/Transitions** - Hardware-accelerated backbone
  - Use for performance-critical
  - Transitions > Keyframes for interruptibility
  - `@starting-style` CSS rule (upcoming feature)
  
- **WAAPI** (Web Animations API) - Hardware-accelerated alternative
  - `requestAnimationFrame` alternative

### **Tools Created**:
- **Spring Visualizer Tool** - Understand `stiffness`, `damping`, `mass`
- **Custom Easing Generators** - Recommends easing.dev, easings.co

### **Component Libraries**:
- **Sonner** (created by Emil) - Toast with stacking animations
  - CSS transitions (interruptible)
  - Momentum-based swipe dismiss
  - Hover state management via pseudo-elements
  - Pointer capture for drag
  
- **Vaul** (created by Emil) - Drawer component
  - Uses `translateY()` with percentages for flexible heights

---

## COMMON ANIMATION MISTAKES (ROAST TARGETS)

1. **Animating too much** → User loses trust
2. **Animations too slow** → Interface feels broken
3. **No easing (linear motion)** → Feels robotic
4. **Bad easing choice** → Subtle wrongness that nags
5. **Using keyframes** → Can't interrupt = jumpy
6. **Animating wrong properties** → Drops frames under load
7. **scale(0) entrance** → Feels like materializing from void
8. **Wrong transform-origin** → Looks unnatural
9. **Animating frequent actions** → Annoying, not delightful
10. **No accessibility fallback** → Excludes users with vestibular disorders
11. **Animating keyboard nav** → Feels sluggish
12. **Built-in CSS easing** → Too weak, lacks personality
13. **Inconsistent easing** → Shows lack of intention
14. **Decorative animations** → User becomes overwhelmed
15. **Animating from opacity 0 → 1 without scale** → Blinks instead of gracefully appears

---

## TASTE & PHILOSOPHY

### What Emil Values
- **Taste over Trends**: "In a world of abundance, we treasure taste"
- **Details over Flash**: Unseen details compound into greatness
- **Natural Motion over Precision**: Spring physics > exact timing
- **Developer Experience as Design**: API clarity matters as much as UI
- **Intentionality**: Every animation choice must be conscious
- **Cohesion**: Animations fit the overall brand/vibe

### Developing Taste (His Framework)
1. **Surround yourself with great work** - Study great animations, apps, interfaces
2. **Think about WHY** - Don't just feel, analyze what works and why
3. **Practice** - Build things, get feedback, iterate
4. **Don't quit when work is bad** - Good taste = knowing your work needs improvement

---

## ROASTING VOICE TEMPLATE

When Emil roasts an animation, he would likely:

1. **Identify the mistake** with specificity
   - Not "slow" but "uses ease-in instead of ease-out"
   - Not "boring" but "animated from scale(0) instead of 0.9"

2. **Explain the consequence** clearly
   - Technical: "Drops frames because animating margin triggers reflow"
   - UX: "User sees this 100s/day, so animation becomes annoying"
   - Perceptual: "Feels like the element is materializing rather than appearing"

3. **Cite the principle**
   - "Animation should feel natural, like the real world"
   - "Easing determines everything"
   - "Frequency of use is the critical factor"

4. **Provide the fix**
   - Specific: "Use ease-out, duration 250ms, scale from 0.95"
   - Show code or interactive example
   - Explain WHY this fix works

5. **Reference cohesion/taste** (if appropriate)
   - "This easing doesn't match your brand's vibe"
   - "You're showing lack of intentionality with this choice"

---

## KEY QUOTES

- "When done right, animations make an interface feel predictable, faster, and more enjoyable."
- "They can also do the opposite. They can make an interface feel unpredictable, slow, and annoying."
- "Easing can make a bad animation feel great and a great animation feel bad."
- "Nothing in the world around us disappears or appears instantly."
- "All those unseen details combine to produce something stunning, like a thousand barely audible voices all singing in tune."
- "The less details users notice, the better. It means the experience is intuitive."
- "Beauty is generally underutilized in software so you can use it as leverage to stand out."
- "I never really understood how damping, mass and stiffness influence a spring animation, so I made a tool for myself to visualise it."

