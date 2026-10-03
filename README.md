# Practice the Awkward Bit

A private conversation rehearsal app for someone who overthinks awkward exchanges. Built for the October 2026 DEV Build for a Friend challenge. Real friend details and handover feedback have not yet been supplied; do not imply user validation in a submission.

## Run

Node 22.13+; run `npm install`, then `npm run dev`. `npm run build` produces the deployment. Use a recent desktop browser with WebGPU and a compatible GPU. The initial model download requires internet and can be large. The inference runs locally after model loading; a fully offline site install is not implemented.

## Model

WebLLM `gemma-2-2b-it-q4f16_1-MLC`, Google's open-weight instruction model, quantized by MLC. Model weights, tokenizer and compiled runtime download from WebLLM's configured asset hosts. Model use is subject to the Gemma Terms of Use; this is open-weight, not a claim that Gemma 2 is OSI-certified open source. See https://ai.google.dev/gemma/terms and https://huggingface.co/google/gemma-2-2b-it and https://github.com/mlc-ai/web-llm.

## Features

Three editable scenarios; supportive, neutral or mildly pushy role-play; five replies; separate feedback generation; retry from any user reply; optional browser-local saving, deletion and text export; separate downloaded-model removal with confirmation. Tailwind CSS 4 standard palette, typography, spacing and radius tokens.

Feedback quotes must match a user reply. Suggestions come from three safe wording options. Alternatives may use only words from the quoted reply plus a small set of connecting and polite words; unsupported new words are rejected. This is deliberately conservative and can reject reasonable synonyms. It reduces invented details but does not guarantee semantic correctness.

## Privacy

The app contains no conversation API or analytics. Inference occurs in a dedicated worker on the device. Transcripts are in memory unless explicitly saved to localStorage or downloaded. Model assets are cached by WebLLM; deleting a saved practice deletes the transcript, not model cache. Users should delete saved conversations on shared devices. Hosting access logs may contain normal request metadata, but the app does not include transcripts in requests.

## Validation and limits

Run `node --experimental-strip-types tests/practice.test.ts` for rewind, prompt, and structured feedback validation checks. Gemma loading, a real generated reply, structured feedback, reply rewind, and browser-local save/restore were exercised in the desktop browser. IndexedDB caches model assets. This is a smoke test, not a quality benchmark: feedback can still invent details or give awkward wording. The export control was exercised, but automated download capture was unavailable. No friend testing has occurred. Text-only and English-first; no clinical assessment, personality scoring, cloud fallback, or mobile compatibility guarantee. Keep one practice tab open to avoid loading duplicate models into GPU memory.

## Submission checklist

- Identify one real friend and explain the problem, with their identity private if desired.
- Record a real app demo on a compatible device, including feedback and retry.
- Document self-testing and model limitations honestly.
- Add public demo/repository links accessible to judges (the initial Sites deployment is private).
- Use the DEV submission template and required tags before October 5, 2026, 12:29 PM IST.
- Note changes committed after the deadline in this README.

## Credits

WebLLM / MLC AI, Google Gemma, React, Tailwind CSS 4, lucide-react, and the Sites starter and supplied UI primitives. Application source: MIT; dependencies and model artifacts retain their respective licenses.
