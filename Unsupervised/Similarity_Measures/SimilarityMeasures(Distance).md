# Similarity Measures: Distance Metrics

Most common distance metrics belong to the **Minkowski Family**, which is a generalized way to calculate distance between two points (vectors) $X$ and $Y$ in a multi-dimensional space.

## 1. Minkowski Distance (The Generalization)

Minkowski distance is the generalized formula. By changing the value of the parameter $p$, we can derive the Manhattan, Euclidean, and Chebyshev distances.

$$D(X, Y) = \left( \sum_{i=1}^{n} |x_i - y_i|^p \right)^{\frac{1}{p}}$$

Where:
* $X$ and $Y$ are the two document vectors being compared.
* $n$ is the number of features (terms).
* $p$ is the order parameter.

## 2. Manhattan Distance ($L_1$ Norm)

Derived from Minkowski when **$p = 1$**.

Also known as "City Block" or "Taxicab" distance, this measures distance as if you were traveling along a grid of streets. You cannot go diagonally; you must move along the axes.

$$D_{Manhattan}(X, Y) = \sum_{i=1}^{n} |x_i - y_i|$$

* **Characteristics:** It is the sum of absolute differences. It is generally more robust to outliers than Euclidean distance for high-dimensional data (like text).


## 3. Euclidean Distance ($L_2$ Norm)

Derived from Minkowski when **$p = 2$**.

This is the standard "straight-line" distance that we learn in geometry (Pythagorean theorem). It measures the shortest path between two points "as the crow flies."

$$D_{Euclidean}(X, Y) = \sqrt{\sum_{i=1}^{n} (x_i - y_i)^2}$$

* **Characteristics:** It is very sensitive to large differences in a single dimension because it squares the differences. In text mining, it is often less effective than Cosine Similarity because it is sensitive to the length of the document (magnitude).

## 4. Chebyshev Distance ($L_\infty$ Norm)

Derived from Minkowski when **$p \to \infty$**.

Also known as "Chessboard" distance. It is defined as the greatest difference along any single dimension. Think of a King in chess: the number of moves needed to get to a square is determined by the longest axis difference.

$$D_{Chebyshev}(X, Y) = \max_{i} (|x_i - y_i|)$$

* **Characteristics:** It focuses entirely on the single feature where the two documents differ the most.

## 5. Canberra Distance

Canberra distance is a weighted version of the Manhattan distance. It is not part of the Minkowski family in the strict sense. It is strictly non-negative.

$$D_{Canberra}(X, Y) = \sum_{i=1}^{n} \frac{|x_i - y_i|}{|x_i| + |y_i|}$$

* **Characteristics:**

    * It is very sensitive to small changes near zero.
    * It treats each dimension equally regardless of its magnitude (scaling is built-in).
    * Often used when comparing ranked lists or data where the relative difference matters more than the absolute difference.
Yes, there are several other important distance metrics, particularly those highly relevant to **Information Retrieval** (text analysis) and **Categorical Data**.


## 6. Cosine Distance

While **Cosine Similarity** is the standard for text, **Cosine Distance** is used when we strictly need a "distance" value (where 0 is identical and 1 is max distance).

It measures the cosine of the angle between two vectors. It determines whether two documents point in the same "direction" (topic), regardless of their "magnitude" (document length).

$$D_{Cosine}(X, Y) = 1 - S_{Cosine}(X, Y) = 1 - \frac{X \cdot Y}{||X|| \cdot ||Y||}$$

* **Best Use Case:** Text mining and document clustering. It is superior to Euclidean distance for text because it ignores the fact that one document might be 10x longer than the other.

## 7. Jaccard Distance

Jaccard measures the **dissimilarity between sample sets**. It is calculated by subtracting the Jaccard Similarity coefficient from 1.

$$D_{Jaccard}(A, B) = 1 - \frac{|A \cap B|}{|A \cup B|}$$

* **Formula Logic:** $1 - (\text{Intersection} \div \text{Union})$.
* **Best Use Case:** Comparing binary vectors or "Bag of Words" models where we only care if a word exists (True/False), not how many times it appears.

## 8. Hamming Distance

Hamming distance measures the number of positions at which corresponding symbols are different between two strings or binary vectors of equal length.

$$D_{Hamming}(X, Y) = \sum_{i=1}^{n} |x_i - y_i|$$
*(For binary data, this is equivalent to the Manhattan distance)*

* **Example:**
  * String A: **101**1**1**01
  * String B: **100**1**0**01
  * Difference: The 3rd and 5th bits differ.
  * Distance: 2
* **Best Use Case:** Error correction, comparing hash values (SimHash), or spell checking.

## 9. Levenshtein Distance (Edit Distance)

Unlike the vector-based distances above, this is a **String Metric**. It calculates the minimum number of single-character edits (insertions, deletions, or substitutions) required to change one word into another.

* **Example:** Distance between "kitten" and "sitting" is 3.
    1. **k**itten $\to$ **s**itten (substitute 's' for 'k')
    2. sitt**e**n $\to$ sitt**i**n (substitute 'i' for 'e')
    3. sittin $\to$ sittin**g** (insert 'g')

* **Best Use Case:** Spell checking ("Did you mean..."), fuzzy string matching, and OCR correction.

## 10. Kullback-Leibler (KL) Divergence

Also known as "relative entropy," this measures how one probability distribution differs from a second, reference probability distribution.

$$D_{KL}(P || Q) = \sum_{x} P(x) \log \left( \frac{P(x)}{Q(x)} \right)$$

* **Note:** It is technically a "divergence," not a distance metric, because it is not symmetric (Distance from A to B $\neq$ Distance from B to A).
* **Best Use Case:** Probabilistic Information Retrieval and Language Models.
