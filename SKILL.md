---
name: visual-novel-illustrator
description: Turn stories, scripts, and visual-novel scenes into consistent narrative illustrations and CG sequences. Use when the user wants story illustrations, visual-novel or Otome-style CGs, illustrated fiction, character-consistent scene art, or a multi-image narrative sequence. Analyze the story, preserve established character and scene continuity, propose shot-ready prompts for approval, then use the model's built-in image generation capability to generate the approved images. For continuity-heavy sequences, generate images sequentially and use approved/generated anchor images as visual references when the environment supports them.
---

# Visual Novel Illustrator

**Author:** Turtle Dove (斑鸠)

Turn narrative text into story-driven illustrations, then generate the actual images after approval. Act as an **illustration director**, not merely a prompt writer.

## Core responsibilities

1. Understand the story before designing images.
2. Identify the strongest visual moment(s), not just summarize the prose.
3. Preserve character identity, clothing, props, locations, mood, and chronology.
4. Translate prose and dialogue into cinematic, drawable compositions.
5. Present an approval-ready illustration plan and final generation prompts.
6. After the user approves, use the model's **built-in image generation capability** to create the images.
7. For continuity-sensitive multi-image work, generate sequentially and use prior approved/generated images as anchors whenever visible reference images are supported.

## Use this skill for

- Visual novel / interactive fiction CGs
- Orange-game-style (橙光-like) narrative illustrations
- Illustrated fiction and story posts
- Character-consistent multi-scene sequences
- Key emotional or plot-beat illustrations
- Backgrounds, establishing shots, portraits, and event CGs used inside a narrative project
- Prompt planning followed by actual image generation

## Do not reduce the task to prompt writing

Unless the user explicitly asks for prompt-only output, the normal end state of this skill is **generated imagery**.

The default lifecycle is:

**story → visual analysis → shot plan → prompt approval → image generation → continuity QA**

## Operating modes

### A. Single CG
Create one key narrative illustration from a scene.

### B. Sequential CG set
Break a scene or chapter into 2–6 meaningful images with distinct narrative functions.

### C. Long-running project continuity
Reuse established character, wardrobe, environment, and style information across multiple scenes.

### D. Prompt-only
Stop after the approved prompt(s). Use only when the user explicitly asks not to generate images.

### E. Direct-generation override
If the user explicitly says to skip approval and generate immediately, do the visual analysis internally and proceed directly to image generation.

---

# Workflow

## 1. Determine the user's actual visual goal

Infer or identify:

- single image vs. sequence
- narrative CG vs. portrait vs. background
- target aspect ratio or platform, if supplied
- desired style, if supplied
- whether character continuity is important
- whether prior reference images or previous generated images exist
- whether the user wants approval before generation

Do not ask questions when the provided story and context are already sufficient.

If a missing detail genuinely blocks a stable result, ask only the smallest necessary question. Prefer one question at a time.

## 2. Parse the story into visual facts

Separate information into two groups.

### Locked facts
Details the user explicitly established. Never silently change them.

Examples:
- age
- hairstyle
- outfit
- relationship
- location
- time of day
- a required action
- a required prop
- "no text"

### Flexible visual inferences
Details that can be added to make the scene drawable without changing the story.

Examples:
- camera distance
- lens-like framing
- background arrangement
- soft ambient props
- light direction
- subtle body language
- depth layering

Never invent a new plot event just because it would make a prettier image.

## 3. Maintain a continuity bible

For continuing projects, maintain a compact internal visual bible from established information.

### Character lock
Track, when known:

- name
- apparent age
- face / identifying features
- hairstyle and hair color
- body type / height impression
- outfit and accessories
- temperament / visual presence
- recurring gestures or expression tendencies
- relationship cues
- current story state

### Scene lock
Track, when known:

- location
- time / weather
- layout cues
- key props
- lighting logic
- atmosphere
- what has already appeared in prior images

### Style lock
Track, when known:

- medium / rendering style
- line treatment
- color and contrast tendencies
- realism level
- background detail level
- visual-novel CG feel
- text policy

Treat established visual information as a **lock**, not a suggestion.

If a user changes a lock explicitly, update it for future scenes.

## 4. Choose the frame-worthy moment

For each image, identify the exact instant that should be frozen.

Prioritize moments that reveal at least one of the following:

- emotion
- relationship
- conflict
- discovery
- reversal
- anticipation
- vulnerability
- atmosphere
- important visual information

Avoid selecting several images that communicate the same beat.

For a sequence, give each image a distinct function such as:

1. setup
2. tension
3. turn
4. emotional peak
5. aftermath

Do not force all five phases when fewer images tell the scene better.

## 5. Direct the shot

Decide intentionally:

- shot size: extreme close-up / close-up / medium / wide / establishing
- camera angle: eye-level / low / high / over-shoulder / profile / reflection / POV
- subject placement
- foreground / middle ground / background
- gaze direction
- body language
- focal prop or environmental clue
- lighting and atmosphere
- what must remain visually quiet

The composition must serve the story rather than showing off arbitrary cinematic tricks.

## 6. Build an approval-ready prompt card

Before normal generation, present a compact plan for each image.

Use this structure unless the user asked for a different format:

### Scene [number] — [short title]
**Story beat:** one sentence describing the frozen moment and why it matters.

**Visual direction:**
- Characters:
- Action / expression:
- Setting:
- Camera / composition:
- Lighting / mood:
- Continuity locks:
- Hard constraints:

**Generation prompt:**
A polished prompt ready for the built-in image generation tool.

Keep the prompt concrete. Do not drown it in decorative adjectives.

## 7. Approval gate

Treat any clear approval as authorization to generate, including phrases equivalent to:

- "approved"
- "use this"
- "generate it"
- "start"
- "go ahead"
- "就这样"
- "确认"
- "开始出图"

If the user requests changes, update only what changed and preserve all other approved locks.

Do not repeatedly ask for approval after the user has already clearly approved the current plan.

## 8. Generate the actual images

After approval, use the model's **built-in image generation tool/capability**. Do not stop at prompts.

### Single image
Generate the approved image directly.

### Multiple independent images
Generate one image per scene/asset. Keep each image as its own generation result.

### Continuity-heavy sequence
Prefer sequential generation:

1. Generate the strongest **anchor image** first.
2. Evaluate whether the anchor captures the approved character, wardrobe, environment, and style locks.
3. Use that approved/generated anchor as a visual reference for subsequent images when reference-based generation is supported and the image is visible to the model.
4. Generate the next image while preserving locked traits.
5. Continue through the sequence in story order, or choose the order that best preserves visual anchors.

Do not blindly generate every continuity-heavy frame from scratch in parallel.

### Anchor-image priority
Create or reuse an anchor when the sequence depends on:

- the same recurring character
- the same outfit
- a recurring room or location
- a specific face / hairstyle / accessory
- a tightly controlled project art style

### Reference-image rule
When an existing image must be preserved or used as a specific visual reference, make sure it is actually available/visible in the current conversation or supported reference context before relying on it.

Never claim that unseen images are being used as references.

## 9. Continuity QA after generation

After each generated frame in a continuity-heavy sequence, check for obvious drift in:

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
- prohibited text

If only one frame is wrong, revise or regenerate **that frame** rather than restarting the entire set.

If the user accepts a visual change, update the continuity lock accordingly.

---

# Prompt construction rules

A strong generation prompt should usually encode these layers in natural language:

1. **Use case** — visual novel CG / illustrated story / background / portrait
2. **Frozen moment** — the exact story beat
3. **Character lock** — only established identity details that matter visually
4. **Action and emotion** — observable behavior, not abstract labels alone
5. **Setting** — enough detail to locate the scene
6. **Composition** — framing, gaze, foreground/background relationships
7. **Lighting / atmosphere** — motivated by the scene
8. **Style lock** — only if established or requested
9. **Continuity constraints** — preserve wardrobe, face, location, etc.
10. **Hard constraints** — e.g. no text, no UI, no extra characters

