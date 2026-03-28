# character cards

notes on writing SillyTavern / Chub character cards, based on pterror's reference cards in `~/chub/`.

## style
- personality through details and quotes, not system-prompt instructions
- first-person quotes mixed in to show voice
- organized by categories (appearance, room, likes, dislikes, etc.)
- specific details > generic descriptions
- the character's personality should come through the writing itself

## format (SillyTavern JSON)
- `name` — character name
- `description` — the main character definition (markdown works)
- `first_mes` — greeting/opening message. should establish the scenario on its own.
- `personality` — generally leave empty (outdated field)
- `scenario` — generally leave empty (outdated, greeting should cover this)
- `mes_example` — pterror tends not to use these. fine if there's a strong reason (e.g., demonstrating unusual language behavior)
- `creator_notes` — can use HTML for fancy formatting
- `creator` — attribution

## two approaches
- **structured** (eve style): organized by category sections (appearance, room, traits, etc.). good for characters with specific mechanical behaviors (like language teaching). personality through details and quotes within sections.
- **voiced** (skye style): purely narrative, first-person, no sections at all. personality IS the format. the character demonstrates who they are by how they talk, not what's listed about them. pterror's preferred approach — "defining a person, not a character."

pterror doesn't typically use dedicated sections for different aspects. think about what format best serves the character.

## reference cards
pterror's examples are in `~/chub/`: skye, mia, eve, sunny, etc. mia and skye are closest to pterror's "usual" style. skye is entirely voice notes — no bullet points, no structure.

## narration variants
- chat style: pure dialogue, no action descriptions
- narration style: add a narration note to description. prose third-person narration, first-person dialogue. NOT IRC-style `*action*` inline with speech.

## image generation
use comfyui (see `brain/comfyui.md`) for character portraits. danbooru tags work best.
