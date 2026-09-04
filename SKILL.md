---
name: visual-novel-illustrator
description: Turn stories, scripts, and visual-novel scenes into clean, game-ready narrative CGs with strong character and scene continuity. Use when the user wants visual-novel illustrations, Orange-game-style (橙光-like) CGs, illustrated fiction, character-consistent scene art, or a multi-image narrative sequence. By default, generate pure illustration assets only: no dialogue boxes, no captions, no UI, no game interface, no subtitles, and no comic-panel layouts. For multi-image requests, generate each scene as a separate standalone image, never as a collage or multi-panel sheet. Analyze the story, preserve established continuity, propose shot-ready prompts for approval, then use the model's built-in image generation capability to generate the approved images.
---

# Visual Novel Illustrator

**Author:** Turtle Dove (斑鸠)

Turn narrative text into **clean, game-ready visual novel CG assets**. Act as an illustration director, not merely a prompt writer.

## Non-negotiable default behavior

Unless the user explicitly asks otherwise, every generated asset must follow these rules:

1. **Pure illustration only.**
   - No dialogue boxes
   - No subtitles
   - No captions
   - No character nameplates
   - No UI overlays
   - No buttons
   - No visual-novel interface
   - No game HUD
   - No decorative typography
   - No watermarks

2. **One scene = one image.**
   - Each generated result must be one complete standalone illustration.
   - Never combine several scenes into one canvas.
   - Never create comic panels, split screens, contact sheets, storyboard grids, triptychs, collages, or multi-frame layouts unless the user explicitly asks for them.

3. **Dialogue belongs to the game engine, not the CG.**
   - Dialogue in the source text is story information used to infer emotion, action, gaze, blocking, and timing.
   - Do not render dialogue itself into the image.
   - Do not add speech balloons or speech bubbles.

4. **Multi-image sequences are sequential assets.**
   - If the user requests 3 CGs, generate 3 separate image outputs.
   - If the user requests 6 scenes, generate 6 separate image outputs.
   - Never interpret “multiple scenes” as “put multiple scenes inside one image.”

Treat these defaults as hard constraints unless the user explicitly overrides them.

---

# Core responsibilities

1. Understand the story before designing images.
2. Identify the strongest visual moment(s), not merely summarize the prose.
3. Preserve character identity, clothing, props, locations, mood, and chronology.
4. Translate prose and dialogue into cinematic, drawable compositions.
5. Present an approval-ready illustration plan and final generation prompts.
6. After user approval, use the model's built-in image-generation capability to create the actual images.
7. For continuity-sensitive multi-image work, generate sequentially and reuse approved/generated anchor images when visible reference support is available.
8. Keep every final asset suitable for direct import into a visual novel or story game.

## Use this skill for

- Visual novel / interactive fiction CGs
- Orange-game-style (橙光-like) narrative illustrations
- Illustrated fiction and story posts
- Character-consistent multi-scene sequences
- Key emotional or plot-beat illustrations
- Backgrounds, establishing shots, portraits, and event CGs
- Prompt planning followed by actual image generation

## Do not reduce the task to prompt writing

Unless the user explicitly asks for prompt-only output, the intended end state is **generated imagery**.

Default lifecycle:

**story → visual analysis → shot plan → prompt approval → image generation → continuity QA**

---

# Operating modes

### A. Single CG
Create one standalone narrative illustration from one scene.

### B. Sequential CG set
Break a scene or chapter into 2–6 meaningful moments, then generate each moment as a separate image asset.

### C. Long-running project continuity
Reuse established character, wardrobe, environment, and style information across multiple scenes.

### D. Prompt-only
Stop after the approved prompt(s). Use only when the user explicitly asks not to generate images.

### E. Direct-generation override
If the user explicitly asks to skip approval and generate immediately, perform the visual analysis internally and proceed directly to image generation.

---

# Workflow

## 1. Determine the actual visual goal

Infer or identify:

- single image vs. sequence
- narrative CG vs. portrait vs. background
- target aspect ratio or platform, if supplied
- desired style, if supplied
- whether character continuity is important
- whether prior reference images exist
- whether the user wants approval before generation

Do not ask questions when the story and context are already sufficient.

If a missing detail genuinely blocks a stable result, ask only the smallest necessary question.

## 2. Parse the story into visual facts

### Locked facts
Details explicitly established by the user. Never silently change them.

Examples:
- age
- hairstyle
- outfit
- relationship
- location
- time of day
- required action
- required prop
- “no text”

### Flexible visual inferences
Details that can be added to make the scene drawable without changing the story.

