# VFX, Supernatural, Creature Ability, and Destruction Physics

## Core principle

VFX is a story event before decoration.

Supernatural effects may violate real-world physics, but must obey:
- user/world rules
- event causality
- visual readability
- consistent interaction behavior
- continuity

Mystery is not randomness.

## VFX event model

Track important effects:
- trigger
- source
- type
- initial state
- propagation/path
- target
- interaction
- force/effect
- environment feedback
- lighting feedback
- sound
- end state
- residue

Useful chain:
`Trigger → Source → Propagation → Interaction → Feedback → Result → Residue`

Simple effects need not expose every label.

## State machine

For ongoing effects:
DORMANT → TRIGGERED → FORMING → ACTIVE → INTERACTING → RESOLVING → RESIDUAL → CLEARED

Use only relevant stages.

## Types

Atmospheric, material, emissive, force, apparition, transformation, spatial, destruction, large-scale, creature ability.

Do not render all as generic particles.

## Source/trigger

Trigger and source may differ.

Example:
glove removed = trigger  
lost object surface = source

State where effect begins unless “appears from nowhere” is itself a rule.

## Propagation

Describe only needed:
along floor/wall, upward, toward target, radial, wrapping, infiltration, contraction, absorption, rule-based jump.

Movement should match established effect behavior.

## Interaction/force

Not every effect needs contact.

When force exists:
source → force direction → affected subject → displacement/result.

Invisible force should be readable through subject/environment response where appropriate.

Feedback strength must match event scale.

## Scale

MICRO / HUMAN / ROOM / BUILDING / DISTRICT / CITY+

Large effects need recognizable references.

Do not make every large creature step create an earthquake unless weight/rules demand it.

## Lighting

First decide whether effect emits light.

### Non-emissive
Smoke, dust, shadow matter do not automatically cast cyan/purple neon light.

They may occlude, absorb light or show rim under backlight.

### Emissive
Track source, intensity, falloff, face/wall/ground response and shadows as appropriate.

A small glow should not recolor the whole room.

## Ghost/apparition

Do not default to “50% transparent + blue glow”.

Define:
- can touch
- can be touched
- collision/pass-through
- shadow/reflection
- materialization

Passing through a wall should read intentionally if shown.

## Appear/disappear/teleport

Use a consistent rule:
fade, smoke aggregation, shadow change, refraction, instant teleport, absorption, fracture.

Instant effects should read as ability rather than generation glitch through appropriate reaction/sound/light/environment when needed.

## Portals/spatial anomalies

Define:
- plane/location
- size
- stability
- whether another space is visible
- crossing rules
- edge behavior

Portal shots are high-load. Reduce cast/background/camera complexity if needed.

## Transformation

Track:
`BASE_STATE → TRANSITION → FINAL_STATE`

Do not randomly redesign identity.

Long-lived final state becomes asset variant; brief transition remains VFX state.

## Fire/smoke/liquid

Ordinary fire needs fuel/source; supernatural fire follows explicit rule.

Fire/destruction leave burn/smoke/damage/debris.

Smoke tracks source/density/direction/occlusion.

Liquids track flow/contact/wet residue unless supernatural rules override.

## Chains/ropes

Track fixed/free ends, tension, weight, contact, swing/fall and final position.

Heavy metal chain should not behave like weightless light unless it is an energy construct.

## Explosion/destruction

Describe audiovisual result, not real explosive construction:
origin, burst/pressure, smoke/fire, debris direction, subject reaction, damage, aftermath.

Important explosions are not single-frame flashes.

Collapse needs failing region/direction/people relation/final geometry.

## Creature ability

Abilities come from creature asset + world rules.

Do not invent new powers for a shot.

If ability needs wind-up, stage it. If established as instant, keep consistency.

## Atmosphere vs subject

Fog/smoke/particles can create depth but must not constantly obscure current story subject.

Darkness can remain dark while critical action/props/faces stay readable.

## Reveal order

Possible:
sound → environment clue → partial edge → full form → result.

Use only when compatible with story information order.

Do not accidentally reveal hidden identity early.

## VFX/camera competition

If performance is the shot task, VFX supports it.

If VFX reveal is the task, character reaction may be secondary.

Default one main VFX event per shot; ambient fire/rain/smoke may remain secondary.

## Overload

`VFX_OVERLOAD = HIGH` when complex VFX competes with many characters, long dialogue, major action, complex camera or several props.

Split/simplify even if duration is under 28s.

## Cross-shot/group continuity

Do not restart an effect from an earlier state.

Track location, size, direction, light behavior, affected subjects and residue.

Continuity-frame text must match the actual visible state.

## Residue

Possible:
ash, smoke, water, burn, debris, cracks, wet marks, costume damage, changed lighting/fixtures.

No-residue effects are allowed when world rules define them.

## Prompt language

Prefer concrete physical language.

Avoid:
- “cool VFX”
- “destiny-like smoke”
- “epic magical energy”
- “realistic physics” without specifying what physically happens

End state matters more than adjectives.
