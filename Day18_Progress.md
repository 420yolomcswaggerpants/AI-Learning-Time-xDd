# Day 18 Progress: DPO Training + Final Model Selection + Full-Stack Integration

## What I Did Today

### Concept Quiz (Separate Chat, Ongoing)
- Quizzing on all concepts while training, evaluating, and integrating
- Routine repetition, no labels

### DPO Preference Generation
- Generated 500 preference pairs via DeepSeek API
- Cleaned and validated preference data using clean-preferences.py
- Output: preference_pairs_clean.jsonl

### DPO Training on 0.5B SFT
- Trained DPO on SFT 0.5B using local AMD 7900 XT
- Output: rlhf/nimbus-dpo-0.5b
- Epochs: 1
- Learning rate: 5e-6
- Beta: 0.1

### DPO Evaluation Results
| Model | Token Overlap | Judge Overall |
|-------|---------------|---------------|
| DPO 0.5B | 0.5664 | 3.913 |
| SFT 0.5B | 0.5816 | 3.830 |
| Teacher 3B v2 | 0.5635 | 4.035 |
| Distilled v4 | 0.5415 | 3.830 |

Conclusion: DPO improved judge overall above SFT. Token overlap slightly lower because DPO optimizes preference, not exact phrasing. DPO 0.5B selected as final deployable model.

### Final Model Selection
- Deployable live demo: `nimbus-dpo-0.5b`
- High-quality but too large for free hosting: `nimbus-sft-3b-v2-merged`
- Distillation documented as negative result
- SFT 0.5B is strong baseline, superseded by DPO for quality

### Backend Integration Complete
- FastAPI backend loads DPO model + hybrid RAG + cross-encoder reranking + security checks
- Fixed issues:
  - Security module import names (hyphens → underscores)
  - Audit logger relative import
  - DPO model path (was pointing to distilled model)
  - JSON serialization of float32 confidence
  - Cross-encoder device placement to GPU
  - HIP_VISIBLE_DEVICES set at top of main.py
- Endpoints:
  - GET /health
  - POST /v1/answer
- Local testing successful: returns answer, sources, confidence

### Frontend Integration Complete
- Streamlit chat interface calls backend /v1/answer
- Shows answer, confidence, and sources
- Timeout increased from 30 to 120 seconds
- Local testing successful

### Security Module Integrated
- input_validation.py
- prompt_injection_defense.py
- output_filter.py
- rate_limiter.py
- audit_log.py
- adversarial_tests.py
- threat-model.md

All security components are imported and used in the backend request flow.

### Cleanup Completed
- Repo reduced from ~9.4 GB to ~5.5 MB
- Model files moved to external backup
- .gitignore updated to exclude models, checkpoints, raw data, logs, secrets

### Git Push
- Initial capstone repo pushed to GitHub
- Final integration fixes committed and pushed

### README
- Comprehensive README written with architecture, evaluation results, struggles, limitations, future work
- Later suggested additions: deployment status, GPU config note, API example, security wiring, known free-hosting limitations

## Current Status
- Capstone functionally complete locally
- Full stack works: Streamlit frontend → FastAPI backend → DPO 0.5B + RAG + security
- Best deployable model selected and integrated
- Distillation negative result documented honestly
- Repo clean and pushed

## Next Steps
- Update README with final deployment notes (if desired)
- Upload final models to HuggingFace
- Deploy frontend/backend to free hosting if feasible
- Final end-to-end testing
- Final evaluation summary
- Continue daily concept quiz

## Key Milestones
- DPO improved model quality over SFT
- Full-stack integration working locally
- Security module wired into backend
- Repo cleaned and pushed
- Local GPU ROCm setup validated

## Honest Findings
- DPO > SFT > Distilled for 0.5B deployable model
- Teacher 3B v2 best overall quality, but not deployable for free
- Distillation did not improve student despite correct KL implementation
- Full integration required multiple fixes: imports, paths, JSON types, device placement
