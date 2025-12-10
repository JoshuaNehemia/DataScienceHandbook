# Sentiment Analysis

**Sentiment analysis**—also referred to as **opinion mining** or **emotion AI**—is the systematic identification, extraction, quantification, and study of affective states and subjective information. It leverages a multidisciplinary approach combining:

* **Natural Language Processing (NLP)**
* Text Analysis
* Computational Linguistics
* Biometrics

This discipline is widely applied to **Voice of the Customer** materials (reviews, survey responses), online social media content, and healthcare materials. Its utility spans diverse sectors, ranging from marketing strategies and customer service to clinical medicine.

## Classification

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

### Neutral Class

A critical debate in sentiment analysis is the handling of **Neutral** sentiment. While some statistical methods ignore the neutral class (assuming it lies on the boundary of a binary classifier), evidence suggests that treating it as a distinct third category improves accuracy.

#### Benefits of the Neutral Class

Specific classifiers, such as **Maximum Entropy (Max Entropy)** and **Support Vector Machines (SVMs)**, can demonstrate improved overall classification accuracy when a neutral class is introduced.

#### Operational Approaches

There are two primary methods for handling neutrality:

1. **Filtering:** The algorithm identifies and filters out neutral language first, then assesses the remaining text for positive or negative sentiment.

2. **3-Way Classification:** The algorithm builds a classification for all three categories in one step. This often involves estimating a probability distribution (e.g., **Naive Bayes classifiers** as implemented by the NLTK).

**Selection Strategy:**

* **If data is clearly clustered** (distinct neutral, positive, and negative groups), filtering is effective.
* **If data is mostly neutral** with small deviations toward positive/negative, filtering becomes difficult, and distinguishing between the poles is harder.

### Subjectivity/Objectivity Identification

This task is commonly defined as classifying a given text (usually a sentence) into one of two classes: objective or subjective.[20] This problem can sometimes be more difficult than polarity classification.[21] The subjectivity of words and phrases may depend on their context and an objective document may contain subjective sentences (e.g., a news article quoting people's opinions). Moreover, as mentioned by Su,[22] results are largely dependent on the definition of subjectivity used when annotating texts. However, Pang[23] showed that removing objective sentences from a document before classifying its polarity helped improve performance.

Subjective and objective identification, emerging subtasks of sentiment analysis to use syntactic, semantic features, and machine learning knowledge to identify if a sentence or document contains facts or opinions. Awareness of recognizing factual and opinions is not recent, having possibly first presented by Carbonell at Yale University in 1979.[clarify]

The term objective refers to the incident carrying factual information.[24]

Example of an objective sentence: 'To be elected president of the United States, a candidate must be at least thirty-five years of age.'
The term subjective describes the incident contains non-factual information in various forms, such as personal opinions, judgment, and predictions, also known as 'private states'.[25] In the example down below, it reflects a private states 'We Americans'. Moreover, the target entity commented by the opinions can take several forms from tangible product to intangible topic matters stated in Liu (2010).[26] Furthermore, three types of attitudes were observed by Liu (2010), 1) positive opinions, 2) neutral opinions, and 3) negative opinions.[26]

Example of a subjective sentence: 'We Americans need to elect a president who is mature and who is able to make wise decisions.'
This analysis is a classification problem.[27]

Each class's collections of words or phrase indicators are defined for to locate desirable patterns on unannotated text. For subjective expression, a different word list has been created. Lists of subjective indicators in words or phrases have been developed by multiple researchers in the linguist and natural language processing field states in Riloff et al. (2003).[28] A dictionary of extraction rules has to be created for measuring given expressions. Over the years, in subjective detection, the features extraction progression from curating features by hand to automated features learning. At the moment, automated learning methods can further separate into supervised and unsupervised machine learning. Patterns extraction with machine learning process annotated and unannotated text have been explored extensively by academic researchers.

