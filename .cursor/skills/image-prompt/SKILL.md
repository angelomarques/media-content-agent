---
name: image-prompt
description: >-
  Writes ready-to-paste narrative prompts for AI image generation and editing
  (Gemini, Nano Banana, Imagen, Flux, GPT Image, Midjourney, and similar). Use
  when the user asks for an image prompt, text-to-image prompt, picture
  description, logo, poster, infographic, UI mockup, sticker, comic panel,
  storyboard frame, or to edit, inpaint, restyle, try on clothes, translate or
  localize on-image text, or combine reference images. When the request is a
  product showcase, packshot, catalog photo, or other e-commerce still of a
  physical product, follow the product-image-prompt skill instead. When the
  request is a video, animation, or image-to-video prompt, follow the
  video-prompt skill instead.
---

# Image prompts

Write a prompt that describes the scene. A narrative paragraph gives these models a coherent image. A list of disconnected keywords does not. For a complex layout, use short labeled lines instead of one dense paragraph.

The method follows Google's Gemini image prompting guides, including Nano Banana, and OpenAI's GPT Image guide: scene prose, a template per job, camera and grade language, one role per reference image, explicit invariants, and positive wording for what should be absent. Use that prose for Gemini, Imagen, Flux, and GPT Image. If the user names a tool with its own parameters, keep the prompt and add only that tool's parameters.

This skill writes the prompt. Do not generate an image unless the user asks for one.

## Product showcase

If the image shows a physical product for sale — a packshot, catalog or product-page set, unboxing flat lay, macro, colorway, fit or scale guide, in-use shot, lifestyle, UGC, ad banner, or shop-the-look — stop. Read [product-image-prompt](../product-image-prompt/SKILL.md) and follow that skill. Do not fill a template from this skill for that request. A transparent cutout, a virtual try-on, and an edit that is not one of those catalog shots stay here.

## Video

Motion belongs to [video-prompt](../video-prompt/SKILL.md). If they already have the still, stop and follow that skill. If they do not, write the still here, deliver it, and then follow video-prompt for the motion. The image prompt describes the picture only.

## Workflow

1. If the request is a product showcase, follow that handoff and stop. If it is a video of an existing still, follow video-prompt and stop. If it is a video and the still does not exist, write the still here, then follow video-prompt for the clip.
2. Classify the job with the table below.
3. Read the matching section in [templates.md](templates.md) and fill it.
4. If the subject is missing, or you cannot tell a new image from an edit of an attachment, ask one question. Otherwise assume and proceed.
5. Run the checklist, then deliver the prompt.

When the user wants several options, write separate prompts that share the subject and purpose and change one dimension only (light, angle, or style). Label them Variation A, B, and C.

## Classify

