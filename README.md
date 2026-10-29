# Media content agent

Skills for creating media with AI. Cursor loads them from `.cursor/skills/` in this project.

## Skills

- **image-prompt** — Writes a narrative prompt for AI image generation and editing. The method follows Google's Gemini and Nano Banana guides and OpenAI's GPT Image guide: describe the scene, then fill a template for the job (photo, sticker, text, infographic, UI mockup, comic, edit, translate, try-on, sketch render, cutout, style transfer, reference images with a role each, or a scene driven by a current fact). A product showcase is handed to product-image-prompt.
- **product-image-prompt** — Writes catalog prompts for a physical product. One master shot is the source of truth, and later shots keep that product identical: what's-in-the-box flat lay, macro, colorways, scale or fit, in-use, lifestyle, UGC, negative-space banner, and shop-the-look.
- **video-prompt** — Writes a motion prompt for AI video models. Image-to-video is Subject + Movement, and it does not re-describe the still. Text-to-video adds the setting. A camera move is handed to video-camera-control. A missing still is handed to image-prompt or product-image-prompt first.
- **video-camera-control** — Writes the camera clause: one push, pull, pan, tilt, track, orbit, or static camera per shot, with a direction and a speed. video-prompt calls it whenever a clip names a camera path. A multi-shot plan is one move per shot.
