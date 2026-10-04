# EEE Practice App — v65

Adds "Move to Results Page" - shown only on the exact question a student
opened via "Review Ques", hidden everywhere else, exactly as specified.

## How it works

Tap "Review Ques" on, say, Q5 in the Results list. Q5 opens with a
"Move to Results Page" button underneath its explanation. That button:

- Appears ONLY on Q5 - not on Q4, Q6, or any other question.
- Disappears the moment the student moves away from Q5 using Forward,
  Back, or Topics.
- Reappears if they step back onto Q5 again, since it's tied to that
  specific question being on screen - not a one-time thing.
- Tapping it jumps straight to Results, skipping however many questions
  are in between.

Plain Back from Results (the fix from v64) still goes straight to the
last question as before, but does NOT show this button there - it's
reserved for the explicit "Review Ques" entry point only, per what was
asked.

## Verified before shipping

Tested the full sequence directly: tapped Review Ques on Q3 of a
5-question test, confirmed the button appears only there; stepped
Forward to Q4 and confirmed it's gone; stepped Back twice to Q2 and
confirmed it's still gone (not just hidden on the immediate neighbour);
stepped Forward back onto Q3 and confirmed it reappears; tapped it and
confirmed it lands on Results; then confirmed a plain Back press from
Results (no Review Ques involved) correctly does NOT show the button on
the last question it lands on.

## Folder structure

```
v65/
├── app.js                 # *NEW* reviewEntryIndex tracking + "Move to Results Page" button
├── service-worker.js         # Cache bumped to v65
├── data/, index.html, upload.js, upload.html, home.html, manifest*.json, style.css   # Unchanged from v64
├── libs/, icons/
└── README.md

v64/, v63/, v62/, v61/, v60/ ... v1/   # All untouched
```

## Changelog

### v65 - "Move to Results Page" on the Review Ques entry question only
- **<span style="color:red">**\*NEW\*** "Move to Results Page" button</span>**, shown only on the specific question opened via "Review Ques" - hidden on every other question, including the one landed on via a plain Back-from-Results press.
- No changes to question editing, PDFs, media storage, or anything else from v64.

## Still pending

- Enable "Allow delivery of PDF and ZIP files" in Cloudinary settings if not already done (from v56)
- Confirm libs/jspdf and libs/docx exist at the right paths in the repo (from v53)
- Firebase Media Storage real-world test (from v35 - Cloudinary works)
- Continue Fault Analysis question batches (Unsymmetrical Faults next)
- Bring back "Ask a Doubt" once students are onboarded (from v17)
- Firebase backend for Student Marks + Doubts (still your call)
- Level-2 unlock gated on Level-1 score
- Desktop .exe project not yet synced past v7
