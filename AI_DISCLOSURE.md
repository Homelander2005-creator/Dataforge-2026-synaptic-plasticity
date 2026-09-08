# AI / Code / Asset Disclosure

AI assistance was used to help with:
- project planning and educational framing;
- drafting and editing explanatory text;
- generating the V9 and V10 HTML/CSS/JavaScript implementation, including the V10 functional additions (explicit A→X/A→Y comparison panel, learner-controlled interference stepper, manual decay time-stepper, adaptation-delay calculation, memory trace log, parameter-inspector tooltips, and the accessibility pass) and a subsequent visual redesign pass (instrument-panel color system, serif/monospace/sans type system, panel-vs-narrative layout, hero trace animation) that changed styling only, not the underlying computation;
- organizing the README and supporting documents;
- verifying the two primary BDH citations (Kosowski et al. 2025; Engdahl et al. 2026) against the actual paper text via web search, and running the V10 script's logic through an automated Node-based test harness to check for errors before handoff.

The team must review, test, understand and defend every component before submission. In particular, the team should independently confirm the V10 interaction logic in a real browser (desktop, tablet, mobile) before the deadline, since the AI-assisted verification above was logic-level (Node + DOM stub), not a rendered-browser test.

Original project computation:
- The 4×4 associative memory simulation and update logic in `artifact/index.html` were created specifically for this submission.
- No external code library is embedded.
- No external model weights or datasets are included.

External research:
- Research claims are cited in REFERENCES.md and in the supporting PDF.
- BDH is described from the primary BDH paper rather than represented as the toy model.

Assets:
- No external graphics or fonts are bundled.
- The artifact uses browser-native HTML/CSS/JavaScript.
