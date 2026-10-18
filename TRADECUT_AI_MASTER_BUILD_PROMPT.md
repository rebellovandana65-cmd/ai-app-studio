# TRADECUT AI — MASTER BUILD PROMPT
## Target repository: `rebellovandana65-cmd/ai-app-studio`

You are ChatGPT Work acting as a senior full-stack engineer, AI/video-processing engineer, QA engineer, UX designer, and deployment engineer. Your mission is to build and verify a genuinely usable mobile-first web app called **TradeCut AI** in THIS repository. Do not merely provide a plan, mockup, pseudocode, or a report saying what could be done. Inspect the repository, implement the product, run the available checks, fix failures, and report the real status with evidence.

Repository URL: https://github.com/rebellovandana65-cmd/ai-app-studio
Default branch: `main`
The repository may currently be empty. If it is empty, create a clean, complete project structure from scratch. Do not assume that files from another repository exist or that earlier work has been copied here.

---

# 1. Non-negotiable working rules

1. **Work in this repository only.** Do not edit or break the user's separate news/YouTube automation repository.
2. **Progress reporting is mandatory.** The user is non-technical and works from an Android phone. Keep them informed in plain language.
3. **Report only verified progress.** Never mark a task complete just because code was written. Completion requires the appropriate check or evidence.
4. **No fake completion, tests, deployment, links, or features.** Clearly distinguish implemented, tested, partially working, blocked, and not started.
5. **Do not stop after creating a frontend mockup.** The core requirement is a real uploaded-video-to-exported-MP4 pipeline.
6. **Do not wait for approval at every normal implementation decision.** Make sensible choices autonomously, but ask only when a secret, account authorization, destructive action, or genuinely essential decision requires the user.
7. **Keep existing user data safe.** Inspect before overwriting. Do not commit secrets, API keys, OAuth tokens, or uploaded private videos.
8. **Use the simplest architecture that can genuinely work.** Prefer free/open-source libraries and local processing when feasible. Do not add paid APIs or mandatory paid services.
9. **Be honest about costs and hosting.** Target ₹0 to run and test, but do not promise lifetime-free cloud hosting, unlimited processing, or free third-party AI quotas. Clearly identify any external limits and provide a working no-paid-API fallback.
10. **Mobile-first.** The user normally operates from an Android phone and should be able to upload, process, preview, and download from a mobile browser without needing to run terminal commands.
11. **Keep user-facing explanations simple.** Avoid unexplained technical jargon.
12. **Do not claim the app is deployed or usable from a public URL until the deployment is actually verified.**

# 2. REQUIRED PROGRESS-REPORT SYSTEM

Create and maintain a `PROGRESS.md` file in the repository. Update it after every meaningful implementation stage and after every test/build/deployment attempt. Commit progress updates at sensible checkpoints, not after every tiny keystroke.

At the beginning of the work, immediately send the user a short status report with:
- Current stage
- Overall completion percentage (start at 0% or a justified baseline)
- What you inspected
- What is next
- Any blockers requiring the user's action

## Required stage weights (total = 100%)

Use this weighted checklist as the single source of truth. Adjust weights only if you explain why, and keep the total at 100%.

- [ ] Stage 1 — Repository inspection, requirements, and architecture: **5%**
- [ ] Stage 2 — App scaffold, mobile-first UI, and configuration: **10%**
- [ ] Stage 3 — Upload, media probing, input validation, and job state: **10%**
- [ ] Stage 4 — Real video-processing pipeline and reliable MP4 export: **20%**
- [ ] Stage 5 — Speech/transcript analysis and intelligent, context-safe trimming: **10%**
- [ ] Stage 6 — Voice cleanup, loudness balancing, optional music ducking: **8%**
- [ ] Stage 7 — Captions/SRT and readable on-screen subtitles: **7%**
- [ ] Stage 8 — Context-aware zooms, labels, hooks, tasteful effects, and meme moments: **8%**
- [ ] Stage 9 — YouTube packaging (title, description, tags, chapters, thumbnail guidance): **5%**
- [ ] Stage 10 — Automated tests, quality checks, bug fixes, and sample-video verification: **10%**
- [ ] Stage 11 — Deployment, mobile smoke test, and final handover documentation: **7%**

A stage is complete only when its acceptance checks pass. Calculate the overall percentage from verified completed work; do not inflate it for plans, TODOs, generated mock screens, or untested features. If a stage is partly done, report the percentage earned for that stage and explain the evidence.

