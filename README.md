# ELIZA
Created by Chris Berg for ECON1626 Economics of Artificial Intelligence (RMIT). Based on [keithweaver/eliza](https://github.com/kweaver00/eliza) by Keith Weaver (MIT License)

An interactive browser demo of ELIZA, the classic 1966 natural language processing program, packaged as a single self-contained HTML file.

## What is ELIZA?

ELIZA is one of the earliest conversational programs in computing history. Created between 1964 and 1966 by Joseph Weizenbaum at the MIT Artificial Intelligence Laboratory, it simulated a Rogerian psychotherapist using a straightforward technique: pattern matching and keyword substitution. Despite having no understanding of the conversation, users frequently attributed genuine comprehension to it — a reaction Weizenbaum called the "ELIZA effect."

The program works by scanning user input for weighted keywords (e.g. *family*, *dream*, *computer*), selecting a response template for the highest-weight match, and substituting parts of the user's own sentence back into the reply with pronouns flipped. If no keyword is recognised it falls back to neutral prompts like *"Can you elaborate?"*.

This demo is relevant to ECON1626 (Economics of AI) as a historical case study in human–AI interaction, the gap between apparent and actual machine intelligence, and early public reactions to conversational systems.

## Running

Pull and open `eliza.html` in any modern browser. No server, build step, or internet connection required — everything is bundled into the single file.

## How it works

The implementation has four logical parts, all inlined into `eliza.html`:

| Component | Role |
|---|---|
| Response data | ~40 weighted keyword entries, synonym mappings, and wildcard patterns (e.g. `i am *1-3* happy`) |
| `analyze()` | Scans input against the sorted keyword list; handles wildcards and pronoun flipping |
| `selectResponse()` | Picks from candidate responses, boosting unused ones and wildcard-capable ones to reduce repetition |
| UI | Fixed input bar, chat bubbles, auto-dismissing notifications; no frameworks |

The original multi-file project (HTML + 4 JS files + 4 CSS files + CDN dependencies) has been consolidated into a single portable file with all assets embedded as base64 and all jQuery calls replaced with vanilla JS.

## "Show Working" panel

Click **Show Working ▶** (top-right corner) to open a live decision panel alongside the chat. After each of Eliza's replies the panel shows exactly how the response was chosen:

1. **Your message** — what you typed
2. **After cleaning** — the text after lowercasing and punctuation removal
3. **Searching rules** — which keyword rules were checked (highest priority first), where the search stopped, and whether a match was found or the fallback triggered
4. **Choosing a response** — how many responses the matched rule has, which was selected, and (for wildcard responses) what text was extracted from your message and any pronoun substitutions applied

The panel is intended to make the mechanics of the algorithm visible to students with no programming background.

## Demos

Type into the chat box and press Enter. Two scripted demos are also available:

- `run demo1` — a short stress/school conversation
- `run demo2` — the same dream message repeated eight times, demonstrating response variation

## Acknowledgements

Based on [keithweaver/eliza](https://github.com/kweaver00/eliza) by Keith Weaver (MIT License).
Original ELIZA program by Joseph Weizenbaum, MIT AI Lab, 1966.
