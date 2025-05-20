    # IL-PCSR: Legal Corpus for Prior Case and Statute Retrieval (Sample Dataset)
This is a 5% sample of the IL-PCSR dataset. It has 313 queries , 159 precedents and 46 statutes.
---

## Dataset Overview

### Files and Their Contents

1. **Metadata File**
   - **`metadata.json`**:  
     This file maps query IDs to their associated precedent and section IDs.  
     - **Keys**:
       - `query`: List of query IDs.
       - `precs`: List of precedent IDs.
       - `secs`: List of  statute IDs.

2. **Gold Standard File**
   - **`gold.json`**:  
     This file provides the ground truth citations for each query.  
     - **Structure**:
       ```json
       {
         "query_id": {
           "precs": [list of cited precedent IDs],
           "secs": [list of cited section IDs]
         }
       }
       ```

3. **Text Files**  
   These files contain the full text of queries, precedents, and statute , structured by paragraphs.
   - **`queries.json`**:  
     Maps query IDs to their paragraphs.
     - **Format**:
       ```json
       {
         "query_id": [
           [rhetorical_role, paragraph_text],
           ...
         ]
       }
       ```
   - **`precedents.json`**:  
     Maps precedent IDs to their paragraphs, similar to `queries.json`.
   - **`statutes.json`**:  
     Maps  statute IDs to their paragraphs, similar to `queries.json`.

---

## How to Use the Dataset

### Understanding Metadata
- Use `metadata.json` to determine the list of all precedents (`precs`) and statute (`secs`) .
- **Example**:  
  For a query ID `Q1`, retrieve the associated precedents and statute from .

### Evaluating Against Ground Truth
- Use `gold.json` to get the ground truth citations (both precedents and statute) for a given query.
- **Example**:  
  For a query ID `Q1`, verify retrieved precedents and statute against `gold.json`.

### Accessing Text Data
- Use `queries.json`, `precedents.json`, and `statutes.json` to get the full text for queries, precedents, and statute respectively.
- Each text entry is an array of paragraphs, where each paragraph includes:
  - **Rhetorical Role**: The legal context or role of the paragraph (e.g., "Issue", "Facts").
  - **Paragraph Text**: The full text of the paragraph.
