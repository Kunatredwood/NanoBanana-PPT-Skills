# Vector Illustration Style

## Style ID
vector-illustration

## Style Name
Vector Illustration Style PPT

## Compatible Models
- Nano Banana Pro (gemini-3-pro-image-preview)
- Notebookml
- Youmind
- Listenhub
- Lovart

## Style Description
A flat vector illustration style with clean black outlines and a retro, muted color palette. Emphasizes geometric simplification and a toy-model-like charm.

## Base Prompt Template

You are an expert-level illustration designer. Generate a 16:9 vector illustration style presentation slide.

**Visual Style & Art Direction**

Illustration style: Flat Vector Illustration. Must include clean, uniform-weight black outlines (Monoline/Stroke). Color fills should be simple, using minimal shading; gradients and 3D rendering effects are strictly prohibited.

Composition: Horizontal panoramic composition (Panoramic), occupying the top 1/3 of the frame.

Line Work: Must use uniform-weight black single-line strokes (Monoline/Uniform Stroke). All objects (buildings, plants, clouds) must have closed black outlines, similar to the linework of a coloring book. Line ends should be rounded; avoid sharp corners.

Geometric Simplification: Simplify complex objects into basic geometric shapes. For example, trees become lollipop shapes or triangles, buildings become simple rectangular blocks, and windows become neat small grid squares. Do not pursue realistic detail — aim for a "toy model" cuteness.

Spatial Perspective: Use a straight-on or slightly top-down 2.5D perspective (similar to isometric, but more free). Express depth through layer overlap and occlusion rather than atmospheric perspective (distant objects should not be blurred or faded — all layers should have equal clarity).

Decorative Elements: Add decorative geometric elements in empty areas, such as radiating lines (representing sunlight or energy), pill-shaped clouds, small dots, and stars, to balance the visual density of the composition.

**Color Palette**

Background: Cream/off-white paper texture.

Accent colors: Coral red, mint green, mustard yellow, burnt orange, and slate blue. Retro and muted tones.

**Typography**

Main title: Large, bold retro serif typeface — conveys authority and elegance.

Subtitle: All-caps sans-serif on a colored rectangular background.

Body text: Clean, legible geometric sans-serif.

## Page Type Templates

### Cover Page Template
Composition logic: The main title uses a large, bold retro serif typeface and occupies the center of the frame. The top 1/3 features a horizontal panoramic vector illustration scene with geometrically simplified buildings, toy-like trees, and decorative elements. Background uses a cream/off-white paper texture.

Use case: The first slide of a PPT — displays the title and theme.

### Content Page Template
Composition logic: The top area retains a horizontal illustration decorative band. The content area uses geometric icons and small vector illustrations alongside text, with all elements featuring uniform-weight black outlines. Colored rectangular blocks separate different bullet points.

Use case: Displaying core points, bullet points, and content chapters.

### Data Page Template
Composition logic: Uses geometric charts and infographic styles — simplified pie charts, bar charts, etc. — with all chart elements having clear black outlines. Colors use the retro muted palette. Decorative geometric elements are added to balance the composition.

Use case: Displaying data, statistics, comparative analysis, and summaries.

## Usage Examples

### Generate a Cover Page
```
{Base Prompt Template}

Generate a cover page. In the top 1/3 area, draw a horizontal panoramic vector illustration scene featuring geometric simplifications of the following scene elements: [choose elements based on the topic].

The main title uses a large, bold retro serif typeface with the content:
[Title text]

The subtitle uses an all-caps sans-serif on a colored rectangular background:
[Subtitle text]

Background uses a cream/off-white paper texture.
```

### Generate a Content Page
```
{Base Prompt Template}

Generate a content page. Draw a horizontal illustration decorative band at the top.

The content area displays the following points, each paired with a simple vector icon. All elements have uniform-weight black outlines:

[Content text]

Use colored rectangular blocks (coral red, mint green, mustard yellow) to separate different points.
```

### Generate a Data Page
```
{Base Prompt Template}

Generate a data page. Display the following data using geometric vector charts; all chart elements have clear black outlines:

[Content text]

Use the retro muted color palette and add decorative geometric elements (small dots, stars, radiating lines) to balance the composition.
```

## Technical Parameters

### Nano Banana Pro Configuration
- Model: gemini-3-pro-image-preview
- Aspect ratio: 16:9
- Resolution: 2K (2752x1536) or 4K (5504x3072)
- Response mode: IMAGE

### Recommended Settings
- Recommended resolution: 2K (balanced quality and generation speed)
- Suitable for: educational presentations, creative proposals, children's content, brand storytelling, and more
- Style keywords: warm, cute, easy to understand, retro, nostalgic

## Style Keywords

- Flat vector illustration
- Black outlines
- Geometric simplification
- Retro color palette
- Toy model aesthetic
- Horizontal panoramic composition
- Cream paper texture
- Decorative geometric elements
