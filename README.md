# Image Search System with Natural Language Query (No Metadata)

## 📖 Overview

This system enables users to perform natural language searches on a collection of images without relying on any pre-existing metadata. By leveraging state-of-the-art **CLIP-based embeddings**, the application matches text-based queries directly with visual content, making it ideal for scenarios where metadata is unavailable or incomplete.

### Key Features:
- **Natural Language Queries**: Users can search for images using everyday language (e.g., "blue sky with mountains" or "red sports car").
- **No Metadata Requirement**: Images are indexed directly using their visual features; no additional tagging or annotations are needed.
- **High Accuracy**: Uses **CLIP** embeddings to bridge the gap between text and images for accurate results.

---

## 🛠️ Technical Details

### Architecture:
1. **Data Preparation**:
   - Images are loaded from a specified directory (`data/`) and stored in Haystack's **In-Memory Document Store**.
   - Each image is indexed as a document with its content type set to `"image"`.

2. **Embeddings**:
   - Image and query embeddings are generated using the **CLIP ViT-B-32** model from `sentence-transformers`.
   - Embeddings are stored and updated in the document store for efficient retrieval.

3. **Search Pipeline**:
   - The **MultiModalRetriever** from Haystack processes user text queries and compares them with image embeddings to retrieve the most relevant matches.
   - Results are ranked based on similarity scores.

4. **Frontend Interface**:
   - **Streamlit** provides an intuitive interface for users to input queries and view results.
   - Top-ranked images are displayed alongside their relevance scores.

### Tech Stack:
- **Backend**: Python, Haystack, `sentence-transformers`.
- **Frontend**: Streamlit for interactive UI.
- **Embedding Models**: `sentence-transformers/clip-ViT-B-32`.
- **Storage**: In-Memory Document Store.

---

## 🏃‍♂️ How to Run

1. **Install Dependencies**:
   ```bash
   pip install streamlit haystack sentence-transformers
   ```

2. **Prepare Data**:
   - Place all images in the `data/` directory.

3. **Run the Application**:
   ```bash
   streamlit run app.py
   ```

4. **Use the Application**:
   - Enter a search query in the text input field.
   - View the top-matching images and their similarity scores.

---

## 📌 Notes
- Ensure all images are stored in supported formats (e.g., `.jpg`, `.png`).
- The system is designed to work without any pre-existing metadata, relying solely on the visual features of the images.
- You can fine-tune the embeddings model or use a different CLIP variant for domain-specific improvements.
