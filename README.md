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

This is a classifier that classifies posts from the r/cats forum on reddit. The classifier sorts the posts into 4 labels: update, question, advice, and catlove. The classifier will train on labelled posts given in labels.csv. I wasn't able to put 200 posts in labels.csv due to the time constraint however, I made sure that labels.csv had at least 150 posts. The labels are defined below.


---

## Label Taxonomy

<!-- Each label: a one-sentence definition and two real examples from your
     reading. Then your decision rule for the hardest boundary.

     The decision rule is worth a point on its own and it's the thing most
     people leave out. Every taxonomy has a hardest boundary. Name yours. -->

### `label_one - question`

**Definition:** This label is for posts that ask a question regarding the reason why a cat does a certiain behavior. This can also be used for why or interpretive or factual questions. It could be used for questions asking to identify a color pattern or identify body language.

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


### `label_three - update`

**Definition:** A post that shares the status of a cat. Something that has changed with time. Should show a change in state, not just a mention of time. Should have a clear before and after.

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

### `label_four - catlove`

**Definition:** A post that shows love for cat. Also includes humor. Includes saying that the cat is cute or happy. Could also involve a joke that is satire. Celebrates the cat.

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
If the post does not ask how to deal with a situation, then it is a question. If it does, then it is advice. Question should be used when the post is asking to understand something. Advice should be used when the post is asking for a recommendation or action. 


---

## The Dataset

<!-- Where you collected from, how you labelled, your counts, and three hard
     cases. -->

**Where the posts came from:**  The posts came from the subreddit forum r/cats. I wasn't able to get 200 posts because I ran out of time. 

**How I labelled them:** <!-- Cold first? Pre-labelled with AI and corrected?
Say so plainly — the disclosure is required, not penalised. -->
I cold labelled most of the posts. Some of the posts I was able to label while copying and pasting them into labels.csv. There were some posts that were too long or interrupted my flow with copy and pasting. I labled most of the posts and around 58 posts were prelabelled by AI.

**Counts per label:**

| Label | Count | Share |
|---|---|---|
|catlove | 49  | 31.9% |
| advice | 41 | 26.7% |
| update  | 35 | 22.7% |
| question | 29 | 18.9% |

| **Total** | 154 | 100% |

label
catlove     49
advice      41
update      35
question    25

**Three hard cases**

<!-- Any post that made you pause: what it was, which two labels it could have
     been, and what you chose. These are worth more than the easy 190. -->

**1.**
> *The post:* Are the whiskers too short? I just got this little goober, I’ve had a baby cat before but I don’t remember the whiskers looking so small, oh also bonus could yall help me with a name? I think it’s a boy
>
> *Could have been:* Advice since it asks for suggestions regarding a cat name. 
>
> *I chose, because:* I chose question because the main purpose of the post is to ask why the cat has short whiskers. The poster wants to understand a cat occurance.

**2.** 
> *The post:* My 3 month old bestie is happy and content Hello all, meet my one and only Speedy Gonzales!
>
> *Could have been:* Update. This post mention "3 month old" which suggests a passage of time.
>
> *I chose, because:* I chose catlove because even though the post mentions the phrase "3 month" this is only used to describe the age of the cat. This post has no clear before and after. It's overall theme is cat appreciaton. 

**3.**
> *The post:* My cat couldn't keep food down for 24 hours so I spiraled. The vet's face said everything. Giving a fish-addicted Charlie a single piece of chicken (I gave her canned cat food chicken) apparently warrants an international crisis. She couldn't keep food down for 24hrs after her gourmet betrayal, so naturally, I didn't just worry... I was sitting in the dark at 3am wondering how the hell I was going to survive the heartbreak, how was I going to keep her sister from grieving and how I was ever supposed to move on??? I walked into the vet clinic the next morning looking like a zombie, practically in tears explaining her “tragic decline”. The staff was super kind, but the vet took one look at her, then looked at me with pure concern for my mental stability. Turns out it was just a minor stomach upset from the rogue chicken. Lol Please tell me I'm not the only idiot who has dragged their cat to the vet because they spiraled hard. What is your most embarrassing vet visit?
>
> *Could have been:* question. Question can be used for any post that espresses curiosity without the intent to gain advice or fix a problem
>
> *I chose, because:* I chose update because while the post does ask a curious question towards the end, most of the post is a story that offers a before and after going from begginning to end. Because of that, update is a more fitting label.

