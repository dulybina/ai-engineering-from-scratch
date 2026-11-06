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
| 2026-10-29 | 00-setup-and-tooling/08-editor-setup | 3/3 | Installed jupyter/black/ruff/remote-ssh/gitlens, applied lesson settings.json (was {}); predicted Black would delete unused import and Ruff would flag spacing (swapped), then saw it in ~/editor-lab/messy.py; thought terminal used system python and Pylance had none (it's the reverse: Pylance on wrong interpreter); warm-up fixed the Container Toolkit miss |
| 2026-11-03 | 00-setup-and-tooling/09-data-management | 2/3 | Installed datasets 5.1.0 in .venv; cached reload 3.50s -> 0.31s; predicted Parquet ~0.75x of CSV (actual 0.69x on text-heavy reviews) and JSON biggest; seed=42 splits matched 100/100, no seed only 19/100; thought .gitignore covers *.parquet (only under data/) and that the HF cache is skipped for secrets (it's outside the repo); quiz: thought streaming=True means faster parallel download |
| 2026-11-04 | 00-setup-and-tooling/10-terminal-and-shell | 3/3 | Thought '> train.log' captures the traceback (stderr goes to screen; saw it in ~/shell-lab); read 'tail -3' as picking values across the file; thought a '&' job on an SSH box survives a dropped connection (SIGHUP demo: plain died, nohup lived); installed tmux, hit Ctrl+B ' instead of " (Shift+'), then 3-pane session survived detach; rsync 25 B vs 10 MB predicted right; final plan missed 2>&1; warm-up fixed streaming |
| 2026-11-04 | 00-setup-and-tooling/11-linux-for-ai | 3/3 | Read cores/RAM from /proc (4 logical CPUs, 15.5 GB; /proc/meminfo is 0 bytes on disk); decoded 644 and 600 right (own ssh key is 600); saw run.sh 'Permission denied' at 664; predicted ~/.cache/uv as biggest at 1.4G exactly; learned uv hard-links cache into .venv (73M extra when measured together); knew Linux is case-sensitive; warm-up fixed SIGHUP |
| 2026-11-05 | 00-setup-and-tooling/12-debugging-and-profiling | 3/3 | Sorted crash vs silent bugs right (shape crashes; shuffled labels and lr=1.0 train silently); spotted unnormalized pixels via max=255; predicted log(0)=inf (it's -inf) and log(-1)=NaN; saw NaN spread to every layer's grads, so detect_nan finds when, breakpoint finds where; predicted data loading dominates (91% at num_workers=0, epoch 0.60s -> 0.41s with 3 workers on 4 CPUs) |

## Review queue
- 00-setup-and-tooling/03-gpu-setup-and-cloud: nvidia-smi checks the driver/GPU (torch.cuda.is_available() checks PyTorch); VRAM is GPU memory, not swap (synchronize() now recalled correctly)
- 00-setup-and-tooling/06-python-environments: 'CUDA not available' with an NVIDIA GPU usually means torch.version.cuda is newer than the driver's CUDA shown by nvidia-smi; venvs do not block GPU access
- 00-setup-and-tooling/07-docker-for-ai: NVIDIA Container Toolkit exposes host GPUs/driver to containers via --gpus; it does not install drivers in the container (driver = host kernel module, CUDA toolkit = image) (recalled correctly in 08 warm-up)
- 00-setup-and-tooling/09-data-management: streaming=True gives an IterableDataset read row by row on demand without downloading the full dataset (about size, not speed; no ds[i] or len) (recalled correctly in 10 warm-up)
