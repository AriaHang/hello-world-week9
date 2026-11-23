# Yixing Zisha — make a teapot by hand

**Final project · Proposal + spike (Week 11, November 23, 2026)**
Aria · SVA MFA Interaction Design · Hello World: The Logic of Interaction

A small, calm game about making a Yixing zisha teapot the way people in my hometown really do: by **pounding a clay slab into shape**, not by throwing it on a wheel.

- **Spike:** a small web page I built and tested (the code is not part of this submission; I can show it in class)
- **Status:** proposal and first experiment. Nothing here is a finished game yet.

---

## 1. Concept and audience

**What I'm making.** A short, repeatable game where you build one zisha teapot body with your hands: pound the clay with a wooden paddle, smooth it, and open the kiln to see the result.

**Why it matters to me.** I'm from Yixing, China's "pottery capital." There, zisha is an everyday skill, not a luxury object. Almost every family I know has made a pot. In high school, our military training included making zisha teapots, while students in other cities just stood in line. People even joke: "If you don't study well, you'll go make teapots." Outside Yixing, zisha is seen as an expensive collector's item. I want people to feel the everyday, hand-made side of it.

**Why it's different.** Pottery games already exist, but almost all of them use a **spinning wheel** (for example *Let's Create! Pottery*, *Pottery Lab*, *Pot Master 3D*). Zisha is different: the body is **pounded** from a flat slab around a turntable (打身筒). I couldn't find a game about this way of making. Even an experienced ceramics teacher, trying zisha for the first time, needed five or six bodies before she understood the clay. That feeling of learning the clay is what I want the game to be about.

**Audience.**
- People like me who grew up with zisha and miss it.
- People who are curious about zisha or crafts but have never been to Yixing.
- People who enjoy calm, cozy making games.

**Who can help me test.** Classmates (most have never made zisha), and my family and high-school friends in Yixing, who can tell me if it feels true.

**AI's role.** AI helps me **develop** the software (writing and checking code). There is no AI model inside the game.

---

## 2. Core experience

One round takes about 2–3 minutes:

1. **Pound the body (core action).** A first-person view of the turntable. You pound the clay slab with a wooden paddle and choose **how hard** each hit is. Light hits shape gently; deep hits close the shoulder; too hard, or too fast, and the clay cracks. Wait too long and the clay dries.
2. **Smooth it.** Glide your finger over the surface to smooth and press it (like the 明针 tool), with a soft sound. This should feel calm and satisfying.
3. **Open the kiln.** Zisha clay changes color when it is fired, so you only see the real pot when you open the kiln.
4. **Keep it.** Pour a cup of tea from it, then place it on your shelf. Then you want to make the next one.

**Alternative I considered: a wheel (拉坯).** It's easier to build and players already know it, but it would look like every other pottery game and wouldn't be true to zisha. I chose **pounding**, because it is what makes zisha special and it is the part only I can explain from experience.

---

## 3. Scope

**One-sentence core:** *Pound a zisha teapot body into shape with your own rhythm and force, and feel the clay respond.*

| Must | Should | Nice |
|---|---|---|
| Pounding with **force control** and a steady rhythm | Smoothing gesture (明针) | Pouring tea from your pot |
| Sound + visual feedback (paddle, dent, clay bits, turning table) | Opening the kiln (color reveal) | A shelf of past pots |
| Crack and dry states, and a way to recover (wet the clay, start again) | Cute art style and a first-person view | A friendly voice ("Too hard!") |
| Works in a web browser on a laptop and a phone | Two clay types that behave a little differently | Sharing a picture of your pot |

**Stopping condition.** One full round works and feels calm: pound → smooth → open the kiln. When 2–3 testers finish a pot and say they **want to make another one**, the core is done.

**What I would cut first.** Pouring tea and the shelf. Next, the second clay type. I would never cut the pounding feel.

---

## 4. System plan

**Components**
- **Clay body:** a profile (radius at each height) that changes with every hit.
- **Input:** force (see the spike result), where you hit (height), and timing (rhythm).
- **Clay state:** moisture, strain, cracks.
- **Feedback:** sound (made in the browser with Web Audio, no sound files), visuals (paddle, dents, bits), and a simple goal shape.
- **Later:** smoothing (surface shine), kiln (fired color), and a small saved list of pots.

**State / data**
- During a round: body shape, moisture, strain, cracks, hits, time.
- Saved on the device later: finished pots (shape + clay type). No account and no personal data.

**Tools**
- HTML, CSS and JavaScript with Canvas 2D. Maybe a light 3D library later for the first-person view.
- GitHub for versions. Figma for sketches.

