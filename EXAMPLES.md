# Examples

**Visual Novel Illustrator**  
Created by **Turtle Dove (斑鸠)**

These examples demonstrate the intended behavior of the skill. They are not rigid output templates; the skill should adapt to the user's story and requested level of detail.

---

## Example 1 — Single visual-novel CG

### User

```text
Age: 9.
Children's shoe section in a shopping mall.

Xu Zai is standing in front of a mirror wearing white sneakers. There is a small transparent glitter panel on the side of the shoe, and it catches the light when she moves. She has already walked back and forth three times. On the fourth pass, she deliberately rises onto her toes.

Make the girl look at the mirror.
No text.
Show me the prompt first, then generate after I confirm.
```

### Expected skill behavior

#### Scene — The fourth pass

**Story beat:** Xu Zai pauses in front of the mirror and subtly rises onto her toes, watching how the new shoes look on her.

**Visual direction:**
- Characters: Xu Zai, nine years old
- Action / expression: facing the mirror, attention fixed on her reflection; one foot subtly lifted onto the toe
- Setting: bright but ordinary children's shoe department in a shopping mall
- Camera / composition: medium-wide three-quarter view; both the girl and her reflection are visible; the sneakers remain readable in the lower part of the frame
- Lighting / mood: soft commercial lighting with a small natural glint on the transparent shoe panel; intimate, observational mood
- Continuity locks: white sneakers; transparent glitter panel; age; mall shoe section
- Hard constraints: no subtitles, captions, UI, logos, or invented readable text

**Generation prompt:**

```text
Visual-novel narrative CG. A nine-year-old girl named Xu Zai stands in the children's shoe section of a modern shopping mall, facing a full-length mirror while trying on clean white sneakers. A small transparent glitter panel on the side of the sneakers catches the overhead store light. She has just stopped after walking back and forth and now deliberately rises slightly onto her toes, studying her own reflection with quiet interest. Frame both the girl and her reflection in a natural medium-wide three-quarter composition, keeping the shoes clearly visible. Soft ordinary mall lighting, believable body language, polished story-driven illustration, finished but unobtrusive background. No text, no subtitles, no dialogue box, no UI, no watermark, no invented readable signage.
```

The skill then waits for approval. After the user confirms, it generates the image using the built-in image-generation capability.

---

## Example 2 — Three-image continuous CG sequence

### User

```text
Turn this into three visual-novel CGs. Keep both characters visually consistent.
Show me the plan first. After I approve, generate the three images continuously.

The boy waits under the convenience-store awning because of the sudden rain. The girl runs toward him from across the street, holding her school blazer over her head. She reaches the awning laughing, but then notices blood on his knuckles. Her smile disappears. He quietly hides his hand behind his back.
```

### Expected shot plan

#### Scene 1 — Across the rain
**Function:** setup / anticipation  
**Frozen moment:** He notices her running toward him through the rain.  
**Composition:** wider shot; boy in sheltered foreground, girl crossing rain-heavy middle ground.  
**Continuity locks:** uniforms, convenience-store awning, rain, same time of day.

#### Scene 2 — Safe under the awning
**Function:** interaction / warmth  
**Frozen moment:** She reaches him laughing, slightly breathless, blazer still held above her head.  
**Composition:** medium two-shot; physical distance closes; rain becomes background texture.

#### Scene 3 — The hidden hand
**Function:** turn / tension  
**Frozen moment:** Her eyes drop to the blood on his knuckles as he begins moving that hand behind his back.  
**Composition:** tighter two-shot or over-shoulder framing; her changed expression and his hand both readable.

### Expected generation behavior after approval

1. Generate the best anchor frame first — usually Scene 2, because both characters, clothes, location, and lighting are clearly visible.
2. Confirm the anchor is compatible with the approved design.
3. Generate Scene 1 using the anchor as a visual continuity reference when supported.
4. Generate Scene 3 using the same anchor/reference chain.
5. If Scene 3 changes a face, uniform, or location noticeably, regenerate only Scene 3.

The skill should not turn the three scenes into unrelated images with different-looking characters.

---

## Example 3 — Long-running character consistency

### User

```text
This is a continuing visual-novel project.

Character lock for Shen Yu:
- 21 years old
- short black hair, slightly uneven fringe
- narrow eyes
- slim build
- usually wears a washed black hoodie and silver ring on the right index finger
- looks distant in public but reacts subtly around Lin Qiao

Use the attached approved portrait as the visual anchor.

New scene:
At 2:13 a.m., Shen Yu is sitting alone on the floor of a laundromat, leaning against a washing machine. He receives a voice message from Lin Qiao but does not play it yet.
Make one CG. Show me the prompt before generating.
```

### Expected continuity handling

The skill should lock:

- 21-year-old appearance
- short black hair / uneven fringe
- narrow eyes
- slim build
- washed black hoodie
- silver ring on right index finger
- previously approved visual identity from the attached portrait

The new scene may invent small non-plot visual details — e.g. fluorescent laundromat lighting, rows of machines, reflections on tile — but must not redesign Shen Yu.

If the approved portrait is actually visible to the model, it can be used as the visual reference during generation. If it is not available in the current context, the skill must not pretend it can reference it.

---

## Example 4 — Prompt-only mode

### User

```text
Do not generate anything. I only need a prompt for an illustration model.

A woman opens the door to her childhood bedroom after fifteen years. Nothing inside has been moved except that the desk lamp is on.
```

### Expected behavior

The skill should still:

1. interpret the narrative beat
2. choose a camera position
3. make the emotional subtext drawable
4. provide a polished prompt

But it must stop before calling image generation because the user explicitly selected prompt-only mode.

---

## Example 5 — Direct-generation override

### User

```text
Use our established character designs. Split this scene into two images and generate them directly. Don't show me prompts first.
```

### Expected behavior

The skill performs the story and continuity analysis internally, then goes directly to generation. It must not force an approval step the user explicitly waived.

For continuity-sensitive images, generate them sequentially rather than as two unrelated one-off generations.