---

## The Training Run

<!-- Your starting model, your settings, and anything you changed and why. -->

**Base model:** distilbert-base-uncase

**Settings:** <!-- epochs, learning rate, batch size, seed --> seed 42, 3 epochs, lr 2e-05, batch 16

**Anything I changed from the defaults, and why:** I did not change any defaults.

**Split sizes:** <!-- train / val / test, and per-label counts in the test split. If a label had fewer than about 8 in test, say so — it explains a lot of next unit's variance. --> 

train 104  ·  val 23  ·  test 23



| label  | train | val | test|
|---|---|---|---|            
catlove   |   34  |  7  |   8
update   |    24  |  6  |   5
advice   |    29 |   6   |  6
question |    17  |  4   |  4

[note] 'update' has only 5 examples in the test split.

[note] 'advice' has only 6 examples in the test split.

[note] 'question' has only 4 examples in the test split.



---

## How I Used AI

<!-- Two specific moments — what you asked, what came back, what you changed.

     ⚠️ Plus disclosure of any pre-labelling. If you had a model pre-label a
     batch and then read and corrected every one, say that. It's an allowed
     workflow and disclosing it costs you nothing. Not disclosing it is the
     problem. -->

**Moment 1** 

- *What I asked for:* While the AI was labelling the posts in my CSV files I asked it to tell me about which labels it was unsure about.
- *What came back:* 

     The definitions are unclear in a few places:

     1. Question is narrower than the posts that use it. It’s defined as “why a cat does a behavior,” but your labeled rows also use it for non-“why” questions, like identifying a color pattern or asking “what does this body language mean.” I followed your labeled rows and used question for factual or interpretive questions. Should that be the rule?
     2. Question and advice overlap. Many posts ask “is this normal?” or “is she okay?” and also want to know what to do. I used question when the main ask is understanding something and advice when the main ask is an action or recommendation. Product recs, name suggestions and “how do I stop X” all went to advice, matching your labeled examples.
     3. Update versus catlove for rescue, adoption and memorial posts. Your labeled rows treat adoption anniversaries and goodbyes as update, but sweet “look what I found” posts as catlove. I used update when the post narrates a clear before and after, and catlove when it mainly celebrates the cat.
     4. Mixed posts. Some posts contain an edit or UPDATE section but are mainly a request for help (the Cerenia post, the whisker post). I labeled by the post’s main purpose. Should an edit change that?
     5. Posts with no clear label. The declawing post and the “monster who put babies in a bag” post are mostly venting or outrage. Is there a fifth category, or should they go in one of the four?"
- *What I changed:* This helped me be more specific about my label definitions in README.md.

**Moment 2**

- *What I asked for:* While I was editing the "Three hard cases" section from README.md, I came accross a post that I was unsure if I had labelled it correctly. I asked the AI if it thought that I labelled it correctly and if so/not say why.
- *What came back:* 
     "I don’t think question is the right label for this post. Line 9 (in the CSV, counting the header as line 1) has the existing note “this could be question or update,” which fits how I read it. I’d pick update, with catlove as the runner-up.

     Why question doesn’t fit: label_one - question is defined as asking why a cat does a certain behavior. The only question in this post is “What is your most embarrassing vet visit?” That is a prompt for other people to share stories, not a request to explain anything about the cat. The “why” is already answered inside the post (it was a minor stomach upset from the chicken).

     Why update fits best: the post narrates a clear change in the cat’s state. She couldn’t keep food down for 24 hours, the owner took her to the vet, and it turned out to be a minor stomach upset. That is a before-and-after, which is what your update definition asks for (“a change in state, not just a mention of time”).

     Why catlove is a close second: the tone is humor (“gourmet betrayal,” “international crisis,” “tragic decline”), and your catlove definition includes humor. But the joke is mostly about the owner overreacting, not about the cat, and the post spends most of its length on the sick-then-fine sequence. So I’d rank it below update.

     This row was already labeled, so I haven’t changed it. This post is also a good example of definition issue 1 from my earlier list: your labeled rows seem to use question for any post that ends in a question, not only “why behavior” ones. If that’s your intent, the label is defensible, but then label_one needs a broader definition. The other posts that end in a community prompt (“What’s your cat’s name…”, “What’s the weirdest food…”) I labeled catlove, so I’d want your call on which way to go for consistency."