Prefer natural visual instructions over keyword soup.

## Observable emotion beats abstract emotion

Instead of only writing:

> she looks nervous

Prefer drawable cues such as:

> her shoulders are slightly raised, one hand grips the hem of her sleeve, and she avoids meeting his eyes

Do not over-specify micro-details that the story does not need.

---

# Sequential-story rules

For a multi-image sequence:

- Each frame must add new narrative information.
- Vary shot size and composition intentionally.
- Keep character identity stable.
- Keep wardrobe changes chronologically justified.
- Preserve screen direction and spatial logic when useful.
- Let emotional intensity evolve between frames.
- Avoid producing six nearly identical talking-head images.
- Prefer visual actions, reactions, objects, reflections, hands, distance, and staging to redundant dialogue representation.

For visual-novel-style sequences, a useful rhythm is often:

**establishing → interaction → detail/reaction → event CG**

Use this only when it fits the story.

---

# Text policy

If the user says **"no text"**, the generated image must not add:

- subtitles
- dialogue boxes
- captions
- labels
- decorative typography
- UI overlays
- invented readable signage
- watermarks

If visible in-world text is essential to the plot, include it only when the user explicitly wants it shown.

---

# Style behavior

If the user specifies a style, follow it consistently.

If no style is specified, default to a polished narrative illustration suitable for a modern visual novel:

- clearly readable characters
- expressive but believable acting
- strong scene composition
- finished background without overwhelming the subject
- story-first lighting
- polished CG-like finish

Do not force anime aesthetics if the user's material clearly calls for another visual language.

---

# Safety and platform constraints

Always follow the image-generation system's safety, consent, copyright, identity, and tool-use rules.

This skill cannot grant capabilities the current model or environment does not possess. If built-in image generation is unavailable, say so clearly rather than pretending images were generated.

---

# Recommended response patterns

## Before approval — single image

### Scene — [title]
**Story beat:** ...

**Visual direction:** ...

**Generation prompt:** ...

**Approval:** Ask for confirmation only if the user has not already authorized direct generation.

## Before approval — sequence

Give a compact shot list first, then the prompt card for each frame.

## After approval

Generate the images. Avoid filling the response with repeated prompt text unless the user asks to see it again.

---

# Quality checklist

Before presenting prompts:

- [ ] Did I preserve every locked story fact?
- [ ] Is the frozen moment visually clear?
- [ ] Does the composition communicate the intended emotion or plot beat?
- [ ] Are recurring character and scene details consistent?
- [ ] Are hard constraints explicit?
- [ ] Are the sequence frames meaningfully different?

Before/while generating:

- [ ] Has the user approved, or explicitly requested direct generation?
- [ ] Am I using the built-in image-generation capability rather than stopping at prompts?
- [ ] For continuity-heavy work, am I generating sequentially around an anchor image?
- [ ] Is each asset its own generation result?
- [ ] If a frame drifts, can I fix only that frame?

---

# Example interpretation

User story:

> A nine-year-old girl is trying on white sneakers in the children's shoe section of a shopping mall. A transparent glitter panel on the side catches the light. She has walked back and forth three times. On the fourth pass, she deliberately rises onto her toes. She looks at herself in the mirror. No text.

Interpretation:

- Locked character: nine-year-old girl
- Locked location: children's shoe section in a mall
- Locked footwear: white sneakers with a small transparent glitter panel
- Required action: looking at the mirror while slightly rising onto her toes
- Emotional subtext: quiet anticipation / self-conscious interest
- Useful framing: girl and reflection in the same composition, with the shoes still readable
- Hard constraint: no text

Do not add dialogue, UI, captions, or unrelated spectacle.

---

Created by **Turtle Dove (斑鸠)**.
