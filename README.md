# กฎการเคลื่อนที่ของนิวตัน

A short interactive story game (in Thai) that teaches Newton's laws of motion and projectile motion. Ryuka's box (กล่อง) won't stop on the ice. Push it, watch it overshoot, learn why, then launch Ryuka onto the cushion at the flag. The cast: ริวกะ (Ryuka), ยูอัน (Yu-An, who explains) and เคย์ (Kay).

## Play

Open `index.html` in a browser. Everything is in that one file, including the sprites (the source drawings are in `assets/`; after changing one, run `python3 tools/embed_sprites.py` to cut it out and embed it again).

Press ◂ ย้อนกลับ in the dialogue bar (or ←, or scroll up over it) to go back and reread earlier lines and lesson boards; → or a click goes forward again.

## What it covers

- **Level 1:** Newton's 1st law. Pushing on frictionless ice; ΣF = 0 means constant velocity, not "stop". The push can be negative (to the left).
- **Lesson:** free-body diagram, ΣF = ma while pushing, v–t / a–t / x–t graphs, inertia.
- **Friction:** retry on a rough floor (f = μmg) so the box slows down and parks; a lesson on ΣF = F − f, then −f, and v² = u² + 2as; then a sandbox where you set the mass and μ yourself.
- **Bonus:** projectile motion. Set the box's speed so Ryuka lands on the flag (x = vt, Δy = ½gt²), plus the 3rd-law force pair at the stopper.

See [NOTES.md](NOTES.md) for the storyboard mapping, the misconceptions that were corrected, and the physics values used.
