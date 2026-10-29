---
name: video-camera-control
description: >-
  Writes the camera clause for AI video prompts: push-in, pull-back, pan, tilt,
  track, orbit, or a static camera, and a multi-shot list where each shot has
  one move. Use when the user asks for camera control, a camera move, a dolly,
  push, pull, pan, tilt, tracking shot, or orbit, or when video-prompt is
  writing a clip that names a camera path. One main move per shot. Subject
  motion stays with video-prompt.
---

# Video camera control

Write how the camera moves. One main move per shot, with a direction and a speed. A vague line ("cinematic camera", "make it cool") and a stack of moves in one clip both come out unstable.

The method follows Kling's camera-control guide and applies to Kling, Runway, Veo, Sora, Luma, Pika, and similar models. [video-prompt](../video-prompt/SKILL.md) owns subject motion and calls this skill for every camera clause. This skill writes the prompt. Do not generate a video unless the user asks for one.

## When video-prompt calls this

Read this skill when the clip names a camera path, or the job is a camera move. Keep video-prompt's Subject + Movement sentence. Append one camera clause from [moves.md](moves.md). If this skill is used alone, write the subject action in that same shape so a person or animal does not freeze, then the camera clause.

Image-to-video still does not restate the room, the wardrobe, or the light. The still has them. Text-to-video still names the setting, because nothing is attached. A missing still goes to [image-prompt](../image-prompt/SKILL.md), or to [product-image-prompt](../product-image-prompt/SKILL.md) when the subject is a product for sale. A product stays the same object. The move only shows a detail or the whole object.

## Workflow

1. If the still does not exist yet, follow the handoff above and stop.
2. Pick one move from the table. If they named several moves for one clip, split them into a shot list, one move each, and record that under **Assumptions**.
3. Read the matching section in [moves.md](moves.md) and fill it.
4. If they asked for a camera and did not name the move, use a slow push-in and record that under **Assumptions**.
5. Run the checklist, then deliver in the same shape as video-prompt.

When they want several options, keep the subject and change only the move, the speed, or the direction. Label them Variation A, B, and C.

## Classify

| Move | Words to use | Use when |
| --- | --- | --- |
| Push in | slow push-in toward {subject} | A face, logo, texture, or action should get closer |
| Pull back | pulls back from {subject} to reveal {environment} | The clip should show scale or the room around a close subject |
| Pan | pans left, or pans right | A lineup, a room, a street, or action moving sideways |
| Tilt | tilts up, or tilts down | The frame travels from a low detail to a high one, or the reverse |
| Track | tracks forward, or tracks alongside | The subject is traveling and the camera should follow |
| Orbit | orbits slowly | The camera turns around a still or slow subject |
| Static | static camera | The subject carries the motion |

Map their words onto that list: dolly in and zoom in become push in; dolly out and zoom out become pull back. Record the mapping under **Assumptions**.

Shot size (wide, medium, close-up) may sit in the same sentence. It is not a second move.

## Write

Single-shot formula:

> Subject + Movement, then Camera move + speed + what it emphasizes or reveals

- Name the direction: push in, pull back, pan left, pan right, tilt up, tilt down, track forward, orbit slowly, or static camera.
- One main move. "Push in, pan left, tilt up, and orbit" in one clip is the failure mode. Split it.
- Say the speed: slow, unless they asked for fast. Add "stable" for a pan, a tilt, or a track. Do not also ask for handheld shake.
- A push-in and a pull-back need a purpose: "to emphasize the garnish" or "to reveal the skyline". A pan and a tilt need a destination: "pans right across the desk" or "tilts up from the shoes to the face".
- A pull-back needs a clear starting subject and a clear thing to reveal. A tilt needs a clear top and a clear bottom. If the picture has neither, pick another move and say so under **Assumptions**.
- Keep the subject's own action small during the move. A slow push-in on someone who also turns, walks, and changes expression smears. A push-in on a still or slow subject holds.
- The subject's path and the camera's path stay easy to follow. Do not send a fast subject one way and pan the other way.
- Do not combine opposites. "Static camera with a fast push-in and an orbit" is two instructions. Pick one.
- Leave quality tags out of the sentence. 4K, duration, and mode are settings. Higher resolution does not repair a vague move.
- A multi-shot storyboard is one move per shot. Repeat the same subject description. Each shot starts where the previous one ended.

When they name a multi-shot or storyboard mode, such as Kling Omni, put the shot list in one fenced block:

```text
Shot 1: Wide shot. The creator walks into the studio. Static camera.
Shot 2: She sits at the desk. The camera slowly pushes in.
Shot 3: The camera pans right across the monitor.
```

Otherwise deliver one prompt per shot, in order.

For a product, the default move is a slow push-in on one detail. Use a pull-back when they want the whole object, and a slow pan when they want a lineup. The product does not change shape, labels, or construction.

## Checklist

- The move is one of: push in, pull back, pan left, pan right, tilt up, tilt down, track, orbit, static.
- The shot has one main move.
- Speed and direction are in the sentence.
- A push-in or pull-back says what it emphasizes or reveals.
- Subject action is simple enough to act out during that move.
- Image-to-video does not re-describe the still.
- The camera clause does not contradict the subject clause.
- Duration, ratio, and 4K sit under **Settings**.

## Deliver

Same shape as video-prompt. Omit **Assumptions** when you assumed nothing. The fenced block is the only text they paste.

**Job:** Image-to-video, push-in
**Assumptions:** Slow push-in, because they asked for a camera move and did not name one.
**Attach:** the still, as the scene
**Settings:** 16:9, 5 seconds

```text
The woman looks past the camera and smiles. The camera slowly pushes in to emphasize her face.
```

**Refine next:**

- Keep the push-in, and have her stay still except for one blink.
- Same action, but the camera pulls back to reveal the chair and the wall behind her.

Faces, hands, and product edges drift when the camera travels. Add one recovery prompt that repeats the same move and a simpler subject action. Say so in one sentence. Do not promise a perfect first generation.
