# DataForge 2026  Synaptic Plasticity as Short-Term Memory

## Central claim
Recent neural activity can temporarily change synaptic strength, allowing a small network to store short-term associations; decay and competing writes can make those memories interfere.

## Intended learner
Average data-science / ML student with basic familiarity with vectors and neural networks.

## Prerequisites
- Basic idea of a neural network
- No neuroscience background required
- Comfort reading a simple update equation

## Learning objectives
After using the artifact, a learner should be able to:
1. Explain what a synapse is in the simplified computational model.
2. Explain why a changing synaptic weight can act as short-term memory.
3. Predict how learning rate, retention and competing writes affect recall.
4. Distinguish the toy model from the full BDH architecture.
5. State one limitation: fast memory is vulnerable to decay and interference.

## Artifact
Open `artifact/index.html` in a browser. It is a self-contained, dependency-free interactive demo.

The demo contains a small 4×4 associative synaptic matrix. A write applies a simplified Hebbian update after decaying the existing fast memory:
`w(t+1) = retention*w(t) + eta*pre*post`
where pre/post are 1 for the selected cue/target and 0 otherwise.

This is an educational toy model, NOT the official BDH model.

## Why the interaction is real
The slider values change the numerical update rule. Writing an association modifies the matrix; passing a time step decays it; querying reads the strongest current synapse. The output and failure cases are computed live.

## BDH module
The Dragon Hatchling (BDH) paper describes a brain-inspired post-Transformer architecture whose working memory during inference relies on synaptic plasticity with Hebbian learning using spiking neurons. It also reports concept-related strengthening of individual synapses.

Our demo isolates this mechanism for teaching. It does not reproduce the complete BDH architecture, training procedure or benchmark results.

## Evidence levels
- **Published primary evidence:** claims about BDH are sourced to Kosowski et al. (2025).
- **Published primary evidence:** short-term plasticity in machine-learning units is supported by Rodriguez et al. (2022).
- **Published primary evidence:** recent computational work on synaptic plasticity includes Brito & Gerstner (2024) and related 20232024 work listed in REFERENCES.md.
- **Independent educational computation:** all matrix behavior in the demo is our own toy simulation.
- **Not claimed:** benchmark reproduction or biological validation.

## Submission materials
- `artifact/index.html`  public artifact source
- `docs/blog.pdf`  supporting blog/explainer
- `docs/one_page_concept_summary.pdf`  required one-page concept summary
- `REFERENCES.md`  primary sources and evidence notes
- `AI_DISCLOSURE.md`  AI assistance disclosure

## Deployment
For a public artifact URL, upload the `artifact/` folder to a static hosting service such as GitHub Pages, Netlify, Vercel, or another host that serves `index.html` without sign-in.

## Provenance and licenses
| Category | Source | License / notes |
|---|---|---|
| Code | Written for this submission (HTML/CSS/vanilla JS, `artifact/index.html`) | No external library embedded; no build step |
| Fonts | System font stacks only (`ui-serif`, `ui-monospace`, `system-ui` and OS fallbacks) | Not bundled  rendered from the visitor's OS, no license needed |
| Graphics | Inline SVG (network diagram, favicon, hero trace) hand-written for this submission | Original, no external image files |
| Data / weights | None used | The artifact ships no datasets or model weights |
| Research claims | External findings cited inline and in `REFERENCES.md` | Attributed to original authors; not reproduced verbatim beyond short quotes |
| Documents | `docs/blog.pdf`, `docs/one_page_concept_summary.pdf` | Original text written for this submission |

## Design strategy for judging
This resource is intentionally built around one falsifiable claim rather than a collection of unrelated visualizations. The learner first runs a guided experiment, then changes the two variables that correspond to the toy mechanism: write strength and retention. The artifact exposes the complete 4×4 synaptic state, places output beside ground truth, and includes computed experiments for decay, interference, and adaptation. The failure mode is part of the lesson.

The BDH section is deliberately evidence-separated into three explicit levels (see below):
- **Level 1  our toy model:** the live matrix is our independent toy computation;
- **Level 2  research literature:** short-term plasticity as an active ML research direction (Rodriguez et al. 2022; Brito & Gerstner 2024);
- **Level 3  Dragon Hatchling (BDH):** architectural claims sourced only from the primary BDH paper.

The intended 60-second judge path is:
**Run experiment → inspect matrix (A→X vs A→Y numbers) → recall → change retention → rerun → explain decay/interference → inspect adaptation delay → inspect BDH connection.**

## V10  competition-focused upgrade

V10 builds directly on the working V9 mechanism (same update rule, same functions, same 60-second run button) and adds depth that a strict judge would ask for, without adding pages, frameworks, or unrelated features.

