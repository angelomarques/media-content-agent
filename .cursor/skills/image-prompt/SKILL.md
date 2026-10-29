---
name: image-prompt
description: >-
  Writes ready-to-paste narrative prompts for AI image generation and editing
  (Gemini, Imagen, Flux, GPT Image, Midjourney, and similar). Use when the user
  asks for an image prompt, text-to-image prompt, picture description, logo,
  poster, product shot, sticker, comic panel, storyboard frame, or to edit,
  inpaint, restyle, or combine reference images.
---

# Image prompts

Write a prompt that describes the scene. A narrative paragraph gives these models a coherent image. A list of disconnected keywords does not.

The method follows Google's Gemini image prompting guide: scene prose, a template per job, camera language, and positive wording for what should be absent. Use that prose for Gemini, Imagen, Flux, and GPT Image. If the user names a tool with its own parameters, keep the paragraph and add only that tool's parameters.

This skill writes the prompt. Do not generate an image unless the user asks for one.

## Workflow

1. Classify the job with the table below.
2. Read the matching section in [templates.md](templates.md) and fill it.
3. If the subject is missing, or you cannot tell a new image from an edit of an attachment, ask one question. Otherwise assume and proceed.
4. Run the checklist, then deliver the prompt.

When the user wants several options, write separate prompts that share the subject and purpose and change one dimension only (light, angle, or style). Label them Variation A, B, and C.

## Classify

| Job | Use when | Template |
| --- | --- | --- |
| Photorealistic | Photo, portrait, cinematic still | [Photorealistic](templates.md#photorealistic) |
| Sticker or illustration | Sticker, icon, emoji, flat asset | [Sticker](templates.md#sticker) |
| Text in image | Logo, wordmark, poster, title with set copy | [Text](templates.md#text) |
| Product | Packshot, mockup, e-commerce, ad still | [Product](templates.md#product) |
| Minimalist | Background, slide, hero with room for type | [Minimalist](templates.md#minimalist) |
| Sequential | One comic panel or storyboard frame | [Sequential](templates.md#sequential) |
| Edit | Add, remove, or modify something in an attached image | [Edit](templates.md#edit) |
| Inpaint | Change one region and keep the rest untouched | [Inpaint](templates.md#inpaint) |
| Style transfer | Recreate an attached photo in a named style | [Style transfer](templates.md#style-transfer) |
| Composition | Build a new scene from two or more attached images | [Composition](templates.md#composition) |
| Refine | A follow-up on an image already generated | [Refine](templates.md#refine) |

An attached image selects an edit job. Among edit jobs, pick the most specific one: inpaint over a general edit, composition when two or more images each contribute an element.

Placement defaults when the user names a surface and no ratio:

| Placement | Ratio |
| --- | --- |
| Story, reel, or TikTok cover | 9:16 |
| Feed post | 4:5 |
| YouTube thumbnail or landscape hero | 16:9 |
| Logo, sticker, app icon, packshot | 1:1 |
| Portrait | 3:4 |

## Write

- One paragraph for a new image. One direct instruction for an edit. No tag soup (`8k`, `masterpiece`, `trending on artstation`) unless the user is on an older keyword-tag model and asked for tags.
- Name materials, not categories. "Matte black ceramic with a thin unglazed foot" beats "nice mug".
- State the purpose when the image is a designed artifact: who it is for and where it will be seen.
- Put exact rendered text in quotation marks and describe the typeface. Say what not to misspell by quoting the string once.
- For a cutout sticker or icon, say the background must be white.
- State the aspect ratio in words inside the prompt (`square`, `vertical 9:16`, `landscape 16:9`).
- For a photo or cinematic still, control the camera: shot size, angle, and lens. Useful terms include wide-angle, macro, low-angle, 85mm portrait lens, and Dutch angle.
- Describe an absence as the scene you want. "An empty street with wet asphalt and no traffic" beats "no cars".
- For edits, say what stays the same: identity, layout, light, crop, and aspect ratio. Name images in order (`the first image`, `the second image`). On Gemini-style editors the last attached image tends to set the ratio; say the target ratio anyway.
- If character features have drifted across turns, stop stacking edits. Write a new prompt that restates face, age, wardrobe, and setting in full, and tell the user to start a fresh chat, attaching the best prior frame if the tool allows.

## Tool parameters

Add these after the paragraph, only when that tool was named:

| Tool | Add |
| --- | --- |
| Gemini, Imagen, Flux, GPT Image | Nothing. For edits, the user attaches images in the order the prompt names. |
| Midjourney | `--ar W:H` from the aspect ratio. Add `--stylize` only if they gave a stylization level. Do not add `--no` for things the paragraph already settles. |
| Stable Diffusion | A negative prompt only for artifacts they want suppressed (extra fingers, watermark). Keep scene content in the positive prompt. |

## Checklist

- Subject, action, and setting are specific enough that two artists would draw the same scene.
- Light and mood are present on new scenes.
- Purpose is present for logos, ads, covers, and UI assets.
- Aspect ratio is inside the prompt.
- On-image text is quoted exactly.
- Edit prompts say what must not change.
- The prompt contains no "no X" line that a positive sentence could replace.
- Assumptions are outside the prompt, not inside it.

## Deliver

Use this shape. Omit **Assumptions** when you assumed nothing. The fenced block is the only text they paste.

**Job:** Product mockup
**Assumptions:** Square frame. No label copy, because no brand name was given.
**Attach:** none

```text
A high-resolution studio photograph of a frosted glass serum bottle with a pale sage pump, standing on wet pale stone. It is a packshot for a minimal skincare product page. A three-point softbox setup creates gentle edge highlights and soft contact shadows. The camera is slightly above the bottle at 45 degrees, with sharp focus on the pump collar and the liquid line. Square.
```

**Refine next:**

- Keep everything else the same, but emboss the word "SOLA" in small type on the glass.
- Keep everything else the same, but lower the camera so the pump sits in the top third.

For an edit, **Attach** names each file's role and order. **Refine next** is one small change and, when the job is typography or a recurring character, one recovery prompt. Complex lettering and identical faces across images often need that follow-up. Say so in one sentence when the job is one of those two. Do not promise a perfect first generation.
