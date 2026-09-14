# Generative AI - Assignment 1

Aishwarya Nevrekar (27PGAI0028)

- Brief: [assignment-1 in the course repository](https://github.com/aagarwal4/generative-ai-pgp-ji-2026/tree/main/assignment-1)
- Part 1 notebook: [Part1_Topic_Detection_Summarization.ipynb](./Part1_Topic_Detection_Summarization.ipynb) ([PDF](./Part1_Topic_Detection_Summarization.pdf))
- Part 2 notebook: [Part2_Job_Postings_Analysis.ipynb](./Part2_Job_Postings_Analysis.ipynb) ([PDF](./Part2_Job_Postings_Analysis.pdf))

Both notebooks use LangChain with the `llama3.2` model served locally by Ollama, which the brief advises for
processing the full datasets. Structured answers are defined with Pydantic models.

## Part 1: Topic Detection and Summarization of News Articles (45 marks)

Dataset: `data/bbc-news-data.csv`, first 30 articles.

| Step | What the notebook does |
|------|------------------------|
| 2. Topic classification (10) | Few-shot prompt with a description of each category; `with_structured_output` returns one of Business, Entertainment, Politics, Sport or Tech |
| 3. Summarization (10) | 2-3 sentence summary covering who, what, when, where and why |
| 4. Key entity extraction (10) | People, organizations and locations as JSON lists (`JsonOutputParser`) |
| 5. Update the DataFrame (15) | `Detected_Topic`, `Summary` and `Key_Entities` added to the article columns |

Output: [`outputs/part1_bbc_first30_results.csv`](./outputs/part1_bbc_first30_results.csv) (also `.json`)

## Part 2: Job Postings Analysis (55 marks)

Dataset: `data/job_title_des.csv`, first 25 postings.

| Step | What the notebook does |
|------|------------------------|
| 2. Job category classification (10) | Few-shot prompt over broad domains with "Other" as the fallback |
| 3. Requirements extraction (30) | Skills, education and experience extracted as JSON; "Not specified" when missing |
| 4 & 5. Apply the chain and update the DataFrame (15) | `Predicted_Category`, `Required_Skills`, `Education_Required` and `Experience_Required` added for every posting |

Output: [`outputs/part2_jobs_first25_results.csv`](./outputs/part2_jobs_first25_results.csv) (also `.json`)

## Bonus: all rows (20 marks)

The bonus cells run the same pipelines over both complete datasets.

- [`outputs/part1_bbc_ALL_results.csv`](./outputs/part1_bbc_ALL_results.csv): all 2,225 articles (also `.json`)
- [`outputs/part2_jobs_ALL_results.csv`](./outputs/part2_jobs_ALL_results.csv): all 2,277 postings (also `.json`)

## Results

| | Rows | Notes |
|---|---|---|
| Part 1 | 30 | Topic matches the dataset's category for 83.3% of articles |
| Part 2 | 25 | Skills found for 24, education stated for 11, experience stated for 16 |
| Bonus Part 1 | 2,225 | Topic matches the dataset's category for 82.6% (Business 85%, Entertainment 82%, Politics 98%, Sport 96%, Tech 47%) |
| Bonus Part 2 | 2,277 | Skills found for 2,212 postings; education stated for 59%, experience for 78% |

## How to run

From the repository root, after the setup in the [main README](../README.md):

```bash
uv run jupyter notebook "Assignment 1/Part1_Topic_Detection_Summarization.ipynb"
uv run jupyter notebook "Assignment 1/Part2_Job_Postings_Analysis.ipynb"
```

The bonus cells save each finished row to `outputs/*_cache.jsonl` while they run, so an interrupted run
continues where it stopped.
