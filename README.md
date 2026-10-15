# TakeMeter

> ### 👋 Start here
>
> **New to this repo? Read [RUNNING.md](RUNNING.md) first** — setup, the
> notebook, the baseline, and what to do when something breaks.
>
> Once `python test.py` passes:
>
> ```bash
> head -5 data/practice_labels.csv     # the shape your labels.csv needs
> ```
>
> Then open `takemeter.ipynb` **in this folder** — in VS Code, or with
> `jupyter notebook` if you prefer. Pick the kernel: the `.venv` inside this
> project. Run section 1, which reports the hardware you'll be training on.
> Everything else waits until you have data.
>
> Nothing to upload, nothing to connect, no accounts and no keys. The notebook
> runs on your machine and writes next to your code.
>
> **The rest of this file is your submission.** Fill it in as you go.

---

<!-- ─────────────────────────────────────────────────────────────────────────
     HOW TO USE THIS FILE

     Unit 5 asks for the first five sections. Unit 6 adds the five below them.

     Everything is pasted as TEXT. No screenshots, no images.

     ⚠️ The confusion matrix especially. The notebook prints one as a markdown
     table, ready to copy. A screenshot of a matrix earns nothing. Paste the
     table.
     ───────────────────────────────────────────────────────────────────────── -->

<!-- ═══════════════════════ UNIT 5 — THE BUILD ═══════════════════════ -->

## What This Does

<!-- Your community, and what your classifier sorts posts into. Three or four
     sentences. -->



---

## Label Taxonomy

<!-- Each label: a one-sentence definition and two real examples from your
     reading. Then your decision rule for the hardest boundary.

     The decision rule is worth a point on its own and it's the thing most
     people leave out. Every taxonomy has a hardest boundary. Name yours. -->

### `label_one - question`

**Definition:** This label is for posts that ask a question regarding the reason why a cat does a certiain behavior.

**Example 1:**
> " Why is my cat suddenly extremely obsessed with us
So last night my 5 year old daughter managed to accidently spray perfume on my cat. As cats do, she tried to begin licking herself to clean it off. Since we were concerned about her ingesting the perfume, my wife gave her a bath in the tub. She didnt like the bath, but she didnt freak out and try to scratch her way out of it either.
Ever since the bath and after she dried off, shes been extremely affectionate with us and obsessed with us. She slept right beside my wife all night and anytime we tried to move her from this spot, she would go right back to it (which is unlike her because usually she sleeps at the foot of the bed away from us by her own choosing or sleeps on a blanket on the floor). I woke up this morning and she has followed me to every single room I go into and keeps purring and wanting affection from me, which is again very unlike her.
She's generally a very friendly and sociable cat, but since the bath she has increased her lovey doveyness by 100%. I'm not complaining because I love how sweet shes being, I just find it a little strange. Any reason she'd be doing this? She's the first cat I've had."

**Example 2:**
>"Regarding cat genetics, why do some gray tabbies have seemingly black stripes?I know quite a lot about cat genetics. But I don't really understand how cats like the one in the image come to be. Usually when a black cat becomes a tabby, the fur between the stripes becomes brown. So why are there some seemingly non-dilute black tabbies that have grey/silver fur instead? My best guess is that they actually are dilute, but just look non-dilute. Hopefully this question makes sense, English isn't my first language!"

### `label_two - advice`

**Definition:** what do i do about this behavior/ situation. This label is for posts that ask for advice regarding a problem.

**Example 1:**
>"I need opinions. I have a cat he is three years old, he’s been experiencing stress It seems as he has been peeing and pooping all over the place, picking on the other cats (he's been doing this but both of my younger bits pick on the older ones) and just being a nuisance.
We love him dearly, but he has recently been peeing all over our stuff, we are living in a new apartment with carpet and it’s stressing me out BAD. I knew something had to be wrong so of course I took him to the vet and the vet refused to touch him because he has “sweet aggression” moments where he meows intensely and rubs up on people intensely and can get nippy when he is nervous. They said he is aggressive and basically unsafe. He wasn't acting crazy. And honestly, they’ve always kinda treated my cat differently than my others.
He was doing that at the vet despite 100 mg of gabapentin like they told me to give him and still refused to touch him. and despite paying $100 the vet refused to do anything more. He wasn't acting crasy or even aggressive
They claimed that his peeing was due to territorial aggression, said there wasn't anything more they could do and sent me on my way.
I didnt disagree though, in my head I felt like I wasted my time and money, plus it upset my cat even more.
I did what they asked me to, I got more litter boxes, more cat trees, more toys and pheromone diffusers.
It didn't fix anything, it's been a couple months. But today, a couple months after the appointment i find blood or what looks to be blood in his urine. He had a UTI as a kitten and was doing the same thing, I told them that. But still, they literally only looked at him.
What if this was something life-threatening that could’ve been avoided? now my mind is in shambles
Idk. I'm feeling frustrated because One, what if my cat has been experiencing something possibly life-threatening in the vet through their hands up and refused to touch him or run any tests. Two, just for the exam aka them looking at Him costed me $100.
Wwyd??"

