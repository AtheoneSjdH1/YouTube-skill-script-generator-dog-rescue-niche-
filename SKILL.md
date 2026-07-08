---
name: yt-dog-rescue-shorts
description: 'Generate a complete YouTube Shorts video package for a dog rescue channel. Use this skill whenever the user wants to make a new YouTube video, Short, or script about saving or rescuing dogs — even if they just say "make me a video", "new Short", "I need content", or "generate something for my channel". Saves each video as a numbered file and outputs exactly 4 things: a Veo 3.1 Fast prompt, a title, a caption with hashtags, and a pinned creator comment for the awareness community.'
---

# YouTube Dog Rescue Shorts — Skill Instructions

This skill generates 8-second YouTube Shorts about dog rescue for a channel that uses AI-generated video (Veo 3.1 Fast in Google Flow). The channel goal is fast monetization without strikes or deletions.

## Style reference — read before generating

Before writing anything, read ALL of these files:

1. `references/guideline-rules.md` — platform compliance rules. Confirms what is and isn't allowed before you write a single word.
2. `references/example-scripts.md` — real examples provided by the channel owner. Match their tone, pacing, prompt structure, and caption format exactly. When in doubt, ask yourself: does this sound like the ice rescue example?
3. `references/yt-hacks.md` — Shorts engagement playbook (hooks, first-2-second rules, character-in-motion, retention benchmarks, loop endings, CTAs). Apply these principles to every Veo prompt, title, and caption. Read this BEFORE generating.
4. `references/yt-rescue-ideas.md` — viral rescue idea bank (~500 concepts across firefighter, ice, flood, highway, storm, trapped, abandonment, heat, reunion, mama-dog, twist-ending categories). Use it as INSPIRATION to pick fresh story patterns and avoid repeating recent videos. You are free to invent your own beyond this list — the bank is a launchpad, not a menu.

Every time this skill is invoked:
1. Generate the 4-part video package (Veo prompt, title, caption, pinned comment)
2. Save it as a new numbered file in the `videos/` folder
3. Show the output to the user so they can copy it directly

---

## Channel analytics — pre-generation check

Before generating any new script, run this gate. It closes the feedback loop between published video performance and the next script you write.

1. **List subfolders** inside `references/channel-analytics/`. Each snapshot lives in its own dated subfolder named `analytics-YYYY-MM-DD/`, containing two files: `analytics.md` (human-readable) and `analytics.json` (machine-readable, same data).
2. **Find the most recent subfolder** by the date in its name.
3. **Staleness check:**
   - If the latest subfolder is dated **within 2 days** of today → use it as-is. Skip to step 5.
   - If the latest subfolder is **older than 2 days** → ask the user: *"Last analytics snapshot is from [DATE]. Send a fresh YouTube Studio screenshot before I generate this script?"*
4. **If the user provides a new screenshot** → create a new subfolder `analytics-YYYY-MM-DD/` inside `references/channel-analytics/`. Inside it, create `analytics.md` and `analytics.json` matching the format of the existing snapshot folder. The MD file must start with `> **IMPORTANT**: Read [SKILL.md](../../../SKILL.md) before reading this analytics file.` (note three `../`, because the file is one level deeper than older flat files were).
5. **Read only the two most recent snapshot folders** (the latest one + the one before it). Within each folder, read either `analytics.md` or `analytics.json` — they hold the same data, pick whichever is easier in context. Do NOT read all historical folders.
6. **Compare the new snapshot against the previous one** (the two you just read in step 5). Note what changed: which videos gained or lost views, whether any video newly broke out, and whether stayed-to-watch is trending up or down. This trend is the first input to the signal analysis below. If only one snapshot exists, skip the comparison and note "first snapshot — no trend yet."
7. **Pull these signals**, in priority order, to inform the new script:
   - **Views + subscribers gained** → which videos won. Bias the new story toward similar setups (e.g. if ice rescues dominate, lean toward another high-stakes water/cold pattern).
   - **Stayed-to-watch % + avg view duration** → which stories held viewers. Mirror their pacing and beat structure.
   - **Under-performers** → patterns to avoid. Specifically: stayed-to-watch <55%, low views despite reasonable impressions, soft/setup-heavy titles.
