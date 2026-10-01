# Retrieval-Based and Fine-Tuned LLM Approaches for Industrial Asset Health Monitoring

This repository contains simple and heavily commented code for industrial failure-sensor reasoning using the FailureSensorIQ dataset.

The goal is to answer multiple-choice questions about relationships between:

- industrial assets,
- failure modes,
- sensor readings.

The repository has two main parts:

1. Retrieval-based reasoning
2. LLM-based reasoning with Qwen2.5-7B-Instruct

No Hugging Face login code, API key, or secret is included in this repository.

---

## Repository structure

```text
failure-sensor-reasoning-llm/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── data/
│   └── README.md
│
├── notebooks/
│   ├── 01_retrieval_based_reasoning_clean.ipynb
│   └── 02_llm_based_reasoning_qwen_clean.ipynb
│
├── results/
│   └── README.md
│
├── figures/
│   └── README.md
│
└── paper/
    └── README.md
```

---

## Dataset files

Place the dataset files inside the `data/` folder.

Expected files:

```text
all.jsonl
all_10_options_all_perturbed_simple.jsonl
all_10_options_perturbed_complex.jsonl
sample_50_questions.jsonl   # optional
```

The notebooks also search `/kaggle/input/` automatically when running on Kaggle.

---

## Methods

### Retrieval-based reasoning

The retrieval notebook compares:

- TF-IDF
- BM25
- Semantic search
- Hybrid search

Each answer option is checked separately. The option with the highest final score is selected.

### LLM-based reasoning

The LLM notebook compares:

- Zero-shot Qwen2.5-7B-Instruct
- Few-shot Qwen2.5-7B-Instruct
- QLoRA fine-tuned Qwen2.5-7B-Instruct

The LLM notebook needs a GPU.

---

## How to run

### Step 1: Install packages

```bash
pip install -r requirements.txt
```

### Step 2: Add data files

Put the JSONL files inside the `data/` folder.

### Step 3: Run notebooks

Run the notebooks in this order:

```text
notebooks/01_retrieval_based_reasoning_clean.ipynb
notebooks/02_llm_based_reasoning_qwen_clean.ipynb
```

---

## Important notes

- No tokens or secrets are used.
- Retrieval methods can run on CPU.
- LLM prompting and QLoRA fine-tuning need GPU memory.
- If you use Kaggle, enable GPU before running the LLM notebook.
- If memory is limited, set `MAX_EVAL_SAMPLES` or `MAX_TRAIN_SAMPLES` to a small number for testing.

---

## Citation

If you use this code, please cite the related paper or repository.

```bibtex
@misc{damarla2026failuresensorreasoning,
  title={Retrieval-Based and Fine-Tuned LLM Approaches for Industrial Asset Health Monitoring and Decision Support},
  author={Damarla, Seshu K. and Zhu, Xiuli},
  year={2026},
  note={GitHub repository}
}
```
