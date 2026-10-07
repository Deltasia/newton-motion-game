# กฎการเคลื่อนที่ของนิวตัน — prototype notes

Open `index.html` in any browser (sprites are embedded, no server needed).

## Characters

| In the game | Art | Role |
|---|---|---|
| ริวกะ | `assets/ryuka.jpg` | Rides the box; the one who never stops. |
| ยูอัน | `assets/Yu-An.jpg` | Explains the physics (was "พ่อมัน" in the storyboard). |
| เคย์ | `assets/Kay.jpg` | The player's side (was "????/ผัวริวกะ" in the storyboard). |

The embedded sprites are the drawings from `assets/` with the white paper cut out (so Ryuka can stand on the box and fly over the ice) and scaled down; the dialogue portraits are head-and-shoulders crops of the same drawings. `tools/embed_sprites.py` regenerates both and rewrites them inside `index.html` (adjust its `FACE_CROP` if a new drawing is framed differently).

## Story flow (follows storyboard 48–57)

| Storyboard | In the game |
|---|---|
| 48 ด่านที่ 1 | Ryuka asks you to push the box (กล่อง) into the green parking spot in front of the flag. Slider = push force (N), from −300 to 300 N, button = ผลัก/เล่น. Free-body diagram shows N, mg, F (labelled in Thai) and flips with the sign of F. |
| 49 | The push only lasts for the first 0.8 m (a short shove, well under a second at typical forces). Ryuka calls "แค่นี้น่าจะพอให้ไปจอดหน้าธงแล้ว หยุดผลักได้เลย" right after. |
| 50 | On ice (no friction) the box keeps going past the flag at constant speed ("บ๊ายบาย~"), disappears behind the panel, and the panic heart bar drains. Player can rewind and retry with a different force or go to the lesson. A negative push sends the box off to the left, also without stopping; ยูอัน explains that the sign is the direction, then rewinds so the player can push towards the flag. |
| 51–52 พาร์ทสอน | "เหมือนจะมีอะไรหายไป?" / "ช่วยกูก่อน" / ยูอัน names the misconception. |
| 53–54 | ΣF = sum of **external** forces; y-forces (N, mg) cancel. |
| 55 | **Corrected**: shows ΣF = F_push ≠ 0 *while pushing* (a = F/m), then ΣF = 0 after release. Uses the player's own force, not 123456 N. |
| 56 | **Corrected**: the question is now "ในเมื่อไม่มีใครผลักมันแล้ว ทำไมกล่องยังเคลื่อนที่ต่อไปได้ล่ะ!?" (no longer "where did the force go?"). Answer: motion doesn't need a force to keep going, and force isn't stored in the box → graphs of the player's own run (tabs for v–t, a–t and x–t), inertia, the 1st law, and why real carts stop (friction). Quiz. |
| *new* ด่านที่ 1 ลองใหม่ : มีแรงเสียดทาน | Same level, but the ice becomes a rough floor (μ = 0.10, f = μmg = 39.2 N). The player retries until the box slows down and parks in the green spot (answer = 196 N, range about 184–208 N). Pushing with \|F\| ≤ f doesn't move the box (static friction cancels the push, pointing right when the push points left). Hints after the 2nd and 3rd miss. |
| *new* พาร์ทสอน : แรงเสียดทาน | f = μN = μmg; ΣF in each phase (F − f, then −f, then 0 once stopped); v–t / a–t / x–t graphs of the player's own run; v² = u² + 2as used for both phases. Quiz on the direction of the net force while slowing down. |
| *new* ด่านที่ 1 ท้าทาย | Sandbox: the player sets push force F (−1000 to 1000 N), total mass m (20–80 kg) and μ (0–0.25) and tries again. Starts at m = 60 kg, μ = 0.15. After the first success, ยูอัน points out that the right push is always 5 × f, because the mass cancels. μ = 0 brings back the "never stops" ice behaviour. |
| 57 แถม | **Changed to projectile motion**: back on ice, a stopper halts the box, Ryuka keeps going (1st law) and flies off the ice platform. Slider = box speed (m/s); land on the cushion at the flag. Then a lesson on the 3rd law at the impact, x = vt / Δy = ½gt², and two quizzes. |

The title screen lists every chapter by a formal name (เลือกบทที่ต้องการ); each one plays on to the end.

## Panel, graphs and going back