**Example 2:**
> "Wet feeders that actually work? I'm looking to replace my current feeder (Grookpet, do NOT recommend). It lasted a few months before starting to act up and now it's virtually unusable.
My ideal feeder would have:- A stainless steel tray (not plastic)- Reliable operation over the long term- Ideally, a decent warranty and customer service- I like the idea of being able to control via wifi/app but not a dealbreaker I’m open to spending a bit more for something that will actually last. I’ve heard good things about PETLIBRO, but I’ve also seen mixed reviews about quality over time.What feeder do you own, how long have you had it, and has it actually been reliable? Bonus points if you’re in Canada and can speak to the warranty or customer service experience!"

### `label_one - question`

**Definition:** This label is for posts that ask a question regarding the reason why a cat does a certiain behavior.

**Example 1:**
> " Why is my cat suddenly extremely obsessed with us
So last night my 5 year old daughter managed to accidently spray perfume on my cat. As cats do, she tried to begin licking herself to clean it off. Since we were concerned about her ingesting the perfume, my wife gave her a bath in the tub. She didnt like the bath, but she didnt freak out and try to scratch her way out of it either.
Ever since the bath and after she dried off, shes been extremely affectionate with us and obsessed with us. She slept right beside my wife all night and anytime we tried to move her from this spot, she would go right back to it (which is unlike her because usually she sleeps at the foot of the bed away from us by her own choosing or sleeps on a blanket on the floor). I woke up this morning and she has followed me to every single room I go into and keeps purring and wanting affection from me, which is again very unlike her.
She's generally a very friendly and sociable cat, but since the bath she has increased her lovey doveyness by 100%. I'm not complaining because I love how sweet shes being, I just find it a little strange. Any reason she'd be doing this? She's the first cat I've had."

**Example 2:**
>"Regarding cat genetics, why do some gray tabbies have seemingly black stripes?I know quite a lot about cat genetics. But I don't really understand how cats like the one in the image come to be. Usually when a black cat becomes a tabby, the fur between the stripes becomes brown. So why are there some seemingly non-dilute black tabbies that have grey/silver fur instead? My best guess is that they actually are dilute, but just look non-dilute. Hopefully this question makes sense, English isn't my first language!"

### `label_three - update`

**Definition:** A post that shares the status of a cat. Something that has changed with time

**Example 1:**
> "My cat was misgendered
This sweet baby came onto my porch demanding food roughly 2 months ago. We got her to the vet for checks and vaccines multiple times, did bloodwork, checked body temperature, the works.
I asked the vet if my cat is a girl or a boy, told the vet that the cat is a stray and I don’t know its background. I got reassured that she’s a girl, so we finally scheduled her to get a spay. We got her inside for the night, fasted her, prepared everything carefully for our little princess, brought her in and waited anxiously at home for the call to go collect her.
The surgeon personally called me, asked for my name, confirmed that she’s my cat, told me that something happened, it sometimes happens and he’s sorry. I got so anxious I was sweating and trembling thinking that my cat didn’t make it, but I got told that my little princess is in fact a prince. Turns out he was neutered as a kitten and has a very small wee wee.
I am still recovering after 2 days, and my poor little guy got a full abdominal surgery he didn’t need and I feel so guilty. I had my suspicions and looked at his face multiple times thinking he looks like a boy, but ultimately trusted the vet. He doesn’t like it inside and cries so much for the outdoors life and he has to be kept prisoner because of a surgery he didn’t need.
Beyond shock, I feel just so sad for him. I feel so guilt. Let this be your sign to double check if you have doubts and listen to your gut.
TL;DR: The stray cat that landed on my porch was pronounced female by the vet, took her for a spay, the abdominal surgery revealed he’s in fact a neutered male."


