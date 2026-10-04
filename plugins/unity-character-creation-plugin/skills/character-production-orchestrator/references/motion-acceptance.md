# Source motion and bake acceptance

A contact sheet with the requested rows/columns is not a completed animation. Judge the intended action in timed playback and trace the pixels to actual production inputs. Static plugin checks cannot prove motion quality.

## Production origin

AI-generated concept art or a turnaround can be an inspected design reference. Do not ask an image generator to produce the full action/direction sprite sheet and then call it a Unity bake. Do not slice generated contact-sheet cells and treat them as source clip samples. The default hybrid pipeline requires an actual authoring rig, AnimationClip, deterministic Editor exporter execution and raw registered pass images. A separately requested hand-drawn pipeline must be explicitly recorded; never silently relabel it hybrid-baked-frames.

Before accepting a bank, inspect the real source rig/clip and exporter implementation, plus their execution result and output files in the target project. Record source asset paths/GUIDs and revisions, camera/pass layout, action/direction, duration, ordered sample times, exporter path/revision, execution log path, and raw/final frame paths in FRAME_BANK_SPEC.md. Preserve raw files. A prose statement saying "baked" is insufficient. Metadata is a traceability record, not a cryptographic proof of authenticity.

Assemble contact sheets and looping previews from these actual ordered final frames at their declared durations. Label action, direction, indices and times. Never regenerate the review sheet with an image generator. Use lossless PNG source frames for pixel/alpha review; a JPEG screenshot can demonstrate concerns but cannot establish source transparency or exact pixel measurements.

## Identity and geometric consistency

Compare head/face/hair, clothing seams/palette, torso volume and limb proportions against the accepted direction master. Preserve source art, camera and anatomical limb identity across all samples. Record any intentional foreshortening or pose-driven projection; do not mistake projected length for bone stretch. Constant rigid source segment lengths are the baseline. Child joints stay attached; limb scales or local translations require explicit justification and actual render review.

Overlay registered consecutive frames and source/cleaned pairs, and review timed playback. Head location may change with approved bob; head shape must not randomly redraw. Changes in lighting, canvas registration or source identity are failures until explained. Pixel cleanup repairs approved poses using the registered raw sample; it must not invent a different person or new independent pose sequence.

## Walk motion gate

Before baking every view, validate a source walk in one locked direction with body+base clothing only. Start South for a new project; isolate the user's reported direction for incident diagnosis. Require:

- An explicit mapping Leg A/B to anatomical L/R for the whole clip, and stable parent joint anchors.
- Two distinguishable contact poses: opposite anatomical legs advance at half-cycle, with corresponding near/far ordering appropriate to the view.
- Two passing poses: the support and swinging legs can be tracked; feet do not merely teleport or rotate under an otherwise frozen lower body.
- Coherent pelvis, thigh, shin and foot trajectories. Screen depth and airborne foot lift are different components; do not detach a foot or stretch a shin to fake a stride.
- A recorded stride/ground-motion convention. With world movement, support-foot motion matches ground travel; for an in-place clip, its ground sweep corresponds to the recorded stride/speed. Diagnose sliding by playback with actual world movement.
- Subtle opposing arm swing correlated with leg phase, including forearm/hand continuity. Intentional held grips override the free-arm rule and are recorded.
- Small declared body bob with comparatively stable head; direction-appropriate silhouette, ankle/ground contact and a seamless cycle.

Record contact/passing captures, foot/hand trajectories or measured pose landmarks, chosen tolerances and two continuous source cycles. Tolerances come from native size, camera and style; do not invent universal pixel thresholds. Motion-only foot differences, a stiff repeated torso/arm pose, or a nearly unchanged frame sequence need investigation rather than automatic acceptance. Small South depth movement can be correct, so assess intended gait rather than demanding a wide side-view stride.

## Sampling the walk

A proposed phase-aligned baseline for a .5-second walk is 8 unique frames at 16 FPS:

| Index | Source time (seconds) | Phase |
| --- | --- | --- |
| 0 | .0000 | Contact A |
| 1 | .0625 | Transition |
| 2 | .1250 | Passing A |
| 3 | .1875 | Transition |
| 4 | .2500 | Contact B |
| 5 | .3125 | Transition |
| 6 | .3750 | Passing B |
| 7 | .4375 | Transition toward Contact A |

Do not append .5000 to the loop. A 12-FPS/.5-second loop has 6 samples, but none exactly at .125 or .375. If that schedule is chosen, inspect those source passing poses separately and verify that exported motion still reads correctly. Eight frames are not a quality guarantee; changing FPS cannot correct bad source anatomy or incoherent gait. Do not enforce walk counts/FPS on idle or any other action. Each action chooses a schedule that communicates its own critical phases, including contact/release and terminal poses.

## Runtime and recovery

Review the source loop, raw loop, cleaned loop and runtime loop at the same direction and timing. If source is coherent and raw is not, fix sampling/camera/pass export. If raw is coherent and final is not, revert or repair cleanup. If final is coherent and runtime is not, inspect frame order, timestamps, phase mapping, pivot, layer selection and item coverage. Do not keep regenerating a valid master to repair a later stage.

For a poor multi-direction sheet, preserve source evidence and mark affected bank acceptance pending/failed. Recover one action in one direction, first without equipment, and produce a real timed preview. Then add one outfit/weapon and verify layer synchronization/occlusion. Expand one direction at a time only after this baseline works. Every view receives its own action review; eight rows do not prove eight valid directions. Missing actual project inputs prevent a confirmed root-cause diagnosis, but independent plugin instructions can still be corrected.
