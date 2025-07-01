# Product_Catalogue_pdf_to_xlsx
This project is a Streamlit application designed to extract product information, including both text data and images, from PDF product catalogs and organize it into a downloadable Excel file.

## What it Does

The application streamlines the process of converting unstructured PDF catalog data into a structured Excel format. Specifically, it performs the following steps for each uploaded PDF:

1.  **PDF Upload and Temporary Storage**: Allows users to upload one or more PDF catalog files, which are temporarily stored for processing.
2.  **Product Data Extraction**: Utilizes the Google Gemini API to intelligently parse the PDF and extract key product details such as "Style ID," "SKU," "Price" (if available), and "Color." It's designed to handle variations in data ordering within product columns.
3.  **Image Extraction and Filtering**: Extracts images from the PDF using PyMuPDF. It also offers an optional feature, powered by the OpenAI Vision API, to filter out banners, advertisements, and collages, ensuring only relevant single product images are included.
4.  **Excel File Generation**: Compiles the extracted product data into a pandas DataFrame and then saves it to an Excel (.xlsx) file.
5.  **Image Embedding**: Embeds the extracted product images directly into the corresponding rows of the generated Excel file.
6.  **Download and Cleanup**: Provides a convenient download link for the generated Excel file and cleans up all temporary files and directories after processing.

## How to Run Locally

To get this Streamlit application up and running on your local machine, follow these steps:

### 1\. Clone the Repository

First, clone this repository to your local machine:

```bash
git clone <repository_url>
cd pdf_to_xlsx
```

### 2\. Set Up a Virtual Environment (Recommended)

It's highly recommended to use a virtual environment to manage dependencies:

```bash
python -m venv venv
# On Windows
.\venv\Scripts\activate
# On macOS/Linux
source venv/bin/activate
```

### 3\. Install Dependencies

Install the required Python packages using pip:

```bash
pip install -r requirements.txt
```

[cite\_start]The `requirements.txt` file specifies the necessary libraries[cite: 1]:

  * [cite\_start]`pymupdf` [cite: 1]
  * [cite\_start]`openai` [cite: 1]
  * [cite\_start]`pydantic` [cite: 1]
  * [cite\_start]`xlsxwriter` [cite: 1]
  * [cite\_start]`google.generativeai` [cite: 1]

### 4\. Configure API Keys

This application requires API keys for Google Gemini and OpenAI. You should store these securely. Streamlit recommends using `st.secrets` for this purpose.

Create a `.streamlit` folder in your project root, and inside it, create a file named `secrets.toml`:

```
# .streamlit/secrets.toml
GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
OPENAI_API_KEY="YOUR_OPENAI_API_KEY"
```

Replace `"YOUR_GEMINI_API_KEY"` and `"YOUR_OPENAI_API_KEY"` with your actual API keys.

### 5\. Run the Streamlit App

Once the dependencies are installed and API keys are configured, you can run the Streamlit application:

```bash
streamlit run app.py
```

This command will open the Streamlit app in your web browser, usually at `http://localhost:8501`. You can then upload your PDF files and start processing them.
