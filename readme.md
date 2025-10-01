# AI Document Comparator

- A powerful, **AI-powered web application** built with **Streamlit** for comparing two documents (Original vs. Revised) and generating detailed analysis reports.  
- Use **Google Gemini AI** and **LangChain** for intelligent diff analysis, this helps to identifies changes, assesses impacts, and provides actionable recommendations.  
- Supports multiple file formats with OCR for scanned PDFs.

## Introduction

The **AI Document Comparator** is a Streamlit application designed to **automate and enhance document comparison workflows**.  

- It Extract and preprocess text from uploaded documents.
- Perform **section-level comparisons** to detect additions, removals, modifications, and unchanged content.
- Generate comprehensive reports including:
  - Executive summaries  
  - Impact analysis  
  - Image comparisons  
  - Provide recommendations  
- Export results in **multiple formats (PDF, DOCX, TXT, JSON)** 

## Features

### Intelligent Document Comparison
- Section-by-section and criteria-level analysis.
- Classifies changes as **Added, Removed, Modified, or Unchanged**.
- Includes unchanged content for full context.
- **Impact analysis** (e.g., compliance implications).
- Recommendations for each change (e.g., update policies).

### Image & Visual Analysis
- Detects added, removed, or modified images.
- Reports on captions, labels, and alterations.

### Text Extraction
- Robust **PDF handling** with `PyPDF2` and OCR fallback (`PyMuPDF` & Tesseract).
- Native support for **DOCX** (`python-docx`), **TXT**, and **JSON** (flattens nested structures).

### Metrics & Previews
- Quick **similarity percentage**, length/word/line differences.
- **Side-by-side previews** with keyword highlighting (e.g., *Actual, Revised, Change*).

### Report Generation
- **PDF**: Landscape-formatted with tables and styled content (via ReportLab).  
- **DOCX**: Structured Word reports (via python-docx).  
- **TXT**: Plain text summary with formatted tables.  
- **JSON**: Structured data export for further processing.  

### User Interface
- Upload Original and Revised Documents Sections.
- Sidebar with:
  - System status  
  - Usage guide  
  - Supported formats such as docx, pdf, txt and json 
- **API connection testing** and error handling.  
- **Session state management** for persistent results.

### Advanced Capabilities
- **Pydantic models** for output validation.  
- `difflib` for similarity calculation.  
- Environment-based configuration (**API keys via `.env`**).  

## Supported Formats

| Format          | Extension | Notes                                                                 |
|-----------------|-----------|----------------------------------------------------------------------|
| **PDF**         | `.pdf`    | Native text extraction; OCR fallback for scanned documents (Tesseract). |
| **Word**        | `.docx`   | Full paragraph extraction; page estimation based on word count.      |
| **Text**  | `.txt`    | Direct reading with line-based page estimation.                      |
| **JSON**        | `.json`   | Flattens nested structures for comparison; line-based estimation.    |

## Installation

### Clone the Repository
```bash
git clone https://github.com/yourusername/ai-document-comparator.git
cd ai-document-comparator
````

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Set Up Environment Variables

Create a **.env** file in the project root:

```text
GEMINI_API_KEY=your_api_key_here
```

### Run the Application

```bash
streamlit run app.py
```

## 🚀 Usage Guide

1. **Launch the App**
   Run the above command to start the Streamlit server.

2. **Upload Documents**

   * Upload *Original Document* (baseline) and *Revised Document* (updated version).
   * Supported file types are auto-detected.

3. **View Extraction Summary**

   * File stats: size, lines, words, pages.
   * Quick metrics: similarity, differences.

4. **Compare Documents**

   * Click **"🔍 COMPARE DOCUMENTS"** to start AI-powered analysis.
   * Processing takes **30–60 seconds** depending on document size.
   * Results include:

     * Metrics table
     * AI comparison table
     * Executive summary
     * Section analysis
     * Image report
     * Recommendations

5. **Preview & Interact**

   * Side-by-side text areas with **highlighted differences**.
   * Sidebar includes **API testing and usage tips**.

6. **Download Reports**

   * Export results in **PDF, DOCX, TXT, or JSON** format.


## 🛠️ Tech Stack

* **Frontend/UI**: [Streamlit](https://streamlit.io/)
* **AI/LLM**: Google Gemini AI + [LangChain](https://www.langchain.com/)
* **Document Processing**: PyPDF2, PyMuPDF, Tesseract OCR, python-docx
* **Reports**: ReportLab, python-docx
* **Utilities**: Pydantic, difflib
* **Environment Config**: dotenv
