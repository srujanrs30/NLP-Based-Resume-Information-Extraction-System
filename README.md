# NLP-Based-Resume-Information-Extraction-System

Overview

This project extracts structured information from resumes using a hybrid NLP pipeline.

It identifies:

Name
Email
Skills
Experience

The system combines:

Custom-trained SpaCy NER models
Pretrained skill extraction model
Rule-based + fuzzy matching techniques

Features:
Custom Name Extraction (NER)
Custom Experience Extraction (NER)
Skill Extraction (ML + Dictionary + Fuzzy Matching)
Email Extraction (Regex)
Fallback using SpaCy pretrained model

Project Structure:
project/
├── models/
│   ├── en_name_model-1.0.0.whl
│   └── en_experience_model-1.0.0.tar.gz
├── unique_skills.txt
├── main.py
├── requirements.txt
└── README.md

Installation:
1. Install dependencies
pip install -r requirements.txt
2. Download SpaCy fallback model
python -m spacy download en_core_web_sm
3. Install custom models
pip install models/en_name_model-1.0.0.whl
pip install models/en_experience_model-1.0.0.tar.gz

Requirements:
spacy==3.7.2
huggingface_hub
rapidfuzz
Usage

Run the script:

python main.py
Example Output
EXTRACTED INFO:

Name: John Doe
Email: john@email.com
Skills: ['python', 'machine learning']
Experience: ['2 years', 'Software Developer']

How It Works:
Input Resume
   ↓
Name Model (Custom NER)
   ↓
Experience Model (Custom NER)
   ↓
Skill Model (Hugging Face)
   ↓
Dictionary Matching + Fuzzy Matching
   ↓
Fallback Model (SpaCy)
   ↓
Structured Output

Important Notes:
Internet required on first run (downloads skill model)
unique_skills.txt must be present
Install models before running the script

Limitations:
- Depends on training data quality
- May miss complex experience formats
- Skill coverage depends on dictionary

Future Improvements:
Merge all models into a single pipeline
Add API support (FastAPI / Flask)
Improve experience extraction accuracy
Support multiple resume formats (PDF, DOCX)

Tech Stack:
- Python
- SpaCy
- Hugging Face Hub
- RapidFuzz
- Regex
