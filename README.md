# Infinite Wiki

A minimal, zero-dependency, infinite encyclopedia powered by the Gemini API. Every word generated is a clickable hyperlink that generates a new, highly detailed definition in real-time.

Adhering to a strict minimalist design philosophy, this project contains no build steps, no bundlers, and no external libraries.

## Features
- **Single File:** The entire application (HTML, CSS, JS) is contained within `index.html`.
- **Zero Dependencies:** No Node.js, React, or SDKs. Uses native browser APIs (`fetch`, `TextDecoder`, `DocumentFragment`).
- **Native Streaming:** Parses Server-Sent Events (SSE) directly from Google's REST endpoints for ultra-low latency text streaming.
- **Local Storage:** Your API key is saved locally in your browser's `localStorage`. It is never sent anywhere except directly to Google's API.

## Usage

1. Obtain a [Google Gemini API Key](https://aistudio.google.com/app/apikey).
2. Open `index.html` directly in any modern web browser (no local server required).
3. Paste your API key into the input field in the top right corner.
4. Search for a topic, or click "Random" to begin.
5. Click any word in the generated text to infinitely traverse topics.

## Architecture Notes
- **State Management:** Handled implicitly by the DOM to avoid Virtual DOM overhead.
- **Network:** Uses `AbortController` to instantly kill pending streams if a new topic is clicked, saving bandwidth and preventing race conditions.
- **Model:** Hardcoded to use `gemini-2.5-flash` with `thinkingBudget: 0` for maximum speed.
