# Practice the Awkward Bit

A private conversation rehearsal app for someone who overthinks awkward exchanges. Built for the October 2026 DEV Build for a Friend challenge. Real friend details and handover feedback have not yet been supplied; do not imply user validation in a submission.

## Run

Node 22.13+; run `npm install`, then `npm run dev`. `npm run build` produces the deployment. Use a recent desktop browser with WebGPU and a compatible GPU. The initial model download requires internet and can be large. The inference runs locally after model loading; a fully offline site install is not implemented.

## Model

WebLLM `Llama-3.2-3B-Instruct-q4f16_1-MLC`, Meta's open-weight instruction model, quantized by MLC. Model weights, tokenizer and compiled runtime download from WebLLM's configured asset hosts. Model use is subject to the Llama 3.2 Community License and acceptable use policy; this is open-weight, not a claim that Llama is OSI-certified open source. See https://huggingface.co/meta-llama/Llama-3.2-3B-Instruct and https://github.com/mlc-ai/web-llm.

## Features

Three editable scenarios; supportive, neutral or mildly pushy role-play; five replies; separate feedback generation; retry from any user reply; optional browser-local saving, deletion and text export. Tailwind CSS 4 standard palette, typography, spacing and radius tokens.

## Privacy

The app contains no conversation API or analytics. Inference occurs in a dedicated worker on the device. Transcripts are in memory unless explicitly saved to localStorage or downloaded. Model assets are cached by WebLLM; deleting a saved practice deletes the transcript, not model cache. Users should delete saved conversations on shared devices. Hosting access logs may contain normal request metadata, but the app does not include transcripts in requests.

## Validation and limits

Run `node --experimental-strip-types tests/practice.test.ts` for rewind and prompt contract checks. Build/type verification does not establish model response quality. Model loading, latency and conversation quality must be measured on a suitable browser/GPU before claiming them in the submission. No friend testing has occurred. Generated feedback can be inaccurate. Text-only and English-first; no clinical assessment, personality scoring, cloud fallback, or mobile compatibility guarantee.

## Submission checklist

- Identify one real friend and explain the problem, with their identity private if desired.
- Record a real app demo on a compatible device, including feedback and retry.
- Document self-testing and model limitations honestly.
- Add public demo/repository links accessible to judges (the initial Sites deployment is private).
- Use the DEV submission template and required tags before October 5, 2026, 12:29 PM IST.
- Note changes committed after the deadline in this README.

## Credits

WebLLM / MLC AI, Meta Llama, React, Tailwind CSS 4, lucide-react, and the Sites starter and supplied UI primitives. Application source: MIT; dependencies and model artifacts retain their respective licenses.
