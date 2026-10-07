# 🎬 FootageFlow AI Video Editing Engine

> **Note:** This repository serves as an architectural overview and portfolio showcase for my work as **Co-Founder and Lead AI Engineer** at **FootageFlow** (Persist Ventures).

## 📖 Overview

**FootageFlow** is an AI-powered video editing platform designed to turn raw footage into structured stories. By simply providing prompts such as *"make a nostalgic 1-min recap,"* the system leverages LLMs (GPT-4) alongside video metadata to generate comprehensive editing plans and autonomously execute them using FFmpeg.

## 🏗️ Technical Architecture

### Tech Stack
- **AI / LLMs**: OpenAI GPT-4 API, Python
- **Video Processing**: FFmpeg, FFprobe
- **Backend**: FastAPI, Django, Celery
- **Database**: PostgreSQL

### Core Features & Implementation Details

1. **AI Editing Planner (LLM Integration)**
   - Built a custom orchestration layer that extracts metadata (duration, resolution, audio waveforms) from raw footage using FFprobe.
   - Feeds metadata into GPT-4 to generate a structured JSON editing plan, mapping out cuts, transitions, text overlays, and audio syncs to fit the requested narrative and mood.

2. **`FFmpegChainBuilder` Engine**
   - Engineered a modular `FFmpegChainBuilder` in Python to dynamically construct complex FFmpeg filtergraphs.
   - Supports advanced video manipulations:
     - Dynamic letterboxing and aspect ratio conversion.
     - Animated captions aligned with audio (using Whisper for transcription).
     - Soundtrack alignment and ducking (lowering background music volume when dialogue is present).
   - **Impact**: Modularizing the filtergraphs and chaining transitions natively within FFmpeg improved render speeds by **10x** compared to iterative processing.

3. **Asynchronous Render Pipeline**
   - Deployed the rendering engine using **Celery** and **FastAPI** to handle long-running video generation tasks efficiently, backed by PostgreSQL to track job states and progress.

## 💡 Engineering Challenges Solved

- **Complex FFmpeg Filtergraphs**: Managing massive, dynamically generated FFmpeg filtergraphs that would often fail due to mismatched stream mapping. Solved by writing a robust Python abstraction layer that validates stream inputs/outputs before execution.
- **Audio/Video Syncing**: Synchronizing AI-generated captions and background music drops with specific visual cues required parsing microsecond-level timestamps from the LLM and perfectly aligning them in FFmpeg.

## 🔗 Connect With Me

If you're interested in AI-driven media processing, complex backend architectures, or have a project in mind, let's connect!
- [LinkedIn](https://www.linkedin.com/in/tari-yekorogha/)
- [Upwork](https://www.upwork.com/freelancers/~01cb3c617ddbf2a8a8)
- [Twitter / X](https://x.com/whoisatary)