| Job | Use when | Template |
| --- | --- | --- |
| Photorealistic | Photo, portrait, cinematic still | [Photorealistic](templates.md#photorealistic) |
| Sticker or illustration | Sticker, icon, emoji, flat asset | [Sticker](templates.md#sticker) |
| Text in image | Logo, wordmark, poster, title with set copy | [Text](templates.md#text) |
| Infographic | Explainer, labeled diagram, timeline, flow | [Infographic](templates.md#infographic) |
| UI mockup | App or web interface that should look shipped | [UI mockup](templates.md#ui-mockup) |
| Product showcase | Packshot, catalog, product page, or ad still of a product for sale | Stop. Follow [product-image-prompt](../product-image-prompt/SKILL.md) |
| Minimalist | Background, slide, hero with room for type | [Minimalist](templates.md#minimalist) |
| Sequential | One comic panel, a strip, or a recurring character | [Sequential](templates.md#sequential) |
| Edit | Add, remove, or modify something in an attached image | [Edit](templates.md#edit) |
| Inpaint | Change one region and keep the rest untouched | [Inpaint](templates.md#inpaint) |
| Translate | Change the language of text already in an image | [Translate](templates.md#translate) |
| Try-on | Dress a person using provided garment images | [Try-on](templates.md#try-on) |
| Sketch render | Turn a drawing into a realistic image | [Sketch render](templates.md#sketch-render) |
| Cutout | Extract a product onto a transparent background | [Cutout](templates.md#cutout) |
| Style transfer | Recreate an image in a named style, or apply a reference style to a new subject | [Style transfer](templates.md#style-transfer) |
| Composition | Build a new scene from two or more attached images | [Composition](templates.md#composition) |
| Live data | A current fact should change the picture, and the tool can search | [Live data](templates.md#live-data) |
| Refine | A follow-up on an image already generated | [Refine](templates.md#refine) |

An attached image selects an edit job. Among edit jobs, pick the most specific one: translate, try-on, sketch render, or cutout over a general edit; inpaint over a general edit; composition when two or more images each contribute an element.

Placement defaults when the user names a surface and no ratio:

| Placement | Ratio |
| --- | --- |
| Story, reel, or TikTok cover | 9:16 |
| Feed post | 4:5 |
| YouTube thumbnail or landscape hero | 16:9 |
| Cinematic ultrawide or wide banner | 21:9 |
| Logo, sticker, app icon, packshot | 1:1 |
| Portrait | 3:4 |

On Gemini image models, a strip can be 4:1, 1:4, 8:1, or 1:8. Use those only when the user asked for a banner edge or a tall strip.

## Write

- One paragraph for a simple scene. For an infographic, UI, multi-panel strip, or an edit with several invariants, use short labeled lines in this order: scene, subject, details, constraints. No tag soup (`8k`, `masterpiece`, `trending on artstation`) unless the user is on an older keyword-tag model and asked for tags.
- Start an edit or a composite with the operation: Add, Remove, Change only, Transform, Translate, or Place. A new scene can open on the subject.
- Name materials, not categories. "Matte black ceramic with a thin unglazed foot" beats "nice mug".
- State the purpose when the image is a designed artifact: who it is for and where it will be seen.
- Put exact rendered text in quotation marks and describe the typeface, size, color, and placement. Give each line its own quoted string and type style. Say the words appear once. For an unusual brand spelling, spell it letter by letter under the quoted word. To localize, quote the final words in the target language and name the language. If the copy is not final, propose it first, then quote those words in the prompt.
- For a cutout sticker or icon, say the background must be white.
- State the aspect ratio in words inside the prompt (`square`, `vertical 9:16`, `landscape 16:9`).
- For a photo or cinematic still, control the camera: shot size, angle, lens, and aperture. When the look depends on it, name the camera body and a film stock or grade. See the photorealistic template.
- Describe an absence as the scene you want. "An empty street with wet asphalt and no traffic" beats "no cars".
- For edits, say what stays the same: identity, layout, light, crop, and aspect ratio. Repeat that preserve list on every follow-up. Name images as Image 1, Image 2, in attach order, and give each one role, such as structure, texture, identity, product, or palette. On Gemini-style editors the last attached image tends to set the ratio; say the target ratio anyway.
- For a real place and date, state both and ask for period-accurate clothing and surroundings. Do not retell the event the date already implies.
- If character features have drifted across turns, stop stacking edits. Make a character anchor first: the character on a plain background with outfit, face, proportions, and palette locked. Later prompts attach that image and restate those traits. See the sequential template.

## Tool parameters

Add these after the paragraph, only when that tool was named:

| Tool | Add |
| --- | --- |
| Gemini, Nano Banana, Imagen, Flux | Nothing inside the prompt. The user attaches images in the order the prompt names. These models accept a set of references in one prompt; still assign each image one role. Use [Live data](templates.md#live-data) only for these search-capable models. |
| GPT Image | Nothing inside the prompt. If they are calling the API, set `quality` to high for dense text, infographics, and identity edits, and low only for a fast draft they asked for. Set `input_fidelity` to high when a face or a product label must survive a large edit. Mention those settings beside the prompt, not in it. |
| Midjourney | `--ar W:H` from the aspect ratio. Add `--stylize` only if they gave a stylization level. Do not add `--no` for things the paragraph already settles. |
| Stable Diffusion | A negative prompt only for artifacts they want suppressed (extra fingers, watermark). Keep scene content in the positive prompt. |

## Checklist

- Subject, action, and setting are specific enough that two artists would draw the same scene.
- Light and mood are present on new scenes.
- Purpose is present for logos, ads, covers, and UI assets.
- Aspect ratio is inside the prompt.
- On-image text is quoted exactly. Localized text is quoted in the target language.
- Each reference image has one role.
- Edit prompts say what must not change.
- Scene absences are written as the scene you want. A Constraints block may still forbid extra text, watermarks, and a redesign of locked elements.
- Assumptions are outside the prompt, not inside it.

## Deliver

Use this shape. Omit **Assumptions** when you assumed nothing. The fenced block is the only text they paste.

**Job:** Photorealistic portrait
**Assumptions:** Vertical 4:5, because they asked for a feed post and gave no ratio.
**Attach:** none

```text
A photorealistic medium close-up of an older potter wiping clay from his hands, looking down at a wet bowl on the wheel. The setting is a small studio with a north window. Soft side light creates a quiet atmosphere and picks out the clay on his knuckles and the linen apron. Captured with a 50mm lens at a wide aperture so the shelves behind him fall into blur. Vertical 4:5.
```

**Refine next:**

- Keep everything else the same, but shift the light so it catches the rim of the bowl.
- Keep everything else the same, but lower the camera to the height of the wheel.

For an edit, **Attach** names each file's role and order. **Refine next** is one small change and, when the job is typography or a recurring character, one recovery prompt. Complex lettering and identical faces across images often need that follow-up. Say so in one sentence when the job is one of those two. Do not promise a perfect first generation.
