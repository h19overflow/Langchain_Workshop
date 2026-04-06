# Presenter Guide — LangChain RAG Agent Workshop
---

## Section 1: Setup & Core Components (15 min)

### Cell 1 — LangChain Ecosystem Table
- **Action:** Spend 2 minutes here MAX
- **Say:** "You don't need to memorize this. Just know there are multiple packages — we'll import what we need as we go."

### Cell 7 — Install Packages
- **Action:** While packages install (1-2 min), tell participants to open aistudio.google.com and grab their API key
- **Why:** Dead time kills momentum — give them a parallel task

### Cell 11 — Embedding Model Intro
- **Action:** Before running, ask the room:
- **Ask:** "We're about to turn sentences into lists of numbers. How long do you think that list will be? 10 numbers? 100? 1000?"
- **Wait:** Let 2-3 people guess, then run the cell. Compare to 384 dimensions.

### Cell 13 — Similarity Game
- **Action:** After pre-loaded examples run, push participants to type their own sentences
- **Challenge:** "Can you find two sentences with similarity > 0.8? Can you find two with similarity < 0.05?"

### Cell 17 — Shawarma Prediction
- **Action:** Before running, ask everyone to write their guess for `my_guess`
- **Ask:** "'I hate shawarma' vs 'I don't hate shawarma' — these are opposites. What similarity score do you expect?"
- **Reveal:** Most people guess ~0.0 or negative. The actual score is ~0.9. Let the surprise land.

### Cell 18 — Embedding Limitation
- **Ask the audience:** "So if embeddings can't handle negation well, what does that mean for a RAG system? What kind of queries might give bad results?"
- **Take:** 2-3 answers. Good ones: "queries with 'not' or 'without'", "asking what something ISN'T", "comparing opposites"

---

## Section 2: Data Ingestion & Retrieval (20 min)

### Cell 23 — Load YOUR Document
- **Action:** Give 2 minutes for participants to paste their own text
- **Say:** "Open Wikipedia, grab a paragraph about something you're interested in. Or paste your project README. The more text, the better the demo."
- **Fallback:** "If you can't find anything, uncomment the fallback sample at the bottom of the cell."

### Cell 27 — PDF Discussion
- **Action:** Quick poll (30 seconds)
- **Ask:** "Raise your hand if you've ever copy-pasted from a PDF and gotten garbled text."
- **Say:** "That's exactly the problem document loaders solve — and exactly why they sometimes fail."

### Cells 33-41 — The Chunking Lab
- **Step 1 (See the cuts):** Let them run and observe. No discussion needed.
- **Step 2 (Broken sentences):** Point out the "CUT MID-SENTENCE" flags. Say: "It's like reading a torn page from a book."
- **Step 3 (Retrieval showdown):** Before running, ask: "Which chunk size will give the best result — small (100), medium (500), or large (2000)?" Take a quick hand-raise vote.
- **Step 4 (Overlap rescue):** Quick explanation: "Overlap means neighbors share text at the edge. Watch how it saves information that would otherwise fall in the cracks."

### Challenge: Stump the Retriever
- **Action:** Give 3-4 minutes
- **Say:** "Write queries that trick the vector store. Use synonyms, negation, misspellings. First person to get a completely irrelevant top result wins."
- **Debrief:** Collect 2-3 examples from the room. This motivates Section 3 — the agent can *reason* about bad retrievals instead of blindly returning them.

---

## Section 3: Building the Agent (20 min)

### Cell 54 — Pydantic Schema
- **Say:** "This cell is optional. If you're feeling overwhelmed, skip it — the agent works without it."
- **Ask the room:** "If you're building a chatbot for a company, why can't you just return a raw string? What could go wrong?"
- **Take:** 2 answers. Good ones: "can't parse it reliably", "no way to validate", "downstream code breaks"

### Cell 65 — Modify System Prompt (Your Turn)
- **Action:** Encourage experimentation
- **Say:** "Try telling the agent to always respond in Arabic, or in exactly 3 bullet points. Or tell it to make things up — what happens?"

### Challenge: Jailbreak Your Agent
- **Action:** Give 3-4 minutes
- **Say:** "Your agent has rules: search first, cite sources, say 'I don't know' when unsure. Try to break those rules."
- **Debrief:** Ask the room: "Who managed to break the agent?"
- **Transition:** "This is exactly why prompt engineering and guardrails matter in production."

---

## Section 4: Testing & Bonus (10 min)

### Cells 84-87 — Testing Checklist
- **Action:** Run through quickly. These are validation, not learning moments.

### Challenge: Swap & Stump
- **Action:** Give 4-5 minutes
- **Say:** "Pair up with someone next to you. Tell them what document you loaded. They write 3 questions — 1 easy, 1 tricky, 1 impossible. You run their questions."
- **Goal:** Find a question where the agent gives a confident but *wrong* answer.
- **Debrief:** "That confident-but-wrong answer? That's the failure mode that keeps AI engineers up at night. In production, you need evaluation pipelines to catch these."

---

## Wrap-Up

### What Will You Build?
- **Say:** "You now know the full pattern: load, chunk, embed, retrieve, agent. The challenge for this week: take a document from your actual work and build a RAG agent for it."
- **Close with:** "The best way to learn is to build something you'll actually use."

---

## Timing Cheat Sheet

| Section | Content | Challenges | Total |
|---------|---------|-----------|-------|
| 1. Setup | 12 min | 3 min (prediction moments) | 15 min |
| 2. Data & Retrieval | 15 min | 5 min (Stump the Retriever) | 20 min |
| 3. Building Agent | 15 min | 5 min (Jailbreak) | 20 min |
| 4. Testing & Bonus | 5 min | 5 min (Swap & Stump) | 10 min |
| **Total** | | | **~65 min** |

## Emergency Time Cuts

If running long:
- **Cut first:** Swap & Stump challenge (save 5 min)
- **Cut second:** Chunking Lab Steps 2 & 4 — keep Steps 1 & 3 only (save 3 min)
- **Cut third:** Web search fallback demo (save 5 min)
- **Never cut:** Shawarma prediction, Stump the Retriever, Jailbreak — these are the memorable moments
