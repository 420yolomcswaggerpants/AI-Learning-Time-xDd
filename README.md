# AI engineering log

A daily record of learning AI engineering by building, starting from my first LLM API call. One entry per working day: what I built, what broke, what I measured, and what I decided.

## The short version

| Days | What happened |
|---|---|
| 1–15 | 21 small projects: API apps, five retrieval (RAG) variants and an evaluation harness, LoRA and full fine-tunes, then backpropagation, attention and a transformer block from scratch in NumPy |
| 16–18 | [Nimbus](https://github.com/420yolomcswaggerpants/nimbus-ai-support), an end-to-end LLM support platform: synthetic data, fine-tuning, hybrid retrieval, DPO, a distillation attempt that did not beat the baseline, and security hardening |
| 19–23 | Review. No new projects; annotating and studying what I had built |
| 24 onward | BrickGenie, a Claude-tutored math game for pre-K through grade 8: product definition, build, first production deploy on day 28, audits, content for every grade, and preparation for the first testers. The code is private |

## Entries worth reading first

- [Day 3](Day3_Progress.md): deciding that calling an API is not AI engineering, and changing course
- [Day 7](Day7_Progress.md): the first evaluation harness, and a fine-tune that overfit
- [Day 15](Day15_Progress.md): 21 projects in 15 days, with an honest self-assessment
- [Day 18](Day18_Progress.md): capstone results, including what did not work
- [Day 28](Day28_Progress.md): first production deploy, and the defects a green test suite missed
- [Day 30](Day30_Progress.md): two full audits, and why about 280 parallel reviewers produced nothing while seven with clear file ownership finished the job

## Projects by day

| Day | Project | Repository |
|---|---|---|
| 2 | AI email generator | [ai-email-generator](https://github.com/420yolomcswaggerpants/ai-email-generator) |
| 2 | Rule-based support agent | [support_agent](https://github.com/420yolomcswaggerpants/support_agent) |
| 3 | DocuBot, document Q&A | [docubot](https://github.com/420yolomcswaggerpants/docubot) |
| 4 | First LoRA fine-tune, deployed | [nimbus-finetune](https://github.com/420yolomcswaggerpants/nimbus-finetune) |
| 5 | Semantic RAG | [rag-system](https://github.com/420yolomcswaggerpants/rag-system) |
| 6 | Hybrid RAG (BM25 + embeddings, RRF) | [hybrid-rag](https://github.com/420yolomcswaggerpants/hybrid-rag) |
| 7 | RAG evaluation harness | [rag-evaluation](https://github.com/420yolomcswaggerpants/rag-evaluation) |
| 7 | Full fine-tune vs. LoRA | [nimbus-full-finetune](https://github.com/420yolomcswaggerpants/nimbus-full-finetune) |
| 9 | Reranking RAG | [reranking-rag](https://github.com/420yolomcswaggerpants/reranking-rag) |
| 9 | Query-expansion RAG | [query-expansion-rag](https://github.com/420yolomcswaggerpants/query-expansion-rag) |
| 10 | Own training loop | [own-training-loop](https://github.com/420yolomcswaggerpants/own-training-loop) |
| 10 | Attention from scratch | [attention-from-scratch](https://github.com/420yolomcswaggerpants/attention-from-scratch) |
| 10 | Tiny transformer from scratch | [tiny-transformer](https://github.com/420yolomcswaggerpants/tiny-transformer) |
| 11–12 | Model evaluation on a held-out set | [model-evaluation](https://github.com/420yolomcswaggerpants/model-evaluation) |
| 12 | FastAPI model serving | [fastapi-model-serving](https://github.com/420yolomcswaggerpants/fastapi-model-serving) |
| 13 | Synthetic-data fine-tuning | [synthetic-data-finetune](https://github.com/420yolomcswaggerpants/synthetic-data-finetune) |
| 13 | Neural network from scratch | [ann-from-scratch](https://github.com/420yolomcswaggerpants/ann-from-scratch) |
| 14 | Deep neural network from scratch | [deep-neural-network](https://github.com/420yolomcswaggerpants/deep-neural-network) |
| 15 | MNIST classifier from scratch | [mnist-classifier](https://github.com/420yolomcswaggerpants/mnist-classifier) |
| 15 | Transformer training (PyTorch) | [transformer-training](https://github.com/420yolomcswaggerpants/transformer-training) |
| 15 | RLHF simulation (REINFORCE) | [rlhf-simulation](https://github.com/420yolomcswaggerpants/rlhf-simulation) |
| 16–18 | Nimbus capstone | [nimbus-ai-support](https://github.com/420yolomcswaggerpants/nimbus-ai-support) |

## How I work

I build with AI coding agents, and I am responsible for what they produce. That means gates: tests, simulations, content checkers and independent review passes, and reading the result myself. The entries record where that held and where it did not.

Day 1 says I was aiming at AI project and management roles. The work changed that, and the entry stays as I wrote it.