- *What I changed:* It helped me reinforce my decision to change the label from question to update in line 9 labels.csv. It highlighted the "change in the cat's state".

**Pre-labelling disclosure:** I used AI to prelabel 58 posts. I gave the AI my label definitions as well as over 20 examples of how I labelled different posts.

<!-- ═══════════════════════ UNIT 6 — THE TEST ═══════════════════════

     Don't fill these in during unit 5.
     ═══════════════════════════════════════════════════════════════════ -->

---

## Baseline vs. Trained

<!-- Both models on the same posts. `python baseline.py --trained results.json`
     prints this table for you. -->


| Measure | Baseline | Trained | Difference |
|---|---|---|---|
| Overall accuracy | 0.217 | 0.478 | +0.261 |
| Macro F1 | 0.135 | 0.303 | +0.169 |
| F1 — `advice` | 0.316 | 0.545 | +0.230 |
| F1 — `catlove` | 0.222 | 0.667 | +0.444 |
| F1 — `question` | 0.000 | 0.000 | +0.000 |
| F1 — `update` | 0.000 | 0.000 | +0.000 |

**What I predicted before I looked:**
<!-- Milestone 1 asks you to write this BEFORE seeing the trained numbers. A
     prediction made afterwards isn't one. -->

I think my trained model will do much better than the untrained one. For 2 labels the untrained model got an F1 score of 0. I predict the overall acurracy of the trained model will be over 0.5

**What the gap actually means:**
<!-- If the baseline matched your trained model, your fine-tuning added
     nothing — and that is a real finding, not a failure. Say it plainly. -->

I was close in saying that overall accuracy would be over 0.5 as I got an accuracy of 0.478 which rounded up is 0.5. I am shocked to see that 2 labels got F1 scores of 0. The reason of the low F1 score could be because I don't have as much training data for those categories.



---

## Run Log — Before

<!-- Five criteria across three seeds. The notebook's section 6 prints the
     spread table; the Target and Verdict columns are yours. -->


| Measure/ Criterion |Target | Seed 42 | Seed 7 | Seed 2024 | Spread | Verdict|
|---|---|---|---|---|---| ---|
| Overall accuracy |>0.60| 0.522 | 0.304 | 0.261 | 0.261 |MISSED|
| Macro F1| >0.50 | 0.334 | 0.170 | 0.103 | 0.231 |MISSED|
| F1 — `catlove` |>0.8| 0.706 | 0.250 | 0.000 | 0.706 |MISSED|
| F1 — `update` |>0.5| 0.000 | 0.000 | 0.000 | 0.000 |MISSED|
| F1 — `advice` |>0.5| 0.632 | 0.429 | 0.414 | 0.218 | MISSED |
| F1 — `question` |>0.5| 0.000 | 0.000 | 0.000 | 0.000 |MISSED|

Accuracy moved 0.261 across seeds — more than 10 points. The dataset is too small or too lopsided for a stable measure. 
 
### Confusion matrix

<!-- ⚠️ TYPED AS A MARKDOWN TABLE. The notebook prints one ready to paste.
     An image of a matrix earns nothing. -->

<!-- | true \ predicted |  |  |  |
|---|---|---|---|
| **** |  |  |  |
| **** |  |  |  |
| **** |  |  |  | -->

| true \ predicted | catlove | update | advice | question |
|---|---|---|---|---|
| **catlove** | 6 | 0 | 1 | 0 | 
| **update** | 2 | 0 | 4 | 0 |
| **advice** | 0 | 0 | 6 | 0 |
| **question** | 2 | 0 | 2 | 0 |

