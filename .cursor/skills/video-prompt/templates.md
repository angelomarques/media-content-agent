# Video prompt templates

Fill the matching template as one or two simple sentences. Drop a slot the user ruled out. Examples are quality targets, not text to reuse.

Duration, aspect ratio, and quality mode go under **Settings** in the delivery, not in the fenced prompt.

## Image-to-video

{Subject} {concrete movement}. {What holds still, when a face, product, logo, painting, old photo, or the rest of a cinemagraph must survive.} {Background element} {its movement, only if the background should move}.

The subject is whoever or whatever is already the focus of the still: a person, animal, plant, or object. The movement is the body part or object changing, not a goal. "Puts on sunglasses with her hand" tells the model the action. "Put on sunglasses" does not.

Match the still-type table in SKILL.md. A portrait stays at a blink, a breath, or hair. A product stays rigid. A cinemagraph names the one moving element and freezes the rest.

Leave out clothing, place, lens, and style. Those are in the image. Add a background clause only when something behind the subject should move.

One action in five seconds. At ten seconds, one action and a short follow-through joined by "then".

Weak, because the actor and the gesture are missing:

```text
Put on sunglasses.
```

The same idea, aimed at the person in the painting:

```text
Mona Lisa puts on sunglasses with her hand.
```

The same idea, with the background moving too:

```text
Mona Lisa puts on sunglasses with her hand, and a ray of light appears in the background.
```

A still that already implies a simple action:

```text
The little boy smiles at the camera.
```

Two subjects, listed in order:

```text
The two people turn toward each other and hug.
```

A subject and the air around them:

```text
The model smiles while the wind lifts her hair.
```

An object doing one plausible action:

```text
The cat kneads the dough with both paws.
```

Speed as part of the movement, still one action:

```text
The cyclist pedals hard along the highway, and the wheels blur with speed.
```

A portrait, with the face locked and the camera fixed:

```text
The woman breathes once and blinks. Her face stays stable, and a few strands of hair shift.
```

A product accent. The object does not turn:

```text
A thin stream of liquid splashes beside the bottle. The bottle stays rigid, and its label stays sharp.
```

A cinemagraph. One element moves:

```text
Steam curls up from the cup. Everything else in the frame stays frozen.
```

An old photo. The smallest motion, and the print survives:

```text
The man blinks and his smile deepens slightly. The grain and the tones stay as they are.
```

If they attached a still and named no action, pick the smallest motion that still type allows. An empty prompt is only for when they explicitly want the model to invent the motion. Say that under **Assumptions**, and still offer one directed prompt they can paste instead.

## Text-to-video

{Shot size} of {subject} {movement}, in {setting}. {Background movement, if any.}

The model has no image, so the setting has to be in the sentence. Keep it to one place and one action. Do not add a second beat unless the clip is 10 seconds and the second beat is a follow-through.

```text
A medium shot of a baker sliding a blistered loaf onto a wire rack, in a narrow kitchen at dawn. Flour hangs in the light from the street window.
```

If they also asked the camera to move, write the subject and the setting here, then append the clause from [video-camera-control](../video-camera-control/SKILL.md). Do not invent the camera sentence in this file.

## Camera move

Stop. Follow [video-camera-control](../video-camera-control/SKILL.md). Subject motion for the same clip still uses the image-to-video or text-to-video section above. The camera clause comes only from that skill.

## Start and end

{Subject} {the movement that connects the first still to the second}.

Both frames are attached. Do not describe either picture. Describe only the change between them. If the change is a camera reveal, add the clause from [video-camera-control](../video-camera-control/moves.md#reveal). If the two pictures show different scenes, say so under **Assumptions**: the clip will read as a transition, and a smaller change between frames holds together better.

```text
The woman lowers her hand from her hat to her side and turns her face toward the window.
```

Attach the first still as the opening frame and the second as the end frame, in that order.
