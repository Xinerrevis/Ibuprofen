# PubMed Auto-Downloader

## What is the project?
This is a Google Colab script designed to automatically find, filter, and download scientific articles from PubMed. Utilizing the `metapub` library, the code reads PubMed IDs (PMIDs) from a CSV file, resolves direct PDF links for Open Access papers, and downloads them into a specified local directory.

## Origins
This tool was developed as the first phase of the PhD project at the Faculty of Pharmaceutical Sciences, University of São Paulo (USP - FCF) of Jheniffer Rabelo, supervised by Prof. Dr. Fábio Lobato and Prof. Dr. Felipe Lourenço. The ultimate goal of the research is to build a robust database to extract pharmacokinetic and dissolution information regarding ibuprofen. 

## How to use
1. **Install dependencies:**
   ```bash
   pip install pandas requests metapub
   ```
2. **Set your NCBI API Key:** 
   Add your API key to the script: `os.environ['NCBI_API_KEY'] = "YOUR_API_KEY"`.
3. **Prepare your input:**
   Create a CSV file containing a column named `pmid` with the PubMed IDs of the articles you want to download.
4. **Run the script:**
   Execute the function by passing your CSV path and the desired output folder:
   ```python
   download_with_metapub_findit('your_file.csv', './PDF_Corpus_Metapub')
   ```

## Expected Results
- **PDF Corpus:** A local folder populated with the downloaded PDF files, named in the format `PMID_<pmid>.pdf`.
- **Audit Log:** An automated log file (`metapub_missing_audit.csv`) generated in the output directory, detailing any PMIDs that failed to download (e.g., behind hard paywalls or invalid IDs) along with the specific failure reasons.
