# Generative AI - Jio Institute PGP AI & DS (AY 2026-27), Term 4

Aishwarya Nevrekar (27PGAI0028)

Course repository: [aagarwal4/generative-ai-pgp-ji-2026](https://github.com/aagarwal4/generative-ai-pgp-ji-2026)

This repository contains my solutions and generated outputs for the Term 4 Generative AI coursework.

| Assignment | Topic | Folder |
|------------|-------|--------|
| Assignment 1 | Topic Detection and Summarization of News Articles; Job Postings Analysis | [assignments/Assignment 1](./assignments/Assignment%201/) |
| Assignment 2 | Retrieval-Augmented Generation for Mutual Funds Analysis | [assignments/assignment-2](./assignments/assignment-2/) |

## Repository structure

- `assignments/Assignment 1/` — notebooks, PDFs, datasets, and output CSV/JSON files
- `assignments/assignment-2/` — assignment notebook, starter notebook, dataset, and Chroma vector database

## Setup

Requires [Ollama](https://ollama.com/download) and [uv](https://docs.astral.sh/uv/).

```bash
git clone https://github.com/milindnevrekar-beep/genai_term4_solutions.git
cd genai_term4_solutions
ollama pull llama3.2
uv sync
uv run jupyter notebook
```

Open the notebooks from the relevant `assignments` folder and run all cells.

For Assignment 1:

```bash
uv run jupyter notebook "assignments/Assignment 1/Part1_Topic_Detection_Summarization.ipynb"
uv run jupyter notebook "assignments/Assignment 1/Part2_Job_Postings_Analysis.ipynb"
```

For Assignment 2:

```bash
uv run jupyter notebook "assignments/assignment-2/Assignment_2_Aishwarya_Nevrekar_27PGAI0028.ipynb"
```
