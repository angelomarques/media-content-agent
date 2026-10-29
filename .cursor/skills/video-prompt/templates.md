# Video prompt templates

Fill the matching template as one or two simple sentences. Drop a slot the user ruled out. Examples are quality targets, not text to reuse.

Duration, aspect ratio, and quality mode go under **Settings** in the delivery, not in the fenced prompt.

## Image-to-video

{Subject} {concrete movement}. {Next subject} {its movement}. {Background element} {its movement}.

The subject is whoever or whatever is already the focus of the still: a person, animal, plant, or object. The movement is the body part or object changing, not a goal. "Puts on sunglasses with her hand" tells the model the action. "Put on sunglasses" does not.

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

If they attached a still and named no action, pick the smallest motion the picture already suggests: a smile, a blink, steam rising, a curtain shifting. Write that as subject plus movement. An empty prompt is only for when they explicitly want the model to invent the motion. Say that under **Assumptions**, and still offer one directed prompt they can paste instead.

## Text-to-video

{Shot size} of {subject} {movement}, in {setting}. {Background movement, if any.} {Camera clause, only if they asked.}

The model has no image, so the setting has to be in the sentence. Keep it to one place and one action. Do not add a second beat unless the clip is 10 seconds and the second beat is a follow-through.

```text
A medium shot of a baker sliding a blistered loaf onto a wire rack, in a narrow kitchen at dawn. Flour hangs in the light from the street window.
```

With a camera they asked for:

```text
A wide shot of a red-crowned crane stepping through shallow water, looking for food. The camera slowly follows at water level.
```

## Camera move

{Subject} {small movement, or "holds still"}. The camera {path, speed, and direction}.

Use this when they asked for a move, or when the only change is the frame. A person or animal who holds perfectly still looks frozen, so give them one small action unless the user wants a locked subject. Name the path in plain words: pushes in, pulls back, pans left, rises, follows, or orbits.

A description of a new scene here causes a cut. Keep the clause about the camera, not about a different place.

```text
The woman stays seated and blinks once. The camera slowly pushes in.
```

```text
The cyclist keeps pedaling. The camera tracks alongside, low to the road.
```

## Start and end

{Subject} {the movement that connects the first still to the second}.

Both frames are attached. Do not describe either picture. Describe only the change between them. If the two pictures show different scenes, say so under **Assumptions**: the clip will read as a transition, and a smaller change between frames holds together better.

```text
The woman lowers her hand from her hat to her side and turns her face toward the window.
```

Attach the first still as the opening frame and the second as the end frame, in that order.
