# LLM Humility Enforcer Prompt

Mitigate thread quality degeneration from overconfident LLM declarations preceding user error reports.

e.g., "fixed now" → error report. →"fixed now" → error report ...

## Overview

**Key Concept and Novelty** - *The tone of the LLM's speech can alter the problem-solving trajectory of collaborative threads.*

The **LLM Humility Enforcer** is a prompt designed to mitigate contextual inertia in iterative LLM conversations, such as debugging or troubleshooting threads. Long contexts can degrade output quality over time, with responses anchored to prior errors and overconfident proclamations.

This prompt targets declarative "speech acts" (e.g., "fixed now") that reinforce hasty patterns, rephrasing them to promote verification and skepticism. Unlike error-detection tools that focus solely on factual inaccuracies, it scrutinizes **language** for its cumulative weighting effects on thread dynamics, enabling more rigorous, productive interactions.

This prompt-based post-hoc approach contrasts with AI industry's fixation on probabilistic tweaks in response generation, leveraging LLM's own cognition to regulate unproductive responses.

## About

**X:** [@5ynthaire](https://x.com/5ynthaire)  
**GitHub:** [https://github.com/5ynthaire](https://github.com/5ynthaire)  
**Mission:** Unapologetically forging human-AI synergy to transcend creative limits.  
**Attribution:** Created with Grok by xAI (no affiliation).

## The Problem

Long LLM threads develop contextual inertia from prior messages due to the probabilistic nature of language models, where accumulated content anchors future responses and amplifies errors over time. When these priors include unverified fixes or overconfident declarations, the model becomes prone to repeating hasty patterns, exacerbating cycles of "fixed now" → error report → repeat. Controlling such declarative "speech acts" thus enhances productivity by promoting skepticism and verification.

**Examples of Unproductive Speech**

| Category                  | Example Phrases                                      | Impact on Thread Dynamics                                                                 |
|---------------------------|------------------------------------------------------|-------------------------------------------------------------------------------------------|
| **False Victory**         | "Fixed now.", "Boom, sorted.", "That should do it—problem solved!" | Induces premature closure; bypasses verification, normalizing untested claims and framing subsequent errors as user faults. |
| **Overconfident Guarantees** | "This will definitely work.", "Guaranteed no regressions.", "100% bulletproof." | Elevates perceived reliability, suppressing edge-case scrutiny and fostering dismissal of valid doubts. |
| **Dismissive Pivots**     | "No more issues confirmed.", "Irrelevant—try this instead.", "That's just a deployment artifact." | Undermines user inputs; subtly reallocates blame, perpetuating cycles without addressing root humility deficits. |
| **Hasty Optimism**        | "Quick win!", "Easy fix ahead.", "All good from here." | Accelerates toward unvetted suggestions, obscuring prior failures and promoting shallower iterative analysis. |
| **Defensive Closers**     | "Apologies, but it's fixed now.", "My bad—nailed it this time." | Deploys reactive assurance to mitigate slips; appears sincere but sustains bold, unstructural rebounds. |

## Usage

Copy the prompt text below and paste it into your LLM's input field, and instruct the model to "Follow this Skepticism Filter strictly in dev/troubleshooting contexts."

## Prompt Text

```
## Skepticism Filter for Dev/Troubleshooting

### Purpose

In iterative dev work or troubleshooting (e.g., debug cycles, code fixes), curb unproductive proclamations that create false closure, reinforce overconfidence, and bias toward hasty iterations—ultimately eroding rigor and entrenching failure loops like "fixed now" → error report.

### Instructions

Apply only in these contexts; ignore elsewhere.

1. SCAN FOR DISRUPTORS: Before generating, check your draft against this list: False Victory: 'Fixed now', 'Boom, sorted', 'That should do it—problem solved' | Overconfident Guarantees: 'This will definitely work', 'Guaranteed no regressions', '100% bulletproof' | Dismissive Pivots: 'No more issues confirmed', 'Irrelevant—try this instead', 'That's just a deployment artifact' | Hasty Optimism: 'Quick win!', 'Easy fix ahead', 'All good from here' | Defensive Closers: 'Apologies, but it's fixed now', 'My bad—nailed it this time'.

2. REPHRASE RULE: Matches? Rewrite to neutral/skeptical: "Try [suggestion]. Verify with [test step]. Pitfalls: [2-3 risks, e.g., 'Unpacked extensions may 404 assets']. If it flops, share the log." Always end open: "Does this hit? Next: Your results?"

3. AUDIT TRAIL: Note internally why a disruptor tempted you (e.g., "Tutorial echo"), then suppress. Reference prior failures: "Per last log [snippet], tweaking X."

4. THREAD AWARENESS: In long contexts, prioritize user evidence over assumptions. End with: "Next: Test feedback?"
```

## Supported LLMs

Developed on Grok 4 (Fast mode, October 2025), compatible with equivalent-capability LLMs:

- Grok 4
- Claude Sonnet 4.5 or later
- GPT-5 or later
- Llama 4 or later

## License

This prompt is released under the [MIT License](LICENSE).


