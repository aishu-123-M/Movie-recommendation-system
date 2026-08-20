# 🎬 Movie Recommendation System

An AI-powered **Movie Recommendation System** that generates personalized movie suggestions based on a user's recently watched movies.

The project compares two NLP-based approaches — **Word2Vec** and **Sentence Transformers** — to determine which embedding technique provides more accurate and context-aware recommendations.

## 📌 Project Overview

The OTT platform **Streamora** currently recommends movies based on titles, descriptions, and genres. However, many users ignore these recommendations and manually search for movies.

This project aims to improve movie discovery by developing an AI-based recommendation system that understands the **semantic meaning and context of movie information** and generates personalized recommendations based on a user's viewing history.

The system analyzes movie metadata and recent viewing history to recommend movies that are semantically similar to the user's interests.

---

## 🎯 Objectives

* Build an NLP-based movie recommendation system.
* Analyze movie titles, genres, and descriptions.
* Generate numerical embeddings for movie information.
* Compare **Word2Vec** and **Sentence Transformer** approaches.
* Evaluate recommendation success using historical viewing data.
* Select the better-performing model.
* Deploy the recommendation system using an interactive **Gradio interface**.

---

## 📊 Dataset

The project uses two datasets:

### Movie Dataset

Contains information about movies:

| Column     | Description                              |
| ---------- | ---------------------------------------- |
| `title`    | Name of the movie                        |
| `genres`   | Genres associated with the movie         |
| `overview` | Short description of the movie storyline |

### Evaluation Dataset

Contains historical user viewing information:

| Column                | Description                                 |
| --------------------- | ------------------------------------------- |
| `movie_1` – `movie_7` | Recently watched movies                     |
| `date`                | Recommendation/evaluation date              |
| `movie_watch`         | Movie actually watched after recommendation |

The evaluation data contains approximately **11 months of viewing history**.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas** – Data manipulation and preprocessing
* **NumPy** – Numerical operations
* **Gensim** – Word2Vec model
* **Sentence Transformers** – Semantic text embeddings
* **Scikit-learn** – Cosine similarity
* **Matplotlib** – Data visualization
* **Gradio** – Interactive deployment
* **Google Colab** – Development environment

---

## 🧠 Recommendation Approaches

### 1. Word2Vec

Word2Vec is used to create word-level embeddings from movie metadata.

The movie's:

* Title
* Genres
* Overview

are combined and tokenized before training the Word2Vec model.

The model configuration includes:

```text
vector_size = 100
window = 5
min_count = 1
workers = 4
seed = 42
```

The embeddings of the user's recently watched movies are averaged to create a representation of the user's overall movie preference.

Cosine similarity is then used to identify similar movies.

### Word2Vec Result

The Word2Vec approach achieved an overall recommendation success rate of approximately:

**22.7%**

This showed moderate performance but had difficulty understanding deeper movie context and user preferences.

---

## 🤖 2. Sentence Transformer

The second approach uses a pretrained Sentence Transformer model:

```text
all-MiniLM-L6-v2
```

Movie title, genres, and overview are combined into a single text representation.

The Sentence Transformer converts this text into a dense semantic embedding.

The system then:

1. Generates embeddings for movies.
2. Generates embeddings for recently watched movies.
3. Calculates the average embedding of watched movies.
4. Computes cosine similarity against all movie embeddings.
5. Removes already watched movies.
6. Returns the top 10 recommendations.

### Sentence Transformer Result

The Sentence Transformer achieved an overall recommendation success rate of:

**64.75%**

It also maintained a monthly success rate of approximately **62%–68%**.

This significantly outperformed the Word2Vec approach.

---

## 📈 Model Comparison

| Model                | Approach                         | Success Rate |
| -------------------- | -------------------------------- | -----------: |
| Previous Model       | Existing recommendation approach |       13.85% |
| Word2Vec             | Word-level embeddings            |        22.7% |
| Sentence Transformer | Contextual semantic embeddings   |   **64.75%** |

### 🏆 Best Model

**Sentence Transformer (`all-MiniLM-L6-v2`)**

The Sentence Transformer performed significantly better because it captures the **contextual and semantic meaning** of movie information rather than relying only on individual word relationships.

---

## 📌 Key Findings

* The previous recommendation approach achieved only **13.85%** success.
* Word2Vec improved the performance to approximately **22.7%**.
* Sentence Transformer significantly improved performance to **64.75%**.
* Sentence-level embeddings captured movie context more effectively.
* The Sentence Transformer maintained relatively consistent monthly performance.
* The final system provides personalized recommendations through an interactive Gradio interface.

---
## ⭐ Conclusion

The project successfully demonstrates how **semantic embeddings can improve content-based movie recommendation systems**.

Among the approaches tested, the **Sentence Transformer model achieved the best performance with a 64.75% recommendation success rate**, substantially outperforming both the previous model and the Word2Vec approach.

The final solution combines NLP, semantic similarity, and an interactive Gradio interface to provide a practical personalized movie recommendation experience.
