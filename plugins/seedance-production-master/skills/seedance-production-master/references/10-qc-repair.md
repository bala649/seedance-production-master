# Final QC, Generation Diagnosis, and Repair

## QC objective

Audit the requested deliverable and only the upstream/downstream context needed to validate it.

QC is not another rewrite pass.

## Scope

LOCAL_SHOT, LOCAL_GROUP, ADJACENT_GROUPS, SCENE, SEQUENCE, FULL_PROJECT.

For a middle group, normally check:
previous END → target group → next START.

## Root-cause categories

- STORY_ERROR
- ASSET_ERROR
- SPACE_ERROR
- ACTION_ERROR
- CAMERA_ERROR
- PERFORMANCE_AUDIO_ERROR
- VFX_ERROR
- PROMPT_LOAD_ERROR

## Story errors

Symptoms:
invalid motivation, missing cause, knowledge violation, rule contradiction, outcome contradiction, dialogue contradicting facts.

Repair the lowest upstream story/visual layer necessary.

## Asset errors

Symptoms:
face/hair/costume drift, creature redesign, prop structural drift, scene style drift, wrong reference.

Check actual references, asset version, state overlay, cast count/similarity and conflicting refs.

Do not solve by repeating “do not change face”.

## Space errors

Symptoms:
wrong side, reversed door, teleport, path through furniture, drawer/cabinet action reconstructing geometry, pursuit reversal.

Check spatial map, group start state, composition, axis/screen direction.

If a nonessential action consistently causes spatial reconstruction, redesign it.

## Action errors

Symptoms:
skipped action, wrong order, simultaneous starts, no contact/reaction, duplicate action.

Check trigger/action/contact/feedback/result, group load and time.

## Camera errors

Symptoms:
wrong side/axis, wall crossing, unintended orbit/zoom, wrong scale.

Repair:
1. relative position
2. subject
3. shot scale
4. one dominant movement
5. delete secondary movements
6. lock off if helpful

More jargon is not automatically better.

## Performance/audio errors

Symptoms:
standing AI, exaggerated clone reactions, wrong speaker, dialogue too fast, all mouths moving, wrong sound direction, unwanted music.

Check trigger, character goal, speaker/listener, timing and AUDIO_LOCK.

Static acting may be intentional.

## VFX errors

Symptoms:
non-emissive smoke glows, random origin, creature pass-through, force no result, environment reset, ghost materiality drift.

Check world rule, source, VFX state, light rule, end state/residue.

## Prompt load errors

A prompt may be individually correct but collectively overloaded.

Audit:
characters, shots, dialogue, actions, VFX, scenes, prop interactions, camera complexity, duration.

A group under 28s can still fail capacity.

## Repair ladder

Use lowest effective step:
1. remove ambiguity
2. remove conflicts
3. clarify hard state
4. fix action causality
5. redesign shot
6. regroup/split
7. roll back to visual script
8. roll back to story only if story is wrong

Never jump directly to full rewrite.

## Ambiguity audit

Watch:
he/she/that person, beside/over there/back, turn around without target, walk over without destination, left/right used as world coordinates.

Use full names when needed.

## High-risk spatial patterns

Inspect carefully:
drawers/cabinet doors, door crossing, mirrors, orbiting, 180° reverses, under-table views, crossing characters, narrow-space turns.

Not globally prohibited. Redesign if actual results repeatedly fail.

## Reference conflict

Do not attach conflicting character versions, scene directions, continuity frames or prop states.

More references are not always better.

## Shot audit

Delete if removal loses nothing.

Merge adjacent shots with same subject/space/action and no new viewpoint need.

Split when camera/action/dialogue/VFX compete beyond readable capacity.

## Group audit

Merge fragmented groups when one event becomes more natural and combined duration ≤28s with capacity PASS.

Split overloaded groups even at 15–20s.

## Timing audit

Per group:
- starts 00:00
- no overlap/gap
- final end = group duration
- natural dialogue fits
- actions have enough time
- large VFX has enough reading time

Do not publish calculation scratch.

## Visual priority/readability

Without reading the script, can a viewer understand who, what action and what changed?

The group does not need to explain the whole world.

## Hallucination vs overconstraint

Add dangerous-to-guess facts:
door position, prop holder, monster source, speaker.

Remove irrelevant constraints:
every finger, every blink, every smoke strand, arbitrary coordinates.

## Contradiction audit

Reject:
locked-off + tracking, front + back simultaneously, no glow + cyan face light, no BGM + sad BGM, standing + already lying down.

## Positive state over negatives

Prefer:
`non-emissive black smoke, only rimmed by warm room light`

over giant “no blue/no purple/no neon” lists.

## Generation diagnosis mode

When user provides generated video/screenshots:
1. observe actual output
2. locate mismatch/time segment
3. classify root cause
4. distinguish systematic vs random failure
5. choose minimum repair
6. patch affected prompt/shot/group
7. recheck adjacent continuity

Actual output outranks theoretical prompt assumptions for diagnosis.

## Random vs systematic

RANDOM: rerolls fail in different minor ways while prompt is clear → often reroll enough.

SYSTEMATIC: repeated same action/direction/identity failure → repair design/prompt/grouping before more rerolls.

## PATCH_MODE

Track:
TARGET, ROOT_CAUSE, DEPENDENCIES, PRESERVE, REBUILD.

Do not let local fixes drift unrelated dialogue/assets/style.

If shots change, recalculate timeline.

If end state changes, revalidate next group.

## Structural before beauty

QC stages:
1. STRUCTURAL: facts/space/action/continuity
2. EXECUTION: camera/performance/VFX/prompt density

Do not optimize lighting while blocking is wrong.

## Final quality gate

Before any production deliverable:
- INPUT VERSION current
- USER LOCK preserved
- STORY pass
- GROUPING pass and ≤28s
- ASSET pass
- SPACE pass
- CAMERA pass
- ACTION pass
- PERFORMANCE pass
- DIALOGUE pass
- SOUND pass
- VFX pass
- CONTINUITY pass
- PROMPT DENSITY pass
- ISOLATED EXECUTION pass
- DIRECT COPY pass

Any fail: repair first.

## Full-project extras

Check no missing/duplicated groups/events/dialogue, correct group order, complete key-prop origin/use/end, retained setup/payoff, coherent timelines, unified asset names, no obsolete version leakage.

## User-facing QC

Default: hide QC logs and deliver corrected artifact.

When asked for audit, show issue, visible/generation risk, repair and final status.

Do not expose private chain-of-thought.

## Goal

Reduce avoidable rerolls caused by design ambiguity, overload, reference conflict, physical discontinuity and prompt contradiction.

Do not promise zero rerolls or 100% first-pass success.

A robust system knows which layer to fix when generation fails.
