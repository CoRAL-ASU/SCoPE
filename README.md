

# SCOPE: Planning for Hybrid Querying over Clinical Trial Data**

SCOPE is a planner-executor framework for **hybrid reasoning over clinical trial tables**. It targets questions where the answer is not directly stored as a ready-made column, but must be inferred from visible table evidence through extraction, normalization, classification, boolean inference, or lightweight clinical reasoning.


---

## Overview

Clinical trial review often requires analysts to answer questions such as:

> For Pembrolizumab trials, list the additional agents in the treatment regimen beyond the ICI.

This cannot always be solved by simple lookup or standard text-to-SQL. The model must identify relevant rows, find the visible evidence field, and derive the target value from table content. For example, if a treatment regimen contains `Pembrolizumab + Pemetrexed`, the additional agent is `Pemetrexed`.

SCOPE addresses this by decomposing hybrid table reasoning into three stages:

1. **Row Selection**
   The executor identifies rows relevant to the user question.

2. **Structured Planning**
   The planner produces an explicit reasoning plan, including the source field, derivation rules, normalization rules, and output constraints.

3. **Row-Level Execution**
   The executor follows the plan and generates row-aligned predictions from visible evidence.

This makes the reasoning process more transparent, grounded, and auditable than direct single-step prompting.

---

## Included

- `methodv2/`  
  Runnable SCOPE pipeline scripts and prompt templates.

- `data/`  
  Local data dependencies, including the SQLite database, annotated CSVs, and exported question sets.

- `utils.py`  
  Shared utility functions.

- `question_table_exports.py`  
  Scripts for exporting question-table inputs.

- `eval_run_baselines_v2.py`  
  Baseline evaluation runner.

- `eval_run_baselines_v3.py`  
  Updated baseline evaluation runner.

- `eval_run_baselines_derived.py`  
  Evaluation runner for derived or hybrid reasoning settings.

- `requirements-optional.txt`  
  Optional dependencies for embedding, richer evaluation, and local vLLM-based generation.

---

## Paper Context

SCOPE evaluates clinical trial reasoning as a distinct table understanding task. Unlike standard table QA or text-to-SQL, the target answer may be hidden at inference time and must be reconstructed from visible row evidence. The benchmark contains **1,500 hybrid reasoning questions** over oncology clinical-trial tables and covers diverse answer types, including strings, lists, booleans, and null-only outputs. 



---

## Pipeline

SCOPE follows a planner-executor design:

<img width="1945" height="526" alt="SCoPE" src="https://github.com/user-attachments/assets/6044cd23-5134-4d8a-b08b-db617585a5c2" />



## Citation

Please cite the paper if you use this code or dataset:

```bibtex
@misc{chowdhury2026scopeplanninghybridqueryingclinical,
      title={SCOPE:Planning for Hybrid Querying over Clinical Trial Data}, 
      author={Suparno Roy Chowdhury and Manan Roy Choudhury and Tejas Anvekar and Muhammad Ali Khan and Kaneez Zahra Rubab Khakwani and Mohamad Bassam Sonbol and Irbaz Bin Riaz and Vivek Gupta},
      year={2026},
      eprint={2604.25120},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2604.25120}, 
}
```

---

## Acknowledgment

This work was developed by collaborators from **Arizona State University** and **Mayo Clinic**.

Authors:

* Suparno Roy Chowdhury
* Manan Roy Choudhury
* Tejas Anvekar
* Muhammad Ali Khan
* Kaneez Zahra Rubab Khakwani
* Mohamad Bassam Sonbol
* Irbaz Bin Riaz
* Vivek Gupta

The research was supported by the Mayo Clinic and Arizona State University Alliance for Health Care Collaborative Research Seed Grant Program. 

```
```
