# StudyLab — What helps you remember?

**PSYC 402 · Memory & Cognition · Final Lab Project**

A browser-only, responsive psychology demonstration comparing immediate cued recall of **18 unrelated word pairs** studied with **written words, picture-supported words, or spoken words**. The website has no build step, server, database, tracking, or external data collection. Data can be downloaded manually as CSV.

## Deploy to GitHub Pages

1. Make a **new public repository**, such as `studylab-memory` (separate from your practice assignment).
2. Upload `index.html`, `styles.css`, `script.js`, and `README.md` directly to the repository root — **not the ZIP**.
3. In Settings → Pages, choose **Deploy from a branch**, `main`, `/(root)`, Save.
4. Open `https://YOUR-USERNAME.github.io/studylab-memory/` and run all the way through; verify all three CSVs download.
5. Invite group members and Dr. Onyper using repository Settings → Collaborators (the exact settings label may differ).
6. When changing the experiment, commit a descriptive change and test the updated public site.

## Study design & rationale

**Question:** Does immediate cued-recall accuracy differ when word pairs are studied as text, picture-supported text, or spoken audio? **Exploratory secondary question:** Is a participant's *predicted preference* the same as the format with their highest recall in this single session?

**Design:** Within-person, 3 conditions × 6 pairs = 18 items. Each person sees the three conditions in a randomized block order, and the three six-pair stimulus lists are randomly assigned to conditions. Items within each block and final test items are randomized. Written and visual pairs appear for **6 s** each. The audio condition plays through Web Speech API speech synthesis on user action and moves on approximately 6 s after Play. Participants then perform a **30 s backward-by-3 counting distractor**, followed by **18 typed cued-recall trials** in random order, with no feedback until the end.

**Primary DV:** Correctly recalled target words (0–6 per condition). Comparisons of immediate accuracy are descriptive unless using a suitable repeated-measures analysis with adequate sample size. **Secondary:** Response time, preference, user-evaluation ratings. Matching is case-/punctuation-insensitive; spelling mistakes are NOT automatically corrected. Inspect trial-level responses before analysis. The listening section uses device speech synthesis, which differs across platforms. Fallbacks are flagged.

**Important limitations:** The picture condition provides *additional* pictorial cues (not a pure modality manipulation), so any advantage could reflect extra information rather than inherent format superiority. Word-list difficulty, block effects, speech audio differences, and immediate testing may bias outcomes. A single session does **not** test the learning-style “meshing” hypothesis or identify a fixed student learning style. No inference to academic achievement or long-term retention is warranted. Presentation time is approximately matched, but speech duration itself is not precisely standardized.

## Output files

- `session-..._summary.csv`: 1 row, session-level scores, order, preferred format, audio fallback flags, and evaluation ratings.
- `session-..._trials.csv`: 18 rows, one per tested cue, assigned condition, study and test positions, correct target, response, accuracy, response time.
- `session-..._evaluation.csv`: 1 row with voluntary usability ratings for the class evaluation.

**Data handling:** Files save only when a participant clicks Download. The website does **not** transmit or retain responses. No personal data fields are requested; do not add names, emails, participant lists, or raw response files to this public repository. To evaluate the app with at least 10 students, use a class-approved procedure for securely collecting their downloaded CSVs (e.g., instructor-approved DataPipe workflow or secure private exchange). Don't put individual results into public GitHub. If you later implement DataPipe, follow your instructor's approved setup and privacy protocol rather than committing credentials or a DIY database.

## Evaluation plan (for your final presentation)

Recruit ~10 student volunteers after instructor approval. Ask each to finish one session and voluntarily submit summary/evaluation CSV using an approved private method. Compute (1) mean correct out of six by format, (2) percentage who predicted the format with their unique highest score (ties reported separately), and (3) mean clarity/ease/engagement ratings. Visualize the three condition means as a bar chart and user ratings as a second chart. Evaluate whether the app is clear and functional; do not claim causal superiority or generalizable preference matching from this modest sample.

Test across desktop and mobile; include sound-on/off, no Web Speech support, zero recall, skipped answers, restart, and CSV download cases. Keep version history via commits. You can customize the content, but check that item lists remain balanced and timing and export still work.

## Research grounding (verify before final presentation)

- Pashler, H., McDaniel, M., Rohrer, D., & Bjork, R. (2008). Learning styles: Concepts and evidence. *Psychological Science in the Public Interest, 9*(3), 105–119. https://doi.org/10.1111/j.1539-6053.2009.01038.x
- Mayer, R. E., & Moreno, R. (2003). Nine ways to reduce cognitive load in multimedia learning. *Educational Psychologist, 38*(1), 43–52. https://doi.org/10.1207/S15326985EP3801_6
- Dunlosky, J., Rawson, K. A., Marsh, E. J., Nathan, M. J., & Willingham, D. T. (2013). Improving students’ learning with effective learning techniques: Promising directions from cognitive and educational psychology. *Psychological Science in the Public Interest, 14*(1), 4–58. https://doi.org/10.1177/1529100612453266

## Tech notes

Plain HTML/CSS/JavaScript with no framework. Font styles load from Google Fonts when network access is available, with local fallbacks. Audio uses native `speechSynthesis`, not remote audio or an API. Website works by opening `index.html` directly.
