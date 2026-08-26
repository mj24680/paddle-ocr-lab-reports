# Generic Lab Report OCR — Beginner Project

This project teaches a simple two-part workflow:

```text
PDF or image
    -> text OCR
    -> text, confidence, and coordinates
    -> document structure
    -> titles, paragraphs, and tables
    -> JSON, CSV, TXT, and Markdown files
```

The notebook does not search for CBC-specific words. You can use it with another
clear lab report by changing one input path.

## Directory

```text
Paddle OCR/
├── data/
│   └── input/
│       └── cbc_sample_report.pdf
├── paddle_ocr.ipynb
├── requirements.txt
└── README.md
```

The `outputs/` folder is created automatically when the notebook runs.

## Anaconda PowerShell Prompt

Run these commands:

```powershell
conda activate paddle_ocr
Set-Location "C:\Users\user\Desktop\Paddle OCR"
python -m pip install -r requirements.txt
jupyter lab
```

## JupyterLab interface

1. Open `paddle_ocr.ipynb`.
2. Confirm that the kernel is the `paddle_ocr` environment.
3. Run the cells from top to bottom.
4. The first structure-model run downloads extra models and takes longer.

To process a different report, place it inside `data/input/` and change Cell 1:

```python
INPUT_PATH = Path("data/input/your_report.pdf")
```

Supported examples include PDF, PNG, JPG, JPEG, TIFF, and BMP files.

## Outputs

```text
outputs/
├── ocr/
│   ├── ocr_result.json
│   ├── ocr_result.csv
│   ├── recognized_text.txt
│   └── OCR visualization image
└── structure/
    ├── structured_result.json
    ├── document_blocks.csv
    ├── metadata_pairs.csv
    ├── table_1.csv
    ├── paddle_page_1.json
    └── page_1.md
```

## Important limitation

Text OCR and document layout are generic, but medical meaning is a separate
problem. A production system must map document content to a fixed medical schema,
validate values and units, measure accuracy on reports from many laboratories,
and send uncertain results for human review.
