# 🧠 AI Hallucination Detection System

An AI engineering project that identifies potentially unsupported statements in AI-generated answers by comparing them with a supplied reference context. This starter implementation uses Python, TF-IDF, cosine similarity, and evaluation metrics to demonstrate a basic hallucination-detection workflow.

> **Disclaimer:** This is an educational prototype, not a definitive fact-checking system. Similarity scores do not prove that a statement is true or supported. Human review is recommended for important decisions.

## 🚀 Features

- Detect potentially unsupported answer sentences.
- Compare AI-generated answers against reference context.
- Calculate sentence-level TF-IDF cosine similarity.
- Configure a threshold for flagging suspicious statements.
- Evaluate predictions using accuracy, precision, recall, and F1-score.
- Visualize results using a confusion matrix.
- Inspect flagged sentences and their similarity scores.
- Export results to JSON and Markdown reports.
- Run without an external API key.

## 🛠️ Technologies Used

- Python
- Jupyter Notebook
- Pandas
- Scikit-learn
- Matplotlib
- TF-IDF Vectorization
- Cosine Similarity
- Machine Learning Evaluation Metrics

## 📁 Project Structure

```text
ai-hallucination-detection-system/
│
├── ai_hallucination_detection_system.ipynb
├── README.md
├── requirements.txt
│
└── hallucination_detection_outputs/
    ├── hallucination_detection_report.json
    └── hallucination_detection_report.md
```

The output directory and report files are generated when you run the relevant notebook cells.

## ⚙️ Installation and Setup

### Option 1: Run in Google Colab

1. Download `ai_hallucination_detection_system.ipynb`.
2. Open Google Colab.
3. Select **File → Upload notebook**.
4. Upload the downloaded notebook.
5. Run the notebook cells sequentially.

The notebook includes a dependency-installation cell.

### Option 2: Run Locally

Clone the repository:

```bash
git clone https://github.com/<your-username>/ai-hallucination-detection-system.git
```

Navigate to the project directory:

```bash
cd ai-hallucination-detection-system
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate it on Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

On macOS or Linux:

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open `ai_hallucination_detection_system.ipynb` and run the cells in order.

## 🧩 How It Works

### Step 1: Provide Reference Context

Supply the source text against which an AI-generated answer should be checked.

### Step 2: Split the Answer into Sentences

The system separates the generated answer into individual sentences for analysis.

### Step 3: Calculate Similarity

TF-IDF vectorization and cosine similarity estimate the lexical overlap between each answer sentence and the supplied context.

### Step 4: Flag Potentially Unsupported Sentences

Sentences with similarity scores below the configured threshold are flagged for review.

### Step 5: Evaluate the Results

The notebook demonstrates evaluation using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix

### Step 6: Export Reports

The system exports evaluation results and limitations in JSON and Markdown formats.

## 💻 Example Usage

```python
context = """
The product weighs 1.4 kilograms and comes with a two-year warranty.
"""

answer = """
The product weighs 1.4 kilograms and includes a five-year warranty.
"""

result = inspect_answer(
    context=context,
    answer=answer,
    threshold=0.16
)

print(result)
```

The function returns sentence-level similarity scores and flags sentences that fall below the selected threshold.

**Important:** A flagged sentence is not necessarily false. It may simply use wording that differs from the reference context.

## 📊 Evaluation

The notebook demonstrates how to calculate:

| Metric | Purpose |
|---|---|
| Accuracy | Measures the proportion of correctly classified examples. |
| Precision | Measures how many flagged examples are actually labelled as potential hallucinations. |
| Recall | Measures how many labelled potential hallucinations are detected. |
| F1-score | Combines precision and recall. |
| Confusion Matrix | Shows correct and incorrect predictions by class. |

The included dataset is small and synthetic. Its metrics demonstrate the evaluation process only and should not be interpreted as evidence of real-world performance.

## ⚠️ Limitations

- The initial dataset is synthetic and too small for reliable benchmarking.
- TF-IDF measures lexical similarity rather than factual correctness.
- Valid paraphrases may be flagged because their wording differs from the context.
- Contradictory statements may receive high similarity scores when they share many words with the context.
- The baseline does not use an LLM, a natural-language inference model, or external fact-checking sources.
- The selected threshold may not generalize to other domains.

## 🔮 Future Improvements

Potential extensions include:

1. Sentence embeddings for semantic similarity.
2. Natural-language inference models for entailment, contradiction, and neutrality detection.
3. Atomic claim extraction and claim-by-claim verification.
4. Citation validation and evidence-span matching.
5. Larger, expert-labelled evaluation datasets.
6. An interactive Streamlit interface.
7. A FastAPI service for integration with other applications.
8. Monitoring, regression testing, and evaluation dashboards.

## 🛡️ Responsible Use

This project is intended for educational purposes and experimentation. A detection warning should trigger further investigation rather than being treated as proof that a statement is false.

Do not use this prototype as the sole basis for medical, legal, financial, safety, or other high-impact decisions.

## 📜 License

Select a suitable open-source license, such as MIT, and add a `LICENSE` file before publishing the repository.
