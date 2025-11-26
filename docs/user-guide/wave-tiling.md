# Wave Tiling Options

The **Wave Tiling** parameter offers six distinct animation patterns, each creating a different visual effect. This page provides detailed information about each pattern to help you choose the right one for your needs.

## Overview

Wave Tiling controls the direction and pattern of the shimmer wave movement across your object's surface. Each pattern creates a unique visual style suitable for different scenarios.

---

## Pattern Details

### 1. Diagonal 1 (Default)


**Description:** Classic diagonal sweep across the surface from one side to another.

**Visual Characteristics:**
- Smooth, consistent diagonal movement
- Even coverage across the surface
- Predictable, professional appearance
- Works well on both flat and curved surfaces

**Best For:**
- General-purpose shimmer effects
- UI elements (buttons, panels, cards)
- Flat surfaces and planes
- Item highlights in inventory
- First-time setup (good default choice)

**Use Cases:**
```yaml
# Standard collectible item
Wave Tiling: Diagonal 1
Speed: 2.0
Highlight Color: Gold

# UI button hover effect
Wave Tiling: Diagonal 1
Speed: 1.5
Highlight Color: White
```

---

### 2. Diagonal 2



**Description:** Reverse diagonal sweep from one side to another. A bit Different from Diagonal 1

**Visual Characteristics:**
- Opposite direction to Diagonal 1
- Same smooth, professional appearance
- Creates variety when used alongside Diagonal 1
- Mirror effect for paired objects

**Best For:**
- Creating visual variety among similar objects
- Paired or mirrored objects
- Alternating patterns on grouped items
- Secondary or opposite state indicators

**Use Cases:**
```yaml
# Alternate collectible type
Wave Tiling: Diagonal 2
Speed: 2.0
Highlight Color: Silver

# Left/Right UI panel differentiation
Wave Tiling: Diagonal 2 (right panel)
Wave Tiling: Diagonal 1 (left panel)
```

---

### 3. Diagonal 3

<div style="text-align: center; font-size: 2em;">⤢</div>

**Description:** Alternative diagonal pattern with unique sweep characteristics at a different angle.

**Visual Characteristics:**
- Distinct angle from Diagonal 1 and 2
- Unique visual signature
- Less common, more distinctive
- Adds subtle variation

**Best For:**
- Creating visual variety without drastic changes
- Differentiated objects within same category
- Special or unique items
- Custom branding/style requirements

**Use Cases:**
```yaml
# Rare item tier
Wave Tiling: Diagonal 3
Speed: 1.5
Highlight Color: Purple

# Special event items
Wave Tiling: Diagonal 3
Speed: 2.2
Highlight Color: Pink
```

**When to Choose:**
- You've already used Diagonal 1 and 2
- Need a third tier of differentiation
- Want something slightly different from standard

---

### 4. Bottom To Top

<div style="text-align: center; font-size: 2em;">⬆️</div>

**Description:** Vertical scanning effect that sweeps from bottom to top.

**Visual Characteristics:**
- Strong vertical movement
- Scanning/analyzing appearance
- Emphasizes height and vertical dimension
- Tech/sci-fi feeling

**Best For:**
- Tall objects and vertical structures
- Character models (full-body effects)
- Vertical UI elements (progress bars, health bars)
- Scanning and analysis effects
- Elevator or lift UI
- Tower defense highlights

**Use Cases:**
```yaml
# Character power-up activation
Wave Tiling: Bottom To Top
Speed: 3.0
Highlight Color: Cyan
Emission: 0.7

# Sci-fi door scan
Wave Tiling: Bottom To Top
Speed: 4.0
Highlight Color: Blue
Emission: 0.5

# Vertical progress indicator
Wave Tiling: Bottom To Top
Speed: 1.5
Highlight Color: Green
```

**Design Tips:**
- Perfect for "powering up" animations
- Great for vertical reveal effects
- Pairs well with blue/cyan colors for tech aesthetic
- Use faster speeds for urgent scanning effects

---

