# Case Study: YouTube Automation — Topic to Video

## Overview
A multi-step n8n pipeline that takes a video topic through content planning, visual and voice asset generation, video rendering, and YouTube upload.

## Workflow design
The 26-node export includes a manual trigger, topic/configuration nodes, OpenAI ideation, video details, scene prompt splitting, image generation and file conversion, upload-URL requests and asset uploads, ingest waits and checks, voiceover generation, Shotstack payload construction and render-status polling, video download, and YouTube upload.

## Integrations
OpenAI, image-generation and audio-generation services configured through HTTP requests, Shotstack, and YouTube. The exact provider configuration should be read from the exported node parameters and environment settings.

## Why this design
Breaking the process into asset generation, upload, render, and publish stages makes the pipeline easier to inspect and troubleshoot than a single opaque operation.

## Configuration and boundaries
Review API endpoints, request payloads, asset URLs, polling intervals, and YouTube visibility settings. Rendering and upload depend on external service quotas and successful asynchronous processing. Test with private/unlisted output and non-sensitive credentials before public publishing.

## Testing and status
Live-tested by the author in their configured n8n environment. This case study does not claim a specific number of videos, views, or time saved.


## Workflow export

[**Open the n8n workflow JSON**](youtube-automation-topic-to-video.json)