### What's new in V10
1. **Explicit A→X vs A→Y comparison panel.** The matrix no longer just shows numbers  a dedicated panel states both values and which one currently wins recall, satisfying the "truth beside estimate" design standard directly.
2. **Learner-controlled interference.** The learner chooses the number of competing A→Y writes (08) with a stepper; the chart and the stated A→X/A→Y values update to match  interference is no longer a fixed preset.
3. **Manual time stepper for decay.** Alongside the existing decay sweep chart, the learner can step through t = 0, 1, 2… one click at a time and watch the exact numeric value at each step, making "retention per step" concrete rather than abstract.
4. **Adaptation-delay metric.** The plastic-vs-frozen comparison now computes and displays exactly how many post-switch writes were needed before A→Y overtook A→X  a concrete number for the abstract idea that "plasticity has a transition cost."
5. **Memory trace panel.** A short, live log of the last 8 write/query/time-step events, so the causal chain from event history to current synaptic state is never hidden.
6. **Parameter inspector.** Small "i" tooltips next to learning rate and retention explain what each variable does in plain language, on demand rather than by default.
7. **Micro-interactions tied to real state changes.** A brief highlight pulse on the matrix cell and network nodes that just changed  never decorative, always triggered by an actual write.
8. **Accessibility pass.** Skip link, focus-visible outlines, `aria-live` regions on every dynamic result/status panel, `aria-label`s on icon-only controls, and a `prefers-reduced-motion` media query that disables animation for people who request it. State is also expressed in text (not color alone).
9. **Evidence framing made explicit in the UI itself**, not only in the README: the BDH section now visibly labels Level 1 (toy model) / Level 2 (research literature) / Level 3 (BDH), matching the PS1's call to separate evidence discipline.

### Core 6090 second flow (updated)
1. Make a prediction about lower retention.
2. Teach A → X.
3. Recall A  see the explicit A→X vs A→Y numbers and the winner.
4. Add competing A → Y writes (learner-chosen count).
5. Recall again and observe the failure, with the memory trace showing why.
6. Step through decay manually, then run the full sweep.
7. Run the plastic-vs-frozen comparison and read the adaptation-delay number.
8. Connect the isolated mechanism to BDH via the three evidence levels.
9. Complete the one-question knowledge check.

### Scientific honesty
The live interaction still uses the same deliberately simplified Hebbian-style update as V9, unchanged:
`w(t+1) = retention × w(t) + η × pre(t) × post(t)`

This is an educational model, not the complete BDH algorithm and not a full biological model of synaptic plasticity. The artifact separates the toy-model result from claims supported by the cited BDH research, now with the evidence level stated inline at the point of the claim.

### Design principle
The project intentionally remains a single focused learning experiment rather than a multi-page dashboard. Every new V10 control maps to one real variable already present in the V9 mechanism (number of writes, time steps, the same two sliders)  nothing was added that doesn't serve the same causal story:

**write → recall → decay/interference → trade-off → BDH connection**

### Design language
The visual design is deliberately grounded in the subject matter rather than a default template: an instrument-panel aesthetic evoking a dual-trace oscilloscope, since the artifact is literally displaying two competing signals (A→X and A→Y) over time. Amber marks the A→X channel and teal marks A→Y throughout  matrix, network diagram, and every chart use the same two colors consistently, so a judge can track one association across every view. Type is split by job: a serif for headings, system monospace for every actual number and readout (equation, matrix values, stats), and sans-serif for prose  mono is used only where the content is genuinely data, not as decoration. Only the interactive instruments (controls, matrix, charts) sit in bordered panels; explanatory sections (prediction, mechanism, evidence, takeaway) sit directly on the page with hairline rules, so the layout doesn't read as a stack of identical cards. The one non-interactive animation  the hero's oscilloscope trace drawing itself in on load  mirrors the artifact's own decay equation and respects `prefers-reduced-motion`.

### How V10 was verified
- The full script was extracted and executed in Node against a minimal DOM stub, exercising: write/decay math, query/recall logic, the new time-stepper, the new interference-count control (including boundary clamping at 0 and 8), the adaptation-delay calculation, prediction selection, the knowledge check, and reset. All checks passed with no thrown errors.
- HTML tags were checked for balance (divs, buttons, svg) and the extracted JavaScript was checked with `node --check` for syntax errors.
- The file has zero external requests and no dependencies (confirmed by scanning for `src=`/`href=` attributes pointing off-page).
- **Not yet done  please do before final submission:** an actual visual/interaction pass in a real browser at desktop, tablet, and mobile widths, and a check of the browser console for runtime warnings. The sandbox used to build V10 could not install a headless browser, so this logic-level testing is a strong signal but not a substitute for opening it on a phone.
