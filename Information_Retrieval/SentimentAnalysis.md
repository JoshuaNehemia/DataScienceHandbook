##  Sentiment Analysis

In the vast ocean of digital data, understanding *what* is being said is relatively easy for computers. Understanding *how* it is meant—the emotion, the attitude, and the underlying opinion—is a far more complex challenge. [cite_start]This field, known as Sentiment Analysis, stands at the intersection of Natural Language Processing (NLP) and psychology, aiming to translate human feelings into binary logic[cite: 14].

### The Core Objective: Opinion Mining
At its heart, Sentiment Analysis (often called opinion mining) is about determining the emotional tone behind a series of words. [cite_start]It analyzes opinions, evaluations, and attitudes towards specific entities—be they products, services, or events[cite: 15]. [cite_start]The goal is simple yet profound: to classify a statement, such as a movie review or a tweet, into distinct categories like positive or negative[cite: 14, 21].

### The Workflow: From Training to Prediction
[cite_start]The magic of Sentiment Analysis does not happen spontaneously; it is a disciplined two-step process involving **Training** and **Prediction**[cite: 18].

1.  **The Training Phase:** This is where the machine "learns." [cite_start]We feed the algorithm labeled data—text that has already been identified as positive or negative by humans[cite: 21]. [cite_start]A feature extractor processes this input, converting text into a format the machine learning algorithm can digest[cite: 18].
2.  **The Prediction Phase:** Once the model is trained, it enters the real world. New, unlabeled input is fed into the system. [cite_start]The feature extractor does its work, and the classifier model outputs a predicted label based on what it learned previously[cite: 18].


> **The Human Element:** It is crucial to note that the training phase relies heavily on human input. [cite_start]Labeling is a manual process[cite: 22]. [cite_start]The accuracy of the machine is directly largely dependent on the human ability to correctly categorize the initial training data[cite: 22].

### The Algorithms: Choosing the Right Tool
To classify these sentiments, we rely on Machine Learning methods. [cite_start]Unlike **Clustering** (unsupervised learning), which groups data based on structure without labels, **Classification** (supervised learning) assigns specific labels to new data points based on rules derived from labeled examples[cite: 36].

Two prominent methods dominate this introductory landscape:

#### 1. K-Nearest Neighbor (KNN)
[cite_start]KNN operates on a logic similar to a democratic voting system[cite: 40]. When a new piece of data is introduced, the algorithm looks at its "closest neighbors" (K) in the data space.
* [cite_start]**The Rule:** If the majority of the nearest neighbors are positive, the new data is classified as positive[cite: 40].
* [cite_start]**The Mechanism:** It calculates the distance (often Euclidean) between the new test data and the existing training data[cite: 44].
* [cite_start]**The Variable:** The user defines 'K', the number of neighbors to check[cite: 44].


#### 2. Naive Bayes
[cite_start]Naive Bayes takes a probabilistic approach based on the Bayes Theorem[cite: 72].
* [cite_start]**The Assumption:** It assumes that every attribute (or word) is independent of the others[cite: 72].
* [cite_start]**The Math:** It calculates the probability of a sentiment class given the presence of specific words[cite: 72]. [cite_start]For example, it calculates the probability that a chat containing the words "barang mantap sekali" (goods are very steady/good) is Positive versus Negative[cite: 105, 107].
* [cite_start]**The Result:** The class with the highest probability wins. in one example, a positive probability of `210/407484` outweighed a negative probability of `0`, resulting in a positive classification[cite: 106, 108, 109].

### Implementation: Theory into Code
The transition from theory to application is seamless in modern programming environments. [cite_start]Whether using PHP with libraries like `Phpml` [cite: 51] [cite_start]or Python with `sklearn` and `pandas`[cite: 63], the logic remains consistent.

The process involves:
1.  [cite_start]**Vectorization:** Converting text into numerical values (like TF-IDF)[cite: 51, 63].
2.  [cite_start]**Training:** Fitting the model with data (e.g., `train($chats, $labels)`)[cite: 53].
3.  [cite_start]**Prediction:** asking the model to label new input[cite: 53].

Interestingly, different algorithms may yield different results. [cite_start]In a sample test, the phrase "Thanks God" was labeled **Positive** by both KNN and Naive Bayes[cite: 125]. [cite_start]However, a more colloquial negative phrase ("Fuck this exam") was correctly identified as **Negative** by KNN, while Naive Bayes labeled it **Positive** in a specific Python implementation run[cite: 125, 128]. This highlights the importance of testing and selecting the right model for your specific dataset.

---

### **Departmental Announcements**

* **Schedule Change:** The NAS Quiz has been moved to **Week 13**. [cite_start]It will cover material from Week 9 through 12[cite: 135].
* [cite_start]**Week 11 Update:** There will be no offline class for Week 11. It will be replaced by a learning video, with details to be shared via Google Space[cite: 136, 137].

---
**Would you like me to generate a Python code snippet using the `sklearn` library to demonstrate a simple comparison between KNN and Naive Bayes on a small custom dataset?**