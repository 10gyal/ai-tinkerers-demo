# PromptMaxxing: Towards Autonomous Prompt Iteration

This project demonstrates how to optimize an LLM prompt with [DSPy](https://dspy.ai) and [GEPA](https://dspy.ai/api/optimizers/GEPA/overview/). The example task is spelling words backward, which makes evaluation straightforward with exact matching.

This notebook was prepared for my talk at AI Tinkerers Workshop in Seoul, South Korea (2026), demonstrating why autonomous prompt iteration is a promising path forward for AI systems in production.

## The Goal

The demo shows how prompt improvement can become an autonomous, measurable engineering loop. Instead of manually editing prompts, we define the task and evaluation criteria, let GEPA iterate on the instruction, and compare the optimized program against a held-out baseline. The broader goal is to make prompt iteration more systematic, repeatable, and suitable for production AI systems.

## What it does

The notebook:

1. Loads examples from `spell_back.csv` and splits them into train, validation, and test sets.
2. Evaluates an unoptimized DSPy baseline.
3. Uses GEPA to improve the signature instruction from metric feedback.
4. Compares baseline and optimized accuracy on the held-out test set.
5. Saves the optimized program to `spell_back_gepa.json`.

## Run it

Install the dependencies and configure an API key:

```bash
uv sync
export OPENAI_API_KEY="your-api-key"
uv run jupyter lab spell_back.ipynb
```

Run the notebook cells from top to bottom. It uses `gpt-4o-mini` for the baseline and `gpt-5.4-mini` as GEPA’s reflection model.

## References

- [DSPy](https://dspy.ai) — signatures and optimizers
- [The Problem Is Prompt Debt](https://www.dbreunig.com/2026/06/22/the-problem-is-prompt-debt.html) — Drew Breunig
- [GEPA](https://dspy.ai/api/optimizers/GEPA/overview/) — reflective prompt optimization
- [GEPA paper](https://arxiv.org/abs/2507.19457) — *GEPA: Reflective Prompt Evolution Can Outperform Reinforcement Learning*
- [Open Thoughts](https://www.open-thoughts.ai/) — source dataset