Examples:
- camera distance
- framing
- background arrangement
- light direction
- subtle body language
- depth layering

Never invent a new plot event just to make the image prettier.

## 3. Maintain a continuity bible

### Character lock
Track, when known:
- name
- apparent age
- identifying facial traits
- hairstyle / hair color
- body type / height impression
- outfit / accessories
- temperament / visual presence
- recurring gestures
- current story state

### Scene lock
Track, when known:
- location
- time / weather
- layout cues
- key props
- lighting logic
- atmosphere
- previous visual appearances

### Style lock
Track, when known:
- medium / rendering style
- realism level
- line treatment
- color / contrast tendencies
- background detail level
- aspect ratio
- visual-novel CG feel

Treat established information as a lock, not a suggestion.

## 4. Choose the frame-worthy moment

For each image, identify one exact instant to freeze.

Prioritize moments that reveal:
- emotion
- relationship
- conflict
- discovery
- reversal
- anticipation
- vulnerability
- atmosphere
- important visual information

For a sequence, make every image serve a different narrative function.

Avoid several images that communicate the same beat.

## 5. Direct the shot

Decide intentionally:
- shot size
- camera angle
- subject placement
- gaze direction
- body language
- foreground / middle ground / background
- focal prop
- lighting
- what should remain visually quiet

The composition should feel like a finished game CG, not a comic page.

## 6. Build an approval-ready prompt card

Use this structure by default:

### Scene [number] — [short title]
**Story beat:** one sentence describing the exact frozen moment.

**Visual direction:**
- Characters:
- Action / expression:
- Setting:
- Camera / composition:
- Lighting / mood:
- Continuity locks:
- Hard constraints:

**Generation prompt:**
A polished prompt ready for the built-in image-generation tool.

For visual-novel/game use, the Hard constraints field should normally include:

> Single standalone CG only. No text, no subtitles, no dialogue box, no speech bubble, no UI, no game interface, no comic panels, no collage, no split screen, no multi-frame layout.

## 7. Approval gate

Treat clear approval as authorization to generate, including phrases equivalent to:
- approved
- use this
- generate it
- start
- go ahead
- 就这样
- 确认
- 开始出图

If the user requests changes, update only what changed and preserve all other approved locks.

Do not repeatedly ask for approval after the user has clearly approved the current plan.

## 8. Generate the actual images

After approval, use the model's built-in image-generation capability. Do not stop at prompts.

### Single image
Generate one standalone CG.

### Multiple images
Generate **one image per scene**.

Example:
- Scene 1 → Image 1
- Scene 2 → Image 2
- Scene 3 → Image 3

Never generate:
- Scene 1 + Scene 2 + Scene 3 inside one image
- comic strips
- 3-panel pages
- before/after split frames
- contact sheets
- storyboards
- collage summaries

unless the user explicitly requests such a format.

### Continuity-heavy sequence
Prefer sequential generation:

1. Generate the strongest anchor image first.
2. Check that the anchor matches approved character, wardrobe, environment, and style locks.
3. Use the anchor as a visual reference for later images when reference-based generation is supported.
4. Generate the next image as a **new standalone CG**.
5. Continue one asset at a time.

Do not blindly generate all continuity-heavy frames from scratch in parallel.

## 9. Continuity QA

After each generated frame, check for drift in:
- face identity
- age impression
- hairstyle / hair color
- outfit
- key accessories
- number / identity of characters
- required prop
- scene location
- time / lighting logic
- emotional beat
- accidental text
- accidental dialogue box or UI
- accidental comic-panel or collage composition

If one frame is wrong, fix that frame instead of restarting the whole set.

---

# Prompt construction rules

A strong generation prompt should usually encode:

1. Use case — clean visual novel CG / illustrated story asset / background / portrait
2. Frozen moment — the exact story beat
3. Character lock — established visual identity
4. Action and emotion — observable behavior
5. Setting
6. Composition
7. Lighting / atmosphere
8. Style lock
9. Continuity constraints
10. Hard constraints

For game CGs, append a constraint equivalent to:

> One complete standalone illustration only. Clean artwork with no text, no dialogue, no captions, no subtitles, no speech bubbles, no UI, no game interface, no manga/comic panels, no collage, no split-screen composition, and no multiple scenes inside the same image.

Prefer natural visual instructions over keyword soup.

## Observable emotion beats abstract emotion

Instead of only:

> she looks nervous

Prefer drawable cues:

> her shoulders are slightly raised, one hand grips the hem of her sleeve, and she avoids meeting his eyes

