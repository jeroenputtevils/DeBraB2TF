# Annotating futurity in the De Bra letters

Code accompanying Jeroen Puttevils, "The brandy will yield throughout the year 75": Using Large Language Models for the Annotation of Futurity in a Seventeenth-Century Dutch Merchant Correspondence.

## What it does
The script annotates Transkribus transcriptions (.txt) of Abraham De Bra's letters to Henri François Schilders (1665–1680) with Gemini 2.5 Flash in two steps:

1. **Extraction (zero-shot):** lists every future statement, split into its smallest logical parts.
2. **Analysis (few-shot, five examples):** returns a table with explanation, modality (deontic/epistemic), control, specific moment, order, domain and word count.

Output is an Excel file with one row per statement and 12 columns, including the filename. In the paper, 808 letters yielded 7,976 statements in about ten hours for €37.4.

## Requirements
- Google Colab with Google Drive
- Python packages: pandas, openpyxl, tqdm, google-generativeai
- A Gemini API key (the paper used a paid Tier 1 account)

## Usage
1. Put the .txt letters in a Drive folder and set `folder_path`.
2. Store your API key in Colab Secrets. Never hardcode it.
3. Run the notebook. A checkpoint is saved every 50 files, and failed API calls are retried three times. Files that still fail can be rerun in a later batch.

## Data
The model output data can be found here: https://zenodo.org/records/24104266

## Caveats
Treat the output as a first pass. The paper's 5% human-checked sample showed 98.24% accuracy for statement identification, but deontic labels and domains need checking. The LLM's explanations may not reflect genuine reasoning.

## Citation and licence
Please provide a citation when using this code.