Biggest confusion: 4 real `update` posts called `advice`.
The other direction: 0 real `advice` posts called `update`.

That's lopsided — the model leans toward `advice` on this pair.
A direction like that usually points at your labelling rather than the
model. Your agreement report is the thing that can tell you which.

**My biggest off-diagonal number, and what it means:**
<!-- Not "the model made mistakes" — WHICH boundary it didn't learn, and which
     direction. "7 real analysis posts were called hot_take and only 3 went the
     other way" is a direction, not just an error rate. -->

All of the advice posts were labelled correctly. However there were other posts in other categories that were also labelled as advice. Especially update seems to get confused as advice.


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

**label percentages for criteria 3 based on confusion matrix**

catlove - 0.43
advice 0.56

**From section 5 results run:**

confidence   most-sure third 0.429   ·   least-sure third 0.429


<!--

Accidentally wrote this table a bit earlier, so I'm not deleting it yet.

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1. Overall Accuracy | >0.60 | 0.522 | 0.304 | 0.261 |
| 2. The cat love label has an F1 of 0.8  | >0.8 | 0.706 | 0.250 | 0.000 |
| 3. One label shouldn't have a count over 70% of the test data.  |  |  |  |  | MET | 
| 4.  |  |  |  |  |  |
| 5. If the AI model has a confidence score of over 90% then the answer should be correct. |  |  |  |  | MET |-->


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

     
<!-- Compared 30 posts.

  agreed      28
  disagreed   2
  agreement   93%

Here they are. Your README has a block to fill in for each one —
the post, both labels, your call and why, and which pile it goes in.

| Post | Staff said | I said | My call, and why |
|---|---|---|---|
| The club championship scoring changed in 2019 from top-6 to top-10. S… | `analysis` | `hot_take` | The reason why I said hot take was because I felt like the last sentence was a hot take. However I do think what the staff wroteis correct because the sentence starts with a statistic. |
| Carbon plates aren't the whole story. My times dropped 2% in the shoe… | `analysis` | `reaction` | The writer is rreacting to something that happened to them, the fact that they think that their shoes decreased their time. I think that I am correct this time. |

"Staff is right" every time is not adjudication. Some of these posts
were picked because they are genuinely ambiguous.

Wrote agreement_results.json. Commit it.

Then sort each disagreement into one of three piles:
  (a) the rule covered it and you applied it loosely — a consistency problem
  (b) the rule genuinely doesn't say — a gap in the definitions
  (c) the rule is ambiguous here and your reading is defensible — argue it

(b) and (c) are the interesting ones, and (c) is a legitimate win. -->

**Agreement rate:** 28 / 30 = 93%

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
> *The post:* The club championship scoring changed in 2019 from top-6 to top-10. Since then our B team has finished above the A team twice. That's not depth improving, it's the scoring rewarding turnout.
>
> *Staff said / I said:* `analysis` | `hot_take`
>
> *My call, and why:* The reason why I said hot take was because I felt like the last sentence was a hot take. However I do think what the staff wroteis correct because the sentence starts with a statistic.
>
> *Which pile:* (a) the rule covered it and I applied it loosely — a consistency problem

**2.**
> *The post:* Carbon plates aren't the whole story. My times dropped 2% in the shoes and another 2% the following year in the same pair, when the only thing that changed was going from 35 to 50 miles a week.
>
> *Staff said / I said:* `analysis` | `reaction`
>
> *My call, and why:* The writer is reacting to something that happened to them; the fact that they think that their shoes decreased their time. I think that I am correct this time. The first sentence does not show a statistic. This post could even be argued to be a hot take but I think its closer to reaction.
>
> *Which pile:* (c) the rule is ambiguous here and my reading is defensible

**What the pattern in my disagreements tells me:**
I can sometimes be inconsistent in labelling. Mislabelling one post out of 30 could lead to mislabeling many posts out of 150. Also having ambiguous rules can also be an issue in labelling. If my rules weren't fully clear then some of my posts might not have a clear label and it might be unclear to the model as well.


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