### 5. Back To Front

<div style="text-align: center; font-size: 2em;">→</div>

**Description:** Wave travels from back to front in world space, emphasizing depth.

**Visual Characteristics:**
- Creates depth perception
- 3D spatial awareness
- Camera-relative effect
- Volumetric feeling

**Best For:**
- 3D game objects with significant depth
- Objects viewed from a fixed camera angle
- Emphasizing object volume and form
- Creating depth hierarchy
- Foreground/background separation

**Use Cases:**
```yaml
# 3D item showcase
Wave Tiling: Back To Front
Speed: 2.0
Highlight Color: White
Emission: 0.4

# Environmental object highlight
Wave Tiling: Back To Front
Speed: 1.8
Highlight Color: Yellow
```

**When to Choose:**
- Your objects have noticeable depth (not flat)
- Camera position is relatively fixed
- You want to emphasize 3D form
- Creating a "reveal" effect

**Camera Considerations:**
- Effect appearance depends on camera angle
- Works best with consistent camera positioning
- May look different from various viewpoints

---

### 6. Pulse

<div style="text-align: center; font-size: 2em;">⊙</div>

**Description:** Pulsing effect that emanates on full body like heart beat.

**Visual Characteristics:**
- Full glow on specific time intervel
- Attention-grabbing
- Rhythmic, breathing appearance
- Stronger visual presence than directional patterns

**Best For:**
- Quest markers and objectives
- Important pickups or collectibles
- Alert and warning states
- Magical/mystical objects
- Energy sources or power cores
- Beacon-like highlights
- Breathing/living effects

**Use Cases:**
```yaml
# Quest objective marker
Wave Tiling: Pulse
Speed: 2.5
Highlight Color: Bright Yellow
Emission: 0.8

# Magical artifact
Wave Tiling: Pulse
Speed: 1.5
Highlight Color: Purple
Emission: 0.6

# Alert state
Wave Tiling: Pulse
Speed: 4.0
Highlight Color: Red
Emission: 1.0

# Health pickup
Wave Tiling: Pulse
Speed: 2.0
Highlight Color: Green
Emission: 0.5
```

**Design Considerations:**
- Most attention-grabbing pattern
- Use sparingly to maintain impact
- Perfect for "most important" objects
- Can feel overwhelming if overused

**Speed Guidelines for Pulse:**
- Slow (1.0-1.5): Calm, mystical, ambient
- Medium (2.0-2.5): Standard attention-grabbing
- Fast (3.0-4.0): Urgent, warning, critical

!!! warning "Use Sparingly"
    The Pulse effect is very noticeable. Avoid using it on too many objects simultaneously to prevent visual fatigue.

---

## Combining with Other Properties

### Pattern + Speed Combinations

Each pattern responds differently to speed changes:

**Diagonal Patterns (1, 2, 3):**
- Slow speed = elegant, premium feel
- Fast speed = energetic, action-oriented

**Bottom To Top:**
- Slow speed = deliberate scanning
- Fast speed = urgent analysis/warning

**Back To Front:**
- Slow speed = revealing, mysterious
- Fast speed = quick highlight sweep

**Pulse:**
- Slow speed = breathing, ambient
- Fast speed = alert, critical


## Performance Notes

All wave tiling patterns have equivalent performance characteristics:

- ✅ No performance difference between patterns
- ✅ Pattern selection is purely aesthetic
- ✅ Switch patterns freely without performance concern
- ✅ Can be changed at runtime without cost

---

## Testing and Iteration

### Recommended Workflow

1. **Start with Diagonal 1** for baseline
2. **Test in Play Mode** to see animation
3. **Try Pulse** if more attention is needed
4. **Experiment with others** for variety
5. **Consider context** (object type, importance)
6. **Test with color and speed** combinations
7. **Validate with playtesters** for clarity

### A/B Testing

When unsure between patterns:

- Test both with representative players
- Consider readability and clarity
- Evaluate attention-grabbing effectiveness
- Check consistency with game's visual language

---
