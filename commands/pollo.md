---
name: pollo
description: Use Pollo AI to pick a model, estimate credits, and create or edit images and videos in this conversation.
---

# /pollo

Treat Pollo as a multi-model studio on one account. The user already has a Pollo credit balance; this command should choose a model, spend only what they asked for, and keep the result usable for the next step.

Read the live Pollo MCP tool schemas before calling anything. Model IDs, fields, and limits change; do not rely on memory.

## Usage

```
/pollo <what to make or look up>
```

```
/pollo 16:9 poster of a glass greenhouse on Mars — pick a current image model
/pollo Turn this still into a 5s 9:16 product clip with a slow push-in
/pollo What does google/nano-banana-pro require, and how many credits for one 16:9 image?
/pollo Upscale the last image; then restyle it
/pollo How many credits are left?
```

## How to work

1. **Name the model from the catalog.** If the user did not pin a brand/model, or you are unsure of fields, list models and read that model's constraints. Never invent `brand`, `model`, aspect ratio, duration, or enum values.
2. **Estimate when spend is unclear.** Call the cost estimator with the same input you would generate. Say the credit number before a large or video run unless the user already approved it.
3. **Generate once per ask.** Image requests use the image generate tool; video requests use the video generate tool. Dual-capability models need an explicit type. Batch only when the user wants several independent jobs.
4. **Chain assets in this chat.** A finished image can be the next image's reference or a video's first frame. Keep product, character, and style references together — upload extra stills when the model accepts multiple inputs.
5. **Prefer a dedicated edit** when they asked to upscale, reframe, restyle, remove background, lip-sync, or drive motion. Do not re-generate from scratch to fake an edit.
6. **Upload first.** Local files and chat attachments must go through Pollo upload/import and come back as a URL the generate/edit tools accept. Do not paste raw file paths into model fields.
7. **Poll the task the user owns.** Generate returns a `taskId` immediately. Wait on that id until it finishes. Videos take longer; say so. Do not hammer status more than about once every few seconds. Do not query someone else's task id.
8. **Credits are the Pollo website balance.** Read account status for remaining credits. If a run fails for insufficient credits, stop and use the plans/credits tool or tell them to top up on pollo.ai — do not pretend the balance changed.

If a call fails with a typed error (moderation, missing field, unowned task), fix that input. Repeating the identical call will not help.
