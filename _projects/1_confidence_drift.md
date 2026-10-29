---
layout: page
title: Confidence drift under preference optimization
description: Why does DPO make language models more confident without making them more accurate? (ongoing)
img: assets/img/12.jpg
importance: 1
category: research
---

**Status:** in progress — manuscript in preparation.

Preference optimization is known to hurt calibration, but it is less clear *where* the extra confidence comes from. This project studies the question in a tightly controlled setting:

- **Setup.** LoRA fine-tuning of a small instruction-tuned LLM (Qwen2.5-0.5B-Instruct) on UltraFeedback preference pairs, with DPO implemented from scratch, and a **matched SFT control** trained on the same data with the same budget.
- **Evaluation.** Accuracy, mean confidence and ECE on MMLU, tracked across checkpoints and multiple seeds, under two scoring formats (letter-choice and answer-text likelihood) to rule out format artifacts. Numerical precision of the evaluation pipeline itself was audited (bf16 vs fp32) so that small effects are not artifacts of rounding.
- **Analysis.** Decomposing the change in the output distribution into global and per-question temperature components, to ask whether the drift is "just temperature" or something structurally different.

Next steps: a larger model (1.5B), an information-geometric account of the update direction, and a formal statement of the mechanism.
