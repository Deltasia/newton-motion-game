# กฏการเคลื่อนที่ของนิวตัน

A short interactive story game (in Thai) that teaches Newton's laws of motion and projectile motion. Ryuka's cart(?) won't stop on the ice. Push it, watch it overshoot, learn why, then launch Ryuka onto the cushion at the flag.

## Play

Open `index.html` in a browser. Everything is in that one file, including the sprites.

## What it covers

- **Level 1:** Newton's 1st law. Pushing on frictionless ice; ΣF = 0 means constant velocity, not "stop".
- **Lesson:** free-body diagram, ΣF = ma while pushing, v–t graph, inertia.
- **Friction:** retry on a rough floor (f = μmg) so the cart slows down and parks; a lesson on ΣF = F − f, then −f, and v² = u² + 2as; then a sandbox where you set the mass and μ yourself.
- **Bonus:** projectile motion. Set the cart's speed so Ryuka lands on the flag (x = vt, Δy = ½gt²), plus the 3rd-law force pair at the stopper.

See [NOTES.md](NOTES.md) for the storyboard mapping, the misconceptions that were corrected, the physics values used, and the list of student data the game records.

## Collecting student data (for the teacher)

Before playing, each student types their name and class (ห้อง). The game then records how far they got, how long they spent on each part, every try in the levels, their quiz answers, and a short feedback form at the end. These are sent to a Google Sheet that you own. Students don't see any of it. The game also remembers each student's place in that browser, so they can pick up where they left off (เล่นต่อ).

One-time setup (about 5 minutes):

1. Create a new Google Sheet, for example "Newton game – data".
2. In the sheet, open **Extensions → Apps Script**. Delete the sample code, paste in all of [`apps-script/Code.gs`](apps-script/Code.gs), and click **Save**.
3. Click **Deploy → New deployment**, choose type **Web app**, and set **Execute as: Me** and **Who has access: Anyone**. Click **Deploy** and allow access when Google asks.
4. Copy the **Web app URL**. It ends in `/exec`.
5. In `index.html`, find `const LOG_URL = '';` near the top of the main `<script>` and paste the URL between the quotes. Then share or host that `index.html` as usual.
6. To test, open the URL in a browser. It should say `Newton game collector is running`. Then play a level and check that rows appear in the sheet.

The tabs (Sessions, Sections, Attempts, Quiz, Choices, Feedback) are created automatically as data arrives. To get a single overview with one row per student, use the **Newton → สร้างสรุป (Build summary)** menu in the sheet. (Reload the sheet once after step 2 if the menu doesn't show up.) It rebuilds the **Summary** tab with minutes per part as a heat map, the part each student spent the most time on, first-try quiz score, misconceptions, tries per level, and their feedback.

Notes:

- If you change `Code.gs` later, use **Deploy → Manage deployments → Edit → Version: New version** so the URL stays the same.
- If a student is offline or the page closes, the data waits in the browser and is sent the next time the game opens. Rows that were already received are not added twice.
- While `LOG_URL` is empty, nothing is sent anywhere.
- The sheet will hold students' names. Tell students their play is recorded for the class, and keep the sheet private.
