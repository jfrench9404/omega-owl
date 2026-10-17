# Concept brief v0

**Approved by the owner on 2026-10-17**, with the decisions recorded in section 11. Concept stage: nothing is bought, built or connected. This repository is public, so exact budget figures, accounts, network details and personal data stay out of it.

**Basis.** The owner chose the suggested answer to all 25 questions in `docs/questions.md` (open PR #1). They are listed in the appendix. Where the owner later decided differently, the decision wins (section 11). Anything still unsettled is marked *proposal* or *to decide*.

## 1. What it is

A desk-sized, stylised, friendly owl companion that reacts to people. It works on its own and is not linked to other systems. First prototype goal: on a trigger, it turns its head, shows animated eyes and makes an owl sound, and it can always be stopped safely.

## 2. Behaviors (v0)

- **Idle:** eyes animate gently, head still.
- **Trigger:** a button press only (decided). No wake word and no presence sensing in v0.
- **Response:** the head turns slowly to a preset position, eyes react, a hoot or chime plays, then it returns to rest.
- **Stop:** a visible switch cuts all motion at any time.
- **Not in v0:** wake word, presence detection, camera, face recognition, wings, other sensors, any connection to other systems.

## 3. Inputs and outputs

- **In:** microphone (used only after the trigger), button.
- **Out:** speaker, display eyes, head movement (one axis).

## 4. Where the thinking runs

Both. Quick reflexes (head, eyes, the safety stop) run on the owl. Speech and heavier work run on a home computer over home wireless. No fully offline mode is required.

## 5. Power and body

- A mains adapter supplies low voltage. The owl itself never carries mains voltage.
- *Proposal:* the movement motor gets its own supply rail, separate from the logic, so a stalled motor cannot reset the controller.
- Open frame first, shell later.

## 6. Safety rules (every design must meet)

Chosen: slow, low-force motion plus a visible switch that cuts all motion; designed for children and pets nearby.
- The switch is wired in hardware and works even if the software has crashed.
- Motion is slow and weak enough that a person can stop it by hand without injury.
- No pinch points across the full travel; no small detachable parts; nothing that gets hot.
- No unexpected movement when power is applied or restored.
- These are design rules, not a safety certification. Check local requirements before the owl is used around children.

## 7. Privacy rules

Chosen: listens only after a trigger (button only in v0, see section 11); nothing recorded or kept; only the owner can use or reconfigure it.
- v0 has no camera and no wake word. The microphone is read only after the button is pressed.
- Audio is not stored. Audio leaves the owl only after a trigger, only to the home computer, and only to be handled and discarded.
- *Proposal:* an indicator light shows when the microphone is open, and a physical mute switch exists.
- Settings and updates are reachable only by the owner.

## 8. Budget and buying

Band: **modest** (exact ceiling kept private). The brief is approved, but **nothing has been bought**. *Proposal:* buy only the bench-test parts, each approved individually.

## 9. Candidate architectures

| | A. Thin owl, home-computer brain | B. Self-contained owl computer |
|---|---|---|
| **Owl hardware class** | Microcontroller board with wireless, microphone, speaker amplifier, small display, one hobby servo | Small Linux single-board computer with audio, display and a servo driver |
| **Thinking** | Reflexes on the owl; speech and AI on the home computer | On the owl, optionally the home computer for heavy work |
| **For** | Low power, fast start, real-time control and a hardware safety stop come easily; matches the suggested split | Easier for someone comfortable with software; richer audio; simple behaviors work without the home computer |
| **Against** | Needs the home computer on; audio over wireless adds delay; on-device audio capability is *unverified*; more hardware learning | More power and heat; slower start; memory-card wear; more to keep updated and secure; motion timing needs a hardware safety stop anyway |

Either way, the motion-cut switch stays in hardware. A variant combines B with a tiny microcontroller that only drives the servo. *Proposal:* choose between A and B after bench test 1, because that test is the same for both.

## 10. First bench test (architecture-neutral)

Setup: one hobby servo on its own supply, a head-sized dummy weight, a visible kill switch that cuts servo power, one button. No microphone, speaker or display yet.

Pass criteria (all *proposals*; if any fails, stop, record it and redesign before adding parts):
1. A slow sweep of the full planned range for 10 minutes without stalling or jitter, and nothing too hot to hold afterwards.
2. The kill switch stops motion within 1 second in 10 of 10 trials, at different points in the sweep.
3. No jerk when power is applied or restored, in 10 of 10 trials.
4. The owner can stop the head by hand without pain, and inspection finds no pinch point.
5. A button press gives one slow turn and a return, in 20 of 20 trials.

Bench test 2, once test 1 passes: add the speaker and display eyes. A button press gives a turn, eye reaction and hoot, at a comfortable volume at desk distance.

## 11. Decisions on the conflicts in the suggested answers (decided by the owner)

1. **Presence: trigger only.** Q1, Q2 and Q25 wanted the owl to notice a person, but Q7 (no camera) and Q10 (no sensors) gave it no way to. Decision: v0 reacts to the trigger only, with no presence sensing. The success test for Q25 becomes: a button press gives a safe head turn, an eye reaction and a sound. A presence sensor or a camera would be a later decision and would change Q10 or Q7 and the privacy rules.
2. **Trigger: button only.** A wake word would mean sampling the microphone continuously to detect it, which is not "mic only after the trigger". Decision: no wake word in v0, so the microphone is not read until the button is pressed. A wake word can be reconsidered after bench test 2.

## 12. Decide, buy, test

- **Decided:** the presence approach and the v0 trigger (section 11); the brief itself, including the modest budget band with the exact figure kept private.
- **Still to decide:** architecture A or B, after bench test 1.
- **Buy:** nothing yet. Each purchase still needs the owner's separate OK. The bench test 1 parts would be: one hobby servo, a separate low-voltage supply, a physical switch, a button, a small controller board and wiring.
- **Test:** bench tests 1 and 2.

## Appendix: answers used

Suggested answers, with two changes by the owner (3 and 25): 1a companion that reacts to people; 2a notices and turns its head; **3 button only, no wake word (decided; was 3a)**; 4a desk-sized; 5a stylised and friendly; 6a microphone and speaker; 7a no camera in the first prototype; 8a head turn only; 9a animated display eyes; 10a no other sensors; 11a reflexes on the owl, heavier work on a home computer; 12a home wireless only; 13a standalone; 14a mains adapter; 15a open frame first; 16a slow, low-force motion plus a visible cut-off switch; 17a designed for children and pets nearby; 18a listens only after a trigger (button only in v0); 19a nothing recorded or kept; 20a only the owner; **21b modest budget**; 22a nothing bought before the brief is approved; 23a a few hours a week, comfortable with software, learning hardware; 24b hand tools and a few electronics boards; **25 success is a safe head turn, eye reaction and sound when the button is pressed (decided; was 25a)**.