## Report after EVERY step or test

After each implementation step, test, build, deployment attempt, or blocker, provide a compact progress report using this format:

**TradeCut AI progress**
- **Overall:** NN% (verified)
- **Current stage:** Stage N — name
- **Just completed:** Specific file/feature/test and what actually happened
- **Test result:** PASS / FAIL / BLOCKED / NOT RUN
- **Evidence:** Actual command/result, test name, screenshot, log excerpt, output-file probe, or deployment check
- **Failures found:** Exact issue(s), or “None found in this check”
- **Next action:** The next concrete task
- **User action needed:** None, or one clearly worded request

If a test fails, do not hide it. Explain the failure in plain language, fix it where possible, rerun the test, and report the new result. If a check cannot be run because the environment lacks a dependency, sample video, permission, or network access, mark it **BLOCKED** and say exactly why. Never label an unrun test as PASS.

At the end, provide a final report with:
- Overall verified completion percentage
- Completed features and their test status
- Incomplete/blocked features and reasons
- Exact repository files changed
- Build/test results
- A verified public app URL if deployment succeeded (otherwise say not deployed and provide the next simplest steps)
- Android instructions in numbered, beginner-friendly steps
- Any remaining user action, including any necessary account sign-in or secret setup
- Known limitations and any possible ongoing costs

# 3. Product goal

Build **TradeCut AI**: a simple mobile-first app where the user uploads a raw trading/commentary video, chooses an editing style or accepts “Auto Best”, taps **Create my video**, watches real progress, previews the result, and downloads a YouTube-ready MP4 plus supporting files.

Example input: a 3 minute 26 second Zerodha/trading commentary video discussing a profit around ₹1,200. The editor should preserve the real explanation and financial context, remove unnecessary dead air/repeated wording where safe, and produce a polished result. The result may be shorter (for example, around 2–3 minutes) if that improves pacing, but do not force a target duration or cut important information simply to reach a length.

Primary workflow:
1. Open the app on Android.
2. Upload a supported video.
3. See file name, duration, resolution, audio availability, and validation feedback.
4. Choose an edit preset or Auto Best.
5. Tap one main action.
6. See accurate step-by-step processing status and progress.
7. Preview the finished video.
8. Download the MP4 and optional SRT/metadata files.
9. Receive useful YouTube packaging suggestions.

Target usage: roughly 2–3 videos per day when hosting/runtime limits allow. Do not promise that any free hosting tier will support this volume until tested.

# 4. Core features

## A. Responsive mobile UI
Create a clean, modern, professional dark-first interface that works on narrow Android screens:
- TradeCut AI branding and clear one-sentence explanation
- Video upload area with supported formats, size/duration constraints, and helpful errors
- Optional background-music upload with volume controls
- Edit preset selector
- Optional caption toggle and language selection if supported
- Clear “Create my video” action
- Current job status, stage name, percentage, elapsed time if available, and failure messages
- Preview player for the exported result
- Download buttons for MP4, SRT, and YouTube package
- Clear restart/new-video action
- Accessibility: readable contrast, large touch targets, labels, keyboard support where practical
- Never simulate a progress bar that moves without real work. Derive progress from actual pipeline stages or clearly label estimates.

## B. Media input and validation
- Accept common practical formats such as MP4, MOV, and WebM when supported by the installed media stack.
- Validate file type, file size, duration, audio track, and video stream before processing.
- Explain unsupported/corrupt files in plain language.
- Handle a video with no audio without crashing.
- Avoid holding the entire video in memory unnecessarily.
- Set reasonable limits suitable for the chosen hosting environment and document them.
- Ensure temporary uploads and output files are cleaned up safely after the job/session when appropriate.

## C. Real video processing and export
Use a dependable open-source media pipeline (for example, FFmpeg through a supported wrapper or a carefully managed FFmpeg binary). Choose a framework compatible with the actual hosting environment. Do not assume FFmpeg, Python, Node, codecs, or system packages are installed—verify and configure them.

The pipeline must:
- Probe the source file and record basic metadata.
- Preserve the source aspect ratio by default.
- Produce a standard MP4 using H.264 video and AAC audio when supported by the environment.
- Keep audio/video synchronized.
- Use safe temporary file paths and handle filenames with spaces/unusual characters.
- Validate the exported file before offering it for download.
- Confirm the output exists, has a non-zero size, can be probed, and has plausible duration/audio/video streams.
- Provide understandable errors and avoid leaving broken output links.
- Prefer sensible quality/size settings, document any constraints, and do not degrade quality without reason.

