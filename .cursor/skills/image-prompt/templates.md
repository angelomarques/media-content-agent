# Image prompt templates

Fill the matching template as one paragraph, one edit instruction, or the labeled lines that section shows. Drop a slot only when the user ruled it out. Examples are quality targets, not text to reuse.

## Photorealistic

A photorealistic {shot type} of {subject}, {action or expression}, set in {environment}. The scene is illuminated by {light}, creating a {mood} atmosphere. Captured with {camera body, lens, and aperture}, emphasizing {textures and details}. {Film stock or grade, only when the look depends on it.} {Aspect ratio}.

Include a real lens or shot size, and name at least one surface the light should reveal. Name the light setup when it defines the picture: three-point softbox, chiaroscuro, or golden-hour backlight. A camera body changes the image when the lens alone does not: an action camera for wide distortion, a disposable camera for direct flash, medium-format film for shallow focus and grain. Add a grade only for an editorial or cinematic still, such as muted teal or 1980s color negative with fine grain. Skip the grade for a straight documentary photo. When they want a candid photo, ask for texture a camera would catch (pores, fabric wear, flyaway hair) and skip beauty-retouch or campaign-staging language. For a real place and date, state both and ask for period-accurate clothing and surroundings. Do not retell the event that date already implies.

Example:

```text
A photorealistic medium shot of a young baker sliding a blistered sourdough loaf onto a wire rack, flour on her forearms and a quiet, focused expression. The setting is a narrow bakery kitchen at dawn, with a glowing deck oven behind her. Soft side light from a street window creates a warm, calm atmosphere and picks out the flour in the air. Captured with a 50mm lens at a wide aperture so the oven falls into blur, emphasizing the crackled crust and the linen apron. Vertical 4:5.
```

## Sticker

A {style} sticker of a {subject}, featuring {key traits} and a {palette}. The design should have {line style} and {shading style}. The background must be white.

Say "sticker" or "icon" so the model keeps a single contained shape. White background is required for a cutout unless they asked for a colored field.

Example:

```text
A flat vector sticker of a round green frog in a yellow raincoat, holding a tiny red umbrella, with a closed-eye smile. Bold uniform outlines, simple cel shading, and a palette of leaf green, rain yellow, and tomato red. The background must be white.
```

## Text

Create a {image type} for {brand or concept} with the text "{exact text}" in a {font style}. The design should be {style}, with a {color scheme}. {Aspect ratio}.

Quote the text exactly once. Describe the type (weight, a named face or a serif or sans, size, color, case) and where it sits. State the business purpose. Say the words appear once.

For a logo, ask for an original mark: one strong silhouette, flat shapes, balanced empty space, and enough padding that it still reads small. Skip gradients unless they asked. Spell an unusual brand name letter by letter under the quoted word.

For more than one line, give each line its own quoted string and type style. If the copy is not final, propose the words first, then quote those exact words in the prompt. To localize, quote the final words in the target language and name the language. Do not leave the translation to the image model.

Localization example:

```text
Create a square promo still for a bakery's first-order offer, on warm linen with soft studio light. Render "Morning bake" in a soft serif, "10% off" in a heavy block face, and "this week" in a thin sans serif, stacked and centered. For the Portuguese version, keep the same layout and render "Fornada da manhã", "10% de desconto", and "esta semana".
```

Example:

```text
Create a square app icon for a bedtime podcast called Low Light, with the text "Low Light" in a soft condensed serif. The icon is for a dark-mode home screen. The design is a navy field with a single thin crescent above the wordmark, in warm ivory and a muted gold line, with clear padding so the words stay readable at small size.
```

## Product

Product showcases, packshots, and catalog sets are written by [product-image-prompt](../product-image-prompt/SKILL.md). Do not fill a product prompt from this file.

## Minimalist

A minimalist composition featuring a single {subject} positioned in the {region} of the frame. The background is a vast, empty {color} field, creating significant negative space for {what will be overlaid}. Soft, subtle lighting. {Aspect ratio}.

Put the subject on one edge or corner and name the empty region as space for a headline, logo, or UI. One object only.

Example:

```text
A minimalist composition featuring a single matte terracotta sphere in the lower-left third of the frame. The background is a vast, empty warm-gray field, creating significant negative space for a headline on the right. It is a title slide background. Soft light from the upper left, with a faint contact shadow only. Landscape 16:9.
```

## Sequential

A single comic book panel in a {art style} style. In the foreground, {character and action}. In the background, {setting}. The panel has a {caption or speech balloon} with the text "{exact text}". The lighting creates a {mood} mood. {Aspect ratio}.

One panel per prompt, unless they asked for a strip. For a strip in one image, state the panel count, that the panels are equal, and one concrete action per panel. Repeat the same character description in every panel and change only the action.

For a recurring character, first make an anchor: that character on a plain background, with outfit, face, proportions, and palette locked and no caption. Later prompts attach the anchor and restate those traits, plus "do not redesign the character."

Example:

```text
A single comic book panel in clean ligne claire with flat color. In the foreground, a courier on a yellow bicycle looks back over one shoulder, a hand still on the handlebar. In the background, a rain-bright crosswalk and an approaching tram. A caption box at the top reads "She was already late." Even overcast light creates a tense, unsentimental mood. Landscape 16:9.
```

## Edit

Using the provided image of {subject}, {add, remove, or modify} {element}. Make the change {how it should integrate: light, perspective, texture, scale}. Keep {what must stay}.

The new element has to match the photo's light and lens. Do not restyle the whole image.

To change only light or weather, name the new conditions (direction, shadows, precipitation, wet ground) and repeat that identity, geometry, camera, and object placement stay.

Example:

```text
Using the provided image of the storefront, add a small chalkboard sign on the sidewalk to the left of the door. Match the existing daylight, perspective, and grain so the sign looks like it was there when the photo was taken. Keep the facade, the crop, and the aspect ratio unchanged.
```

## Inpaint

Using the provided image, change only the {specific element} to {replacement}. Keep everything else in the image exactly the same, preserving the original style, lighting, composition, and aspect ratio.

Name the region tightly. Repeat that everything outside it stays.

Example:

```text
Using the provided image, change only the metal chair in the foreground to a worn wooden stool. Keep the person, the table, the background, the crop, the lighting, and the aspect ratio exactly the same.
```

## Style transfer

Transform the provided photograph of {subject} into the style of {artist or art movement}. Preserve the original composition, but render it with {stylistic elements: mark-making, palette, medium}.

Keep the subject and viewpoint. Change the rendering, not the layout. Name concrete visual traits of the style, not only the artist's name.

To keep a reference's style and change the subject, name Image 1 as style only (palette, texture, mark-making) and describe the new subject. Say what stays, such as a plain background or the framing.

Example:

```text
Transform the provided photograph of the greenhouse into a risograph print. Preserve the viewpoint and the placement of the plants, but render every shape with a limited palette of misregistered ink, visible halftone grain, and rough paper. Keep the aspect ratio of the photo.
```

## Composition

Using the provided images, treat {image} as {one role: structure, texture, identity, product, or palette}. {Repeat for each image.} {Relationship: what to make from those roles.} Place the result in {new scenario, light, and purpose}. Keep {traits that must survive}. {Aspect ratio}.

Label them Image 1, Image 2, in the order the user should attach them. Give each image one role, not a list of jobs. Say which traits must survive (face, garment, silhouette, weave, glaze).

When inserting into an existing photo, name the destination spot and say Image 1's framing, light, and background stay. Match scale and shadows so the added element looks photographed there.

Example:

```text
The first image is a pencil sketch of an armchair; use it only as the structure. The second image is a rust linen swatch; use it only as the upholstery texture. Turn those into a realistic 3D armchair and place it in a sunlit, nearly empty living room for a furniture catalog. Keep the sketch's silhouette and the swatch's weave. Landscape 3:2.
```

## Infographic

```text
Create an infographic for {audience} that explains {topic}.
Scene: {steps or parts, in order}.
Style: {diagram treatment and palette}.
Text: {quoted labels only}.
Constraints: original diagram, each label once, clear spacing, {aspect ratio}.
```

Name every step in order. Quote the labels. A request for a "detailed infographic" without the sequence is not enough.

Example:

```text
Create an infographic for home cooks that explains how a moka pot brews.
Scene: fill the base with water, add grounds to the funnel, screw on the top chamber, heat, then coffee rises into the upper pot.
Style: flat side-view diagram, warm brass and cream, thin leader lines.
Text: "Water", "Grounds", "Heat", "Brewed coffee".
Constraints: original diagram, each label once, generous spacing. Square.
```

## UI mockup

```text
Create a realistic {device} UI mockup for {product}.
Layout: {header, sections, and real controls, in order}.
Style: {background, type, accent}. It should look like a shipped interface, not concept art.
Constraints: practical spacing, no decorative illustration, {aspect ratio}.
```

Describe the product as if it already exists. Name real controls (list, button, field), not a mood.

Example:

```text
Create a realistic mobile UI mockup for a neighborhood tool library.
Layout: a header with the library name, a search field, a short list of tools with a photo and a status, and a bottom tab for hours.
Style: white background, dark text, one green accent. It should look like a shipped interface, not concept art.
Constraints: practical spacing, no decorative illustration. Place the UI in a phone frame. Vertical 9:16.
```

## Translate

Translate only the text in the provided image into {language}. Keep the layout, type style, size, placement, spacing, and hierarchy. Do not change icons, photos, logos, or colors. Do not add words.

Quote each replacement string when you know it. If you do not, name the language and say to translate verbatim.

Example:

```text
Translate only the text in the provided image into Portuguese. Render "Fornada da manhã" where the headline is, and "10% de desconto" where the offer is. Keep the layout, type style, size, placement, spacing, and hierarchy. Do not change icons, photos, logos, or colors. Do not add words.
```

## Try-on

Image 1 is the person. The following images are the garments, in attach order.
Change only the clothing. Keep the face, skin tone, body, pose, hair, and expression.
Fit the garments to that pose with realistic folds and occlusion. Match the photo's light and shadows.
Keep the background, camera, and framing.

Example:

```text
Image 1 is the person. Image 2 is the jacket. Image 3 is the boots.
Change only the clothing. Keep the face, skin tone, body, pose, hair, and expression.
Fit the jacket and boots to that pose with realistic folds and occlusion. Match the photo's light and shadows so the clothes are not pasted on.
Keep the background, camera, and framing.
```

## Sketch render

Turn this drawing into a photorealistic image.
Preserve the layout, proportions, and perspective.
Add {materials and light} consistent with the sketch.
Do not add objects or text.

Example:

```text
Turn this drawing into a photorealistic image.
Preserve the layout, proportions, and perspective of the valley and the cabin.
Add weathered timber, overcast daylight, and a dirt path consistent with the sketch.
Do not add objects or text.
```

## Cutout

Extract the product from the provided image onto a transparent background.
Keep the silhouette crisp, with no halo.
Preserve the product shape and the label text exactly.
Add a soft contact shadow only if they asked for one.
Do not restyle the product.

Use this only for a cutout. A normal packshot uses the product template.

Example:

```text
Extract the product from the provided image onto a transparent background.
Keep the silhouette crisp, with no halo.
Preserve the bottle shape and the label text exactly.
Add a soft contact shadow in the alpha.
Do not restyle the product.
```

## Live data

Look up {current fact}. Use that result to decide {what in the scene changes}. Show it as {scene, composition, and style}. Leave the frame free of captions unless the user asked for type. {Aspect ratio}.

Use this only when the fact is current, the user did not already supply it, and the tool is a Gemini image model that can search. If the tool cannot search, ask for the fact and write a normal scene prompt that states it. Do not invent today's weather, score, or price inside the prompt.

Example:

```text
Look up the current weather and local time in Lisbon. Use that result to set the sky, the light, and whether the sidewalk is wet. Show a small bakery window on a tiled street, photographed from across the road at eye level, with the frame free of captions. Vertical 9:16.
```

## Refine

Keep everything else the same, but {one change}.

Use this for a follow-up turn. One change per prompt: light, expression, color, crop, or a single object. Repeat the preserve list every time, not only the change. If identity has drifted, do not use this template. Attach the character anchor, or write a new prompt that restates the character in full.

Examples:

```text
Keep everything else the same, but make the lighting warmer and lower, as if it were late afternoon.
```

```text
Keep everything else the same, but change the expression to serious. Do not change the face shape, wardrobe, or background.
```
