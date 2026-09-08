# Submission Checklist

## Required by the PS1
- [x] Interactive artifact with a meaningful control and live computation
- [x] One-sentence falsifiable claim
- [x] Visible model state
- [x] Ground truth beside model output
- [x] BDH connection with evidence discipline
- [x] Limitation / failure case
- [x] README
- [x] One-page concept summary PDF
- [x] Supporting blog PDF
- [x] At least 3 recent primary papers listed
- [x] AI assistance disclosure
- [x] Source/license record

## Still needs to be done by the team before submission
1. **Open `artifact/index.html` in an actual browser** (desktop, tablet, and a real phone) and click every control listed below. This was verified with automated Node-based logic tests, not a rendered browser, so a manual pass is required:
   - Run 60-second experiment
   - Prediction choices
   - Write A → X / Compete A → Y / Query A / Reset
   - Advance time (t+1) button and the decay time-stepper (−/+)
   - Interference stepper (−/+, check it stops at 0 and 8)
   - Learning-rate and retention sliders, and their "i" tooltips
   - Decay sweep, interference sweep, and comparison buttons
   - Knowledge check
   - Check the browser console for any warnings on each page load.
2. Put the `artifact/` folder on a public host and test it on a phone.
3. Create a public GitHub repository and upload the files.
4. Replace any team-name/placeholders in the PDFs if required by the competition form.
5. Add the public artifact URL and GitHub URL to the README.
6. Verify every technical statement against the primary papers (BDH: arXiv:2509.26507; BDH-CQ: arXiv:2608.09888  both confirmed to exist and match the quoted claims during V10 development).
7. Prepare a 60-second live demo: write A→X, query A, use the interference stepper to add competing A→Y writes, query A again, point to the adaptation-delay number, and explain the failure.
8. Confirm the exact Unstop submission fields and upload formats before final submission  note the PS1 round deadline is 08 Sep 2026, 11:59 PM IST.
