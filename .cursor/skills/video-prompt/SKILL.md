---
name: video-prompt
description: >-
  Writes ready-to-paste prompts for AI video models (Kling, Runway, Veo, Sora,
  Luma, Pika, and similar). Use when the user asks for a video prompt,
  image-to-video or text-to-video prompt, to animate a photo, direct subject
  motion, or specify a camera move. Image-to-video uses Subject + Movement and
  leaves the still's scene undescribed. Text-to-video adds the setting because
  no image is attached. A named camera move is handed to video-camera-control.
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
3. Read the matching section in [templates.md](templates.md) and fill it.
4. If a text-to-video request has no subject or no action, ask one question. Otherwise assume and proceed. On image-to-video, if they attached a still and named no action, infer one motion the picture already suggests and record it under **Assumptions**.
5. Run the checklist, then deliver.

When they want several options, share the subject and change one dimension only (the action, the speed, or the camera). Label them Variation A, B, and C.

A sequence is one prompt per clip. Each clip is one action, and the next clip starts where the previous one ends.

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

> Prompt = Subject + Movement, Background + Movement

- Name the subject that is already in the image, then the physical movement. "Put on sunglasses" fails. "Mona Lisa puts on sunglasses with her hand" works, because the model can see who acts and which body part moves.
- Several subjects: one clause each, in the order they should move. "Mona Lisa puts on sunglasses with her hand, and a ray of light appears in the background."
- Do not describe wardrobe, style, lighting, or the room. The still already contains them. Restating them, or inventing a different scene, tends to produce a cut or a transition. Photos with no named motion tend to stay static.
- Simple words and one sentence, or two short clauses. One action for a 5-second clip. A 10-second clip may add one follow-through with "then".
- The movement should obey ordinary physics and be something that picture could already do. A large departure from the still causes a cut.
- Skip motions these models smear: a bouncing ball, the arc of a throw, or finger-level choreography. Offer a simpler action that reads as the same idea, and say so under **Assumptions**.
- The camera stays fixed unless they asked for a move. When they do, the clause comes from video-camera-control: one named move, a direction, and a speed.
- A product, face, or layout in the still is locked. Say what moves. Do not ask the clip to redesign it.
- Spoken lines stay out of the motion prompt. If they asked for lip sync and the tool has a speech field, put the line in that field and let the motion prompt say who is speaking.
- If they named a model that generates sound, and they asked for sound, add one short sound clause. Room tone and footsteps are enough. Do not write dialogue into the motion sentence.

Text-to-video adds the setting, because nothing is attached. Still one or two simple sentences: subject, movement, setting. A camera clause, when they asked for one, comes from video-camera-control. Do not write a shot list or timestamps in this skill. A multi-shot camera plan is that skill's shot list.

Duration, aspect ratio, and quality mode are settings beside the prompt, not words inside it.

| Placement | Ratio |
| --- | --- |
| Story, reel, or TikTok | 9:16 |
| YouTube or landscape | 16:9 |
| Square | 1:1 |

Default duration is 5 seconds. Use 10 seconds when they asked for a longer clip or the action needs a follow-through. Kling accepts 16:9, 9:16, and 1:1. If they asked Kling for another ratio, use the nearest of those three and record it under **Assumptions**.

## Tool parameters

Add these beside the prompt, only when that tool was named. Nothing goes inside the motion sentence.

| Tool | Add |
| --- | --- |
| Kling | Standard or Professional, duration (5 or 10), and ratio (16:9, 9:16, or 1:1). Professional when they asked for quality. Standard when they asked for a fast draft. |
| Runway, Luma, Veo, Sora, Pika, others | Duration and ratio on that tool's controls. If the tool has a negative field, use it only for artifacts (flicker, extra limbs, a warped face). Keep the scene in the positive prompt. |

## Checklist

- Every moving thing is a named subject plus a concrete movement.
- The action is one a person could act out from the sentence.
- Image-to-video does not re-describe the still.
- The motion could happen in that picture, and it fits the duration.
- Multiple subjects are listed in order.
- A camera clause is present only when they asked, and it comes from video-camera-control.
- A product or face in the still is not redesigned.
- Duration and ratio sit under **Settings**, outside the fenced prompt.
- Assumptions sit outside the prompt.

## Deliver

Omit **Assumptions** when you assumed nothing. Omit a **Settings** line the user already fixed. The fenced block is the only text they paste.

**Job:** Image-to-video
**Assumptions:** 5 seconds. The still shows a seated woman, so the action is a smile and a look off-camera.
**Attach:** the still, as the scene
**Settings:** 9:16, 5 seconds

```text
The woman looks past the camera and smiles, and her hair lifts in a light breeze.
```

**Refine next:**

- Keep the same action, but have her raise one hand to hold her hat.
- Keep her motion the same, and add a slow push-in.

For a set, repeat the block in clip order and say which result to extend or attach next. Faces, hands, and product labels often drift. When the clip features one of those, add one recovery prompt that repeats the lock and the same action. Say so in one sentence. Do not promise a perfect first generation.