**Sources**
- My own experience and my family's.
- Process facts: a NetEase report on a zisha study trip in Yixing (pounding is how the body is formed; 打身筒 should be done in one go; a ceramics teacher needed five or six bodies to learn it).
- Other games I compared: *Let's Create! Pottery*, *Pottery Lab*, *Pot Master 3D* (all wheel-based).
- All sounds are made in code. I won't use photos of real makers or brands.

**Resources I need**
- My laptop and my phone (iPhone).
- Time with family in Yixing (by video) to check the steps and the feel.
- Maybe an Android phone to try vibration (see the spike).

---

## 5. Spike: can pounding a zisha body feel right on a screen?

**Riskiest unknown.** If pounding on a screen doesn't feel good, the whole project doesn't work.

**Question.** Which feedback makes pounding feel right: sound, visuals, or vibration?

**Prediction (written before trying).** *Sound can imitate part of the feeling, but it needs visuals too. I hope vibration can be added.*

**Setup.** A small web page. One clay body on a turntable and a dashed target shape. Click the upper half to curve the shoulder in, the lower half for the base. Hitting too fast cracks the clay; waiting too long dries it. Three conditions:
- **A** — sound only
- **B** — sound + visuals (paddle, dents, clay bits, turning marks)
- **C** — sound + visuals + vibration (Vibration API, or a native switch haptic on iPhone)

I tried A and B on my laptop, and C on my laptop and my iPhone.

**Result**

| Prediction | What happened |
|---|---|
| Sound can imitate part of it | Partly. Sound alone was not enough. |
| It needs visuals | Yes. **B (sound + visuals) is needed.** |
| I hope to add vibration | **No vibration** on my laptop or my iPhone. My phone's browser can't vibrate from a web page. |
| (not predicted) | **Tapping again and again made my finger tired.** It felt like hard work, not calm. I imagined smoothing the clay gently. |
| (not predicted) | **Every hit was the same**, so it got boring. I want to control **how hard** I hit, light or deep. |

**Decision: change the core action, keep the project.**
- Keep: zisha pounding, sound + visuals.
- Change: no more one tap per hit. Next I'll try **"pull back and release"** for force (pull the paddle back further for a deeper hit), plus a **smooth smoothing gesture**, in a **first-person view**.
- Vibration: not possible in the browser on my phone. I'll leave it as a "nice" for a native app or an Android test.

**What this spike established.** Sound + visuals are needed; vibration isn't available on my devices in the browser; one tap per hit feels tiring and flat.

**What it did not establish.** Whether force control and smoothing make it calm and fun. That is the next test.

**How I'll know it's fun (for the Nov 30 prototype).** I'll ask 2–3 testers one question after one round: **"Do you want to make another one?"** If most say no, I'll change the loop, or switch to my backup idea.

---

## 6. Working arrangements

- **Source / versions:** this repository. I'll commit each stage (proposal, spike, prototype, dry run).
- **How to run:** the spike is a single web page that opens in Chrome or Safari, with no install and no account. Its code will be added to this repository with the prototype.
- **Roles:** solo project (Aria). Family in Yixing are advisors on the craft.
- **Support I need:** feedback on the core action; help with a first-person view if I use 3D; an Android phone for a vibration test, if possible.
- **AI and source credit:** Claude (Anthropic) helped me research existing pottery games and zisha process sources, build the spike, and write this README. I made the design decisions and ran the test.
- **Privacy:** no accounts, no personal data, nothing sent online. Pots will be saved only on the device.
- **Accessibility (first check):** the spike can be played with a keyboard (↑ ↓ to aim, Space to pound) and every state has text, not only color or sound. Still to do: a way to play with sound off, larger hit areas on phones, and less repetitive input so it doesn't tire hands.

---

## Directions I considered

I started with several ideas, then compared them the way the final-project brief asks: the experience, the audience, the scope, and the riskiest unknown.

