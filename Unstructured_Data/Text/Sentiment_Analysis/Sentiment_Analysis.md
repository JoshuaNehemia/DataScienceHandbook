# Sentiment Analysis

**Sentiment analysis**—also referred to as **opinion mining** or **emotion AI**—is the systematic identification, extraction, quantification, and study of affective states and subjective information. It leverages a multidisciplinary approach combining:

* **Natural Language Processing (NLP)**
* Text Analysis
* Computational Linguistics
* Biometrics

This discipline is widely applied to **Voice of the Customer** materials (reviews, survey responses), online social media content, and healthcare materials. Its utility spans diverse sectors, ranging from marketing strategies and customer service to clinical medicine.

## 1. Classification Types and Levels

The fundamental task in sentiment analysis is determining the sentiment orientation of a text.
[Learn more about classification]().

### Polarity Classification

The most basic form of analysis classifies a text as **Positive**, **Negative**, or **Neutral**. This can be performed at various levels of granularity:

* **Document Level:** Analyzing the sentiment of the entire text.
* **Sentence Level:** Analyzing sentiment sentence-by-sentence.
* **Feature/Aspect Level:** Determining sentiment regarding specific entities or attributes within the text.

### Beyond Polarity (Emotion Detection)

Advanced sentiment classification moves beyond simple binary polarity to identify specific emotional states, including **enjoyment, anger, disgust, sadness, fear, and surprise**.

### Specialized Variations

There are several other distinct types of analysis, including:

* **Aspect-based Sentiment Analysis:** Focusing on specific components (e.g., a phone's battery vs. its screen).
* **Grading Sentiment Analysis:** Utilizing scales (positive, negative, neutral).
* **Multilingual Sentiment Analysis:** Processing text across different languages.
* **Detection of Emotions:** Strictly identifying emotional responses.

## 2. Historical Evolution and Key Research

The field has evolved from psychological pattern recognition to complex computational algorithms.

* **Early Precursors:** The **General Inquirer** provided early methods for quantifying text patterns. Separately, psychological research focused on deducing a person's psychological state via the analysis of their verbal behavior.

* **Lexical & Emotional Scaling (Volcani & Fogel):** A patent by Volcani and Fogel introduced a method to identify words and phrases regarding different emotional scales. A modern system based on this, **EffectCheck**, provides synonyms to adjust the level of evoked emotion on these scales.

* **Document-Level Polarity (Turney & Pang):** Subsequent efforts focused on a "mere polar view" (positive vs. negative). **Turney** and **Pang** applied distinct methods to detect polarity in product and movie reviews, respectively.

* **Multi-way Scaling (Pang, Lee, & Snyder):** Research expanded to predict granular ratings. **Pang and Lee** moved beyond binary classification to predict star ratings (3- or 4-star scales). **Snyder** performed in-depth analysis of restaurant reviews, predicting ratings for specific aspects like food and atmosphere on a five-star scale.

* **The 2004 AAAI Spring Symposium:** This event marked the unification of various approaches (learning, lexical, knowledge-based). Linguists and computer scientists aligned interests, proposing shared tasks and benchmark data sets for systematic research on affect, subjectivity, and sentiment.

## 3. The Neutral Class and Statistical Classifiers

A critical debate in sentiment analysis is the handling of **Neutral** sentiment. While some statistical methods ignore the neutral class (assuming it lies on the boundary of a binary classifier), evidence suggests that treating it as a distinct third category improves accuracy.

### Benefits of the Neutral Class

Specific classifiers, such as **Maximum Entropy (Max Entropy)** and **Support Vector Machines (SVMs)**, can demonstrate improved overall classification accuracy when a neutral class is introduced.

### Operational Approaches

There are two primary methods for handling neutrality:

1. **Filtering:** The algorithm identifies and filters out neutral language first, then assesses the remaining text for positive or negative sentiment.

2. **3-Way Classification:** The algorithm builds a classification for all three categories in one step. This often involves estimating a probability distribution (e.g., **Naive Bayes classifiers** as implemented by the NLTK).

**Selection Strategy:**

* **If data is clearly clustered** (distinct neutral, positive, and negative groups), filtering is effective.
* **If data is mostly neutral** with small deviations toward positive/negative, filtering becomes difficult, and distinguishing between the poles is harder.

## 4. Scaling Systems and Contextual Scoring

A different methodological approach involves quantitative scaling rather than categorical classification.

### Scoring Mechanisms

Words associated with sentiment are assigned a numerical value, such as:

* A **-10 to +10** scale (Most Negative to Most Positive).
* A **0 to +4** scale.

### Contextual Adjustments

Using Natural Language Processing, unstructured text is analyzed to score concepts based on their environment. This allows for a sophisticated understanding of sentiment where the score of a concept is adjusted by surrounding modifications.

* **Modifiers:** Words that **intensify**, **relax**, or **negate** sentiment will alter the score of the concept they accompany.
* **Strength Scoring:** Alternatively, texts can be assigned separate positive *and* negative strength scores to determine the presence of sentiment, rather than just an overall polarity.
