---
name: product-image-prompt
description: >-
  Writes catalog-consistent prompts for product photography: master hero,
  what's-in-the-box flat lay, macro detail, colorway lineup, scale or fit
  comparison, in-use, lifestyle, UGC, negative-space ad banner, and
  shop-the-look composite. Use when image-prompt classifies a product
  showcase, or when the user asks for a packshot, PDP or catalog photo,
  unboxing flat lay, product macro, color variation, lifestyle or UGC product
  photo, shop-the-look, or an ad still of a physical product. Keeps every
  later shot identical to one master image.
---

# Product image prompts

Write prompts for a product showcase. The master shot is the single source of truth. Every later shot attaches that image and keeps the product identical. A narrative paragraph, not a keyword list. This skill writes the prompt. Do not generate an image unless the user asks for one.

Logos, UI, stickers, comics, portraits, transparent cutouts, virtual try-ons, and other non-catalog images stay in [image-prompt](../image-prompt/SKILL.md). A video of the product stays in [video-prompt](../video-prompt/SKILL.md). Write the still here first when they do not have one, then hand that image over as the locked product.

## Workflow

1. If they asked for a video and already have the product still, stop and follow video-prompt. If they asked for a video and have no still, write the shot this skill owns, then follow video-prompt for the motion. The still prompt does not describe motion.
2. Classify the shot with the table below.
3. Read the matching section in [shots.md](shots.md) and fill it.
4. Decide the master. An attached product photo is the master. With no photo, the master is a text-to-image prompt, and every later prompt says to attach that result.
5. If the product itself is missing, ask one question. Otherwise assume and proceed.
6. Run the checklist, then deliver.

A showcase with no shot named is the master only. Name the other shots they can ask for after it. A full catalog is every shot the known facts support, in the order below. Do not invent box contents, colorways, or companion products. Ask once for those, or leave those shots out and name the missing fact under **Assumptions**.

When they want several options of one shot, share the product and purpose and change one dimension only (light, angle, or setting). Label them Variation A, B, and C.

## Classify

| Shot | Use when | Template |
| --- | --- | --- |
| Master | Hero, packshot, or the first image in a set | [Master](shots.md#master) |
| Flat lay | What's in the box, unboxing, included parts | [Flat lay](shots.md#flat-lay) |
| Macro | One feature fills the frame | [Macro](shots.md#macro) |
| Colorways | Original beside other finishes | [Colorways](shots.md#colorways) |
| Scale | Fit on a body, or size next to a familiar reference | [Scale](shots.md#scale) |
| In use | Close view of someone using one feature | [In use](shots.md#in-use) |
| Lifestyle | Person and product in a full scene | [Lifestyle](shots.md#lifestyle) |
| UGC | Casual smartphone photo of everyday use | [UGC](shots.md#ugc) |
| Banner | Product parked to leave room for ad copy | [Banner](shots.md#banner) |
| Shop the look | Several attached products in one arrangement | [Shop the look](shots.md#shop-the-look) |

Placement defaults when they name a surface and no ratio:

| Placement | Ratio |
| --- | --- |
| Master, flat lay, macro, colorways, scale | square |
| Product page or feed | vertical 4:5 |
| Story, reel, or TikTok | vertical 9:16 |
| Lifestyle hero or YouTube | landscape 16:9 |
| Banner or wide ad | landscape 16:9, or 21:9 if they asked for ultrawide |

## Master

A real product photo is the master when they have one. Do not write a new hero that replaces it. Write a polish prompt only if they asked to relight or clean that photo, and keep the product identical.

Text-to-image master: studio light, a named surface, an angle that shows one feature, sharp focus on one detail. Name materials and finish.

Every other shot opens with "Using the provided master image of {product}." Then the lock:

> The product is the same object as the master image: same silhouette, proportions, materials, color, hardware, logos, and construction.

Colorways change only the named finish. Macro also keeps the master's light and style. Lifestyle, in-use, and UGC may change the room and the light. They may not change the product.

In-use and lifestyle share one brand model. Describe that person once and reuse the description. UGC is a different customer. If they attach a model photo, that image is the person's identity and the master remains the product's identity.

## Write

- Fill the shot as one paragraph. Name materials, not categories.
- State the aspect ratio in words inside the prompt.
- State the purpose: product page, ad, unboxing, fit guide, or social post.
- The lighting sentence says what the light is for.
- On-image text is a banner job. Quote each line, name the type, and say the words appear once. Leave the field empty of type when they did not give copy.
- Name images Image 1, Image 2, in attach order. One role each: master product, model identity, or companion product. The last attached image tends to set the ratio; say the target ratio anyway.
- Describe the scene you want. A Constraints line may still forbid extra text, watermarks, and a redesign of the product.
- Same tool parameters as image-prompt. Gemini, Nano Banana, Imagen, and Flux get nothing inside the prompt. The user attaches images in the order the prompt names.

## Checklist

- Two artists would build the same product from the paragraph.
- The master is either an attachment or the first prompt in the set.
- Later prompts open on the master image and repeat the lock.
- Only the named finish, feature, scene, or crop changes.
- Shop-the-look products come from attached images.
- Aspect ratio and purpose are inside the prompt.
- Assumptions sit outside the prompt.

## Deliver

Omit **Assumptions** when you assumed nothing. The fenced block is the only text they paste. For a set, repeat the block in catalog order and say which result to attach next.

**Job:** Master hero
**Role:** Anchor. Attach this result as the master on every later shot.
**Assumptions:** Square frame. No label copy, because no brand name was given.
**Attach:** none

```text
A high-resolution, studio-lit product photograph of a matte sand insulated bottle with a black screw lid, standing on pale limestone. It is the hero image for a product page. The lighting is a three-point softbox setup to give a soft highlight along the lid edge and a faint contact shadow. The camera is a slightly elevated 45-degree view to show the slim profile and the lid threads. Ultra-realistic, with sharp focus on the lid gasket. Square.
```

**Refine next:**

- Keep the product identical, but move the highlight so it traces the bottle's vertical seam.
- Keep everything else the same, but crop tighter so the lid fills the top third.

Logos and a product repeated across shots often drift. For a colorway, a logo macro, or a shared model, add one recovery prompt that restates the lock. Say so in one sentence. Do not promise a perfect first generation.
