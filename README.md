# Smart-Claims-Processing-Platform_hidevs
# Smart Claims Processing Platform

This project implements an intelligent system for insurance claims processing using OCR, NLP, and zero-shot classification. It automates document handling, classifies claims by type and priority, routes them intelligently, and checks for policy compliance.

## Features

### Document Processing
- Uses Tesseract OCR to extract text from scanned documents (JPG, PNG).
- Efficiently handles multiple document types through image-based text recognition.

### Claims Classification
- Applies zero-shot classification (BART Large MNLI) from Hugging Face Transformers.
- Categorizes claims into the following types:
  - Auto Claim
  - Health Claim
  - Property Claim
  - Travel Claim
- Detects urgent or high-priority claims based on specific keywords.

### Workflow Optimization
- Routes claims based on type and detected keywords:
  - Auto → Collision Specialist
  - Health → Surgical Review Team
  - Property → Fire Damage Team
- Urgent claims are routed to a high-priority queue automatically.

### Policy Compliance
- Uses a configurable JSON file (`policy_rules.json`) for exclusions and limits.
- Flags violations such as:
  - Alcohol-related incidents
  - Fraudulent claims
  - Expired policies
  - Intentional damage
- Checks if the claim amount exceeds the policy limit.

## Dependencies

Install the required packages before running the notebook:

```bash
sudo apt install tesseract-ocr -y
pip install pytesseract transformers huggingface_hub

## Hugging Face Authentication
You must log in to Hugging Face to use the zero-shot classification model:

from huggingface_hub import login
login("your-huggingface-token")

Generate your token from: https://huggingface.co/settings/tokens

## How to Use

-Upload a claim image (JPG or PNG format).
-Text is extracted using Tesseract OCR.
-The system classifies the claim using a zero-shot model.
-It routes the claim to the appropriate team based on content.
-It checks for policy violations and coverage issues.


## Files
= smart_claims_processing_platform.ipynb – Main implementation notebook

- policy_rules.json – Contains rules for exclusions and maximum limits

## Example Output

```text
Extracted Text:
    "...claim due to road accident and vehicle damage..."

Predicted Claim Type: Auto Claim
Routing Decision: Route to Collision Specialist
Compliance Status: Passed Compliance

## Future Improvements
-Add support for PDF and DOCX document formats
-Integrate with backend claim systems
-Build a web-based UI using Streamlit or Gradio
-Implement analytics and logging functionality

