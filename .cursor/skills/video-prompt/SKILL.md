---
name: video-prompt
description: >-
  Writes ready-to-paste prompts for AI video models (Kling, Runway, Veo, Sora,
  Luma, Pika, and similar). Use when the user asks for a video prompt,
  image-to-video or text-to-video prompt, to animate a photo, direct subject
  motion, or specify a camera move. Image-to-video uses Subject + Movement and
  leaves the still's scene undescribed. Match the motion to the still: a
  portrait, product, landscape, artwork, old photo, logo, or cinemagraph, and
  name what must hold still so it does not warp. Text-to-video adds the setting
  because no image is attached. A named camera move is handed to
  video-camera-control.
  A still that does not exist yet is an image-prompt or product-image-prompt
  job first.
---

# Video prompts

Write the motion. Image-to-video already has a scene, so the prompt names who moves and how. Text-to-video has no scene, so it also names the setting. Simple sentences. A bare verb, a keyword list, or a long restatement of the still produces a pan, a cut, or a frozen picture.

The image-to-video method follows Kling's guide: Prompt = Subject + Movement, then Background + Movement when the background moves too. Use that shape for Kling and for other image-to-video models. This skill writes the prompt. Do not generate a video unless the user asks for one.

## Stills

If they need a still that does not exist yet, stop. Write that still with [image-prompt](../image-prompt/SKILL.md), or with [product-image-prompt](../product-image-prompt/SKILL.md) when it is a product for sale. Then write the motion prompt that attaches the result. A product still stays the same object: silhouette, proportions, materials, color, labels, and construction do not change. Only motion is described.

## Camera

If the clip names a camera path, or the job is a camera move, read [video-camera-control](../video-camera-control/SKILL.md) and write every camera clause from that skill. Keep Subject + Movement here when the subject also acts. A request that is only a camera path is written entirely by that skill. Do not invent a camera sentence in this skill.

## Workflow

1. If the still does not exist yet, follow the handoff above and stop.
2. Classify the job with the table below. If it is a camera move, or the clip names a camera path, follow the camera handoff.
3. Read the matching section in [templates.md](templates.md) and fill it. For image-to-video, apply the still-type table below before writing the sentence.
4. If a text-to-video request has no subject or no action, ask one question. Otherwise assume and proceed. On image-to-video, if they attached a still and named no action, infer one motion inside that still type and record it under **Assumptions**. A portrait with no named action gets a blink and a breath.
5. Run the checklist, then deliver.

When they want several options, share the subject and change one dimension only (the action, the speed, or the camera). Label them Variation A, B, and C.

A sequence is one prompt per clip. Each clip is one action. Attach the last frame of a clip as the first frame of the next.

## Classify

