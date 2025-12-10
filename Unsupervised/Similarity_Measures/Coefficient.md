# Similarity Measures: Coefficients

In Information Retrieval, **Similarity Coefficients** determine how much two objects (like a search query and a document) resemble each other. Unlike distance metrics (where 0 is best), these coefficients usually range from **0 to 1**:

* **1.0**: The objects are identical.
* **0.0**: The objects are completely different.

## The Two Perspectives: Sets vs. Vectors

To truly understand these formulas, it helps to see them from two angles:

1. **Set Notation (Simple):** Treating documents as simple bags of words (Present/Absent).
2. **Vector Notation (Advanced):** Treating documents as weighted vectors (e.g., using TF-IDF weights), where $w_{kq}$ is the weight of term $k$ in the query and $w_{kj}$ is the weight in document $j$.

## 1. Dice Coefficient (Sørensen–Dice index)

The Dice coefficient focuses on the intersection (matches) and gives it **double weight**. It is "optimistic" because it emphasizes what is shared rather than what is different.

### Set Formula

$$Sim_{Dice}(A, B) = \frac{2 |A \cap B|}{|A| + |B|}$$

* **Concept:** Twice the intersection divided by the sum of the sizes.

### Vector Formula

$$sim(q, d_j) = \frac{\sum_{k=1}^n w_{kq} w_{kj}}{\alpha \sum_{k=1}^n w_{kq}^2 + (1-\alpha) \sum_{k=1}^n w_{kj}^2} \quad (\text{typically } \alpha = 0.5)$$

* **Deep Dive:** When $\alpha = 0.5$, the denominator becomes the **Arithmetic Mean** of the two vector lengths. This balances the importance of the query and document equally.

## 2. Jaccard Similarity

Also known as **Intersection over Union (IoU)**, this is the "pessimistic" metric. It is stricter than Dice because it penalizes unique terms (differences) more heavily.

### Set Formula

$$Sim_{Jaccard}(A, B) = \frac{|A \cap B|}{|A \cup B|} = \frac{|A \cap B|}{|A| + |B| - |A \cap B|}$$
* **Concept:** Intersection divided by the Union.

### Vector Formula

$$sim(q, d_j) = \frac{\sum_{k=1}^n w_{kq} w_{kj}}{\sum_{k=1}^n w_{kq}^2 + \sum_{k=1}^n w_{kj}^2 - \sum_{k=1}^n w_{kq} w_{kj}}$$

* **Deep Dive:** The denominator represents the **Union** of the weights. Since the Union is always larger than the Average (Dice) or the Geometric Mean (Cosine), Jaccard typically produces the lowest score among these coefficients.

## 3. Overlap Coefficient (Szymkiewicz–Simpson)

This coefficient measures containment. It checks if the smaller set is "inside" the larger set.

### Set Formula

$$Sim_{Overlap}(A, B) = \frac{|A \cap B|}{\min(|A|, |B|)}$$

* **Concept:** Intersection divided by the size of the smaller set.

### Vector Formula

$$sim(q, d_j) = \frac{\sum_{k=1}^n w_{kq} w_{kj}}{\min\left(\sum_{k=1}^n w_{kq}^2, \sum_{k=1}^n w_{kj}^2\right)}$$

* **Deep Dive:** If the query is fully contained within the document (even if the document has 1,000 other irrelevant words), the score is **1.0**. This makes it ideal for matching specific queries against long, diverse documents.

## 4. Cosine Similarity
This is the industry standard for text analysis. It measures the angle between two vectors, effectively ignoring the length (magnitude) of the documents.

### Set Formula

$$Sim_{Cosine}(A, B) = \frac{A \cdot B}{||A|| \cdot ||B||}$$

### Vector Formula

$$sim(q, d_j) = \frac{\sum_{k=1}^n w_{kq} w_{kj}}{\sqrt{\sum_{k=1}^n w_{kq}^2 \sum_{k=1}^n w_{kj}^2}}$$
* **Deep Dive:** The denominator is the **Geometric Mean** of the lengths. This makes the metric **Length-Invariant**. A short summary and a long book on the same topic will have a high similarity score because they point in the same "direction."

## 5. Asymmetric Similarity

Most similarity measures are symmetric ($Sim(A, B) = Sim(B, A)$). However, sometimes we need to know how much of A (Query) is covered by B (Document), ignoring the rest of B.

### Set Formula

$$Sim_{Asym}(A, B) = \frac{|A \cap B|}{|A|}$$

### Vector Formula

$$sim(q, d_j) = \frac{\sum_{k=1}^n \min(w_{kq}, w_{kj})}{\sum_{k=1}^n w_{kq}}$$

* **Deep Dive:** This is essentially **Recall** relative to the query weights. If the query consists of binary terms, this calculates exactly what percentage of the query terms appear in the document.

### Summary: The Denominator Difference

While all formulas use the same Numerator (the match), they differ in how they **Normalize** (the denominator):

| Measure | Normalization Strategy | Effect |
| :--- | :--- | :--- |
| **Dice** | Arithmetic Mean ($0.5A + 0.5B$) | **Optimistic:** Gives more weight to matches. |
| **Jaccard** | Union ($A + B - Match$) | **Pessimistic:** Penalizes differences heavily. |
| **Overlap** | Minimum ($\min(A, B)$) | **Inclusive:** Scores 1.0 if one is a subset of the other. |
| **Cosine** | Geometric Mean ($\sqrt{A \cdot B}$) | **Balanced:** Ignores document length differences. |
| **Asymmetric**| Query Sum ($A$) | **One-sided:** Measures coverage of the query only. |
