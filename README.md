# Free video generation on Colab

A single Colab notebook that generates AI video on Google's **free** GPU — no
debit/credit card, just a Google account. Built because real video generation
can't run on this laptop (no GPU), but Colab lends you one for free.

## Open it

Once this repo is on GitHub, open the notebook straight in Colab:

> **https://colab.research.google.com/github/Chalcepro/video-colab/blob/main/free_video_colab.ipynb**

Or: go to [colab.research.google.com](https://colab.research.google.com) →
**File → Upload notebook** → pick `free_video_colab.ipynb`.

Then **Runtime → Change runtime type → T4 GPU → Save**, and run the cells top
to bottom.

## What it does

- **Text → video** — type a prompt, get a ~6-second clip (`CogVideoX-2B`).
- **Image → video** — animate a still, including a frame pulled from *your own*
  video (`Stable Video Diffusion`).
- **Video → video** — upload your clip; it keeps *your* motion and composition
  and re-renders the look from a prompt (`CogVideoX-2B`, `strength` dial). This
  is the "same motion, new render" path, and object placement comes from your
  real frames, not the model's guess.
- **Direct it scene by scene** — continue from the last frame with a new prompt
  (`CogVideoX-5B-I2V`), then stitch the chain into one video.
- **Upscale to 1080p** and optionally **smooth to 30fps** (ffmpeg).

### What it still can't do (honest)
These free models don't *track* objects — they predict pixels. Short, simple
motion holds together; busy scenes, occlusions, small details, hands and text
will morph or fade in/out. Video→video and image→video are steadier (they start
from real frames). A true "watch my whole video and remake it perfectly" needs
a bigger model on a real GPU.

## Honest limits

- Short clips (a few seconds), native ~480–720p, upscaled to 1080p.
- ~1–5 minutes per clip once the model is loaded; first run downloads a few GB.
- Decent quality — not Runway/Kling. It's the free tier.
- Free Colab disconnects after a few hours and has a weekly cap. Mount Drive
  (cell 3) so the model cache and your outputs survive between sessions.

There is **no** free "watch my video and remake it from scratch" button — not
here, not anywhere, on a free GPU. The realistic version is the two paths above.
