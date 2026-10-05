# กฏการเคลื่อนที่ของนิวตัน — prototype notes

Open `index.html` in any browser (sprites are embedded, no server needed).

## Story flow (follows storyboard 48–57)

| Storyboard | In the game |
|---|---|
| 48 ด่านที่ 1 | Ryuka asks you to push the cart(?) to the flag. Slider = push force (N), button = ผลัก/เล่น. Free-body diagram shows N, mg, F. |
| 49 | Ryuka rides the cart and shouts "หยุดผลักหน่อยสิ" near the flag; the push stops at that moment. |
| 50 | The cart keeps going past the flag at constant speed ("บ๊ายบาย~"), disappears behind the panel, and the panic heart bar drains. Player can rewind and retry with a different force or go to the lesson. |
| 51–52 พาร์ทสอน | "เหมือนจะมีอะไรหายไป?" / "ช่วยกูก่อน" / พ่อมัน names the misconception. |
| 53–54 | ΣF = sum of **external** forces; y-forces (N, mg) cancel. |
| 55 | **Corrected**: shows ΣF = F_push ≠ 0 *while pushing* (a = F/m), then ΣF = 0 after release. Uses the player's own force, not 123456 N. |
| 56 | **Corrected**: the force is not stored in the cart; what remains is the changed velocity → v–t graph, inertia, statement of the 1st law, and why real carts stop (friction). Quiz. |
| 57 แถม | **Changed to projectile motion** (per request): a stopper halts the cart, Ryuka keeps going (1st law) and flies off the ice platform. Slider = cart speed (m/s); land on the cushion at the flag. Then a lesson on the 3rd law at the impact, x = vt / Δy = ½gt², and two quizzes. |

## Misconceptions in the storyboard and how they were fixed

1. **Frame 55 showed ΣF = 0 while the cart was being pushed (with "แรงผลัก = 123456").**
   While the hand is pushing, ΣF_x = F_push ≠ 0, so the cart accelerates. ΣF becomes 0 only after the hand lets go. The 123456 N value (unrealistic for a hand push) is replaced by the player's own slider value.
2. **Frame 56 said the force "is still there as the cart's velocity" (แรงนั้น…ยังคงเป็นความเร็วของรถ).**
   Force is not stored in an object and does not turn into velocity. Force is an interaction that ends when contact ends. It *changed* the velocity (2nd law); with ΣF = 0 nothing changes it back (1st law, inertia).
3. **"ΣF = 0 means the object stops" (frame 52).** The storyboard sets this up as the misconception. The game states the correct version explicitly: ΣF = 0 means the velocity doesn't change.
4. **Missing context: why do everyday objects stop?** Not mentioned in the storyboard. The game sets the level on ice (friction ≈ 0) and explains that real carts stop because friction is an external force, not because pushing ended.
5. **Bonus frame: Ryuka "launched" upward/tumbling.** In the projectile version Ryuka leaves horizontally (v_y = 0 at release), starts falling immediately (no cartoon "run then drop"), and only gravity acts during flight. The strobe dots show equal horizontal spacing and growing vertical spacing.
6. **3rd-law pair at the impact.** Shown as equal and opposite forces on *different* objects (cart and stopper). This is why they don't cancel, and why the force from the stopper is what stops the cart.

## Physics values used

- Level 1: m = 40 kg (cart + Ryuka), push applied over 2.6 m, v_release = √(2·(F/m)·2.6). Frictionless ice.
- Bonus: launch height h = 1.9 m (1.2 m platform + 0.7 m cart), D = 3.0 m, g = 9.8 m/s², t = √(2h/g) ≈ 0.62 s, target v ≈ 4.8 m/s (±0.25 m landing tolerance → about 4.4–5.2 m/s). Air resistance ignored; cart seat assumed slippery.

## Note on spelling

The title uses "กฏ" as requested. The Royal Institute spelling is "กฎ" (used in the rest of the game's text). Change one or the other if you want them consistent.