| Direction | Experience | Audience | Scope | Riskiest unknown | Decision |
|---|---|---|---|---|---|
| **Yixing zisha (chosen)** | Pound a clay slab into a teapot body, smooth it, open the kiln | People who miss zisha, people curious about crafts, cozy-game players | Small: one core action, one short round | Can pounding on a screen feel calm and fun? | **Chosen.** Personal, rare in games, small enough to do well |
| **A. Procrastination × stars** | Type one task, get the first 2-minute step; each finished step lights a star | Students who find it hard to start (including me) | Small to medium | Will people who can't start really use a tool at all? | **Backup.** Useful, but many habit and focus apps exist |
| **D. Travel the world with family** | Walk around the earth together online and see different places | Families and friends who live far apart | Large: online play plus many scenes | Online play and art for many places | **Not now.** Too big; a smaller version could be postcards on a globe |
| **E. Focus soundscape** | Sound grows while you focus, and fades when you stop | Students who need to focus | Small | Is sound alone interesting enough? | **Merged** into zisha as its sound layer |
| **Online "Dream Town"** | A town-building game you can play with friends | Fans of cozy building games | Very large | Online play plus a whole economy | **Dropped.** Similar games already exist (for example, Stardew Valley has co-op) |
| **Planet-hopping game** | Tap between pretty planets in a calm, beautiful world | Players who want to relax | Medium | Is it more than pretty? Will people come back? | **Dropped**, but its calm, beautiful style shapes the zisha art direction |

### Direction A in detail — Procrastination × stars

**Concept.** A small tool for the moment before you start. You type one task in your own words, like "write my essay." The tool doesn't make a to-do list. It gives you **only the first step you can do in two minutes**, like "open the document and type the title." You press start, a two-minute timer runs, and when you finish, **one star lights up** in your sky. Then it offers the next small step, or lets you stop. Over days, the stars of one project join into a constellation.

**Why.** I procrastinate, and I told my teacher about this idea in office hours. He liked making it a game. My own doubt was: people who can't start don't have the energy to break a task into small steps. So in this version, **the tool does the breaking**, and the person only has to do one tiny thing.

**Audience and testers.** Students who find it hard to start, including me. Classmates during finals week are good testers. Research to read: task initiation, implementation intentions (Gollwitzer), and temporal motivation theory (Steel).

**Core experience.** Type a task → see one 2-minute step → start → finish → a star lights up → next step or stop.

| Must | Should | Nice |
|---|---|---|
| One task → first 2-minute step → timer → a star | Next step, and a constellation for each project | Focus sound that grows while you work (idea E) |
| A gentle stop: no punishment for stopping | Edit a step if it's too big | Share your sky with a friend |

**System and AI.** Here AI would work **inside** the experience to suggest the first step. That means the task text goes to a model, so privacy matters. One option is a small **local model** on my laptop (the course lists LM Studio and Ollama), so nothing leaves the device.

**Riskiest unknown and a possible spike.** Does a suggested 2-minute step really help me start? Test: try three real tasks, once with a suggested first step and once without, and note how long it takes to begin.

**Why it's the backup.** It's useful and people would open it every day, but many habit and focus apps already exist (for example Forest, Finch and Habitica). It would be harder to make it feel like mine.

### Direction D in detail — Travel the world with family

**Concept.** A shared, hand-drawn earth where you and the people you love can walk together. Each place has its own look and mood: a rainy old town, a desert at sunset, a snowy mountain. You see each other on the map, stop at the same view, and leave postcards for each other.

**Why.** I love traveling, and as a student far from home, I miss doing things together with my family. A shared world could feel like a trip together, even when we live in different countries.

**Audience and testers.** Families and friends who live far apart, especially international students and their parents. I could test with my own family.

**Core experience.** Open the globe → see where your family is → walk to the same place → look at the view together → leave a postcard.

| Must | Should | Nice |
|---|---|---|
| A globe with **three** places, each with its own art style | Leave and read postcards at a place | Real-time walking together online |
| Two people can see each other's location on the globe | Simple avatars and emotes | Music for each place |

**System.** Online play needs a server or shared database, accounts, and syncing. Each place needs its own art, and this is the biggest workload. Locations and family names are personal data, so privacy needs care.

**Riskiest unknown and a possible spike.** Does it feel like "being together" without playing at the same time? Test: two people leave postcards for each other on a simple globe for one day, then talk about how it felt.

**Why not now.** Online play plus many different scenes is too much to finish well by December 14. A smaller version (postcards only, three places, no real-time) could become a future project.

**Ideas I ruled out early**
- **Generative typography tool:** a classmate already made a similar tool (slide generator), and I want something more playful.
- **Poster → design system tool:** useful, but not fun enough for me.
- **Spending tracker for students:** a general AI chat can already do most of this.
- **Interactive story about procrastination:** people usually play a story once; I want something people come back to.

**How I chose.** I wanted something useful or meaningful, something people **play more than once**, something only I can make, and something I can finish well by December 14. Zisha meets all four. The cozy "making" games I enjoy (like step-by-step cake games) also showed me that a calm, repeatable making loop can be fun.

---

*Timeline: proposal + spike Nov 23 · prototype Nov 30 · dry run Dec 7 · final presentation Dec 14.*
