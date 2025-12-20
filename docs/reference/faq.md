# Frequently Asked Questions

Common questions and answers about Shimmer Effect Highlight.

## General Questions

### What is Shimmer Effect Highlight?
Shimmer FX | Pickable Object Highlight | Shine FX
       is a Unity shader-based asset that adds animated shimmer and highlight effects to 3D objects. It's perfect for highlighting important items, creating magical effects, or adding visual polish to your game.

### What Unity version do I need?

**Minimum:** Unity 2021.3 LTS  
**Recommended:** Unity 2022.3 LTS or newer

### What render pipeline is required?

The asset requires **Universal Render Pipeline (URP)**. It is not compatible with Built-in RP or HDRP without conversion.

### Can I use this with the Built-in Render Pipeline?

No, the shader is specifically designed for URP. Converting to Built-in RP would require recreating the shader, which is not officially supported.

### Can I use this with HDRP?

Not directly. The shader would need to be rebuilt for HDRP. Consider this a URP-only asset.

---

## Installation & Setup

### Where are the asset files located after import?

All files are imported to: `Assets/GameReadyTools/Shimmer Effect/`

### Why is my material appearing pink/magenta?

This typically means:
1. Your project is not using Universal Render Pipeline
2. Shader Graph package is not installed
3. The shader failed to compile

**Solution:** 
- Verify URP is set up (Edit > Project Settings > Graphics)
- Check Shader Graph is installed (Window > Package Manager)
- Try reimporting the asset

### Do I need to install anything else?

The following packages should be installed (usually automatic with URP):
- Universal RP
- Shader Graph

Post-processing is included with URP but must be enabled in your scene for full bloom effects.

### How do I enable post-processing/bloom?

1. Add a Global Volume to your scene: **GameObject > Volume > Global Volume**
2. Create a new Volume Profile or use the included one
3. Add **Bloom** override and enable it
4. Adjust intensity (0.3-0.5 recommended)

---

## Usage Questions

### How do I apply the shimmer effect to my object?

1. Select your 3D object in the Hierarchy
2. Find the Mesh Renderer component
3. Drag `Shimmer_Effect_Highlight.mat` into the Materials slot

Or create your own material using the Shimmer shader.

### Why don't I see the shimmer animation in the Scene view?

The shimmer effect is **runtime-only** and only animates in **Play Mode**. This is because it uses time-based animation which Unity's Scene view doesn't update.

### Can I control the shimmer effect from C# scripts?

Yes! All properties can be controlled via scripts:

```csharp
Material shimmer = GetComponent<Renderer>().material;
shimmer.SetColor("_HighlightColor", Color.yellow);
shimmer.SetFloat("_Speed", 2.5f);
shimmer.SetFloat("_Emission", 0.6f);
```

### How do I change the shimmer color?

Select the material and change the **Highlight Color** property in the Inspector. For scripts, use:
```csharp
material.SetColor("_HighlightColor", yourColor);
```

### Can I use this on UI elements?

The shader is designed for 3D objects with a Mesh Renderer. For UI (Canvas), you would need to use it on 3D objects positioned in world space or create a UI-specific version.

### Does it work with transparent objects?

Yes, you can adjust the **Alpha** slider to control transparency. However, the shader is optimized for opaque objects. For best transparency results, you may need to adjust the render queue.

---

## Performance Questions

### How many shimmer objects can I have in my scene?

**General Guidelines:**
- **Mobile**: 10-20 visible simultaneously
- **Desktop**: 30-50 visible simultaneously  
- **High-end**: 50+ with proper LOD and culling

Performance depends on:
- Target platform
- Screen resolution
- Other effects in your scene
- Whether bloom is enabled

### Does the shimmer effect impact performance?

The shader itself is well-optimized. The main performance factors are:
1. Number of visible objects using the effect
2. Bloom post-processing (if enabled)
3. Emission values (higher = more bloom cost)

### How can I optimize performance?

- Implement distance-based culling
- Use Material Property Blocks instead of instances
- Reduce emission values
- Disable shimmer on distant objects
- Use LOD system
- See [Best Practices](../examples/best-practices.md) for detailed optimization

### Does it work on mobile?

Yes! Follow mobile optimization guidelines:
- Limit to 10-15 visible objects
- Keep emission below 0.5
- Consider disabling bloom on low-end devices
- Test on actual devices

---

## Visual/Effect Questions

### Which wave pattern should I use?

- **Diagonal 1**: Best for general use, UI elements
- **Pulse**: Most attention-grabbing, use for important items
- **Bottom To Top**: Great for tall objects, scanning effects
- **Back To Front**: Emphasizes 3D depth
- **Diagonal 2/3**: Variety and differentiation

See [Wave Tiling Options](../user-guide/wave-tiling.md) for detailed comparisons.

### Why is my shimmer barely visible?

Try these solutions:
- Increase **Emission** value
- Choose a brighter **Highlight Color**
- Enable **Bloom** post-processing
- Increase contrast between Base Color and Highlight Color
- Increase **Speed** for more movement

### Why is my shimmer effect too intense/distracting?

Reduce the effect:
- Lower **Emission** value
- Decrease **Speed**
- Switch from **Pulse** to **Diagonal** patterns
- Choose less bright colors
- Reduce **Bloom Intensity** in post-processing

### Can I make the shimmer pulse instead of sweep?

Yes! Change the **Wave Tiling** property to **Pulse**.

### How do I make the effect glow?

1. Increase the **Emission** value (try 0.5-1.0)
2. Enable **Bloom** post-processing in your scene
3. Adjust bloom intensity to taste