| Job | Use when | Template |
| --- | --- | --- |
| Image-to-video | A still should move | [Image-to-video](templates.md#image-to-video) |
| Text-to-video | No still; describe the shot | [Text-to-video](templates.md#text-to-video) |
| Camera move | The frame travels, with or without subject motion | [video-camera-control](../video-camera-control/SKILL.md) |
| Start and end | Two frames, and the clip is the motion between them | [Start and end](templates.md#start-and-end) |

An attached still selects image-to-video. A second still used as the destination selects start and end. A request that names only a camera path selects camera move.

## Write

Image-to-video formula:

> Prompt = Subject + Movement, then what holds still. Background + Movement only when the background should move.

The prompt is motion, physics, and a camera clause when they asked for one. It is not lighting, wardrobe, or the room.

- Name the subject that is already in the image, then the physical movement. "Put on sunglasses" fails. "Mona Lisa puts on sunglasses with her hand" works, because the model can see who acts and which body part moves.
- Name what holds still when a face, a product, a logo, a painting, an old photo, or the rest of a cinemagraph must survive. "The bottle stays rigid." "Only the steam moves."
- Several subjects: one clause each, in the order they should move. "Mona Lisa puts on sunglasses with her hand, and a ray of light appears in the background."
- Do not describe wardrobe, style, lighting, or the room. The still already contains them. Restating them, or inventing a different scene, tends to produce a cut or a transition. Photos with no named motion tend to stay static.
- Simple words and one sentence, or two short clauses. One action for a 5-second clip. A 10-second clip may add one follow-through with "then".
- The movement should obey ordinary physics and be something that picture could already do. A large departure from the still causes a cut.
- Skip motions these models smear: a bouncing ball, the arc of a throw, or finger-level choreography. Offer a simpler action that reads as the same idea, and say so under **Assumptions**.
- The camera stays fixed unless they asked for a move. When they do, the clause comes from video-camera-control: one named move, a direction, and a speed.
- A product, face, or layout in the still is locked. Say what moves. Do not ask the clip to redesign it.
- Spoken lines stay out of the motion prompt. If they asked for lip sync and the tool has a speech field, put the line in that field and let the motion prompt say who is speaking.
- If they named a model that generates sound, and they asked for sound, add one short sound clause. Room tone and footsteps are enough. Do not write dialogue into the motion sentence. Kling image-to-video is silent. Skip sound for it. Music and voiceover are a later step.

Match the still, then write the smallest motion that still reads.

| Still | Motion | Lock |
| --- | --- | --- |
| Portrait or selfie | A blink, a breath, or hair. No large head turn. | The face stays stable. The camera stays fixed unless they asked for a push-in. |
| Product | One accent that belongs on that object: a glint, steam, or a pour. | The product stays rigid: shape, label, and edges. |
| Landscape | Clouds, water, mist, or foliage. | The horizon stays level. |
| Artwork | Parallax, a small idle, or a glow on lights already in the picture. | Keep the linework, shading, and palette. Do not ask an illustration to become a photograph. |
| Old photo | A blink or a faint smile. | Keep the grain, the tones, and the era. |
| Logo | One light sweep across the mark. | The shape stays crisp. |
| Cinemagraph | One element moves, such as steam or a glow. | Everything else stays frozen. Static camera. |

A large head turn, or an end pose that must match a second picture, is a start-and-end job. One prompt that swings a face a long way warps it.

A sharp still with the subject separated from the background can take a camera move. A flat still gets a locked camera and one small motion. Say so under **Assumptions**.

If they name Motion Brush, or they want one painted region to move, the sentence still names that region and says the rest holds. Tell them to keep the painted path short, about 10 to 100 pixels. A long stroke smears. That note sits outside the prompt.

Text-to-video adds the setting, because nothing is attached. Still one or two simple sentences: subject, movement, setting. A camera clause, when they asked for one, comes from video-camera-control. Do not write a shot list or timestamps in this skill. A multi-shot camera plan is that skill's shot list.

Duration, aspect ratio, and quality mode are settings beside the prompt, not words inside it.

| Placement | Ratio |
| --- | --- |
| Story, reel, or TikTok | 9:16 |
| Feed or old photo | 4:5 |
| YouTube or landscape | 16:9 |
| Square | 1:1 |

Default duration is 5 seconds. Use 10 seconds when the action needs a follow-through. Use 15 seconds only when they asked for a clip longer than 10. Kling can export 1080p or 4K. Put 4K under **Settings** when they asked for it.

## Tool parameters

Add these beside the prompt, only when that tool was named. Nothing goes inside the motion sentence.

| Tool | Add |
| --- | --- |
| Kling | Duration (5, 10, or 15) and ratio. Professional when they asked for quality. Standard when they asked for a fast draft. Negative prompt, outside the motion sentence: warping, morphing face, extra fingers, flicker, background drift. |
| Runway, Luma, Veo, Sora, Pika, others | Duration and ratio on that tool's controls. If the tool has a negative field, use it only for artifacts (flicker, extra limbs, a warped face). Keep the scene in the positive prompt. |

## Checklist

- Every moving thing is a named subject plus a concrete movement.
- The action is one a person could act out from the sentence.
- Image-to-video does not re-describe the still.
- The motion could happen in that picture, it fits the duration, and it matches the still type.
- A face, product, logo, painting, old photo, or cinemagraph says what holds still.
- Multiple subjects are listed in order.
- A camera clause is present only when they asked, and it comes from video-camera-control.
- A product or face in the still is not redesigned.
- Duration and ratio sit under **Settings**, outside the fenced prompt.
- Assumptions sit outside the prompt.

## Deliver

Omit **Assumptions** when you assumed nothing. Omit a **Settings** line the user already fixed. When Kling is named, add a **Negative** line. The fenced block is the only text they paste.

**Job:** Image-to-video, portrait
**Assumptions:** 5 seconds. The still is a seated portrait, so the motion stays at a breath and a blink.
**Attach:** the still, as the scene
**Settings:** Kling, 9:16, 5 seconds
**Negative:** warping, morphing face, extra fingers, flicker, background drift

```text
The woman breathes once and blinks. Her face stays stable, and a few strands of hair shift.
```

**Refine next:**

- Keep her face stable, but let a light breeze lift her hair.
- Keep the same motion, and add a slow push-in.

For a set, repeat the block in clip order. The last frame of one clip is the first frame of the next. Faces, hands, and product labels often drift. When the clip features one of those, add one recovery prompt that repeats the lock and the same action. Say so in one sentence. Do not promise a perfect first generation.
