# Beat, Generation Group, and Timeline Engine

## Three levels

Beat = dramatic change.  
Generation Group = one independent Seedance generation task.  
Shot = one director viewpoint.

Never force `1 Beat = 1 Group` or `1 Group = 1 Shot`.

## Full map first

For multi-group projects, allocate all major scenes/events, dialogue, actions, reveals, reactions, VFX, results and split points before writing group 1.

Each critical content atom gets one primary owner group. Prevent duplication and omission.

## Content-driven grouping

Group primarily by:
1. scene/spatial continuity
2. core event
3. complete dialogue unit
4. complete action
5. information reveal
6. emotional turn
7. VFX event
8. model capacity
9. stable end state

Duration is a consequence, not the first splitter.

## Hard duration

`HARD_GROUP_MAX_DURATION = 28s`

28 seconds is a ceiling, not a target.

Short groups are valid. Never pad with pauses, empty shots, repeated reactions or duplicate dialogue.

If content exceeds 28s, split at a natural narrative/physical point.

## Capacity model

Check:
- character count
- dialogue volume
- action complexity
- scene count
- VFX complexity
- prop interactions
- camera complexity
- information density

A group under 28s may still be overloaded.

## Merge when

Most/all are true:
- same continuous event
- same/naturally connected space
- stable cast
- no spatial-axis reset
- action/dialogue becomes more complete
- combined duration ≤28s
- capacity remains safe
- merged execution is more stable

Example: “walk to door” + “open door and see anomaly” often belongs together.

## Split when

- clear scene change
- major time jump
- identity/asset state changes dramatically
- visual style changes
- current event already has a complete result
- new core event begins
- axis must be rebuilt
- dialogue/action/VFX compete heavily
- stable handoff is valuable

Same scene does not imply same group.

## Dialogue

Keep natural question/answer/reaction together when possible.

Locked long dialogue:
- preserve exact words
- allow natural delivery time
- split by semantic pause if needed
- use listener reaction/camera coverage instead of unnatural speed

## Action closure

Prefer:
discover → approach → grab  
attack → evade/contact → result  
push door → door opens → reveal

Avoid ending mid-air/mid-contact/half-reveal unless a stable reference workflow genuinely supports it.

## VFX closure

Prefer:
Trigger → form → propagate → interact → result.

Cross-group VFX only when state is reconstructable.

## Emotion

Major emotional change needs stimulus, understanding/reaction and new choice/state.

## Shot density

Shot count is content-driven.

One 18s group may be 1 sustained shot, 3 dialogue shots or 6 action shots.

Each shot has one main viewing task.

## Cut reasons

Use cuts for new information, reaction, action phase, viewpoint change, spatial clarification, emotional change, time/reveal/result.

Avoid decorative cutting.

## Two timelines

Maintain GLOBAL_TIMELINE internally and GROUP_LOCAL_TIMELINE for final prompt.

Each group starts `00:00`.

Shots have no overlap/gap; final shot end = group duration.

Do not duplicate a dense micro-timeline inside each shot unless precise choreography needs it.

## Start/end

Each group has `GROUP_START_STATE` and one `GROUP_END_STATE`.

Start includes relevant characters, location/orientation, props, doors, environment, VFX, injury/costume.

End contains the physical facts downstream must inherit.

## Handoff modes

- HANDOFF_STATE_ONLY
- HANDOFF_FRAME_REFERENCE
- HANDOFF_CUT

Do not globally force one mode.

## No fixed first/last-frame prose sections

Default prompts do not create dedicated 首帧/尾帧 sections.

Per-shot action endpoints + group end state carry semantic continuity.

If the user's workflow uses `@首帧_本组`, it may be listed as a real input reference.

## Group edits

Merge requires recalculating capacity, timeline, shots, space/action continuity and a single new end state.

Split requires a stable `SPLIT_STATE`, not a mechanical halfway cut.

After either, recheck previous end/current start/current end/next start and content ownership.