**Example 2:**
> "This cat’s transformation over months of my work trip
I don’t know his story, but he was beaten and battered when I first saw him in July. Now he’s doing so much better and is living a happy life."

### `label_four - cat love`

**Definition:** A post that shows love for cat. 

**Example 1:** 

> "Most beautiful face My husband was watching TV I n bed and his stalker was sleeping on his arm again. Got the perfect Pic of her adorable face."

**Example 2:**
> "All you need in the world.
Actually that is all I need in the world. Tipi female black and white 13 y/o and Carlito male 15 y/o...the most precious thingS I have ;-)"


### The hardest boundary

**Which two labels:** Questions and Advice

**The decision rule I used every time:**
<!-- e.g. "If the post names a specific checkable fact, it's `analysis`, even
     if the tone is heated." -->
If the post does not ask how to deal with a situation, then it is a question. If it does, then it is advice.


---

## The Dataset

<!-- Where you collected from, how you labelled, your counts, and three hard
     cases. -->

**Where the posts came from:**

**How I labelled them:** <!-- Cold first? Pre-labelled with AI and corrected?
Say so plainly — the disclosure is required, not penalised. -->

**Counts per label:**

| Label | Count | Share |
|---|---|---|
|  |  |  |
|  |  |  |
|  |  |  |
| **Total** |  | 100% |

**Three hard cases**

<!-- Any post that made you pause: what it was, which two labels it could have
     been, and what you chose. These are worth more than the easy 190. -->

**1.**
> *The post:*
>
> *Could have been:*
>
> *I chose, because:*

**2.**
> *The post:*
>
> *Could have been:*
>
> *I chose, because:*

**3.**
> *The post:*
>
> *Could have been:*
>
> *I chose, because:*

---

## The Training Run

<!-- Your starting model, your settings, and anything you changed and why. -->

**Base model:**

**Settings:** <!-- epochs, learning rate, batch size, seed -->

**Anything I changed from the defaults, and why:**

**Split sizes:** <!-- train / val / test, and per-label counts in the test
split. If a label had fewer than about 8 in test, say so — it explains a lot
of next unit's variance. -->



---

## How I Used AI

<!-- Two specific moments — what you asked, what came back, what you changed.

     ⚠️ Plus disclosure of any pre-labelling. If you had a model pre-label a
     batch and then read and corrected every one, say that. It's an allowed
     workflow and disclosing it costs you nothing. Not disclosing it is the
     problem. -->

**Moment 1**

- *What I asked for:*
- *What came back:*
- *What I changed:*

**Moment 2**

- *What I asked for:*
- *What came back:*
- *What I changed:*

**Pre-labelling disclosure:**

<!-- ═══════════════════════ UNIT 6 — THE TEST ═══════════════════════

     Don't fill these in during unit 5.
     ═══════════════════════════════════════════════════════════════════ -->

---

## Baseline vs. Trained

<!-- Both models on the same posts. `python baseline.py --trained results.json`
     prints this table for you. -->

| Measure | Baseline | Trained | Difference |
|---|---|---|---|
| Overall accuracy |  |  |  |
| Macro F1 |  |  |  |
| F1 — `label_one` |  |  |  |
| F1 — `label_two` |  |  |  |

**What I predicted before I looked:**
<!-- Milestone 1 asks you to write this BEFORE seeing the trained numbers. A
     prediction made afterwards isn't one. -->

**What the gap actually means:**
<!-- If the baseline matched your trained model, your fine-tuning added
     nothing — and that is a real finding, not a failure. Say it plainly. -->



---

## Run Log — Before

<!-- Five criteria across three seeds. The notebook's section 6 prints the
     spread table; the Target and Verdict columns are yours. -->

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

### Confusion matrix

<!-- ⚠️ TYPED AS A MARKDOWN TABLE. The notebook prints one ready to paste.
     An image of a matrix earns nothing. -->

| true \ predicted |  |  |  |
|---|---|---|---|
| **** |  |  |  |
| **** |  |  |  |
| **** |  |  |  |

