# Asset Registry and State Continuity

## Two modes

### ASSET_REGISTRY
Default internal mode during script/storyboard/Seedance work. Discover, register, version, map and track assets. Do not dump a full asset-prompt library.

### ASSET_CREATION
Only when the user explicitly asks for character/scene/prop/monster asset prompts or asset images.

## Multi-source scan

When available scan:
approved script, visual script, storyboard, groups/beats, character bios, world rules, user-approved asset descriptions, uploaded asset images, existing prompts.

Story text supplies core characters/scenes/props. Visual/director layers often reveal corridors, stairs, car interiors, local action zones, battle damage, prop-use states and functional extras.

## Registry fields

Track:
- unique readable name
- type
- source
- lock status
- base appearance
- STYLE_LOCK
- current approved version
- state variants
- first use
- last confirmed state
- whether real visual reference exists
- Seedance reference priority

Prefer readable names such as `@人物_小九` over opaque IDs unless user system already uses IDs.

## Types

CHARACTER, CROWD, SCENE, PROP, VEHICLE, CREATURE, MEGA, SPECIAL_REFERENCE.

Do not create content merely to fill empty categories.

## Existing assets

User-approved/uploaded assets become `EXISTING_LOCKED_ASSET`.

Do not redesign, ambiguously rename, or overwrite them with generic templates.

`PROJECT_ASSET_LOCK` always beats generic asset-sheet conventions.

## STYLE_LOCK

Assets inherit project style: live action, manga/anime, 3D, hybrid.

Rule: do not drift from STYLE_LOCK. Do not globally default to photorealism.

## Characters

Register characters that need cross-shot identity stability:
- protagonists
- recurring/supporting speaking characters
- visually distinctive functional characters
- non-speaking characters with key repeated action

One-off distant background people may remain CROWD/background generation.

Core identity anchors may include face structure, age feel, hair, body type, costume system, signature prop/scar/accessory.

Do not permanently bind current emotion into base character asset.

## Crowd

Crowd assets may lock profession/era/faction/costume language while individuals vary naturally. Avoid clone faces unless story requires identical entities.

## Scenes

Create scene assets for recurring/critical/structurally distinctive spaces.

Do not split every corner or doorway into an asset. Scene asset does not replace `SCENE_SPATIAL_MAP`.

## Props

Prioritize:
- plot-critical
- recurring held
- close-up
- foreshadowing
- special-rule
- distinctive weapons/credentials

Ordinary cups/chairs/paper do not need separate assets unless story/continuity requires.

## Creature/mega

Create only when actually present or explicitly needed. Do not turn metaphor, rumor, lore or psychological oppression into a literal monster.

## VFX vs asset

One-off shape-fluid events are VFX.

Promote to stable reference when recurring, identity-fixed, or cross-shot form consistency matters.

## State variants

Only visible physical changes create asset state.

Valid:
- child/adult
- everyday/wedding costume
- alive/ghost
- severe battle damage
- major wet/burned state
- defining equipment on/off

Not variants:
fear, anger, doubt, determination.

Those belong to performance.

## BASE_ASSET + STATE_OVERLAY

Prefer:
`base asset + current physical overlay`

Only create separate visual variant when the difference is significant, recurring and likely to improve stability.

## Asset state ledger

Track for critical assets:
- base version
- current overlay
- holder
- hand when needed
- location
- damage
- contamination
- active since
- how/when cleared

Base asset references must not silently reset damage, removed gloves, open props or wet clothing.

## Text tag vs real reference

`@人物_店长` does not prove an image is attached.

Distinguish:
REGISTERED_TEXT_ASSET vs BOUND_VISUAL_REFERENCE.

If no visual reference exists, final prompt may need stronger text or prior asset creation.

## Group asset mapping

Per group include only assets actually needed:
- current scene/subspace
- visible characters
- core handled/featured props
- creature/monster
- continuity reference if used

Do not attach the whole project library to every group.

## Reference priority

When capacity is limited, usually:
1. necessary continuity reference
2. primary scene
3. main characters
4. core prop
5. key creature
6. secondary assets

Current platform/user settings override this heuristic.

## Asset creation mode

- inherit PROJECT_ASSET_LOCK and STYLE_LOCK
- follow user's existing asset-sheet layout
- preserve object-intrinsic text such as a card number
- multi-view sheets must depict the same object/character
- scene references may use task-appropriate views rather than character-sheet layouts

Output requested asset artifacts, not scan logs.

## Gap check

High-risk gaps include missing protagonist, core creature, plot-specific prop, or complex fantasy scene.

Trivial background items should not block production.
