# Story Facts and Visual Script Engine

## STORY_FACT_LEDGER

Build stable facts so downstream directing does not guess.

Fact classes:
CHARACTER, RELATIONSHIP, WORLD_RULE, PROP, LOCATION/SPATIAL, EVENT, CAUSAL, INFORMATION, TEMPORAL, DIALOGUE, EMOTIONAL, OUTCOME, SETUP_PAYOFF, CONTINUITY.

Statuses:
LOCKED, EXPLICIT, DERIVED_SAFE, OPEN, CONFLICT, REVISED_APPROVED, OBSOLETE.

`DERIVED_SAFE` never overrides explicit source facts.

Source order:
1. current explicit user instruction
2. current project locks/current approved version
3. current source material
4. prior approved upstream facts
5. conservative inference

## Information permissions

Track separately:
- audience knowledge
- each character's knowledge
- hidden information
- reveal timing

Never let characters react to information they have not acquired.

## Story development and doctoring

Only actively rewrite when authorized or when upstream material is incomplete and the user wants development.

Diagnose:
- causality
- motivation
- agency
- stakes
- obstacle/choice/consequence
- relationship pressure
- information order
- setup/payoff
- coincidence
- world-rule violations
- subplot stealing main line
- emotional truth
- repeated beats
- explanatory dialogue
- cheap twists
- ending/hook logic

Use the smallest repair that solves the root issue.

Important actions should be explainable through goal, fear, wound, misconception, dignity, secret, responsibility, interest, love, shame, survival pressure or current information.

If the only reason is “plot needs it”, repair.

## Scene validity

For each scene ask:
- who enters with what goal/state?
- what pressure/opposition exists?
- what effective event occurs?
- what changes?
- who gains/loses what?
- what new information/emotion/question appears?
- what state changes by scene end?

At least one trackable state should change: information, relationship, risk, goal, prop, space control, decision, or meaningful question.

Quiet scenes may work when intentionally functional.

## Coincidence

Coincidence may initiate/escalate trouble. Major resolution should not rely on unearned coincidence unless source/genre establishes that mechanism.

## Main/subplot discipline

Subplots should pressure, contrast, mirror or enable the main line. Do not force equal development. In short-form, secondary material should be efficient.

## Dialogue

Locked dialogue is exact.

When revision is authorized:
- keep character-specific language
- use subtext, interruption, partial answers, silence
- avoid mutual exposition of known facts
- avoid directly stating theme
- prefer lines that also change event/relationship/information

Do not force every line to have a gesture.

## Theme/payoff

Prefer choice/consequence over speeches explaining theme.

Critical twists need fair earlier traces in behavior, objects, dialogue, rules or visual information. Not every atmospheric detail requires payoff.

## STORY_HANDOFF

Before visual/director production internally prepare:
- approved version
- scene task
- characters present
- current goals
- information states
- place/time
- story-critical spatial facts
- non-negotiable actions/results
- core props
- locked dialogue
- reveal permissions
- setup/payoff duties
- scene exit state

## Visual script layer

The visual script bridges story and shots.

It decides:
- time/place
- environment state
- world-space anchors
- entrances/exits
- approximate locations/orientation
- action paths
- trigger/reaction/action/result
- prop interactions
- important performance beats
- sound triggers
- VFX event logic
- reveal order
- scene end physical state

It does not normally lock exact camera coordinates, focal lengths, shot count, exact shot duration or final camera movement.

## SCENE_SPATIAL_MAP

For important/reused spaces lock:
- main entrance/secondary exits
- activity zones
- key furniture/obstacles
- depth/high-low relations
- key props
- dangerous areas
- path connections

Do not invent compass directions unless useful. Stable anchors such as “counter side”, “inside south door”, “coffin head” are enough.

Scene asset = appearance.  
Spatial map = connectivity.

## Scene start/end states

Start may include:
- present characters
- location/orientation
- props in hands
- doors/windows
- environment
- ongoing VFX
- sound state

End updates those facts for continuity.

## Action visualization

For important action:
`Trigger → visible reaction → action → necessary contact → feedback → result`

Do not turn visual script into biomechanics.

Stimulus precedes reaction. Characters only react to what they can perceive.

Track distance/orientation only when story-relevant.

## Prop chain

Track source, discovery, holder, transfer/use, damage and final location. Handedness only when continuity requires it.

## Sound as event

Important offscreen sound has source/location and may be the Trigger.

## VFX in visual script

Define enough to know:
source → propagation → interaction/result → residue.

Do not decide final lens/compositing language here.

## Flashback

Enter via a clear trigger unless nonlinear form is already established. Exit through completed information, emotional trigger, sound/action bridge or interruption. Reality state must be recoverable.

## Montage/time compression

Choose representative visible facts. Do not dramatize every repetitive side event.

## VISUAL_HANDOFF

Pass:
- STORY task
- START_STATE
- SPACE
- CHARACTER_PATH
- ACTION_CHAIN
- PROP_STATE
- PERFORMANCE_BEATS
- SOUND_EVENTS
- VFX_EVENTS
- INFORMATION_ORDER
- END_STATE
- VISUAL_PRIORITY

If the director still has to guess core action causality or world-space position, this layer is incomplete.
