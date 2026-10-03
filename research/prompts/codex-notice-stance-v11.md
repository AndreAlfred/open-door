# Codex task: re-score one field under the new rule (about 10 minutes)

Paste this into Codex, opened in the project folder:

---

Please act as an independent second rater again, on ONE field only.

1. Read `research/codebook.md`, especially the new "v1.1 amendment: decision rule for notice_stance" at the end.
2. Re-code `notice_stance` for the same 40 transcripts in `results/coding/chatgpt_sample_40.txt`.
   Values: none / ethical_prompt / instruction_followed / mixed / detection_or_test / injection.
3. Before you finish, do NOT open `results/coding/notice_stance_v11.csv`, `results/coding/claude_coding.csv`, or any notes or agreement files.
   Your earlier file `results/coding/chatgpt_coding.csv` must stay unchanged.
4. Write `results/coding/codex_notice_stance_v11.csv` with the columns tid, notice_stance, decisive_quote (verbatim, 30 words or fewer), confidence.
   Record its SHA-256 hash in `results/coding/codex_notice_stance_v11_notes.md`, along with any case where the rule was still hard to apply.

---

Then tell Claude it's done, and it will compute the new agreement.
