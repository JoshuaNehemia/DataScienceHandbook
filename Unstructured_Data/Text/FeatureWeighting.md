# Feature Weighting

In the world of data science, text is notoriously difficult to manage. Unlike a neat Excel spreadsheet with defined rows and columns, text data is unstructured.

Comparing two documents to see if they are "similar" is a complex task because computers cannot inherently understand meaning. They only understand numbers. Even after pre-processing (removing stop words, stemming, etc.), we are left with a massive collection of words that need to be quantified before any comparison can take place.

## The Solution: Feature Weighting

To solve the problem of unstructured comparison, we use Feature Weighting. This process involves converting raw data into a numerical representation that a machine can process.

### What is a Feature?

* In Text Processing, a feature is usually a Term (a specific word or phrase).
* In Image Processing, a feature might be the value of an object, such as an RGB pixel value.

The Purpose: The goal of feature weighting is to assign a numerical value to these features to determine how well they represent the content of a document. A word that appears once might carry less weight (importance) than a word that appears ten times.

## TF-IDF

**TF-IDF (term frequency–inverse document frequency)** is a measure of importance of a word to a document in a collection or corpus, adjusted for the fact that some words appear more frequently in general. Like the bag-of-words model, it models a document as a multiset of words, without word order. It is a refinement over the simple bag-of-words model, by allowing the weight of words to depend on the rest of the corpus.

## Term Frequency (TF)

Term frequency, denoted as $tf(t,d)$, measures the relative frequency of a term $t$ within a specific document $d$.

The most common normalized formula is:

$$tf(t,d) = \frac{f_{t,d}}{\sum_{t' \in d} f_{t',d}}$$

Where:

* $f_{t,d}$ is the **raw count** (the number of times term $t$ appears in document $d$).
* The denominator $\sum_{t' \in d} f_{t',d}$ represents the **total number of terms** in document $d$.

### Variations of Term Frequency

Depending on the specific algorithm or use case, there are several other ways to define Term Frequency:

**1. Raw Count**
The simplest method, using only the count itself without normalization.
$$tf(t,d) = f_{t,d}$$

**2. Boolean Frequencies**
Used when we only care about presence, not quantity (e.g., simple keyword matching).
$$tf(t,d) = \begin{cases} 1 & \text{if } t \text{ occurs in } d \\ 0 & \text{otherwise} \end{cases}$$

**3. Logarithmic Scaled Frequency**
This is used to reduce the impact of words that appear very frequently, ensuring they don't overpower the results.
$$tf(t,d) = \log(1 + f_{t,d})$$

**4. Augmented Frequency**
This variation is designed to prevent bias towards longer documents. It standardizes the score by dividing the raw frequency by the frequency of the most common word in that document.

$$tf(t,d) = 0.5 + 0.5 \cdot \frac{f_{t,d}}{\max\{f_{t',d} : t' \in d\}}$$

## Inverse Document Frequency (IDF)

While Term Frequency (TF) counts how many times a word appears in a specific document, **Inverse Document Frequency (IDF)** looks at the entire collection of documents (the corpus).

IDF is a measure of how much information a word provides. It operates on the principle that:

* **Common words** (like "the", "is", "and") appear in many documents and carry **less information**.

* **Rare words** (like "microprocessor", "photosynthesis") appear in fewer documents and carry **more information**.

Mathematically, IDF is the logarithmically scaled inverse fraction of the documents that contain the word.

$$idf(t, D) = \log \frac{N}{n_t}$$

Where:

* $N$: The total number of documents in the corpus ($N = |D|$).
* $n_t$: The number of documents where the term $t$ appears ($n_t = |\{d \in D : t \in d\}|$).

If a term is not found in the corpus, $n_t$ would be 0, leading to a division-by-zero error. To prevent this, it is common to apply **smoothing**. This is done by adjusting the numerator to $1+N$ and the denominator to $1+n_t$, effectively behaving as if there is one extra document containing every term.

There are several variations for calculating IDF depending on the specific information retrieval needs.

| Weighting Scheme | IDF Weight Formula |
| :--- | :--- |
| **Unary** | $1$ |
| **Inverse Document Frequency** | $\log \frac{N}{n_t} = -\log \frac{n_t}{N}$ |
| **IDF Smooth** | $\log \left( \frac{N}{1 + n_t} \right) + 1$ |
| **IDF Max** | $\log \left( \frac{\max_{\{t' \in d\}} n_{t'}}{1 + n_t} \right)$ |
| **Probabilistic IDF** | $\log \frac{N - n_t}{n_t}$ |

## TF-IDF (Term Frequency-Inverse Document Frequency)

The **TF-IDF** score represents the weight of a term in a document relative to the entire corpus. It is calculated by multiplying the Term Frequency by the Inverse Document Frequency.

### The Formula

$$tfidf(t, d, D) = tf(t, d) \cdot idf(t, D)$$

Where:

* $tf(t, d)$: How often term $t$ appears in document $d$.
* $idf(t, D)$: How rare term $t$ is across the entire document set $D$.

### Understanding the Score

The logic behind the score can be broken down into three key behaviors:

1. **High Weight:**
    A high TF-IDF score is achieved when a term has a **high frequency** in the specific document (high TF) but a **low frequency** in the collection overall (high IDF). This identifies words that are significant and unique to that specific document.

2. **Filtering Common Terms:**
    As a term appears in more documents, the ratio inside the IDF logarithm approaches 1. Since $\log(1) = 0$, the IDF component—and consequently the total TF-IDF score—approaches **0**. This effectively filters out non-descriptive words like "the," "is," or "and."

3. **Mathematical Bounds:**
    * Since the ratio inside the IDF log function is always $\ge 1$ (because total documents $N \ge$ documents with term $n_t$), the value of IDF is always non-negative.
    * Therefore, **$tfidf \ge 0$**.