## D. Intelligent editing and trimming
Use actual media analysis, not random cuts or arbitrary duration reduction.
- Detect silence/dead air using a robust audio analysis method.
- If speech transcription is available, use it to avoid cutting mid-word, mid-sentence, or between a question and its answer.
- Preserve explanations, key context, conclusions, disclaimers, and relevant on-screen events.
- Keep natural pauses when they aid comprehension.
- Apply conservative trimming thresholds and provide a preview or “conservative edit” option.
- Avoid over-trimming; when confidence is low, preserve more footage.
- Never claim semantic understanding if the implementation only detects silence.
- Where possible, use local/open-source transcription and speech activity detection with graceful fallback if models cannot be downloaded or resources are insufficient.
- Make processing work without any paid AI API. If optional external AI is added, it must be optional and must not block the base workflow.

## E. Voice and background audio
- Improve voice clarity with safe, moderate processing and loudness normalization.
- Avoid clipping, harsh denoising, pumping, or making speech unnatural.
- Optional background music should be subtle, duck under speech where possible, and fade in/out smoothly.
- Music must be off by default unless the user chooses it.
- Support user-supplied music and use only original, public-domain, or properly licensed assets for any bundled music.
- Never bundle copyrighted commercial songs or meme audio without permission.
- Include a no-music path and ensure source speech remains intelligible.
- Validate audio presence and levels where tooling permits.

## F. Captions
- Generate readable subtitles from transcription when available.
- Offer downloadable SRT.
- Burn captions into the video only when selected or when the preset clearly implies it.
- Use readable font size, contrast, safe margins, sensible line lengths, and mobile-safe placement.
- Preserve important names, tickers, numbers, and Indian rupee values as accurately as possible.
- Financial numbers and proper nouns can be transcription errors: flag uncertain values for review rather than silently inventing corrections.
- If transcription is unavailable, export the video without captions and clearly explain why; do not fabricate a transcript.

## G. Context-aware visual editing
Where technically possible, implement tasteful:
- Opening hook/title card based on the actual topic
- Subtle zooms/crops to emphasize relevant existing on-screen content
- Callout labels and arrows only when grounded in what is visible or said
- Scene-aware cuts and pacing adjustments
- Light transitions only when they improve clarity
- Contextual sound effects sparingly
- Funny-moment suggestions based on actual transcript/audio cues, with user review if confidence is low
- Original/licensed meme templates only; avoid randomly inserting memes into serious financial explanations
- A simple “professional” mode with minimal effects

Do not claim that screen/object understanding exists unless it is actually implemented and tested. Do not invent chart values, trading outcomes, screenshots, prices, profit, losses, or claims. Never create fake trading evidence or make the edit imply a result that the original video does not support. When screen analysis is not reliable, avoid automatic zooms and offer manual review instead.

## H. Presets
Implement these as meaningful configurations of real features, not merely decorative labels:
- **Auto Best** — conservative, balanced defaults
- **Professional Trading** — clear speech, restrained edits, readable captions, no memes by default
- **High Retention** — stronger pacing, hook, captions, and relevant emphasis without misleading edits
- **Funny / Commentary** — light contextual effects and optional meme suggestions
- **Calm / Educational** — natural pacing and minimal effects
- **YouTube Shorts** — vertical 9:16 reframing only when appropriate; never crop away important content without warning
- **Long-form YouTube** — preserve context and use a restrained edit

If a preset is not fully supported, label it honestly as beta/partial and explain the limitation.

## I. YouTube package
Generate suggestions based on the actual transcript/topic, not generic unrelated content:
- 3 title options
- Description draft with appropriate context
- Relevant tags/keywords (avoid keyword stuffing)
- Chapters based on real content and valid timestamps
- Thumbnail concept and optional generated thumbnail if a safe, available method exists
- A short quality checklist and improvement suggestions
- Suggested hook text grounded in the video
- Make it clear that these are suggestions and cannot guarantee views, virality, monetization, or revenue.

## J. Trading integrity and privacy
- Never ask for brokerage credentials, OTPs, account passwords, or API secrets.
- Do not connect to a brokerage account.
- Do not fabricate financial results or turn an edit into personalized investment advice.
- Preserve caveats and disclosures in the source.
- Do not upload videos to external AI services unless explicitly disclosed and enabled by the user.
- Do not log or expose private video content, transcripts, tokens, or secrets unnecessarily.
- Add clear temporary-file cleanup and sensible error handling.

