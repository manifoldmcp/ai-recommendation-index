# AI Recommendation Index: marketing MCP servers

Which marketing MCP servers ChatGPT, Claude, Gemini, Perplexity and Google's AI Overviews name and cite when buyers ask them for one. Each month [Manifold](https://www.manifoldmcp.com) asks the same buyer questions on all five engines and publishes every answer here.

The write-up, with the leaderboard for each category: **[manifoldmcp.com/blog/ai-recommendation-index](https://www.manifoldmcp.com/blog/ai-recommendation-index)**

## Runs

| Run | Prompts | Answers | Citations |
| --- | --- | --- | --- |
| [2026-10-24](data/2026-10-24) | 33 | 165 | 1,614 |

## Files

Each run is a folder under `data/`, named by the date it was asked.

| File | One row per | Columns |
| --- | --- | --- |
| `answers.csv` | prompt and engine | date, category, prompt, engine, model, answered_at, brands_named (in order), brands_cited, citations, answer (full text) |
| `mentions.csv` | brand in an answer | date, category, prompt, engine, brand, named, place, cited |
| `citations.csv` | cited URL | date, category, prompt, engine, position, url, domain, title, brand |
| `prompts.csv` | prompt | category, prompt |
| `brands.csv` | brand counted | brand, pattern (the regular expression matched on the answer), sites |
| `raw/*.json` | call to the API | the tool's full reply, as returned |

## Method

- **Prompts:** the questions in `prompts.csv`, the same each month. A change is noted in this README and on the page.
- **Engines:** ChatGPT and Gemini as their apps answer a person; Claude (with web search) and Perplexity through their APIs; Google's AI Overviews. The model that answered is in `answers.csv`. Asked once each, from the United States, in English, with Manifold's `aeo_run_ai_answers` tool.
- **Named:** a brand is named when its pattern in `brands.csv` matches the answer with links, images and bare URLs taken out. A brand the prompt itself names is skipped for that prompt. A platform's own name (Google, Reddit, LinkedIn) is not a brand; its own MCP server is, where the answer calls it the official one. `place` is the brand's order among the brands the answer names.
- **Cited:** a brand is cited when the answer links a page on one of its `sites` (or a subdomain).
- **Limits:** AI answers change from day to day, and each prompt is asked once per engine per run. Brands outside `brands.csv` are not counted, but the full answers are here to count them yourself.

## Missing a brand?

Open an issue with the brand's name and site. It will be counted from the next run.

## Licence and citation

The data is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Please cite it as:

> Manifold AI Recommendation Index, October 2026. https://www.manifoldmcp.com/blog/ai-recommendation-index

The answers are the engines' own words, recorded for research and comment.
