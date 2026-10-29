# Image prompt templates

Fill the matching template as one paragraph or one edit instruction. Drop a slot only when the user ruled it out. Examples are quality targets, not text to reuse.

## Photorealistic

A photorealistic {shot type} of {subject}, {action or expression}, set in {environment}. The scene is illuminated by {light}, creating a {mood} atmosphere. Captured with {camera or lens}, emphasizing {textures and details}. {Aspect ratio}.

Include a real lens or shot size. Name at least one surface the light should reveal.

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

Quote the text exactly once. Describe the type (weight, serif or sans, case) and where it sits. State the business purpose. For a logo, ask for one simple symbol integrated with the wordmark, not a scene full of objects.

Example:

```text
Create a square app icon for a bedtime podcast called Low Light, with the text "Low Light" in a soft condensed serif. The icon is for a dark-mode home screen. The design is a navy field with a single thin crescent above the wordmark, in warm ivory and a muted gold line, with clear padding so the words stay readable at small size.
```

## Product

A high-resolution, studio-lit product photograph of a {product} on a {surface}. The lighting is a {setup} to {purpose}. The camera angle is a {angle} to showcase {feature}. Ultra-realistic, with sharp focus on {detail}. {Aspect ratio}.

Name material and finish (matte ceramic, frosted glass, brushed metal). The lighting sentence should say what the light is for, not only the gear name.

Example:

```text
A high-resolution, studio-lit product photograph of a matte black ceramic coffee mug on polished concrete. It is a hero image for a product page. The lighting is a three-point softbox setup to give soft highlights along the rim and remove hard shadows. The camera is a slightly elevated 45-degree view to show the clean profile and the inner lip. Ultra-realistic, with sharp focus on a thin ribbon of steam. Square.
```

## Minimalist

A minimalist composition featuring a single {subject} positioned in the {region} of the frame. The background is a vast, empty {color} field, creating significant negative space for {what will be overlaid}. Soft, subtle lighting. {Aspect ratio}.

Put the subject on one edge or corner and name the empty region as space for a headline, logo, or UI. One object only.

Example:

```text
A minimalist composition featuring a single matte terracotta sphere in the lower-left third of the frame. The background is a vast, empty warm-gray field, creating significant negative space for a headline on the right. It is a title slide background. Soft light from the upper left, with a faint contact shadow only. Landscape 16:9.
```

## Sequential

A single comic book panel in a {art style} style. In the foreground, {character and action}. In the background, {setting}. The panel has a {caption or speech balloon} with the text "{exact text}". The lighting creates a {mood} mood. {Aspect ratio}.

One panel per prompt. Quote caption or dialogue exactly. For a storyboard sequence, repeat the same character description in every panel and change only the action and setting.

Example:

```text
A single comic book panel in clean ligne claire with flat color. In the foreground, a courier on a yellow bicycle looks back over one shoulder, a hand still on the handlebar. In the background, a rain-bright crosswalk and an approaching tram. A caption box at the top reads "She was already late." Even overcast light creates a tense, unsentimental mood. Landscape 16:9.
```

## Edit

Using the provided image of {subject}, {add, remove, or modify} {element}. Make the change {how it should integrate: light, perspective, texture, scale}. Keep {what must stay}.

The new element has to match the photo's light and lens. Do not restyle the whole image.

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

Example:

```text
Transform the provided photograph of the greenhouse into a risograph print. Preserve the viewpoint and the placement of the plants, but render every shape with a limited palette of misregistered ink, visible halftone grain, and rough paper. Keep the aspect ratio of the photo.
```

## Composition

Create a new image by combining the provided images. Take {element from the first image} and place it {relation} {element from the second image}. The final image should be {scene, light, and purpose}. {Aspect ratio}.

Number the images in the order the user should attach them. Say which traits of each element must survive (face, garment, product shape, glaze).

Example:

```text
Create a realistic lifestyle photo for a shop catalog. The first image is the ceramic vase; the second is the sunlit kitchen counter. Place the vase on the counter and match the window light and contact shadows to that room. Keep the vase's shape and glaze. Landscape 3:2.
```

## Refine

Keep everything else the same, but {one change}.

Use this for a follow-up turn. One change per prompt: light, expression, color, crop, or a single object. If identity has drifted, do not use this template. Write a new photorealistic or sequential prompt that restates the character in full.

Examples:

```text
Keep everything else the same, but make the lighting warmer and lower, as if it were late afternoon.
```

```text
Keep everything else the same, but change the expression to serious. Do not change the face shape, wardrobe, or background.
```