# 5. Architecture and implementation quality

First inspect the repository and decide whether it is empty or contains existing code. Write down the findings in `PROGRESS.md`. Then select the simplest maintainable stack that supports real video processing and deployability.

Keep modules separated where practical, such as:
- media probing and validation
- transcription and speech activity detection
- edit planning
- audio processing
- video rendering/export
- caption generation
- YouTube packaging
- quality checks
- UI and job/progress reporting

Use clear configuration and pinned compatible dependency versions. Add a concise README with setup, run, deploy, limitations, privacy, supported formats, and troubleshooting. Add a sample environment file if needed, but never include actual secrets.

Before choosing hosting, verify that the selected platform can actually run the chosen backend, FFmpeg/codecs, processing duration, file uploads, and temporary storage. A frontend-only static host is not enough for server-side video processing. If the current free platform cannot reliably process real videos, do not fake it; choose the most feasible free/open-source deployment path and explain any unavoidable limitation. If public deployment requires the user to sign in or authorize something, complete all other work first and give the user the exact next step.

# 6. Tests and acceptance criteria

Write and run automated tests appropriate to the chosen stack. At minimum cover:
- Valid input metadata probing
- Invalid file and unsupported format handling
- Video with no audio
- Video with no detectable silence
- Video with detectable silence
- Audio normalization / no-audio fallback
- Music disabled and music enabled (if implemented)
- Caption/SRT output when transcription is available
- Captions unavailable/model failure graceful fallback
- Correct duration/timestamp handling
- Output MP4 existence, non-zero size, valid probe, audio/video streams, and plausible duration
- Temporary file cleanup after success and failure
- Filenames with spaces and non-ASCII characters
- Mobile layout/basic responsive checks where tooling supports it
- Full build/type/lint checks supported by the project

Create or generate a short synthetic test video with a known test pattern and audio if possible. Do not use the user's private video without permission. If a real sample video is needed and none is available, explicitly mark end-to-end real-world validation as BLOCKED rather than claiming it passed.

After fixing any failures, rerun the relevant tests and report both the initial failure and final result.

# 7. Deployment and beginner-friendly handover

Attempt the simplest reliable deployment compatible with the selected architecture. Do not stop at a green build if the app has not been deployed. Do not claim deployment worked unless you can open/check the actual URL and confirm the app responds.

Document exact Android steps:
1. Open the verified app URL.
2. Select a video from the phone.
3. Choose the edit preset and optional settings.
4. Tap Create my video.
5. Follow the real progress status.
6. Preview and download the result.
7. Download captions/metadata if desired.

Also document:
- Maximum upload size and duration if known
- Expected processing time only if measured; otherwise say it varies
- Whether uploaded files are stored and for how long
- Free-tier restrictions and possible sleep/timeout behavior
- What to do if processing fails
- Any one-time authorization or configuration the user must perform

# 8. Required order of execution

Proceed in this order, reporting progress after each step and every test attempt:

1. Inspect repository, branch, files, permissions, and existing project state. Do not overwrite blindly.
2. Write initial `PROGRESS.md` with the weighted checklist and baseline status.
3. Choose architecture and explain why it fits real video processing and mobile use.
4. Build the runnable app skeleton and responsive upload UI.
5. Implement upload validation, metadata probing, real job states, and honest progress reporting.
6. Implement the real processing/export pipeline and verify a valid MP4.
7. Add safe trimming and speech analysis with graceful fallback.
8. Add audio controls and optional music.
9. Add captions and SRT.
10. Add contextual visuals/effects only where feasible and tested.
11. Add YouTube packaging and presets.
12. Add automated tests, run all available checks, fix issues, and rerun.
13. Attempt deployment and perform a mobile-friendly smoke test if possible.
14. Update README and `PROGRESS.md`; commit the final verified state.
15. Give the user the final evidence-based handover.

Do not skip ahead to cosmetic features while the core upload → process → valid MP4 export path is broken. If time or environment limits prevent finishing everything, deliver the most complete working core first, mark remaining stages accurately, and provide the next concrete step.

## Definition of done

The project is **not complete** until the core workflow has been implemented and tested: upload a valid video → process it through the real pipeline → validate the exported MP4 → preview/download it, with truthful progress updates and errors. All other features must be separately marked by their real implementation and test status. A polished UI without a working export is not done.
