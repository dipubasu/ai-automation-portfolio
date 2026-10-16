# YouTube Automation — Topic to Short-Form Video

## Business problem
Producing a short video usually involves several separate tasks: choosing a hook, writing a script, planning scenes, creating visuals, recording narration, editing, rendering, and uploading. Repeating these steps for every topic can make content production slow and difficult to standardize.

## Solution
I built an n8n pipeline that takes a topic and generates structured video metadata, a short voiceover script, and four scene prompts. It then generates scene images, creates a voiceover, uploads assets to Shotstack, assembles and renders a vertical video, and uploads the result to YouTube with private visibility configured in the exported workflow.

## Business value
- Connects several repetitive production steps into one workflow.
- Creates a consistent starting structure for short-form content.
- Reduces manual handoffs between writing, asset generation, rendering, and upload.
- Leaves the uploaded video private by default in the current export, allowing review before public release.

## How it works
1. A manual run starts from a configured topic.
2. OpenAI generates the title, description, script, and scene prompts.
3. Image and voice assets are generated and uploaded for processing.
4. Shotstack renders a vertical MP4 from the generated assets.
5. The rendered file is downloaded and uploaded to YouTube; the workflow prepares links to the uploaded video.

## Intended use
Creators or small marketing teams that want a repeatable starting point for producing short educational or promotional videos.

## Setup and limitations
Configure OpenAI, Cloudflare image generation, ElevenLabs, Shotstack, and YouTube credentials and account IDs. Verify provider endpoints, asset ingestion status, rendering completion, YouTube privacy settings, and quota limits. AI-generated facts and visuals still need editorial review; the workflow does not guarantee views, engagement, or monetization.

## How I would measure success
Track end-to-end render success, editing time per video, cost per finished video, rework rate, and viewer retention after publishing. These are suggested measures, not claimed results.

## Testing and export
I live-tested this workflow in my own n8n environment. The export uses placeholders for service credentials and is intended to be configured before use in another instance.

[Open workflow JSON](youtube-automation-topic-to-video.json)

## Code reuse and permissions

This project is public for viewing, review, testing, and portfolio evaluation. **Permission is required before reusing, copying, modifying, redistributing, or incorporating any code or other material from this project into another project or product.** Please contact the copyright holder and obtain written permission before reuse. Viewing or testing this project does not grant reuse rights. See the repository root [LICENSE](../LICENSE).
