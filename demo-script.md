# One-minute demo

Use fictional details and one browser tab. Allow the initial model download to finish before recording.

- 0–10s: Show “Your words stay here” and explain that replies and reflection run on the device.
- 10–25s: Choose Decline an invitation. Say “Thanks for inviting me! I’m staying in tonight, but I’d like to join you another time.” Show the real generated reply.
- 25–40s: Generate reflection. Explain that the quote must match your reply and alternative wording is checked for unsupported new words.
- 40–50s: Choose “Try this reply again,” edit the reply, and show the rewind.
- 50–60s: Show optional saving and model-removal confirmation. Explain that saved transcripts and cached model files are separate.

## Privacy evidence capture

Open the browser Network panel before testing. After model loading completes, clear the panel and send a fictional reply, then generate reflection. Capture the resulting requests and inspect request payloads. Report what you actually observe; a quiet panel in one test is evidence of that test, not a guarantee about every browser or extension. Do not record private conversations, account cookies, headers, or credentials.

The source sends inference messages to the local WebLLM worker. Saved practice uses localStorage and export uses a local Blob. Hosting and model downloads still make network requests. localStorage is not encrypted by the app. This source audit is not a captured network trace.
