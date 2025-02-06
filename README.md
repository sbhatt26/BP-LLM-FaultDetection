# Fault Detection and Specification Analysis in Business Process Logic Systems Using LLMs

## Overview

This repository provides an automated framework for analyzing and improving business process logic systems using Large Language Models (LLMs). The system has two primary components:

1. **Specification Analysis**: Identifies missing or redundant specifications and suggests improvements.
2. **Fault Detection in BPMN Files**: Detects logical and structural faults in BPMN workflows and applies corrections.

### Key Features

- **Specification Analysis:** Uses clustering and semantic embeddings to analyze discrepancies in specifications.
- **Fault Detection:** Identifies BPMN-specific errors such as missing decision gateways and incorrect links.
- **LLM Integration:** Leverages the Ollama Mistral and OpenAI GPT-4o models for generating improvement suggestions and BPMN corrections.
- **Automated Correction:** Applies AI-driven improvements to both textual specifications and BPMN XML files.

---

## Project Structure

```
├── data/
│   ├── Additional BPMN XML Files/                # Extra BPMN files for testing
│   ├── Order Management Process/                 # BPMN models related to order processing
│   ├── Project Management Process/               # BPMN models for project workflows
│   ├── Software Development Lifecycle Process/   # BPMN models for SDLC workflows
├── src/
│   ├── Fault Detection/
│   │   ├── BP_LLM_FaultDetection.ipynb           # Fault detection notebook
│   ├── Specification Generation/
│   │   ├── BP_LLM_SpecGeneration.ipynb           # Specification generation notebook
├── README.md                                      # Project documentation
├── requirements.txt                               # Python dependencies
```

---

## Installation

### Prerequisites

- Python 3.8+
- `pip install -r requirements.txt`
- Local Ollama server running Mistral model (`http://localhost:11434/api/generate`)
- OpenAI API key for GPT-4o corrections

### Setup

1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/BP-LLM-FaultDetection.git
   cd BP-LLM-FaultDetection
   ```
2. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```
3. Set API keys in environment variables:
   ```sh
   export OPENAI_API_KEY='your-openai-api-key'
   ```

---

## Usage

### Running Fault Detection

```sh
python src/Fault_Detection/BP_LLM_FaultDetection.ipynb
```

- Parses BPMN files in `data/`.
- Identifies missing decision gateways, incorrect links, and logic errors.
- Generates corrected BPMN files in `data/corrected_bpmn/`.
- Saves fault reports in `fault_detection_report.txt` and suggested corrections in `fault_solutions.txt`.

### Running Specification Generation

```sh
python src/Specification_Generation/BP_LLM_SpecGeneration.ipynb
```

- Analyzes differences between a set of groundtruth specifications and faulty specifications.
- Uses the Ollama Mistral model to suggest improvements in `specifications_improvements.txt`.

---

## Methodology

### 1. Specification Analysis

- **Step 1:** Load groundtruth and faulty specifications.
- **Step 2:** Generate semantic embeddings using SentenceTransformers.
- **Step 3:** Apply Agglomerative Clustering to group similar topics.
- **Step 4:** Identify missing or redundant specifications.
- **Step 5:** Query the Ollama Mistral model for suggested improvements.

### 2. BPMN Fault Detection & Correction

- **Step 1:** Parse BPMN files using `lxml.etree`.
- **Step 2:** Extract tasks, gateways, and events from BPMN XML.
- **Step 3:** Identify missing gateways, incorrect links, and logical errors.
- **Step 4:** Query GPT-4o for recommended corrections.
- **Step 5:** Apply corrections and save updated BPMN files.

---

## Results

- **Specification Analysis Metrics:**
  - **Precision:** 0.92  
  - **Recall:** 0.88  
  - **F1 Score:** 0.91  
- **BPMN Fault Detection:**
  - Successfully corrected missing gateways and logical inconsistencies.
  - Improved BPMN process workflows through automated fault detection & correction.

---

## Future Enhancements

- Extend support for additional BPMN validation rules.
- Improve LLM prompting for more accurate suggestions.
- Optimize clustering and embedding strategies for better fault detection.

---

## License

This project is licensed under the MIT License.
