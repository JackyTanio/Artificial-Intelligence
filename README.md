
# Summarization and OCR Project

This project demonstrates the use of text summarization and Optical Character Recognition (OCR) using the `transformers` library and `tesseract-ocr`. The project focuses on processing PDFs to extract and summarize text, along with performing OCR on images.

## Table of Contents
- [Overview](#overview)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
  - [Text Summarization](#text-summarization)
  - [PDF Text Extraction](#pdf-text-extraction)
  - [OCR Using Tesseract](#ocr-using-tesseract)
- [Output](#output)
- [License](#license)

## Overview

This notebook is designed to extract text from PDFs, summarize it using a pre-trained Transformer model, and perform OCR on image-based text. It leverages the following:
1. **PyPDF2**: For extracting text from PDF files.
2. **Hugging Face Transformers**: For summarizing the extracted text using a model (`t5-base`).
3. **Tesseract-OCR**: For optical character recognition on image-based files.

## Requirements

To run this project, you need the following libraries:
- `PyPDF2`
- `transformers`
- `Pillow`
- `pytesseract`
- `tesseract-ocr`

## Installation

To install the required dependencies, run the following commands:

```bash
pip install pypdf2
pip install transformers
pip install Pillow
pip install pytesseract
apt install tesseract-ocr
apt install libtesseract-dev
```

## Usage

### Text Summarization

The project uses the `t5-base` model from Hugging Face's `transformers` library for text summarization. A pipeline is set up as follows:

```python
from transformers import pipeline

summarizer = pipeline("summarization", model="t5-base", tokenizer="t5-base", framework="tf")
```

### PDF Text Extraction

You can extract text from a PDF using the `PyPDF2` library. For example, to read text from a file:

```python
import PyPDF2

with open('your_pdf_file.pdf', 'rb') as file:
    pdf = PyPDF2.PdfReader(file)
    for page_num in range(len(pdf.pages)):
        page = pdf.pages[page_num]
        text = page.extract_text()
        print(text)
```

### OCR Using Tesseract

Tesseract is used for Optical Character Recognition (OCR). You need to install `tesseract-ocr` and use `pytesseract` in Python:

```bash
apt install tesseract-ocr
pip install pytesseract
```

To perform OCR on an image:

```python
from PIL import Image
import pytesseract

image = Image.open('your_image.png')
text = pytesseract.image_to_string(image)
print(text)
```

## Output

- **Summarized Text**: The text extracted from a PDF is summarized using the T5 model.
- **Extracted PDF Text**: Raw text extracted from the PDF.
- **OCR Text**: Text extracted from images using Tesseract.

## License

This project is licensed under the MIT License.
