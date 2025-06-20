# Song Content Moderation with BERT Embeddings

This notebook implements a simple semantic similarity-based content moderation tool using BERT embeddings and t-SNE visualization.

---

## 🛠️ Setup and Dependencies

- Installs required packages:
  - `transformers`
  - `torch`
  - `scikit-learn`
- Suppresses warnings
- Imports necessary libraries (NumPy, Matplotlib, etc.)

---

## 🧠 Core Functions

### `tsne_plot(data, plot)`
- Visualizes high-dimensional embeddings using 3D t-SNE.
- Reduces BERT embeddings to 3 components.
- Displays colored scatter points with labels.

---

### `aggregate_embeddings(input_ids, attention_masks, bert_model)`
- Passes tokenized text through BERT.
- Uses attention masks to ignore padding.
- Applies mean pooling across valid tokens.
- Returns sentence-level embeddings.

---

### `text_to_emb(list_of_text, max_input=512)`
- Tokenizes raw text with the BERT tokenizer.
- Calls `aggregate_embeddings()` to produce embeddings.

---

### `process_song(song)`
- Basic text cleanup:
  - Removes newlines
  - Removes single quotes from lyrics

---

### `RAG_QA(embeddings_questions, embeddings, n_responses=3)`
- Computes dot product similarity between questions and target embeddings.
- Retrieves top-N most similar predefined responses.
- Forms the core of the retrieval-based QA system.

---

## 🔄 Main Workflow

### 1. **Question Setup**
- Defines 8 predefined questions about:
  - Violence
  - Explicit language
  - Drug references
  - Child-appropriateness
  - Encouragement of positive values

---

### 2. **Response Templates**
- Defines corresponding "yes" statements for each question.
  - Example: "Yes, this song contains violent references."

---

### 3. **Song Analysis**
Analyzes multiple songs:
- `""` — Empty rage song (placeholder)
- `"Sunny Day (Sesame Street Theme)"` — Child-friendly
- `"Straight Outta Compton"` — Explicit content
- `"Barney & Friends Theme"` — Educational

---

### 4. **Embedding Generation**
- Converts all questions, responses, and songs into BERT embeddings using `text_to_emb()`.

---

### 5. **Visualization**
- Generates a 3D t-SNE plot to show the semantic distance between:
  - Questions
  - Songs
  - Predefined responses

---

### 6. **Content Classification**
- Uses `RAG_QA()` to match each song with the most semantically similar response.
- Automatically classifies song content with respect to child-appropriateness.

---

## ✅ Summary

This system functions as a lightweight content moderation tool that:
- Analyzes lyrics using BERT embeddings
- Matches them with safety-related criteria
- Automatically evaluates songs for child-friendliness using semantic similarity

---
