# Acceptance criteria — TakeMeter

Five criteria that say what "working" means for this classifier, written in
unit 5 **before** anything was trained.

**All five are yours this time.** None are given. You've had two projects of
practice.

An acceptance criterion names a number. *"The model is accurate"* is an
opinion. *"Every label has an F1 of at least 0.60 on the held-out set"* is a
criterion.

Under each, write a sentence or two on **why that number**. A reason that says
something about your data or your taxonomy earns credit — *"I picked 0.60 F1
for `reaction` because it's my smallest label and I only have about 50
examples of it"*. A reason that could be attached to any project does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## Pick numbers you can defend

Not numbers that sound impressive. Three labels means a coin-flip guesser gets
about 33%, so a target of 0.40 is barely a target. Your number should sit
somewhere you'd honestly call useful.

**Cover at least three of these five areas.** They're here as prompts, not as a
form to fill in — a criterion that fits none of them is fine if it names a
number.

| Area | A question it could answer |
|---|---|
| Overall accuracy | How often does it need to be right to be worth using? |
| Per-label performance | Is one label allowed to be much worse than the others? |
| Balance | How lopsided can your label counts get before it's a problem? |
| Consistency | If someone else labelled the same posts, how often should you agree? |
| Confidence | Should a confident prediction be right more often than an unsure one? |

Two things worth knowing before you pick numbers, because both will affect
whether you hit them:

- **Your smallest label will have the jumpiest score.** If a label has 50
  examples, about 8 land in the test split. An F1 computed on 8 examples moves
  a lot between seeds. A target for that label should be looser than one for
  your biggest label, and saying so is a good reason.
- **Unit 6 tests across three seeds, and the target has to hold across all
  three.** A target of 0.65 against results of 0.71, 0.62, 0.68 is a **miss**.
  Pick with that in mind — it is stricter than it first sounds.

---

## 1. Overall accuracy is over 60%

<!-- Your criterion. It must name a number. -->



**Why this target:** 60% means that the AI is correct most of the time. However it is still a low number. I'm keeping in mind that the AI could get confused between the borderline options.



---

## 2. The cat love label has an F1 of 0.8

<!-- Your criterion. -->


**Why this target:** The cat love label should be the easiest to identify out of the other labels. Because of this, I am expecting a high F1.




---

## 3. One label shouldn't have a count over 150 out of 200. If it does then the model should stop.

<!-- Your criterion. -->



**Why this target:** This is to deal with lopsided labelling. Stopping the model before it gets to 150 should help when it comes to debugging.

> **Revised in Unit 6:** One label shouldn't have a count over 70% of the test data.

> **Why revised:** The test split can depend on a variety of factors. This makes it so this criteria can always be tested even if the split isn't 200.


---

## 4. The model should be able to consistently label a post the same thing in 2/3 tries.

<!-- Your criterion. -->

**Why this target:** This helps to show that the model is consistent and understands why a post has a certain label. If the model 

**Revised in Unit 6, split into two**

**4a.** The model should be able to consistently have the same overall accuracy, or be in a 10 point range in 2/3 tries. This means running the project 3 times and seeing what the results yield. 

**4b.** There should be no more than 10 points between each seed. If the model is consistent then each seed should yield similar results.

**Why Revised:**  Both of these criteria show consistency and they are testable and easier to understand.

---

## 5. If the AI model has a confidence score of over 90% then the answer should be correct.

<!-- Your criterion. -->



**Why this target:** If the AI has a high confidence score but labels the post incorrectly, that means it does not understand the meaning of the label. If the AI is confident then it should label the post correctly.



---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 6 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath, like this:

         ## 2. Every label performs acceptably

         The model performs well on all labels.

         **Why this target:** ...

         > **Revised in unit 6:** Every label has an F1 of at least 0.60 on
         > the held-out set.
         >
         > **Why revised:** "performs well" gave me nothing to check. I
         > couldn't produce a verdict from it at all.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "Overall accuracy of at least 0.65" → "at least 0.55", because
            0.65 turned out to be optimistic for 200 examples.

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.
     ───────────────────────────────────────────────────────────────────────── -->