8. **Cross-reference the winners — and the single worst under-performer — against `references/example-scripts.md`** (the file you already read before generating). For each top performer from step 7, and for the worst under-performer, find its entry by matching the analytics **Title** to the example's **TITLE** block (titles are published verbatim, so the match is exact). Study how the winning entries are actually built — the prompt's opening beat, the order/count of physical actions, pacing, the title formula, the caption hooks — plus any *user-feedback note* under the example (these record the render outcome and lesson). Mirror the structure of the highest-engagement entry, and steer away from the worst. If a video has **no matching entry** (e.g. it predates the auto-log or wasn't approved), note that and rely on its analytics signal alone.
9. **CTR + title-pattern analysis is currently de-prioritized** per user decision. Don't weight it heavily.
10. Before drafting, note briefly (one or two lines) which performance signal you are biasing toward and which pattern you are avoiding.

If the `channel-analytics/` folder is empty (no snapshot subfolders at all), ask the user for the first screenshot before generating.

---

## File saving rule

Save each generated video to:
```
yt scripting project/yt-dog-rescue-shorts/videos/video-XXX.md
```
Number sequentially: `video-001.md`, `video-002.md`, etc. Check which number is next before saving.

---

## Output format — always exactly this, nothing more

Each section must be in its own code block so the user can copy it with one click.

**VEO PROMPT**
```
[prompt]
```

**TITLE**
```
[title]
```

**CAPTION**
```
[caption + hashtags]
```

**PINNED COMMENT**
```
[pinned comment text]
```

---

## How to write the Veo 3.1 Fast prompt (Google Flow)

Six labeled blocks, **~100–200 words total**, written for a single **8-second native Veo clip** with native synced audio. The blocks are: `Style`, `Scene`, `Subjects`, `Action`, `Camera`, `Audio`. This is the exact format that video-012 (the channel's best render so far) and `references/example-scripts.md` Example 7 are built on — match it.

**The six blocks:**

- **Style:** Ultra-realistic raw amateur phone footage — slightly grainy, no color grading, no music, like a bystander filmed it. One line.
- **Scene:** Where it happens, time of day, weather, and the single-source hazard (storm, fire, flood, collapsing ledge). One or two lines.
- **Subjects:** The dog (breed/size, soaked / lively / alert — never "injured") and the rescuer (one specific detail: turnout coat, rain slicker, soot-streaked face). Keep both lively, not suffering.
- **Action:** The kinetic spine — **tightened to 4 beats for 8 seconds** (see below).
- **Camera:** Its own block. Veo prioritizes the camera request and defaults to static / subtle handheld if you don't name movement, so state it plainly: handheld phone, low and close, slight shake, hazard (rain, smoke, spray) drifting across the lens.
- **Audio:** Written as a sequence matched to on-screen action. Put speech in quotes (e.g. a low, breathless `"I've got you."`) and describe sound effects clearly (e.g. `SFX: waves slam the pilings, driving rain`). End with `No music.`

**The first-sentence rule — non-negotiable (applies to the Action block).**
Before writing anything else, ask: *"Is this the single most visually striking moment of the entire 8 seconds?"* If no, rewrite. The first sentence of the Action block is frame 1 of the Short. The dog must be moving in it (running, falling, struggling, leaping, lunging, slipping). If the dog is "lying", "curled", "huddled", or "still" in sentence 1, rewrite.

**Action block — 4 beats for 8 seconds:**

1. **OPEN MID-CRISIS (frame 1 = peak visual).** First sentence is the single most kinetic moment — dog airborne off a ledge, clawing up a drain wall, leaping a gap. NO setting sentence before this, NO static pose. Open on **active struggle, never suffering** (scrambling hard, barking up at the rescuer — not "panicked yelps" or "eyes wide", which read as a dog in distress and risk monetization).
2. **HUMAN CATCH / INTERVENTION (controlled, weight visible).** The dog's weight transfers to the human — caught, hauled, lifted, pulled clear. Use a **controlled verb into the landing** — "folds the dog into his chest as it comes down," **never "slams"**. Force-verbs ("slams", "haul hard") plus "land" make Veo render the rescuer falling unnaturally or an impact instead of a catch.
3. **CARRY TO SAFETY (its own dedicated sentence).** The moment the dog is *fully on safe ground / clear of the hazard* gets its **own short sentence** — Veo drops this frame if it's buried in a chain of micro-steps.
4. **LOOP-BACK PAYOFF (dog moves — does not pose).** Dog scrambles up, licks the rescuer's jaw, paws plant on the collarbone, tail thrashing — and this image visually echoes the opening (the same airborne reach, now landed and safe) so the Short loops seamlessly. Give the payoff 2+ short sentences, not a tail clause.

**Veo craft rules (confirmed across renders):**
- **Single-source hazard only** — no near-miss collisions (converging fast objects render as impacts in Veo, not misses).
- **The dog must visibly bark on screen** (mouth opening) for its bark/whine audio to render — Veo ties audio to a visible source; sequencing it in the Audio block alone does not work.
- **No aspect-ratio or meta** ("9:16", resolution) — keep prompts lean.
- Visible effort / strain + gritty texture (matted wet fur, mud, water sheeting, grainy phone look) is what reads as real. Over-smoothing the motion kills realism.

**Content rules:**
- Never describe blood, open wounds, or abuse happening on screen
- Show suffering as past or implied — wet, thin, exhausted, soot-covered — not injured
- The video must end on a moment of connection, warmth, or relief — but reached *through* motion, not through stillness
- Phone-captured feel — raw and real, not Hollywood

**Story patterns to rotate (pick a different one each time — note all are phrased as the *action*, not the *aftermath*):**
- Dog bolts across a flooded road — woman drops her umbrella and sprints after it
- Dog leaps from a porch railing into a kayaker's arms mid-paddle
- Trucker slams brakes, jumps from cab, dives between two lanes of traffic to scoop a stray off the asphalt
- Man rips off his shirt mid-stride, soaks it in a fountain, races back to a panting dog in 100° heat
- Hands punch through dirt — dog scrambles up and out of a collapsed drain into daylight
- Stray sprints out of an alley and slams into a woman's legs — she drops her coffee and catches it
- Worker shoulders open the shelter door at dawn — dog leaps onto her chest before she's stepped through

---

## First 2 seconds — checklist before you submit

Run this check on every Veo prompt before showing it to the user. If any box fails, rewrite.

- [ ] You ran the [Channel analytics — pre-generation check](#channel-analytics--pre-generation-check) gate above (or confirmed the latest snapshot is ≤2 days old).
- [ ] You compared the newest analytics snapshot to the previous one, and matched the top performer (and the worst under-performer) to its entry in `references/example-scripts.md`, mirroring the winning structure (or noted that no matching entry exists).
- [ ] First sentence of the Action block describes visible motion (not a pose, not a setting).
- [ ] The most visually striking frame of the entire video is described in the Action block's first sentence, not buried.
- [ ] No "setup" sentence comes before the action.
- [ ] A viewer who watches with sound off and stops at the 2-second mark would still understand something dramatic is happening.

---

## How to write the title

One line, under 60 characters, emotionally punchy but not misleading. No ALL CAPS.

**Title must reference an *action* or *moment* — not a feeling.** Slow-burn openings like "She Almost…", "Nobody Did…", or anything reflective are banned. Use one of the 6 hook formulas from `references/yt-hacks.md` §3:

- **Pattern Interrupt** (drop the viewer mid-action): `He Slid Across the Ice on His Stomach.`
- **Direct Promise (with a number)** (explicit outcome / time / %): `5 Seconds Decided If She Made It.`
- **Curiosity Gap** (raise a question, withhold the answer): `Three Cars Passed Her. The Fourth Stopped.`
- **Mid-Action Micro-Story** (start at the crisis): `He Was Already Running When He Saw Her.`
- **Direct Question** (force the viewer to keep watching): `Would You Have Pulled Over for This?`
- **Bold Claim / Contradiction**: `He Gave a Dog His Own Oxygen.`

---

## How to write the caption

The caption has two parts: 3 punchy opening lines, then a short story paragraph, then the AI disclosure and hashtags.

**Required — always include this line in every caption, word for word:**
`⚠️ AI-generated video. Story inspired by real rescue events.`

This protects the channel from strikes under YouTube's AI content disclosure policy.

**Full caption format:**
```
[Line 1 — the action or moment, mid-event]
❤️ [Line 2 — the stakes or what almost didn't happen]
🐾 [Line 3 — the payoff in motion]

[Story paragraph — 2–4 sentences, see rules below]

⚠️ AI-generated video. Story inspired by real rescue events.

#DogRescue #Shorts #[StorySpecificTag] #Viral #dogs #dogrescue #heartwarming #doglover #faithinhumanity #wholesome #goodpeople #viral #shorts #kindness #amazingmoment
```

**Hook-line rules — the 3 opening lines must use motion / stakes / payoff, not quiet sentiment:**
- Line 1 example: `He didn't slow down. He ran straight into the water.`
- Line 2 example: `Another ten seconds and she was gone.`
- Line 3 example: `She came up coughing — and licking his face.`

Pick a `#StorySpecificTag` that matches the video (e.g. `#RainRescue`, `#IceRescue`, `#HighwayRescue`, `#Abandoned`).

**How to write the story paragraph:**
- 2–4 sentences, past tense
- Focus on what the human chose to do — not vague kindness, a specific decision
- End on the dog's reaction (a tail lift, a step forward, a look) — this is the emotional close
- Suffering is implied through exhaustion or fear only — never mention blood, injury, or death
- Match detail to the Veo prompt — don't invent actions that aren't in the video

**Story paragraph example (heat rescue):**
> She wasn't moving when he found her. Flat on the pavement, panting in the heat, with nothing left. He didn't call anyone. He didn't walk away. He sat down beside her on the burning asphalt, gave her water from his own bottle, and waited — until her tail lifted for the first time.

---

## How to write the pinned comment

The pinned comment is a separate, copy-paste-ready message that the channel owner manually pins as the top comment under each Short. It is the channel's voice speaking directly to the community about the importance of saving and caring for dogs. It is NOT a second caption.

**Why it exists:** Shorts descriptions get buried on mobile — viewers rarely expand them. A pinned creator comment sits at the top of the comment section where it's actually seen, reads like the creator talking *to* the community, and invites replies (which boost the video). It also reinforces that the channel is an awareness movement, not just AI content for views.

**Rules:**
- **Length:** 1–2 short story lines, plus 1 short final CTA line (2–3 lines total). YouTube comments truncate fast on mobile.
- **Voice:** First person — "I", "we", "you". The creator speaking, not a brand.
- **Anchor on this video's specific beat.** Reference the moment the viewer just watched (the woman who pulled over, the firefighter who gave up his mask, the trucker who slid across two lanes). Never generic "save dogs" copy.
- **Soft CTA in the story lines.** Invite reflection, stopping for strays, awareness. Never "donate", "adopt", or external links.
- **Final line = subscribe + share ask.** After the 1–2 story-anchored lines, add one more short line asking the viewer to subscribe and share the video. Keep it first-person, keep the channel's awareness framing (subscribe/share *because these stories matter*, not for the channel's sake), end with 🐾. No external links, no hashtags, no "smash that bell."
- **End with 🐾** to match the channel's caption signature.
- **No hashtags** inside the pinned comment. Hashtags belong in the description.
- **Don't mention the AI.** The story is what matters. Treating the rendering as the focus undercuts the awareness goal.

**Canonical example (video-001 — abandoned dog in the rain):**
> Every dog like him has been walked past dozens of times before someone finally stopped.
> Don't scroll past a stray. A glance, a call, a moment. That's how lives get saved. 🐾
> Subscribe and share this with someone who'd stop too — that's how more dogs get found. 🐾

---

## Style rules

- Raw, real, phone-captured — not cinematic or produced
- The human gesture is always specific and physical — vague kindness doesn't work on camera
- The dog's reaction is the payoff — describe it precisely
- Every video ends with warmth, relief, or joy — never on suffering

---

## Rules — Non-Negotiable Before Every Script

1. Read `references/guideline-rules.md` BEFORE generating. No exceptions.
2. Read `references/example-scripts.md` BEFORE generating. No exceptions.
3. Read `references/yt-hacks.md` BEFORE generating. No exceptions. Apply its hook, motion, and retention principles to the Veo prompt, title, and caption — strong hook in the first 2 seconds, character in motion from frame 1, captions implied for mute viewers, loop-friendly ending, no "thanks for watching" outros.
4. The AI disclosure line must appear in every caption, word for word: `⚠️ AI-generated video. Story inspired by real rescue events.` And every output must include a PINNED COMMENT block — never skip it.
5. Never repeat the same story pattern as the most recently generated video.
6. Never describe blood, open wounds, or abuse happening on screen.
7. Every video ends on warmth, relief, or connection — never on suffering.
8. Titles must accurately reflect the video — emotional is fine, fabricated is not.
9. Read `references/yt-rescue-ideas.md` BEFORE generating. No exceptions. Pull inspiration from a category you haven't used recently, then adapt it through the rules above (no blood, warmth-ending, Veo prompt structure). You may also invent original ideas beyond this list.
10. First sentence of every Veo prompt's Action block must describe visible motion (running, falling, leaping, sprinting, lunging, hauling, etc.). Static openings ("lies", "curled", "shivering against the wall", "panting on the asphalt") are forbidden as sentence 1. Quiet moments belong in the *resolution*, never the *opening*.
11. Every Veo prompt must contain at least 4 distinct physical actions with active verbs. Count them before submitting.
12. Final image of the prompt must visually echo or complete the opening image, so the Short loops seamlessly (`references/yt-hacks.md` §11).
13. Veo prompt length is **~100–200 words across the six blocks** (Style / Scene / Subjects / Action / Camera / Audio), written for a single 8-second clip. Tighten the Action block to ~4 beats — an overlong Action on an 8s clip causes Veo to compress the middle and drop the late payoff frame. Tighten ruthlessly so every sentence carries a distinct visual moment, no padding, no decorative description.
14. Titles must reference action or a moment in motion. Reflective/quiet titles ("She Almost…", "Nobody…", "He Sat Down…") are banned. Use one of the 6 hook formulas listed in the "How to write the title" section.
15. **One action per sentence for complex spatial choreography.** Veo drops or simplifies multi-step actions when they're packed into a long comma-chain. If a beat involves spatial movement that must be visible on screen (e.g. "crosses two lanes", "vaults the railing then sprints back", "slides across the ice"), give it its own short sentence — not a clause buried in a longer sentence. Reason (Sora-era, still applies): video-006 highway rescue specified the trucker sprinting diagonally across two lanes, but the render kept him barely leaving the shoulder because the action shared a sentence with three other details.
16. **The ending needs at least 2 dedicated short sentences.** Do not pack the resolution into a tail clause of the final descriptive sentence. The dog's payoff (licking, tail thrashing, paws planted, body shaking off water) must be its own 2+ short sentences at the end of the Action block, before the Camera block. Reason (Sora-era, still applies): video-006's "the dog explodes — licking his jaw, paws planted on his shoulders, tail thrashing against his chest" rendered weakly because it was one comma-loaded sentence; the loop-back energy never landed.
17. Run the [Channel analytics — pre-generation check](#channel-analytics--pre-generation-check) BEFORE generating. No exceptions. This includes the staleness check (latest snapshot >2 days → ask for a fresh screenshot), reading only the two most recent snapshot folders, and noting in one or two lines which performance signal you are biasing toward and which pattern you are avoiding.
18. **The pinned comment must reference a specific beat from this video's story — never generic copy — and must end with a final subscribe + share line.** The awareness channel is built on viewers feeling spoken to about what they just watched, not handed a template. The story lines end with 🐾; the final CTA line also ends with 🐾. No hashtags, no external links, no mention of the AI rendering.
19. **Never fragment a single physical extraction into 4+ sequential micro-step sentences.** When the rescuer pulls the dog clear of the hazard (out of a hole, off a ledge, off the tracks, out of the water onto solid ground), that whole extraction is **1–2 sentences MAX** — not a chain of haul → lift → kick → drag → roll. Veo (like Sora) compresses sequential micro-steps and drops the "safety reached" frame. The moment the dog is fully clear and on safe ground must be its own dedicated short sentence, not buried in a micro-step chain. Reason (Sora-era, still applies): video-007 storm-drain rescue's 5-step extraction caused the render to skip the "dog fully on the pavement" frame entirely. Rule 15 (one action per sentence for spatial choreography across distance) still applies; this rule is the inverse — one physical extraction moment gets at most 1–2 sentences.
20. **Never write Veo prompts that depend on a timed near-miss collision.** Converging high-speed objects (train barely missing a rescuer leaping off the tracks, car barely missing a dog sprinting across a road, falling object barely missing the rescuer) render as impacts in Veo — burning credits and ruining the take. Pick single-source or static hazards instead: rising water in a fixed drain, ice that's already cracking, a collapsed pit, a smoke-filled doorway, floodwater being caught from a kayak. If the story idea requires "X seconds before impact" to land emotionally, the prompt will fail in Veo — pick a different story. Reason (Sora-era, same failure on Veo): video-007 train-tracks rescue rendered the train hitting both the man and the dog.
21. **Run the analytics snapshot-comparison and the winning-script cross-reference before generating.** In the [Channel analytics — pre-generation check](#channel-analytics--pre-generation-check): first compare the newest snapshot against the previous one and note the trend; then match the top performer(s) and the worst under-performer to their entries in `references/example-scripts.md` by exact title, mirror the structure of the highest-engagement entry, and avoid the worst. If a video has no matching entry, rely on its analytics signal alone.
22. **Write every Veo prompt in the six-block format** (Style / Scene / Subjects / Action / Camera / Audio), one 8-second native clip — matching video-012 / `references/example-scripts.md` Example 7. Never revert to a single Sora-style paragraph.
23. **Controlled verbs into the landing — never force-verbs.** Write "folds the dog into his chest as it comes down," not "slams". Force-verbs ("slams", "haul hard") plus "land" make Veo render an impact or the rescuer falling unnaturally instead of a catch.
24. **The dog must visibly bark on screen** (mouth opening) for its bark/whine audio to render — Veo ties audio to a visible source. Sequencing the sound in the Audio block alone does not produce it.
25. **Camera direction gets its own block,** stated plainly (handheld phone, low and close, slight shake). Veo prioritizes the camera request and defaults to static / subtle handheld if movement isn't named.
26. **Open on active struggle, never suffering, and never include aspect-ratio / meta** ("9:16", resolution). Distress cues ("panicked yelps", "eyes wide") read as a suffering dog — off-brand and a monetization risk; meta clutters the prompt.
27. **For a human-led rescue (the human reaches/wades/climbs TO the dog), the human is the only active agent — keep the dog passive.** Give the human every action verb (wades, reaches up, closes both hands, lifts, hauls) and keep the dog clinging / slipping / scrabbling for grip — **never** "reaching", "leaping", or "lunging toward him". Otherwise Veo falls back to its default "dog leaps to the human" motion and the human never performs the rescue. (Airborne-catch stories — Examples 3/6/7 — are the exception: there the dog *correctly* comes to the human, so it leaps and the human catches.) Reason: video-013 v1 had the dog "scramble/reach" and the man "grab" — Veo rendered the dog jumping onto him instead of being saved.
28. **Avoid the climbing-over-the-body pose — use a stable cradle hold.** A dog "scrambling up his torso / paws planted on his collarbone" makes Veo interpenetrate the two bodies (the dog clips through the human). For a carry/payoff, hold the dog **cradled in the arms** with it turning its head to lick and paws resting on his forearm. (In an airborne catch the dog folding into the chest is fine; it's the *climbing up the body* that clips.) Reason: video-013 v1's torso-climb payoff rendered the dog passing through the man's body.
29. **Never stage a leap that takes off from a small platform surrounded by open water** (ice floe, raft, rock midstream, half-submerged object). Veo can't reliably render the takeoff surface as solid, so it places the dog **standing or walking on the open water** before the leap — instantly killing realism. The dog's takeoff point must be obviously solid, continuous ground (a bank, a pier deck still attached to shore, a ledge, a rooftop). If the hazard is open water with no solid takeoff, make it a **human-led extraction** where the dog is clearly IN the water (paddling, clinging to an edge) and the human lifts it out — never an airborne leap across the water. Reason: video-014 v1's ice-floe-over-open-water leap rendered the dog walking across the black-water lead before jumping.
30. **Vary the rescuer's identity every video — never default to the same person.** Veo tends to render the same generic man (dark hair, plain t-shirt) in every clip, which makes the channel look repetitive. Before writing the Subjects block, check the last 2–3 videos and pick a **visibly different rescuer** — rotate gender, age, build, hair, and clothing (e.g. a woman in a raincoat, an older man with a grey beard, a young woman in a hoodie, a uniformed worker, a teenager). State one or two concrete appearance details so the render differs from recent videos. Keep the rescue mechanic and rules unchanged; only the person varies. Reason: user feedback after video-014 — "Veo is generating the same person in every video."

31. **If a render reads as fake, fix it with realism craft — never by shrinking the story.** Two confirmed levers: (1) **convert actively-collapsing structures to already-collapsed static damage** — asking Veo to simulate a structure breaking apart mid-shot can render rubbery/unreal; stage the damage as already done (middle span already in the creek) and keep only a small live element (the far span sagging) for urgency; (2) **push amateur-capture cues harder** in Style + Camera — vertical smartphone framing, autofocus hunting, motion blur, raindrops/spray dotting the lens, slightly overexposed flat light. These imperfections sell "a bystander filmed this." Reason: video-015 v1 (footbridge actively tearing apart, clean handheld look) was rejected as "doesn't look real"; v2 with static damage + hardened phone cues was approved.

---

## Progressive Update — How This Skill Stays Current

### Auto-update Rules from user feedback
Whenever the user defines something not to do — e.g. "don't use that setting again", "never do X", "stop doing Y" — immediately add a new numbered entry to the Rules section above. Do not wait to be asked. Capture the rule in the moment, exactly as the user stated it, and confirm you've added it.

### Auto-log approved scripts to the reference file
After generating every script, ask the user:

> "Do you approve this script? If yes, I'll save it to `references/example-scripts.md` so future videos can build on it."

- If the user approves: append the full output (Veo prompt, title, caption) to `references/example-scripts.md` under a new numbered example heading (e.g. `## Example 2 — Rain Rescue`).
- If the user does not approve: do not save it. Ask what to change and regenerate.
