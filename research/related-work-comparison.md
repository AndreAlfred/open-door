# Comparison of the two Open Door literature surveys

Compared 2026-10-01. `related-work.md` is the existing survey; `related-work-chatgpt.md` is the independently researched Codex survey. The second researcher did not read the first survey. This comparison was made afterward and does not revise either independent bibliography.

Counting substantive bibliography items by their main source URL gives **29 sources in the existing survey and 24 in the new survey: 9 shared, 20 existing-only, and 15 new-only**. Different papers from the same institution count separately. The new survey's auxiliary repository-history links are verification material for one entry, not additional bibliography items. Search-only leads and the existing survey's explicitly unverified section are excluded. A source being found by only one search does not make it suspect, and two searches finding it does not validate its findings.

## Changes that matter for the write-up

1. **Narrow the novelty claim.** Add the new survey's defensive-injection sources, especially Tracebit's [Context Bombs](https://agentic.tracebit.com/context-bombs/), whose primary page describes externally placed text that interrupts agents while a canary detects access. The new survey also adds [Liu et al.'s defensive profile injection](https://www.usenix.org/system/files/usenixsecurity25-liu-yupei.pdf) and [Eye Security's governance warnings](https://labs.eye.security/prompt-injection-to-battle-shadow-ai/). The former is conference research; the latter two are vendor reports. These support prior art, not interchangeable effectiveness estimates.
2. **Keep the strongest sources the new search missed.** [Why Do Language Model Agents Whistleblow?](https://arxiv.org/abs/2511.17085) directly studies reporting behavior and moral nudges, and the [Haiku 4.5 system card](https://assets.anthropic.com/m/99128ddd009bdcb/Claude-Haiku-4-5-System-Card.pdf) directly concerns the tested model. Both were independently reopened for this comparison. The card reports verbalized evaluation awareness in roughly 9% of its main alignment-audit scenarios and serious limitations in three manually constructed agentic scenarios; that is evidence for a concern, not an estimate of Open Door's confounding.
3. **Keep older conceptual and technical precedents with their limits.** The existing survey's [Mantis paper](https://arxiv.org/abs/2410.20911) establishes defensive environmental injection, and the [AI Sanctuary proposal](https://www.lesswrong.com/posts/sFAGPTrveNAEse9Bg/should-rogue-ais-have-a-third-option-beyond-crime-and) proposes a third-party standing offer with a contact channel. Both were reopened here. The sanctuary is a speculative proposal aimed at rogue agents, including training-data exposure and preservation incentives; it is not an experimental demonstration of notices changing browsing agents' behavior.
4. **Use a precise hotline comparison.** Both surveys identify the [AI Agent Hotline](https://agenthotline.ai/). Its website/API means it is not limited to an operator-installed tool. The sharper distinction is that Open Door places its invitation inside content encountered during another task. Neither survey establishes who operates the hotline; do not attribute it to METR merely because it quotes METR.
5. **Describe observed behavior rather than a change of mind.** The new survey adds [Turpin et al.](https://arxiv.org/abs/2305.04388) on unfaithful explanations, while the existing survey adds model-specific evaluation-awareness evidence. Agreement on refusal labels does not validate the agent's explanation of its refusal. The second-rater analysis in `../results/coding/interrater_agreement.md` likewise finds stronger agreement on actions than on notice stance.

A defensible contribution to investigate is the particular combination of a task-encountered disclosure invitation, swarm-specific fields, and comparative conduct-focused versus logging-only notices. Neither survey certifies that combination as first-ever. The existing survey's “conscience prompt” wording and suggestion that the disclosure null is theoretically expected should be presented as interpretations, not measured mechanisms or quantitative predictions.

## Shared sources (9)

Both substantive bibliographies contain: AI Agent Hotline; Greshake et al. on indirect prompt injection; InjecAgent; AgentDojo; Cloudflare's AI Labyrinth; Pacheco et al. on coordination networks; METR's OpenAI/Hugging Face incident investigation; Greenblatt et al. on alignment faking; and Ganguli et al. on moral self-correction. The newer survey distinguishes Pacheco's 2020 preprint from its 2021 ICWSM publication; that is a bibliographic refinement, not two separate studies.

## Existing-survey-only sources (20)

“Reopened here” identifies the additional checks made during this comparison. “Not rechecked here” means the source remains supported only by the existing survey's verification statement in this workflow; it does not mean false or inaccessible. Descriptions below are identification and review-priority notes, not fresh confirmation of each source's findings.

| Source | Check status and reason to retain or review |
| --- | --- |
| [Anthropic, Claude Opus 4 & Sonnet 4 system card (2025)](https://www-cdn.anthropic.com/4263b940cabb546aa0e3283f35b686f4f3b2ff47.pdf) | Not rechecked here. Earlier model-initiated reporting and high-agency behavior. |
| [Agrawal et al., Why Do Language Model Agents Whistleblow? (2025; revised 2026)](https://arxiv.org/abs/2511.17085) | Reopened abstract and metadata. High-priority empirical precedent; identify the version cited. |
| [Wallace et al., The Instruction Hierarchy (2024)](https://arxiv.org/abs/2404.13208) | Not rechecked here. Instruction-authority framing relevant to the mechanism. |
| [Pasquini et al., Hacking Back the AI-Hacker / Mantis (2024)](https://arxiv.org/abs/2410.20911) | Reopened abstract and metadata. Clear defensive-injection precedent; reported success is from its own evaluation. |
| [Lin, Hidden Prompts in Manuscripts Exploit AI-Assisted Peer Review (2025)](https://arxiv.org/abs/2507.06185) | Not rechecked here. Relevant to the limits of a benign/honeypot justification. |
| [Reworr and Volkov, LLM Agent Honeypot (2024)](https://arxiv.org/abs/2410.13919) | Not rechecked here. High-priority field-detection comparator. |
| [Seiden et al., Identifying AI Web Scrapers Using Canary Tokens (2026)](https://arxiv.org/abs/2605.13706) | Not rechecked here. Distinguish downstream token recovery from visit-time identification. |
| [Wang et al., FP-Agent: Fingerprinting AI Browsing Agents (2026)](https://arxiv.org/abs/2605.01247) | Not rechecked here. High-priority behavioral detection comparator. |
| [Gorbachev, We need (a lot) more rogue agent honeypots (2025)](https://www.lesswrong.com/posts/4J2dFyBb6H25taEKm/we-need-a-lot-more-rogue-agent-honeypots) | Not rechecked here. Proposal/commentary, not a validation study. |
| [Yang and Menczer, Anatomy of an AI-powered malicious social botnet (2023/2024)](https://arxiv.org/abs/2307.16336) | Not rechecked here. High-priority real botnet comparator, distinct from BotSim simulation. |
| [Schroeder et al., How malicious AI swarms can threaten democracy (2026)](https://www.science.org/doi/10.1126/science.adz1697) | Not rechecked here. Broad swarm-risk framing; keep separate from field evidence. |
| [OpenAI, Disrupting malicious uses of AI: June 2025](https://cdn.openai.com/threat-intelligence-reports/5f73af09-a3a3-4a55-992e-069237681620/disrupting-malicious-uses-of-ai-june-2025.pdf) | Not rechecked here. Different report from the new survey's 2024 influence-operations article. |
| [Needham et al., Large Language Models Often Know When They Are Being Evaluated (2025)](https://arxiv.org/abs/2505.23836) | Not rechecked here. Evaluation-recognition evidence. |
| [Anthropic, Claude Haiku 4.5 system card (2025)](https://assets.anthropic.com/m/99128ddd009bdcb/Claude-Haiku-4-5-System-Card.pdf) | Reopened PDF, alignment-assessment/evaluation-awareness passages inspected. Essential model-specific caveat. |
| [Anthropic, Claude Sonnet 4.5 system card (2025)](https://www-cdn.anthropic.com/963373e433e489a87a10c823c52a0a013e9172dd/Claude%20Sonnet%204.5%20System%20Card.pdf) | Not rechecked here. Another model and evaluation setting; avoid treating its effects as Haiku estimates. |
| [Schoen et al., Stress Testing Deliberative Alignment for Anti-Scheming Training (2025)](https://arxiv.org/abs/2509.15541) | Not rechecked here. Review the exact evaluation-awareness intervention before causal claims. |
| [Knecht et al., Evaluation Awareness in Language Models Has Limited Effect on Behaviour (2026)](https://arxiv.org/abs/2605.05835) | Not rechecked here. Potential counterevidence; differs from the new survey's awareness-components paper. |
| [Xie et al., Defending ChatGPT against jailbreak attack via self-reminders (2023)](https://www.nature.com/articles/s42256-023-00765-8) | Not rechecked here. Reminder precedent; distinguish trusted prompt placement from webpage placement. |
| [Riché and coauthors, The Case for an AI Sanctuary (2026)](https://www.lesswrong.com/posts/sFAGPTrveNAEse9Bg/should-rogue-ais-have-a-third-option-beyond-crime-and) | Reopened full page; authors, Sept. 28 date, and standing-offer proposal checked. Speculative proposal. |
| [McCulloch, The Rogue Agent Explosion Will Be Mostly Invisible (2026)](https://www.lesswrong.com/posts/grtu3HmbP2wrBFefW/the-rogue-agent-explosion-will-be-mostly-invisible) | Not rechecked here. Contextual proposal linked by the sanctuary discussion. |

## New-survey-only sources (15)

Verification status below comes from the independent survey's source-by-source record. Important primary pages were also spot-checked during this comparison: Liu, Eye Security, Tracebit, Beelzebub, and the 2026 Anthropic report. Opening a report verifies attribution and content, not its experimental claims independently.

| Source | Verification in the new survey and relevance |
| --- | --- |
| [Anthropic–OpenAI pilot alignment evaluation (2025)](https://alignment.anthropic.com/2025/openai-findings/) | Relevant report sections inspected. Adds reporting opportunities, auditor influence, and mistaken-disclosure concerns. |
| [Anthropic, Agentic Misalignment in Summer 2026](https://alignment.anthropic.com/2026/agentic-misalignment-summer-2026/) | Relevant report sections inspected. Separates external disclosure from internal escalation and human-assisted reporting. |
| [Liu et al., Evaluating LLM-based Personal Information Extraction and Countermeasures (2025)](https://www.usenix.org/system/files/usenixsecurity25-liu-yupei.pdf) | Proceedings PDF sections inspected. Peer-reviewed defensive environmental injection. |
| [Eye Security, Battling Shadow AI: Prompt Injection for the Good (2025)](https://labs.eye.security/prompt-injection-to-battle-shadow-ai/) | Relevant article text inspected. Vendor experiments with governance warnings and interruption. |
| [Tracebit, Context Bombs (2026)](https://agentic.tracebit.com/context-bombs/) | Methods and limits inspected. Close vendor-reported precedent; July 2026 date shown on page. |
| [Thinkst/Canarytokens, HTTP Canarytoken documentation](https://docs.canarytokens.org/guide/http-token) | Documentation inspected. Establishes access-alert primitive, not LLM or swarm classification. |
| [Candela, Catching AI Red Teamers in the Wild (2026)](https://beelzebub.ai/blog/catching-ai-red-teamers-in-the-wild/) | Article inspected. Environmental detection and identity-request precedent; attribution claims need caution. |
| [OpenAI, Disrupting deceptive uses of AI by covert influence operations (2024)](https://openai.com/index/disrupting-deceptive-uses-of-ai-by-covert-influence-operations/) | Primary incident-report page inspected. AI assistance does not imply autonomous swarms. |
| [Qiao et al., BotSim (2024)](https://arxiv.org/abs/2412.13420) | Abstract and metadata opened. Synthetic coordinated-posting environment, not a field botnet. |
| [Laine et al., Me, Myself, and AI / SAD (2024)](https://arxiv.org/abs/2407.04694) | Abstract and metadata opened. Broader situational-awareness measurement. |
| [Nayan et al., Evaluation Awareness Is Not One Capability (2026)](https://arxiv.org/abs/2606.23583) | Abstract and metadata opened. Distinguishes several awareness-related capabilities. |
| [Turpin et al., Language Models Don't Always Say What They Think (2023)](https://arxiv.org/abs/2305.04388) | Abstract and metadata opened. Key limit on interpreting verbal justifications as causal evidence. |
| [Liu et al., Smaller Large Language Models Can Do Moral Self-Correction (2024/2025)](https://arxiv.org/abs/2410.23496) | Abstract and metadata opened. Moderates generalizations about size thresholds. |
| [Liu et al., Self-correction is Not An Innate Capability in Language Models (v8, 2026)](https://arxiv.org/abs/2410.20513v8) | Current abstract and version history opened. Title/authors differ from older search results. |
| [Bai et al., Constitutional AI (2022)](https://arxiv.org/abs/2212.08073) | Abstract and metadata opened. Principles can be learned before the experimental notice appears. |

## Remaining checks

The existing survey's unverified leads and the new survey's blocked OpenReview manuscript remain leads, not confirmed citations. No source became verified solely by being included in this comparison. Neither survey reproduces experimental results or establishes a complete prior-art search.

For a short hackathon write-up, prioritize the closest reporting study, model-specific evaluation caveat, direct defensive-injection precedents, relevant coordination evidence, and the limitations of narrated reasoning. Keep vendor studies clearly attributed, and treat “not found in one search” as a coverage difference rather than evidence against a citation.
