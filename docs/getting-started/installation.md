# Installation

This guide will help you install the Shimmer Effect Highlight asset into your Unity project.

## Requirements

- **Unity Version**: 2021.3 or higher (recommended)
- **Render Pipeline**: Universal Render Pipeline (URP) / High Definition Render Pipeline (HDRP)
- **Shader Graph**: Ensure Shader Graph package is installed

## Installation Steps

### Step 1: Import the Asset

1. Download the Shimmer Effect Highlight package from the Unity Asset Store
2. Open your Unity project
3. Go to **Window** → **Package Manager**
4. Select **My Assets** from the dropdown
5. Find "Shimmer Effect" and click **Download**
6. Once downloaded, click **Import**
7. In the import dialog, ensure all files are selected and click **Import**

!!! success "Installation Complete"
    The asset will be imported to `Assets/GameReadyTools/Shimmer Effect/`

### Step 2: Verify Installation

After importing, you should see the following folder structure:

```
Assets/
└── GameReadyTools/
    └── Shimmer Effect/
        ├── Materials/
        │   └── Shimmer_Effect_Highlight.mat
        ├── Scenes/
        │   ├── Demo Scene
        │   └── Global Volume Profile
        └── Shader/
            └── Shimmer_Effect_Highlight.shadergraph
```

### Step 3: Check the Demo Scene

To verify everything is working correctly:

1. Navigate to `Assets/GameReadyTools/Shimmer Effect/Scenes/`
2. Open the **Shimmer_Effect_Highlight_Demo**
3. Press **Play** to see the shimmer effect in action
4. Explore the various examples and configurations

!!! tip "Demo Scene Benefits"
    The demo scene includes multiple examples showcasing different configurations and use cases. It's an excellent reference for learning how to use the asset effectively.

## Post-Processing Setup (Optional)

For the best visual results, especially with emission effects:

1. Ensure your scene has a **Global Volume** with **Bloom** enabled
2. Use the included **Global Volume Profile** as a starting point
3. Adjust bloom intensity to complement your shimmer effects

!!! info "Bloom Enhancement"
    While not required, enabling Bloom post-processing significantly enhances the glow effect of the shimmer highlights, especially when using higher emission values.

## Next Steps

Now that you've installed the asset, continue to the [Quick Start Guide](quick-start.md) to learn how to apply the shimmer effect to your objects.

## Troubleshooting

### Shader Not Compiling

If you encounter shader compilation errors:

- Verify Shader Graph package is installed (**Window** → **Package Manager** → **Unity Registry** → **Shader Graph**)
- Ensure you're using Universal Render Pipeline
- Try reimporting the asset

### Material Appears Pink

If materials appear pink/magenta:

- Your project may not be using URP
- Check **Edit** → **Project Settings** → **Graphics** → **Scriptable Render Pipeline Settings**
- If needed, create or assign a URP asset

