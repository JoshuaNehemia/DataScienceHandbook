# Cluster Labeling (UNFINISHED)

### 1. The "Difference from Mean" Method
The fastest way to understand a cluster is to compare its average behavior against the average behavior of the entire population.

* **Calculate the Global Mean:** What is the average age/income/spending for *everyone* in your dataset?
* **Calculate Cluster Means:** What is the average for *just* Cluster 0?
* **Compare:** Look for large deviations.
    * *Example:* If the global average age is 35, but Cluster 0's average is 65, "Age" is a defining feature for that cluster.
    * *Example:* If everyone buys bread, but Cluster 1 buys 5x more bread than average, that is a signal.

### 2. Visual Profiling (The Fingerprint)
Numbers in a table can be hard to read. Visualizing the "personality" of a cluster makes labeling much easier.

* **Snake Plots / Parallel Coordinates:** These plot the feature means for each cluster side-by-side. You can trace the line to see where a cluster spikes or dips.
* **Radar Charts (Spider Plots):** These are excellent for checking "all-round" performance. A large shape might indicate "Power Users," while a small shape might indicate "Inactive Users."



### 3. Identify "Paragons" (Representative Samples)
Don't just look at averages; look at the actual members.
* Find the data point that is closest to the **centroid** (the mathematical center) of the cluster.
* This specific row of data is the "Archetype."
* If you are clustering movies and the center of Cluster A is *The Godfather*, and the center of Cluster B is *Toy Story*, your labels become obvious (Crime/Drama vs. Family/Animation).

### 4. Use a Surrogate Model (Decision Trees)
If you are struggling to explain *why* the algorithm grouped points together, train a simple Decision Tree to predict the cluster labels (0, 1, 2) using your original features.
* The Decision Tree will generate rules like: *"If Income > $100k AND Age < 30, then Cluster 0."*
* These rules literally write the label for you: **"Young Wealthy Professionals."**

### Example Scenario: Customer Segmentation
Imagine you ran K-Means on a grocery store dataset and found 3 clusters. Here is how you label them:

| Feature | Global Avg | **Cluster A Avg** | **Cluster B Avg** | **Cluster C Avg** |
| :--- | :--- | :--- | :--- | :--- |
| **Age** | 35 | 22 | 45 | 65 |
| **Spend** | $100 | $20 | $250 | $80 |
| **Visits** | 4/mo | 1/mo | 10/mo | 8/mo |
| **Top Item** | Milk | Beer | Organic Meat | Cat Food |

**The Labeling Logic:**
* **Cluster A:** Young, low spend, low visits, buys beer. $\rightarrow$ Label: **"The Weekend Student"**
* **Cluster B:** Middle-aged, very high spend, frequent visits, buys premium food. $\rightarrow$ Label: **"The Big Spender Family"**
* **Cluster C:** Older, moderate spend, frequent visits, buys pet supplies. $\rightarrow$ Label: **"The Retired Pet Owner"**

### Summary Checklist for a Good Label
A good cluster label should be a **Persona**, not just a description.
* **Bad Label:** "Cluster with High Income and Low Age."
* **Good Label:** "Young Up-and-Comers."

---

**Next Step:** Would you like to see a **Python code snippet** that automatically generates this "Cluster vs. Global Average" table to help you label your data?