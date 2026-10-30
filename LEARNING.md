# My AI Engineering Path
<!-- Managed by the ai-engineering-from-scratch learning skills.
     Repo: https://github.com/rohitg00/ai-engineering-from-scratch -->

## Mission
Ship an AI product. Build goal: not sure yet; decide along the way.

## Placement
- Date: 2026-10-26
- Score: 6/10 (Math & Statistics 1/2, Classical ML 2/2, Deep Learning 1/2, NLP & Transformers 0/2, Applied AI 2/2)
- Entry point: Phase 0: Setup & Tooling (chosen by learner to start from the very beginning; the quiz suggested Phase 7)
- Pace: ~5 h/week

## Path
| Phase | Name | Status | Est. hours |
|-------|------|--------|------------|
| 0 | Setup & Tooling | Do | 16 |
| 1 | Math Foundations | Do | 23 |
| 2 | ML Fundamentals | Do | 26 |
| 3 | Deep Learning Core | Do | 15 |
| 4 | Computer Vision | Do | 27 |
| 5 | NLP — Foundations to Advanced | Do | 30 |
| 6 | Speech & Audio | Do | 18 |
| 7 | Transformers Deep Dive | Do | 14 |
| 8 | Generative AI | Do | 14 |
| 9 | Reinforcement Learning | Do | 13 |
| 10 | LLMs from Scratch | Do | 26 |
| 11 | LLM Engineering | Do | 19 |
| 12 | Multimodal AI | Do | 65 |
| 13 | Tools & Protocols | Do | 76 |
| 14 | Agent Engineering | Do | 55 |
| 15 | Autonomous Systems | Do | 20 |
| 16 | Multi-Agent & Swarms | Do | 28 |
| 17 | Infrastructure & Production | Do | 34 |
| 18 | Ethics, Safety & Alignment | Do | 31 |
| 19 | Capstone Projects | Do | 620 |
| | **Total** | | **1170** |

## Progress log
| Date | Lesson | Quiz | Note |
|------|--------|------|------|
| 2026-10-26 | 00-setup-and-tooling/01-dev-environment | 3/3 | Created .venv with uv (Python 3.12.15, numpy 2.5.4); thought uv picks the latest Python, but it picked a managed 3.12 over system 3.14 |
| 2026-10-26 | 00-setup-and-tooling/02-git-and-collaboration | 3/3 | Committed and pushed LEARNING.md; set up SSH after the HTTPS push failed; expected a merge commit where git did a fast-forward |
| 2026-10-26 | 00-setup-and-tooling/03-gpu-setup-and-cloud | 1/3 | Installed CPU torch 2.14.1; 4000x4000 matmul took ~3.4s (~37 GFLOP/s) vs 1s guessed; got the fp16 VRAM math right; missed nvidia-smi vs torch API and synchronize() (async GPU) |
| 2026-10-27 | 00-setup-and-tooling/04-apis-and-keys | 3/3 | No key yet; ran the fake-key call and read the 401 authentication_error body; warm-up: confused VRAM with swap, but got synchronize() right this time |
| 2026-10-27 | 00-setup-and-tooling/05-jupyter-notebooks | 3/3 | Ran JupyterLab; %timeit gave list 356 ms vs numpy 3.37 ms (~106x, guessed 10x); thought numpy's speed came from parallel batches, but it's mostly compiled C loops plus SIMD; nailed the 40-vs-20 out-of-order trap |
| 2026-10-29 | 00-setup-and-tooling/06-python-environments | 2/3 | Built ~/my-ai-project with uv (19 locked packages from 2 direct deps); predicted the lockfile rebuild correctly; guessed stdlib urllib/json would show up as deps; missed the CUDA-version-mismatch question (thought venvs block GPU access) |
| 2026-10-29 | 00-setup-and-tooling/07-docker-for-ai | 2/3 | Added self to docker group (no newgrp/sg here; needed a fresh login shell); first thought a container has its own 22.04 kernel, then swapped uname/os-release, then saw host kernel 7.0.0-34 inside ubuntu:22.04; built CPU numpy image (54.6s cold vs 2.5s cached); proved qdrant:6333 works and localhost fails; quiz: thought the NVIDIA Container Toolkit installs drivers in the container |

## Review queue
- 00-setup-and-tooling/03-gpu-setup-and-cloud: nvidia-smi checks the driver/GPU (torch.cuda.is_available() checks PyTorch); VRAM is GPU memory, not swap (synchronize() now recalled correctly)
- 00-setup-and-tooling/06-python-environments: 'CUDA not available' with an NVIDIA GPU usually means torch.version.cuda is newer than the driver's CUDA shown by nvidia-smi; venvs do not block GPU access
- 00-setup-and-tooling/07-docker-for-ai: NVIDIA Container Toolkit exposes host GPUs/driver to containers via --gpus; it does not install drivers in the container (driver = host kernel module, CUDA toolkit = image)
