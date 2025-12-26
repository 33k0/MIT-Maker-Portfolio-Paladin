# PALADIN — Maker Portfolio Proxy

This repository contains a **deterministic, offline proxy** of the PALADIN recovery framework used in my research on error-resilient tool-using agents.

The purpose of this codebase is to make the **core control flow and recovery logic inspectable** without requiring model access, large-scale compute, or licensed datasets.

---

## What this repository shows

The included files preserve the **structural invariants** of the full PALADIN system:

- multi-step agent → tool interaction
- explicit failure detection
- branching recovery logic
- reuse of prior recovery patterns
- termination conditions and completion criteria

These components represent the **architectural decisions** behind the system rather than the infrastructure used to run large-scale experiments.

---

## What is omitted (by design)

The following components from the full research system are **not included** in this repository:

- trained or fine-tuned language models  
- licensed datasets (e.g., ToolBench variants)  
- large-scale evaluation infrastructure  
- internal data-generation pipelines  

These elements are omitted due to **ongoing review and dataset licensing constraints**.  
The annotation logic exposed here mirrors the rules used by the full system, and the accompanying Maker Portfolio media includes **real traces and outputs** from the complete implementation.

---

## File overview

### Core simulation

- `simulation.py`  
  Structural simplification of the PALADIN evaluation loop.  
  Preserves the agent–tool interaction cycle, failure handling, recovery branching, and termination logic using deterministic stubs for offline demonstration.

- `simulation_with_paladin_error_match.py`  
  Demonstrates how unseen tool errors are mapped to known failure categories and how previously defined recovery trajectories are reused to complete the task.

### Annotation primitives

- `annotate_clean.py`  
  Defines invariants and normalization rules for valid, non-error agent trajectories.

- `annotate_recovery.py`  
  Defines structured recovery generation conditioned on detected failure types.

These files expose the **core annotation and recovery rules** in isolation for clarity.

---

## Note on dataset construction

The failure–recovery datasets used in the PALADIN paper were generated using a larger internal pipeline that injects failures into real tool-using trajectories and applies the annotation logic shown here at scale.

That internal pipeline is not included in this repository. The code provided here represents a **faithful abstraction** of the underlying rules and decision points rather than a full reproduction of the research environment.

---

## How to read this repository

If you are skimming:

1. Start with `simulation.py` to see the overall control flow  
2. Then read `simulation_with_paladin_error_match.py` to see recovery under unseen failures  
3. Skim the annotation files to understand how success and recovery are formalized  

This repository is intended for **inspection and understanding**, not execution parity.

## Related publication

This work is described in more detail in:

Vuddanti, Shah, et al. *PALADIN: Self-Correcting Language Model Agents to Cure Tool-Failure Cases*. 

arXiv preprint: https://arxiv.org/abs/2509.25238

To appear in the Proceedings of the AAAI Conference on Artificial Intelligence (AAAI), 2026.  
(Oral presentation)
