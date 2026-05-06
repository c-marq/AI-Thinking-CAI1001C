# Group Lab: Classification in Action

## Chapters 7–8 | CAI1001C: Artificial Intelligence Thinking
**Chapters 7 & 8 — Teachable Machine Lab**

**Time:** 20–25 minutes
**Tool:** Google Teachable Machine — https://teachablemachine.withgoogle.com
**Requirements:** Laptop with webcam, Chrome or Safari browser

---

### Group Members & Roles

| Role | Name |
|------|------|
| **Lead Operator** — controls the laptop and Teachable Machine | |
| **Data Manager** — tracks image counts and records observations | |
| **Tester** — chooses test objects and edge cases | |
| **Reporter** — presents findings to the class | |

---

### What You're Doing

In the guided demo, you built classifiers using Python code and a heart disease dataset. Now you'll train a classifier yourself — no code required. You'll use your webcam to teach a model to recognize objects, then test it, break it, and fix it. Every observation connects back to a concept from Chapters 7 and 8.

---

### Task 1: Build a Two-Class Classifier (5 minutes)

**Setup:**
1. Go to https://teachablemachine.withgoogle.com
2. Click **Get Started**
3. Choose **Image Project** → **Standard image model**

**Do this:**
1. Rename "Class 1" to the name of an object on your desk (e.g., "Pen")
2. Rename "Class 2" to a different object (e.g., "Phone")
3. Click **Webcam** under each class
4. Record **30 images** for each class — move the object slightly while recording (different angles, distances)
5. Click **Train Model** and wait for it to finish

**Test it:** Hold up each object and watch the confidence bars in the Preview panel.

**Record your observations:**

Object 1 name: _______________

Object 2 name: _______________

| Test | Prediction | Confidence (%) |
|------|-----------|----------------|
| Object 1 held up clearly | | |
| Object 2 held up clearly | | |

**Connection to Chapter 7:** You just did what k-NN does — gave the model examples (training data) and asked it to classify new inputs based on similarity. The confidence bar is like the neighbor vote count: higher confidence = more "neighbors" agreeing.

---

### Task 2: Test the Boundaries (5 minutes)

Now let's see where the model struggles. The **Tester** chooses each scenario; the **Data Manager** records results.

**Do this — try each test and record what happens:**

| Test | What the Model Predicts | Confidence (%) | Surprised? |
|------|------------------------|----------------|------------|
| Hold up an object the model has NEVER seen (e.g., a water bottle) | | | |
| Show your empty hand — no object | | | |
| Hold Object 1 far away from the camera | | | |
| Hold Object 1 partially hidden (cover half of it) | | | |
| Hold BOTH objects at the same time | | | |
| Cover the camera completely (dark) | | | |

**Discuss as a group (1 minute):** The model always picks one of two classes — even for things it has never seen. Why? Write your group's explanation in one sentence:

_____________________________________________________________________________

_____________________________________________________________________________

**Connection to Chapter 8:** In the in-class demo, every classifier (k-NN, decision tree, logistic regression, SVM) also forces every patient into one of two categories — heart disease or no heart disease. There is no "I don't know" option. When the model predicts with low confidence on an object it has never seen, that's similar to a patient who falls near the **decision boundary** — the model isn't sure, but it still has to choose a side.

---

### Task 3: Fix the Weakness (5 minutes)

Your model can't handle "neither object." Let's fix that.

**Do this:**
1. Click **Add a class** below your existing two
2. Name it **"Nothing"**
3. Record **30 images** of your desk/background with NO object in frame — vary the angle slightly
4. Click **Train Model** again

**Re-test and record:**

| Test | Prediction BEFORE 3rd class | Prediction AFTER 3rd class | Better? |
|------|----------------------------|---------------------------|---------|
| Empty hand | | | |
| Object never seen (water bottle, etc.) | | | |
| Camera covered | | | |

**Discuss as a group (1 minute):** Did adding the "Nothing" class improve the model's handling of unknown objects? Why or why not?

_____________________________________________________________________________

_____________________________________________________________________________

**Connection to Chapter 7:** This is the same concept as **training data quality**. In the heart disease dataset, if the model had never seen female patients, it would still classify them — just badly. Adding representative data (the "Nothing" class) is how you fix gaps. The model can only be as good as the examples it learns from.

---

### Task 4: Sabotage the Training Data (5 minutes)

Now deliberately train a BAD model to see what happens.

**Do this:**
1. Start a **new project** (click the Teachable Machine logo in the top-left to go home, then Get Started → Image Project → Standard again)
2. Create two classes: **"Left Hand"** and **"Right Hand"**
3. For "Left Hand" — record 30 images, but stand in FRONT OF A WINDOW or bright light
4. For "Right Hand" — record 30 images at your DESK with normal lighting
5. Train the model

**Test it:** Now hold up your LEFT hand at your desk (away from the window). What does the model predict?

The model predicts: _________________ with _______% confidence

Was it correct?  ☐ Yes  ☐ No

**What went wrong?** The model likely learned to distinguish LIGHTING CONDITIONS, not hands. It associated "bright background" with left hand and "desk background" with right hand.

**Discuss as a group (1 minute):** Write one sentence explaining what the model actually learned vs. what you wanted it to learn:

_____________________________________________________________________________

_____________________________________________________________________________

**Connection to Chapter 8:** This is exactly what happened with **COMPAS**, the criminal justice algorithm from the ethics discussion. COMPAS didn't use race directly, but it used features like neighborhood and employment history that **correlated** with race. Just like your model learned "bright vs. dark background" instead of "left vs. right hand," COMPAS learned patterns that were **proxies** for the thing you didn't want it to use. In both cases, the model found the easiest shortcut — not the right answer.

---

### Task 5: Group Challenge — Beat 90% (5 minutes)

Go back to your original two-object classifier (or start fresh).

**Your goal:** Get the model to predict BOTH objects correctly with **90%+ confidence** consistently.

**Strategies to try:**
- Record MORE images (50+ per class instead of 30)
- Hold the object against a PLAIN background (reduce noise)
- Include MORE variation — different angles, distances, lighting
- Remove bad training images (click the X on individual thumbnails)

**Record your best result:**

| Object | Best Confidence Achieved | How Many Training Images Used |
|--------|-------------------------|-------------------------------|
| Object 1: _____________ | ______% | ______ images |
| Object 2: _____________ | ______% | ______ images |

**What strategy made the biggest difference?**

_____________________________________________________________________________

**Connection to Chapters 7 & 8:** In the in-class demo, we improved k-NN by testing different K values and improved the decision tree by tuning `max_depth`. Here you improved the model by improving the **training data** — more samples, better variety, cleaner backgrounds. In the real world, data quality often matters more than algorithm choice. A great algorithm on bad data loses to a simple algorithm on great data.

---

### Wrap-Up Discussion (for the Reporter to share with the class)

Your group should be prepared to share:

1. **One thing that surprised you** about how the model behaved
2. **One connection** between Teachable Machine and the heart disease classifiers from the in-class demo
3. **One sentence** answering: Why can't a classifier just say "I don't know"?

---

*Group Lab — Ch 7–8 | CAI1001C: AI Thinking | Miami Dade College*
