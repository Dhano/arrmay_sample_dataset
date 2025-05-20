# IL-PCSR: Legal Corpus for Prior Case and Statute Retrieval (10% Sample Dataset)

This is a sample of the IL-PCSR dataset, containing 10% of queries:

* **Query Judgments**: 62
* **Precedents**: 318
* **Statutes**: 218

---

## Dataset Overview

### Files and Their Contents

#### 1. **Metadata File**

* **`metadata.json`**
  Maps each query ID to its associated precedent and statute IDs.

  * **Keys**:

    * `query`: List of query IDs.
    * `precs`: List of associated precedent IDs.
    * `secs`: List of associated statute IDs.

#### 2. **Gold Standard File**

* **`gold.json`**
  Provides the ground truth (relevant citations) for each query.

  * **Format**:

    ```json
    {
      "query_id": {
        "precs": [list of relevant precedent IDs],
        "secs": [list of relevant statute IDs]
      }
    }
    ```

#### 3. **Text Files**

These contain full judgment texts for queries, precedents, and statutes, structured by paragraphs.

* **`queries.json`**
  Maps query IDs to an array of `[rhetorical_role, paragraph_text]` pairs.
* **`precedents.json`**
  Same format as `queries.json`, but for precedents.
* **`statutes.json`**
  Same format as above, but for statutes.

#### 4. **Summary Files**

* **`precedents_summaries.json`**
  Summarized version of precedents. Follows the same format as `precedents.json`, but the paragraphs are concise summaries.
* **`queries_summaries_for_precs.json`**
  Summarized queries tailored for precedent retrieval tasks. Same paragraph format as `queries.json`.
* **`queries_summaries_for_secs.json`**
  Summarized queries tailored for statute retrieval tasks. Same paragraph format as `queries.json`.

#### 5. **Citation Mapping**

* **`citations.json`**
  Maps each precedent ID to a list of statute IDs that are cited within that precedent.

  * **Format**:

    ```json
    {
      "precedent_id": [list of cited statute IDs]
    }
    ```

---

## How to Use the Dataset

### Exploring the Dataset

* Use `metadata.json` to list all available query, precedent, and statute IDs.
* Example: For a query `Q1`, retrieve associated precedents and statutes.

### Evaluating Retrieval

* Compare your system’s retrieved precedents and statutes with the gold labels in `gold.json`.

### Accessing Full Text

* Use `queries.json`, `precedents.json`, and `statutes.json` for full legal text broken down by paragraph and rhetorical role.
* Use the corresponding summaries (`*_summaries.json`) for summarized versions.

### Understanding Legal Citations

* Use `citations.json` to analyze how precedent cite statutes—helpful for modeling interlinkages between legal sources.