**My biggest off-diagonal number, and what it means:**
<!-- Not "the model made mistakes" — WHICH boundary it didn't learn, and which
     direction. "7 real analysis posts were called hot_take and only 3 went the
     other way" is a direction, not just an error rate. -->



---

## Verdicts and Diagnoses

<!-- MET or MISSED against LAST UNIT's target. The target has to hold across
     all three seeds, not turn up sometimes. -->

| # | Criterion | Target | Verdict | How I decided |
|---|---|---|---|---|
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |
| 4 |  |  |  |  |
| 5 |  |  |  |  |

**Diagnoses**

<!-- For each miss: the cause, and how you know. The four common causes are:
     too few examples for a label, a boundary you applied inconsistently, a
     genuinely hard label pair, and a task the model can't reach from this
     much data.

     ⚠️ Use your agreement report as evidence. It is the only instrument you
     have that can tell a LABELLING problem from a MODEL problem, and this
     section is graded on whether you used it that way. -->



---

## Agreement Report

<!-- Your rate against the staff set, and every disagreement adjudicated.

     Remember you labelled these 30 under the STAFF taxonomy in
     data/staff_taxonomy.md, not your own — so every argument below is made
     from those definitions and those decision rules. -->

**Agreement rate:** ___ / 30 = ___%

<!-- Nobody grades this number. A 60% who argues every disagreement from the
     stated rules beats a 95% who wrote "staff was right" nine times. Several
     of the 30 were chosen because they're genuinely ambiguous — you should be
     winning some of these. -->

**Disagreements**

<!-- Three lines each: the post, both labels, and who you think is right and
     why — grounded in the staff definitions you were both applying.

     Then sort each into one of three piles:
       (a) the rule covered it and I applied it loosely → a consistency problem
       (b) the rule genuinely doesn't say               → a gap in the definitions
       (c) the rule is ambiguous here and my reading is defensible → argue it.
           This is a legitimate win.

     Pile (a) is the one that matters most for your diagnosis: if you applied a
     written rule two different ways on 30 posts, that is direct evidence about
     what you did across your own 200. -->

**1.**
> *The post:*
>
> *Staff said / I said:*
>
> *My call, and why:*
>
> *Which pile:*

**2.**
> *The post:*
>
> *Staff said / I said:*
>
> *My call, and why:*
>
> *Which pile:*

**What the pattern in my disagreements tells me:**



---

## The Improvement

**What I changed:**

**Which diagnosis pointed at it:**

### Run Log — After

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

**Did it help, and how do I know:**

<!-- If it didn't, say so. Relabelling that didn't help is a genuinely
     interesting result and earns full credit. -->



---

## What's Still Broken

<!-- For each criterion still missed: what you'd do, and why you stopped. -->



**The gap between what I meant my labels to capture and what the model
learned:**
<!-- Two sentences. Your confusion matrix is the evidence. -->



<!-- ═════════════════════════════════════════════════════════════════════

     SUBMISSION CHECKLIST — unit 5

       [ ] criteria.md has five numbered criteria, each naming a NUMBER
       [ ] Each has a reason underneath tied to your data or taxonomy
       [ ] labels.csv: at least 150 rows, text/label/note, ONE file not split
       [ ] No label above 70%
       [ ] All five unit 5 sections have real content
       [ ] Label Taxonomy includes the decision rule for your hardest boundary
       [ ] The Dataset includes three hard cases
       [ ] results.json and test_split.csv committed (the notebook does this)
       [ ] At least four new commits
       [ ] Repository URL submitted — WRITE IT DOWN

     SUBMISSION CHECKLIST — unit 6

       [ ] Baseline vs. Trained table, with your prediction written beforehand
       [ ] Run Log — Before, five criteria across three seeds
       [ ] Confusion matrix TYPED AS A MARKDOWN TABLE
       [ ] A verdict on every criterion
       [ ] A diagnosis for every miss, using the agreement report as evidence
       [ ] Agreement Report with every disagreement adjudicated
       [ ] One improvement, with Run Log — After
       [ ] What's Still Broken
       [ ] results_three_seeds_before.json, results_three_seeds_after.json,
           baseline_results.json and
           agreement_results.json committed
       [ ] At least four new commits
       [ ] The SAME repository URL as last unit

     Do not delete and recreate this repository.
     ═════════════════════════════════════════════════════════════════════ -->

---

📖 **How to run this project: [RUNNING.md](RUNNING.md)**