Higher emission + bloom = stronger glow effect.

### Can I use multiple colors on one object?

Not directly with a single material. You would need:
- Multiple materials on sub-meshes
- Or a custom shader modification to support multiple highlight colors

---

## Textures & Materials

### Can I use custom textures?

Yes! The shader supports:
- **Base Map**: Color/albedo texture
- **Normal Map**: Surface detail/bumps
- **Smoothness Map**: Glossiness variation
- **Metallic Map**: Metallic vs non-metallic areas

### Do I need to use textures?

No. The shader works perfectly with solid colors and no textures. Textures are optional for added detail.

### How do I enable Normal/Smoothness/Metallic maps?

Each map type has an "On/Off" toggle in the material properties. Set it to "On", then assign your texture to the corresponding slot.

### What format should my textures be?

- **Base Map**: Standard RGB texture
- **Normal Map**: Must be imported as "Normal Map" in Unity
- **Smoothness Map**: Grayscale (R channel or alpha)
- **Metallic Map**: Grayscale

### Why isn't my Normal Map working?

Ensure the texture import settings have **Texture Type** set to **Normal Map**. Select the texture in Project view and check the Inspector.

---

## Troubleshooting

### The Demo Scene won't open

**Possible causes:**
1. URP not set up in project
2. Missing packages
3. Incompatible Unity version

**Solution:**
- Ensure URP is configured
- Check Package Manager for required packages
- Use Unity 2021.3 or newer

### Material looks different in Play Mode vs Scene View

This is expected. The **shimmer animation only plays in Play Mode**. The static appearance in Scene View is normal.

### Objects are too bright/glowing too much

1. Reduce **Emission** value in material
2. Lower **Bloom Intensity** in Volume Profile
3. Check if multiple emissive effects are stacking

### Performance is poor

See the [Performance Optimization](../examples/best-practices.md#performance-optimization) section in Best Practices for detailed solutions.

### Shimmer direction looks wrong

- Try different **Wave Tiling** options
- Ensure object's UV mapping is correct
- For **Back To Front** pattern, verify camera angle

### Effect doesn't match the Demo Scene

1. Check if Bloom is enabled in your scene
2. Compare all material property values
3. Verify lighting setup is similar
4. Check post-processing settings

---

## Technical Questions

### Can I modify the shader?

Yes! Open `Shimmer_Effect_Highlight.shadergraph` in Shader Graph editor. However:
- Back up the original first
- Changes affect all materials using this shader
- Requires Shader Graph knowledge

### Can I add more properties?

Yes, by modifying the shader graph. You can add:
- Additional texture slots
- Custom animation patterns
- New color properties
- Extra effects

### Does it support GPU instancing?

The shader supports GPU instancing for better performance with many identical objects. This is automatic when using shared materials.

### Can I use it with VFX Graph or Particle System?

Yes, but you'll need to apply the material to particle mesh rendering. The effect works on any mesh with the material applied.

### Is the source code included?

The asset uses Shader Graph, which is a visual scripting system. The shader graph file itself is included and can be modified. There's no traditional "source code" since it's node-based.

---

## Licensing & Support

### Can I use this in commercial projects?

Yes! Standard Unity Asset Store EULA applies. You can use it in unlimited commercial projects after purchase.

### Can I redistribute the asset?

No. The asset cannot be redistributed as-is or in modified form. Each developer/studio needs their own license.

### Can I modify the asset for my project?

Yes! You can modify, customize, and adapt the asset for your project needs.

### Where do I get support?

1. Read this documentation thoroughly
2. Check the Asset Store page for support contact information
3. Use Unity forums or the asset's support thread
4. Contact the publisher through Asset Store

### How do I report bugs?

Contact the publisher through the Asset Store page or support email listed there.

### Will there be updates?

Check the Asset Store page for update announcements. Updates are provided at the publisher's discretion.

---

## Tips & Tricks

### Best color combinations?

See the [Shimmer Controls](../user-guide/shimmer-controls.md#highlight-color) page for recommended colors by purpose.

### How do I create a loot rarity system?

Use different colors and patterns for each rarity tier:
```yaml
Common: White, Diagonal 1, Emission 0.2
Rare: Blue, Diagonal 2, Emission 0.4
Epic: Purple, Diagonal 3, Emission 0.6
Legendary: Gold, Pulse, Emission 0.8
```

### Can I animate properties over time?

Yes! Use C# scripts to modify properties in Update() or with coroutines/tweening libraries.

### How do I sync shimmer with gameplay events?

Use scripts to trigger property changes:
```csharp
// Speed up when player is nearby
float distance = Vector3.Distance(player.position, transform.position);
if (distance < 5f)
    material.SetFloat("_Speed", 3.0f);
else
    material.SetFloat("_Speed", 1.5f);
```

---

## Still Have Questions?

If your question isn't answered here:

1. Review the full [User Guide](../user-guide/material-properties.md)
2. Check [Best Practices](../examples/best-practices.md)
3. Explore the Demo Scene for examples
4. Contact support through the Asset Store page

---

## Quick Problem Solver

| Problem | Quick Fix |
|---------|-----------|
| Material is pink | Enable URP, install Shader Graph |
| No animation | Enter Play Mode |
| Effect too subtle | Increase emission, enable bloom |
| Effect too strong | Decrease emission, slow speed |
| Poor performance | Reduce object count, implement culling |
| Texture not working | Check import settings, enable map toggle |

---

For more detailed information, explore the rest of the documentation or contact support.
