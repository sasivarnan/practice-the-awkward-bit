*A submission for the [Hacktoberfest Weekend Challenge: Build for a Friend](https://dev.to/challenges/hacktoberfest-weekend-2026-10-01).*

## What I Built

I’m an introvert. Sometimes I want to rehearse a conversation before having it—but the words I’m struggling with can also be personal.

That’s the idea behind **Practice the Awkward Bit**: a place to find your words without sending them to an AI service.

You can rehearse: decline an invitation, ask for something back, or join a conversation. Set the scene, choose how cooperative the other person is, and try a few replies.

Gemma plays the other person. When you finish, it offers one thing you expressed clearly, one suggestion, and another way to say it. **“Try this reply again”** takes you back to an earlier message so you can experiment.

I built it for fellow introvert people who want a little practice before a real conversation. Testing so far uses fictional conversations; I haven’t tested it with a friend.

## Demo

[Try the app](https://practice-the-awkward-bit.sasivarnan.chatgpt.site)

Use a desktop browser with WebGPU. Load the model, choose **Decline an invitation**, and try:

> Thanks for inviting me! I’m going to stay in tonight, but I’d like to join you another time.

Then ask for a reflection or retry your reply. The first model download is large and needs internet.

### Private by default

- **Replies and reflection run on your device.** Conversation text is not sent to an inference API.
- **No transcript is saved automatically.** Refresh clears an unsaved practice.
- **You choose what to keep.** Saving uses this browser’s localStorage; export creates a text file. Saved practice can be deleted.

Local storage is not encrypted by the app, so be careful on a shared device. The site and model downloads still make network requests, and hosting can keep ordinary request metadata. Deleting a practice does not delete the cached model.

## Code

[Source on GitHub](https://github.com/sasivarnan/practice-the-awkward-bit) · MIT license for the app.

## How I Built It

React, TypeScript, and Tailwind CSS 4 handle the interface. **Gemma 2 2B** runs locally through [WebLLM](https://github.com/mlc-ai/web-llm), in a dedicated worker.

```text
Model hosts ── download ──▶ IndexedDB cache
                                  │
                      Inside your browser
                                  ▼
React UI ◀── messages ──▶ Web Worker
   │                       WebLLM + Gemma 2 2B
   │                              │
   │                            WebGPU
   ▼
Conversation in memory
   ├─ Optional localStorage save
   └─ Text export

Conversation text stays on the device.
```

Role-play and reflection use separate prompts. Reflection returns structured JSON, and the app checks that its quoted reply actually came from the user.

Model loading, real replies, reflection, rewind, and save/restore worked in the desktop browser test. Tests, type checks, and the build passed. Feedback can still invent details. Treat it as a suggestion to try, not a prediction of how someone will react.

## Why Does Open Innovation Matter?

For this app, open innovation makes the privacy design possible. WebLLM runs Gemma’s weights on the user’s device, so both the conversation and the reflection can happen without a server receiving the transcript.

There is also no per-conversation inference API bill. The user supplies the compute.

I can also inspect the prompts and swap supported models. The tradeoff is a large download and dependence on the user’s hardware. This isn’t a fully offline install, and [Gemma’s terms](https://ai.google.dev/gemma/terms) still apply.

[Rahul’s post on browser-local LLMs](https://dev.to/rahul_80cfa43302b/a-simple-react-hook-for-running-local-llms-via-webgpu-5234) helped frame the worker and loading experience.

## Prize Categories

**Best Use of Gemma:** Gemma powers both the conversation partner and the reflection locally. That makes it possible to rehearse personal exchanges without uploading them for inference.

## Credits

Google Gemma, MLC AI/WebLLM, React, Tailwind CSS, lucide-react, and the Sites/Vinext starter.

Codex helped build, debug, test, and draft this post.