- Every value in the panel has its Thai name next to the symbol (แรงลัพธ์ ΣFₓ, ความเร่ง a, ความเร็ว v, การกระจัด x, เวลา t; in the bonus เวลาลอย, ตำแหน่งแนวราบ, ระยะตก, ความเร็วแนวราบ/แนวดิ่ง). The faint info lines separate items with ";" (a "·" reads as multiplication next to symbols).
- The panel graph has v–t, a–t and x–t tabs (they stay clickable during a run). The t-axis sits at zero, so slowing down (a < 0) and moving left (v, x < 0) show below it.
- ◂ ย้อนกลับ (or ←, PageUp, mouse wheel up over the dialogue bar) steps back through earlier lines. Each line keeps a snapshot of the board, the title and the scene as they were when it was said; the live game is paused underneath until you step forward past the newest line (→, Enter, a click, or "กลับไปบทปัจจุบัน").

## Velocity and force arrows

Forces are thick arrows (red/amber for pushes and weight, purple for friction); velocity is a thin blue arrow (legend at the top-left of every scene). With friction, the blue velocity arrow keeps pointing forward while the net force points backward, so the box slows down. In section 1 the velocity arrow starts at the middle of the box; in the projectile bonus it starts at Ryuka's waist (0.38 m above her feet). There the slider updates the readouts and Ryuka's velocity arrow live before launch, before launch the readout shows the predicted values at touchdown, and once the box moves everything counts up in real time. x and the floor scale are measured from the platform edge (x = 0 where the flight starts, so the flag is at x = D = 3.0 m; x is negative while the box is still on the platform). t counts from the release of the box and changes with the slider; t_ลอย is the time in the air and stays at 0.62 s whatever the speed, like Δy and v_y; in flight the arrow splits into vₓ (constant) and v_y (growing), and the previous try stays on screen as faint dots for comparison.

## Misconceptions in the storyboard and how they were fixed

1. **Frame 55 showed ΣF = 0 while the box was being pushed (with "แรงผลัก = 123456").**
   While the hand is pushing, ΣF_x = F_push ≠ 0, so the box accelerates. ΣF becomes 0 only after the hand lets go. The 123456 N value (unrealistic for a hand push) is replaced by the player's own slider value.
2. **Frame 56 said the force "is still there as the cart's velocity" (แรงนั้น…ยังคงเป็นความเร็วของรถ), and asked "แรงนั้นหายไปไหนล่ะ".**
   Force is not stored in an object and does not turn into velocity. Force is an interaction that ends when contact ends. It *changed* the velocity (2nd law); with ΣF = 0 nothing changes it back (1st law, inertia). The question line was rewritten so it no longer suggests the force went somewhere.
3. **"ΣF = 0 means the object stops" (frame 52).** The storyboard sets this up as the misconception. The game states the correct version explicitly: ΣF = 0 means the velocity doesn't change.
4. **Missing context: why do everyday objects stop?** The new friction level answers it by play: on a rough floor the box slows down and stops because friction acts against the motion, not because the pushing ended.
5. **"Something moving forward must have a force pushing it forward."** The friction quiz targets this: while the box slides forward and slows down, the net force points backward.
6. **Bonus frame: Ryuka "launched" upward/tumbling.** In the projectile version Ryuka leaves horizontally (v_y = 0 at release), starts falling immediately (no cartoon "run then drop"), and only gravity acts during flight. The strobe dots show equal horizontal spacing and growing vertical spacing.
7. **3rd-law pair at the impact.** Shown as equal and opposite forces on *different* objects (box and stopper). This is why they don't cancel, and why the force from the stopper is what stops the box.

## Physics values used

- Level 1 (ice): m = 40 kg (box + Ryuka), push applied only over the first 0.8 m (in the direction of the push), v_release = √(2·(|F|/m)·0.8). μ = 0.
- Friction levels: kinetic friction f = μmg (g = 9.81 m/s²), always against the sliding. Push phase a₁ = (F − f)/m over 0.8 m; slide phase a₂ = −f/m until v = 0 (signs flip for a push to the left). The parking spot is 4.0 m from the start (3.2 m after the hand-off), so the exact answer is F = 5 f for any m and μ (196 N on the first friction floor, f = 39.24 N); success window ±0.25 m. Simplification: maximum static friction is taken to equal kinetic friction, so the box moves only when |F| > f. Very slow runs are sped up on screen (labelled "เร่งเวลา ×n"); the numbers are unchanged.
- Bonus: launch height h = 1.9 m (1.2 m platform + 0.7 m box), D = 3.0 m, t = √(2h/g) ≈ 0.62 s, target v ≈ 4.8 m/s (±0.25 m landing tolerance → about 4.4–5.2 m/s). Air resistance ignored; the top of the box is assumed slippery.