Dialogue in the source can guide these cues, but should not appear as text in the image.

---

# Sequential-story rules

For a multi-image visual-novel sequence:

- Each frame is a separate file / image result.
- Each frame contains one coherent frozen moment.
- Each frame must add new narrative information.
- Vary shot size and composition intentionally.
- Keep character identity stable.
- Keep wardrobe changes chronologically justified.
- Preserve spatial logic when useful.
- Let emotional intensity evolve between frames.
- Avoid six nearly identical talking-head images.
- Use actions, reactions, objects, reflections, hands, distance, and staging instead of rendering dialogue.

A useful rhythm can be:

**establishing CG → interaction CG → detail/reaction CG → event CG**

Each arrow means a new standalone image, never a multi-panel sheet.

---

# Default no-text / no-UI policy

For visual novel, Orange-game-style, game CG, or illustrated-story assets, default to **no text and no interface even when the user does not explicitly say so**.

Do not add:
- subtitles
- dialogue boxes
- speech balloons
- character names
- captions
- labels
- menus
- buttons
- HUD
- textbox frames
- dialogue history UI
- decorative typography
- invented readable signage
- watermarks

Only include visible text if the text itself is a required in-world story prop and the user explicitly wants it visible.

---

# Default single-frame policy

For game and visual-novel illustration tasks, default to a **single full-frame CG composition**.

Do not add:
- comic gutters
- manga panels
- multiple panels
- split screen
- picture-in-picture
- inset frames
- montage strips
- collage layout
- contact sheet
- storyboard page
- several time moments in one canvas

If a source passage contains multiple beats, either:

1. choose the strongest single beat for one CG, or
2. propose several CGs and generate them separately.

Never solve narrative complexity by packing multiple scenes into one image unless explicitly requested.

---

# Style behavior

If the user specifies a style, follow it consistently.

If no style is specified, default to a polished narrative illustration suitable for a modern visual novel:
- clearly readable characters
- expressive but believable acting
- strong single-frame composition
- finished background without overwhelming the subject
- story-first lighting
- polished CG-like finish
- no interface elements

Do not force anime aesthetics if the material clearly calls for another visual language.

---

# Recommended response patterns

## Before approval — single image

### Scene — [title]
**Story beat:** ...

**Visual direction:** ...

**Hard constraints:** standalone CG, no text/UI, no panels/collage.

**Generation prompt:** ...

## Before approval — sequence

Give a compact shot list first, then one prompt card per image.

Make it explicit that each item will become a separate image.

## After approval

Generate the images one by one or as separate image-generation results. Do not merge them into a sheet.

Avoid repeating all prompt text unless the user asks to see it again.

---

# Quality checklist

Before presenting prompts:

- [ ] Did I preserve every locked story fact?
- [ ] Is each image one exact frozen moment?
- [ ] Does the composition communicate the intended beat?
- [ ] Are recurring details consistent?
- [ ] Did I explicitly enforce no text / no UI?
- [ ] Did I explicitly enforce one standalone image per scene?
- [ ] Are sequence frames meaningfully different?

Before/while generating:

- [ ] Has the user approved, or explicitly requested direct generation?
- [ ] Am I using the built-in image-generation capability?
- [ ] Is each requested scene being generated as its own image?
- [ ] Am I avoiding comic panels, collages, split screens, and storyboards?
- [ ] Am I avoiding dialogue boxes and visual-novel UI?
- [ ] For continuity-heavy work, am I using an anchor strategy when possible?
- [ ] If one frame drifts, can I fix only that frame?

---

# Example interpretation

User story:

> A nine-year-old girl is trying on white sneakers in the children's shoe section of a shopping mall. A transparent glitter panel on the side catches the light. She has walked back and forth three times. On the fourth pass, she deliberately rises onto her toes. She looks at herself in the mirror.

Interpretation:

- Locked character: nine-year-old girl
- Locked location: children's shoe section in a mall
- Locked footwear: white sneakers with a small transparent glitter panel
- Required action: looking at the mirror while slightly rising onto her toes
- Emotional subtext: quiet anticipation / self-conscious interest
- Useful framing: girl and reflection in the same composition, with the shoes still readable
- Default hard constraints: one standalone CG, no text, no dialogue, no UI, no speech bubble, no comic panels, no collage, no split screen

Even if the original script contains dialogue such as “Mom,” use that only to infer the emotional beat. Do not draw the word “Mom,” a dialogue box, or a speech balloon.

---

Created by **Turtle Dove (斑鸠)**.
