# Visual Novel Illustrator Skill

> Story text → visual direction → approved prompts → actual generated illustrations.

**Author:** **Turtle Dove (斑鸠)**

`visual-novel-illustrator` is an Agent Skill for turning stories, scripts, and visual-novel scenes into coherent narrative artwork. It is designed for illustrated fiction, visual novels, interactive fiction, Orange-game-style (橙光-like) projects, event CGs, and character-consistent multi-image sequences.

Unlike a prompt-only helper, this skill is designed to continue all the way to **image generation** when the current model/environment exposes a built-in image-generation capability.

## What it does

- Reads prose, dialogue, or scripts as narrative material
- Identifies the strongest frame-worthy moment(s)
- Converts narrative beats into camera-ready visual direction
- Maintains character, wardrobe, scene, prop, and style continuity
- Produces approval-ready generation prompts
- Waits for user approval by default
- After approval, invokes the model's built-in image generation capability
- For continuity-heavy sequences, generates images sequentially around anchor images instead of treating every frame as an unrelated prompt
- Supports prompt-only or direct-generation modes when explicitly requested

## Why this skill exists

Story illustration is not just "write a better image prompt." Long-form visual storytelling has harder problems:

- the same character changes face between images
- clothes and accessories drift
- locations stop matching
- every frame becomes the same medium-shot conversation
- visually pretty images fail to communicate the story beat
- multi-image generation loses emotional and chronological continuity

This skill treats the model as an **illustration director**: story comprehension comes first, visual design second, generation third.

## Repository structure

```text
visual-novel-illustrator-skill/
├── SKILL.md
├── README.md
├── EXAMPLES.md
├── NOTICE.md
└── agents/
    └── openai.yaml
```

## Installation

### Agent Skills compatible environments

Use the repository folder as an Agent Skill package. `SKILL.md` contains the required skill metadata and workflow instructions.

### ChatGPT / OpenAI environments

Where Skills upload/install is available, upload the skill package or install it using the product's Skills interface. The exact product availability can depend on plan, workspace settings, and surface.

### Codex

The skill follows the Agent Skills folder convention and includes `agents/openai.yaml` for OpenAI UI metadata.

> Image generation still depends on the host environment exposing a built-in image generation capability. The skill does not create a new image API by itself.

## Typical workflow

```text
1. User provides story / script / scene
2. Skill extracts locked facts and continuity requirements
3. Skill selects the best visual beat(s)
4. Skill designs the shot(s)
5. Skill presents final prompt card(s)
6. User approves
7. Skill generates the actual image(s)
8. Skill checks continuity and fixes only drifting frames when needed
```

## Example request

```text
Turn this scene into three visual-novel CGs.
Keep the heroine's appearance and clothes consistent.
Show me the shot plan and prompts first.
After I approve, generate all three images in sequence.
No text inside the images.

[story text...]
```

## Long-running projects

For a continuing project, provide or establish:

- character designs
- recurring outfits
- important locations
- art direction
- aspect ratio
- previous approved/generated anchor images

The skill treats established information as **continuity locks** until the user changes them.

## Image-generation behavior

The default behavior is **approval first, generation second**.

Once approved, the skill should not merely repeat the prompt. It should invoke the built-in image-generation tool available to the current model/environment.

For multi-image narrative sequences that depend on visual consistency, the skill prefers:

```text
anchor image → next image using anchor/reference → next image → ...
```

rather than generating every frame independently from scratch.

## Modes

| Mode | Behavior |
|---|---|
| Single CG | One story beat → one final illustration |
| Sequential CG set | 2–6 story beats → coherent multi-image sequence |
| Long-running continuity | Reuse established character / wardrobe / scene / style locks |
| Prompt-only | Stop before image generation |
| Direct generation | Skip the approval gate when the user explicitly requests it |

## Design principles

1. **Story first.** Beautiful but narratively wrong is still wrong.
2. **Locked facts stay locked.** Do not silently redesign established characters or scenes.
3. **Drawable emotion.** Prefer body language, gaze, distance, objects, and staging over abstract emotion labels.
4. **Every frame earns its place.** A sequence should progress, not repeat itself.
5. **Use anchors for continuity.** Recurring faces, outfits, and locations should not be regenerated as unrelated strangers.
6. **No fake generation.** If the current environment has no image-generation capability, say so.

## Examples

See [`EXAMPLES.md`](./EXAMPLES.md) for:

- a single CG example
- a three-image visual-novel sequence
- a long-running character-consistency example
- a prompt-only example

## Attribution

Created by **Turtle Dove (斑鸠)**.

If you fork or adapt the project, keeping the original attribution is appreciated.
