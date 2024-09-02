# Plagiarism_checker
This repo consists of a source code of a Python script which detects plagiarism in a textual document using cosine similarity.
The Python script you provided is designed to check for plagiarism between multiple text files by comparing their contents using a technique called TF-IDF (Term Frequency-Inverse Document Frequency) and cosine similarity. Here's a step-by-step explanation of how the project works:

### Step-by-Step Workflow

1. **Load Text Files**:
   - The script looks for all `.txt` files in the current directory using Python’s `os.listdir()` function. It stores the filenames in a list called `student_files`.
   - It reads the content of each text file into memory, storing them in a list called `student_notes`.

2. **Convert Text to Numerical Form (Vectorization)**:
   - Text data needs to be converted into a numerical format that a computer can process for similarity comparison. This is achieved using TF-IDF vectorization:
     - **TF-IDF**: This is a statistical measure that evaluates how important a word is to a document in a collection of documents. It helps in converting text data into a format that allows similarity computations.
     - The `TfidfVectorizer` from `scikit-learn` is used to transform the text from each file into a TF-IDF vector, effectively turning each document into a numerical vector.

3. **Calculate Similarity**:
   - **Cosine Similarity**: Once the text data is in numerical form (as vectors), the script calculates the cosine similarity between every pair of documents. Cosine similarity measures the cosine of the angle between two vectors, providing a metric for how similar the two documents are:
     - A cosine similarity score ranges from 0 to 1, where 1 means the documents are identical in terms of their TF-IDF representation, and 0 means they have no similarity.
   - The script computes cosine similarity for every pair of documents to identify how similar they are to each other.

4. **Check for Plagiarism**:
   - The script compares each document against all other documents, calculating a similarity score for each pair.
   - If two documents have a high similarity score (close to 1), it suggests potential plagiarism or high content overlap between them.
   - The results are stored in a set called `plagiarism_results` to ensure uniqueness and avoid duplicate comparisons.

5. **Output the Results**:
   - The script prints the filenames of each pair of documents and their similarity score, showing which documents are most similar to each other.

### Key Components

- **TF-IDF Vectorization**: Converts text data into a numerical format that captures the importance of words relative to the entire set of documents.
- **Cosine Similarity**: A metric to measure how similar two documents are in their vectorized form.
- **Plagiarism Detection**: The main purpose of the script, identifying pairs of documents that have high similarity scores indicating possible plagiarism.

### How the Project Works: Overview

1. **Preparation**: Gathers all text files and reads their content.
2. **Processing**: Converts the text into vectors using TF-IDF and calculates the similarity between all documents.
3. **Analysis**: Compares each pair of documents to detect similarity and potential plagiarism.
4. **Output**: Displays the similarity scores, which can be used to determine if further investigation is needed.

### Example of Execution

Let's say you have three text files:
- `student1.txt`: "Machine learning is a field of artificial intelligence."
- `student2.txt`: "Machine learning is a branch of AI."
- `student3.txt`: "Data science involves machine learning."

When you run the script:
1. It reads the content of these files.
2. It converts the contents into vectors using TF-IDF.
3. It calculates cosine similarities between:
   - `student1.txt` and `student2.txt`
   - `student1.txt` and `student3.txt`
   - `student2.txt` and `student3.txt`
4. If `student1.txt` and `student2.txt` have a high similarity score, the script outputs this information, signaling potential overlap or plagiarism.

### Conclusion

The script is a simple but effective way to compare multiple text documents for similarity. It’s particularly useful for detecting plagiarism in educational settings or content similarity in other contexts. The core idea is transforming text data into numerical vectors to make similarity comparisons straightforward using established mathematical techniques like TF-IDF and cosine similarity.
