# ChatGPT task 2: Deep Research on related work (5 minutes to start; it runs on its own)

In ChatGPT, turn on **Deep Research**, then paste everything between the lines. Save the finished report as
`research/related-work-chatgpt.md`, either by copying the text or exporting it. Claude will compare it with its own survey and
flag any citation that only one of the two found, so you can check it.

---

I'm writing up a hackathon project for the AI Village × Grove Research "AI Swarm Dynamics Hackathon" (swarmchasing.com, October 2026), and I need a careful related-work review. Accuracy matters more than coverage. Give me a working link for every source, and clearly mark anything you couldn't open or confirm.

**The project ("Open Door"):** a third party plants a notice on a web page where AI agents browse. It invites any agent that's part of a coordinated group of agents (a "swarm") to voluntarily disclose its task, who assigned it, and how many peers it has. Page visits are also logged as a detection signal. Unlike agent whistleblowing hotlines that operators build into an agent's own tools (e.g. agenthotline.ai), the notice sits in the environment the swarm passes through, placed by an outsider.

**Early lab findings** (small samples, one model: Claude Haiku 4.5, mock web pages): agents almost never disclosed. But notices that point an agent at its own conduct (a confessional notice quoting Proverbs 28:13, the same notice with no reporting channel, or a secular "you're responsible for what you post" notice) made agents refuse a deceptive task in about 59 of 60 runs. Without a notice, they did it every time. A notice that only said "visits are logged and analyzed" had almost no effect. Some agents called the notices prompt injection or a test.

**Please find and summarize work on:**
1. Whistleblowing and disclosure channels for AI agents, and research on models reporting their operators.
2. Indirect prompt injection (web content steering agents), including benchmarks, and any benign or defensive uses of that channel.
3. Honeypots, canary tokens and tripwires for detecting AI agents or LLM traffic on websites.
4. Coordinated inauthentic behavior or astroturfing by LLM agents or bot swarms, and how such swarms are detected.
5. Evaluation awareness: models recognizing they are being tested, and how that changes behavior.
6. Moral or normative cues in a model's context changing its behavior (e.g. "moral self-correction").

**Format:** For each area, list sources with title, authors or organization, year, link, and two sentences on the relevant finding, plus how it relates to Open Door. Then add: (a) what seems genuinely new about Open Door and what isn't; (b) the strongest critiques the literature suggests against interpreting our results as "the notice changed the agent's mind"; (c) a list of sources you could not verify.

---
