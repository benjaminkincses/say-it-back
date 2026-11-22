# Say It Back

[![Made with pollinations.ai](https://raw.githubusercontent.com/pollinations/pollinations/main/packages/ui/src/brand/badge-made-with.svg)](https://pollinations.ai/?ref=badge)

Practise speaking or singing a line and get word by word feedback.

Pick a line or type your own, hear it read aloud, record yourself, and the app
checks your take: which words matched, which were missed or wrong, where the
long pauses were, plus a short coach note.

## How it works

Frontend only. The page calls gen.pollinations.ai directly from the browser
with the visitor's own key:

- Sign-in: the Pollinations drop-in button (`<polli-connect>`), Pollinations
  Pay / BYOP. The key stays in the tab session. There is no key paste box and
  no server.
- Hear the line: `openai/tts-1` on `/v1/audio/speech`.
- Check a take: the recording goes to `/v1/audio/transcriptions` with
  `openai/whisper-large-v3`, `verbose_json` and word timestamps. Words are
  aligned to the target with an LCS match; timing notes come from the word
  timestamps.
- Coach note: `openai/gpt-5.4-nano` on `/v1/chat/completions`.

A demo button shows the full result screen with a canned example, no sign-in
needed.

## Run it

Open `index.html` from any static host, or just open the file in a browser.
Microphone recording needs a secure context (https or localhost), which
GitHub Pages provides.

Built for Pollinations quest #20022.
