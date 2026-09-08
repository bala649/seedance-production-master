# Global Continuity Ledger

## Core invariant

For continuous time/space:
`STATE OUT(N) → STATE IN(N+1)`

Continuity means factual/physical compatibility, not identical pixels or identical screen composition.

## Ledger scopes

Maintain:
PROJECT_CONTINUITY, SCENE_CONTINUITY, GROUP_CONTINUITY, SHOT_CONTINUITY.

Track only what can affect story/execution.

## Categories

CHARACTER, SPACE, ORIENTATION, ACTION, PROP, COSTUME, INJURY, CONTAMINATION, ENVIRONMENT, LIGHT, VFX, SOUND, TIME, INFORMATION.

## Character state

Track:
- present/not present
- world-space location
- pose
- body orientation
- gaze target
- current action
- physical condition
- held items
- emotional stage where relevant

Characters do not appear/disappear without entry/exit/cut/time/rule explanation.

## World location

Use stable anchors:
counter east side, inside south door, coffin head, corridor entrance.

Do not use permanent “screen left” as world geography.

## Action phases

For cross-shot actions:
NOT_STARTED → STARTED → IN_PROGRESS → CONTACT → RESULT → COMPLETED.

A key action should not restart after already completing.

Ordinary unimportant movement may be omitted by editing. Story-critical transfer/contact may not be silently skipped.

## Props

Track:
- unique name
- location
- holder
- hand when needed
- orientation when needed
- open/closed/partial/locked/broken
- damage
- contents

A unique prop cannot have two holders at once.

Door/drawer/coffin/box state changes persist until changed.

## Costume

Track approved version, gloves/headwear/accessories, removed items, tears/wet/burn/contamination.

Calling a base asset in a new group must not reset current physical state.

## Injury/contamination

Track injury location/severity/mobility/visible blood/bandage/clothing effect.

Track rain/mud/dust/blood/oil/water/burn residue when visible and continuous.

States may decay plausibly over time; do not reset instantly.

## Space topology

Lock story-critical doors/exits, stairs, counter, coffin, well, furniture/obstacles, room connections and high/low zones.

Furniture matters when it affects path/blocking/action.

Check `PATH_VALIDITY`.

## Axis/screen direction/eyeline

Maintain `CURRENT_AXIS` when necessary.

Axis may change through visible movement/re-establishment.

Track screen direction in travel/action and gaze targets in dialogue/reveal.

## Environment

Track relevant weather, wind, fire, smoke, water, crowd, vehicles, machines, doors/windows, destruction.

Destruction accumulates.

## Light

Track real sources, direction, fixture state and VFX contribution.

Reverse shots can show different sides while obeying one real source.

## VFX

Track phase, location, size, direction, emissive state, affected subject, residue.

If a cyan lamp turns off, cyan face reflection disappears.

Do not randomly change VFX color/scale.

## Sound

Track sustained sound source, existence, distance and occlusion.

An alarm already sounding does not “suddenly start” again after a cut unless it stopped.

## Time

Classify:
CONTINUOUS, SHORT_ELAPSE, TIME_JUMP, FLASHBACK, FLASHFORWARD, DREAM/ALTERED.

Continuous time requires strongest matching.

Time jumps may change state but do not erase permanent facts.

Flashbacks have their own continuity state; restore reality state when returning.

## Information

Track what each character knows. Audience knowledge and character knowledge are separate.

Relationship/emotion may change quickly only with a trigger, deliberate mask or time transition.

## Hard vs soft state

### HARD STATE
Cannot silently change:
character location/pose/orientation when continuity depends on it, prop holder/state, doors, injury, costume, destruction, major VFX result.

### SOFT STATE
May evolve:
breathing, minor hair, small smoke shape, background-extra microaction, emotion intensity.

Prioritize hard state in final prompts.

## Handoff contract

For adjacent groups track:
- PREVIOUS_END
- NEXT_START
- MUST_MATCH
- MAY_EVOLVE
- CUT_TYPE

Do not require same-frame continuity across scene/time cuts.

## Designed/generated/accepted

- `DESIGNED_STATE`: intended state
- `GENERATED_STATE`: actual model output
- `ACCEPTED_STATE`: actual result user explicitly keeps

Only accepted state may overwrite downstream reality.

A random model mistake must not automatically become canon.

## Change propagation

Classify edits:
LOCAL, SHOT_CHAIN, GROUP, CROSS_GROUP, STORY_GLOBAL.

Example:
remove “open drawer” → remove downstream assumptions that drawer is open or a key came from it unless another action supplies the cause.

Use dependency graph for critical prop/action chains.

## Split/merge/delete

Deleting a shot requires relocating any essential prop transfer, movement, door change, reveal or VFX transition.

Merging shots preserves intermediate action.

Splitting groups requires a stable split state.

## Severity

CRITICAL: story/identity/time/death/core prop  
HIGH: teleport, door, weapon hand, injury, reversed direction  
MEDIUM: lighting/costume minor mismatch  
LOW: non-story micro drift

Repair high-severity first.

## Continuity extraction

Do not paste the whole ledger into Seedance.

For each group extract relevant hard state into `GROUP_CONTINUITY_LOCK`.

## Cross-group gate

From group 2 onward:
previous END must be compatible with current START.

If user requests one middle group and adjacent states exist, check both sides internally.

## Audit response

When asked to audit, report concrete observable issues and fixes, not private chain-of-thought.
