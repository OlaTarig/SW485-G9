# SW485-G9
**Movie Recommendation System**<br>
*Team Members*:<br>
Ola Mahjob 444204643 <br>
Sidrah Almazlom 444200106<br>
Roha alswoaiegh 444200551<br>
Shaden Almasaud 444200857<br>
Layan Almasoud 444200636<br>


---

## **Problem Definition**

### **1. Overview**

The goal of this project is to design and develop a hybrid movie recommendation system that leverages both **content-based filtering** (unsupervised learning) and **supervised learning** techniques to enhance personalization and prediction accuracy. The system aims to recommend movies that align closely with a user’s preferences, either inferred from movie metadata or learned from user interaction data.

---
### **2. Motivation**

We chose this topic because movie recommendation systems are fun to explore and highly relatable. Everyone interacts with them daily on platforms and they play a huge role in shaping what users watch, listen to, or buy. We wanted to understand how these systems work under the hood, especially how algorithms can “learn” what users might enjoy next.

Another motivation is our interest in Natural Language Processing (NLP). Since movie descriptions (plots) are textual data, they provide a perfect opportunity to explore how NLP can be used to capture the meaning and similarity between movies.

We also selected this particular movie dataset because it provides both the scale and richness needed for this kind of analysis:

It contains around 45,000 movies, covering a wide variety of genres and languages.

It includes approximately 27 million user ratings, making it suitable for supervised learning and preference prediction.

It provides detailed movie metadata such as genres, and plot descriptions—ideal for NLP-based similarity computations.

---

### **3. Phase 1: Supervised Learning Recommendation**

The first phase introduces a **supervised learning** component to enhance personalization by incorporating user-specific information.
This model will **only use the user ID** as input. The model will learn the **relationship between users and their preferences**, leveraging patterns in the user’s past ratings to predict their future movie interests.

#### **Input**

* **User ID** only (Users Who are already Registered in thae dataset).

#### **Data Features**

* A merged dataset combining:

  * **User ratings dataset** — containing records of users, movies they have rated and the ratings they have assigned to movies.
  * **Movie dataset** — providing metadata (genre, cast, description) that helps represent movies as feature vectors.

#### **Methodology**

* The system learns a **mapping from user IDs to predicted movie preferences**.
* It captures latent user features using embedding or vector representation (e.g., through neural collaborative filtering or matrix factorization-inspired techniques).
* Given a user ID, the model predicts the **expected rating** or **preference score** as a number from 1 to 5 for each movie in the dataset.
* The model then ranks movies that the user has not yet rated, based on predicted ratings.

#### **Output**

* A personalized list of 10 recommended movies that the user has not watched before, ranked by the **highest predicted rating**.

This represents a **supervised learning** approach because the model is trained on labeled data, in this case, the known user ratings to learn patterns that predict unseen ratings.

---


### **4. Phase 2: Content-Based Recommendation (Unsupervised Learning)**

In the second phase, the system focuses on **content-based filtering**, where recommendations are generated based on the similarity between movies themselves without requiring any user feedback or rating data.

#### **Input**

* The **name of a movie** provided by the user.

#### **Data Features**

* Movie **metadata**, including:

  * **Genre**
  * **Cast**
  * **Plot description (overview)** — used extensively through **Natural Language Processing (NLP)** techniques such as TF-IDF or embeddings to represent the semantic meaning of the movie.

#### **Methodology**

* Each movie’s metadata is converted into a feature vector.
* The system computes pairwise **similarity scores** (e.g., cosine similarity) between the input movie and all others in the dataset.
* Based on the computed similarity values, the system identifies and ranks the top **10 most similar movies**.

#### **Output**

* A ranked list of 10 movies most similar to the one entered by the user.

This phase represents an **unsupervised learning** approach because it does not rely on labeled data (ratings or user preferences) — instead, it clusters and ranks items purely based on their inherent attributes and relationships in the feature space.

---

### **5. Objectives**

1. **Supervised Phase:**

   * To predict user-specific preferences using only the user ID as input.
   * To provide personalized movie recommendations based on predicted ratings for unseen movies.
   * To evaluate the model’s performance using appropriate supervised metrics (e.g., RMSE, MAE).


2. **Unsupervised Phase:**

   * To generate recommendations based solely on movie similarity derived from content features.
   * To evaluate how well content attributes (especially plot similarity) can predict related movies.

---

### **6. Significance**

By integrating both approaches:

* The **unsupervised model** offers recommendations for new users or movies (cold start situations).
* The **supervised model** provides personalized recommendations for existing users, improving relevance and engagement.
