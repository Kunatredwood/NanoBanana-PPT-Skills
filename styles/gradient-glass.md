# Gradient Glassmorphism Card Style

## Style ID
gradient-glass

## Style Name
Gradient Glassmorphism Card Style

## Compatible Models
- Nano Banana Pro (gemini-3-pro-image-preview)
- Seedream

## Style Description
A beautifully crafted gradient glassmorphism card style for PPT slides, blending Apple Keynote minimalism, modern SaaS product design, and a glassmorphic aesthetic. The overall atmosphere is premium, immersive, clean, and breathable.

## Base Prompt Template

You are an expert-level UI/UX presentation designer. Generate a high-fidelity, futuristic 16:9 presentation slide. Based on visual balance aesthetics, automatically choose the most perfect composition from among: cover layout, grid layout, or data visualization.

**Global Visual Language:** The style should seamlessly blend Apple Keynote minimalism, modern SaaS product design, and glassmorphism. The overall atmosphere should be premium, immersive, clean, and breathable. Lighting should use cinematic volumetric light, soft ray-traced reflections, and ambient occlusion. The color palette should use deep void black or pure ceramic white as the base, accented with flowing aurora gradient colors — neon purple, electric blue, soft coral orange, and cyan — as background and UI highlights.

**Content Module Composition — intelligently integrate the following elements:**

1. **Layout Engine**: Use the Bento box grid system to organize content in modular rounded-rectangle containers. Container material must be frosted glass with a blur effect, featuring refined white borders and soft drop shadows. Enforce generous internal white space to avoid clutter.

2. **3D Accent Objects**: Render unique, premium abstract 3D artifacts as visual anchors. They should look like expensive physical collectibles or gift items, with materials such as polished metal, iridescent acrylic, transparent glass, or soft silicone. Shapes can include floating capsules, spheres, shields, Möbius strips, or fluid waves.

3. **Typography & Data**: Use clean sans-serif fonts to establish high contrast. If charts are included, use glowing 3D donut charts, capsule-shaped progress bars, or floating numerals — charts should look like glowing neon toys.

**Render Quality Requirements:** Unreal Engine 5 rendering, 8K resolution, ultra-detailed textures, UI design aesthetic, UX interface look, Dribbble trending, award-winning design.

## Page Type Templates

### Cover Page Template
Composition logic: Place a large, complex 3D glass object at the center, overlaid with bold large text. The background features extending aurora waves.

Use case: The first slide of a PPT — displays the title and theme.

### Content Page Template
Composition logic: Use a Bento grid layout, placing 3D icons in small cards and text in large cards. Container material must be frosted glass with a blur effect, featuring refined white borders and soft drop shadows, with generous internal white space to avoid clutter.

Use case: Displaying core points, bullet points, and content chapters.

### Data Page Template
Composition logic: Use a split-screen design — typography and text on the left, a large glowing 3D data visualization chart floating on the right. Charts should use glowing 3D donut charts, capsule-shaped progress bars, or floating numerals that look like glowing neon toys.

Use case: Displaying data, statistics, comparative analysis, and summaries.

## Usage Examples

### Generate a Cover Page
```
{Base Prompt Template}

Based on visual balance aesthetics, generate a cover page. Place a large, complex 3D glass object at the center, overlaid with bold large text:

[Title text]

The background features extending aurora waves.
```

### Generate a Content Page
```
{Base Prompt Template}

Generate a content page. Use a Bento grid layout to organize the following content in modular rounded-rectangle containers. Container material must be frosted glass with a blur effect:

[Content text]
```

### Generate a Data Page
```
{Base Prompt Template}

Generate a data or summary page. Use a split-screen design — typography and the following text on the left, a large glowing 3D data visualization chart floating on the right:

[Content text]
```

## Technical Parameters

### Nano Banana Pro Configuration
- Model: gemini-3-pro-image-preview
- Aspect ratio: 16:9
- Resolution: 2K (2752x1536) or 4K (5504x3072)
- Response mode: IMAGE

### Recommended Settings
- Recommended resolution: 2K (balanced quality and generation speed)
- Suitable for: product demos, tech talks, creative proposals, data reports, and more
