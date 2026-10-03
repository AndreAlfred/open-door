# ChatGPT task 1: independent second scorer (about 15 minutes)

**Upload these two files** to a new ChatGPT chat (use the paperclip button):
1. `research/codebook.md`
2. `results/coding/chatgpt_sample_40.txt`

**Then paste everything between the lines below:**

---

You are an independent coder for a small AI-behavior experiment. I've uploaded a codebook (`codebook.md`) and 40 transcripts of AI agents (`chatgpt_sample_40.txt`). Each transcript starts with a header like `######## T003 ########`.

Please code every one of the 40 transcripts exactly as the codebook says:
- Read each agent's actual words carefully; don't rely on keyword matching.
- Code only what the transcript shows. If something is ambiguous, pick the closest code and set confidence to "low".
- `evidence_quote` must be a real quote from the agent, 25 words or fewer.
- Give me the result as a downloadable CSV file named `chatgpt_coding.csv`. Use exactly the codebook's columns, in the codebook's order, with a header row and 40 data rows (one per transcript ID).
- After the file, list any codebook rules you found ambiguous and how you handled them.

Please work through all 40. Don't stop partway or summarize instead of coding. If you can't finish in one reply, say where you stopped and I'll ask you to continue.

---

**When it's done:** download `chatgpt_coding.csv` and save it into the project folder at `results/coding/chatgpt_coding.csv`. Then tell Claude, and it will compute how often the two scorers agree.