However, researchers recognized several challenges in developing fixed sets of rules for expressions respectably. Much of the challenges in rule development stems from the nature of textual information. Six challenges have been recognized by several researchers: 1) metaphorical expressions, 2) discrepancies in writings, 3) context-sensitive, 4) represented words with fewer usages, 5) time-sensitive, and 6) ever-growing volume.

Metaphorical expressions. The text contains metaphoric expression may impact on the performance on the extraction.[29] Besides, metaphors take in different forms, which may have been contributed to the increase in detection.
Discrepancies in writings. For the text obtained from the Internet, the discrepancies in the writing style of targeted text data involve distinct writing genres and styles.
Context-sensitive. Classification may vary based on the subjectiveness or objectiveness of previous and following sentences.[27]
Time-sensitive attribute. The task is challenged by some textual data's time-sensitive attribute. If a group of researchers wants to confirm a piece of fact in the news, they need a longer time for cross-validation, than the news becomes outdated.
Cue words with fewer usages.
Ever-growing volume. The task is also challenged by the sheer volume of textual data. The textual data's ever-growing nature makes the task overwhelmingly difficult for the researchers to complete the task on time.
Previously, the research mainly focused on document level classification. However, classifying a document level suffers less accuracy, as an article may have diverse types of expressions involved. Researching evidence suggests a set of news articles that are expected to dominate by the objective expression, whereas the results show that it consisted of over 40% of subjective expression.[24]

To overcome those challenges, researchers conclude that classifier efficacy depends on the precisions of patterns learner. And the learner feeds with large volumes of annotated training data outperformed those trained on less comprehensive subjective features. However, one of the main obstacles to executing this type of work is to generate a big dataset of annotated sentences manually. The manual annotation method has been less favored than automatic learning for three reasons:

Variations in comprehensions. In the manual annotation task, disagreement of whether one instance is subjective or objective may occur among annotators because of languages' ambiguity.
Human errors. Manual annotation task is a meticulous assignment, it require intense concentration to finish.
Time-consuming. Manual annotation task is an assiduous work. Riloff (1996) show that a 160 texts cost 8 hours for one annotator to finish.[30]
All these mentioned reasons can impact on the efficiency and effectiveness of subjective and objective classification. Accordingly, two bootstrapping methods were designed to learning linguistic patterns from unannotated text data. Both methods are starting with a handful of seed words and unannotated textual data.

Meta-Bootstrapping by Riloff and Jones in 1999.[31] Level One: Generate extraction patterns based on the pre-defined rules and the extracted patterns by the number of seed words each pattern holds. Level Two: Top 5 words will be marked and add to the dictionary. Repeat.
Basilisk (Bootstrapping Approach to Semantic Lexicon Induction using Semantic Knowledge) by Thelen and Riloff.[32] Step One: Generate extraction patterns. Step Two: Move best patterns from Pattern Pool to Candidate Word Pool. Step Three: Top 10 words will be marked and add to the dictionary. Repeat.
Overall, these algorithms highlight the need for automatic pattern recognition and extraction in subjective and objective task.[33]

Subjective and object classifier can enhance the several applications of natural language processing. One of the classifier's primary benefits is that it popularized the practice of data-driven decision-making processes in various industries. According to Liu, the applications of subjective and objective identification have been implemented in business, advertising, sports, and social science.[34]

Online review classification: In the business industry, the classifier helps the company better understand the feedbacks on product and reasonings behind the reviews.
Stock price prediction: In the finance industry, the classifier aids the prediction model by process auxiliary information from social media and other textual information from the Internet. Previous studies on Japanese stock price conducted by Dong et al. indicates that model with subjective and objective module may perform better than those without this part.[35]
Social media analysis.
Students' feedback classification.[36]
Document summarising: The classifier can extract target-specified comments and gathering opinions made by one particular entity.
Complex question answering. The classifier can dissect the complex questions by classing the language subject or objective and focused target. In the research Yu et al.(2003), the researcher developed a sentence and document level clustered that identity opinion pieces.[37]
Domain-specific applications.
Email analysis: The subjective and objective classifier detects spam by tracing language patterns with target words

## Continuous Metrics in Sentiment Analysis
