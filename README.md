# Automatic Candidate Screening System

★★★ ★★  

---

## Table of Contents
1. [Introduction](#introduction)  
2. [Part 1: Resume-Job Matching System](#part-1-resume-job-matching-system)  
3. [Part 2: Selection via Chatbot](#part-2-selection-via-chatbot)  
4. [Other Approaches Tried](#other-approaches-tried)  
5. [Technologies Used](#technologies-used)  
6. [Conclusion](#conclusion)  

---

## Introduction
This project aims to automate the screening and pre-selection of job applicants by combining semantic analysis of resumes and job descriptions with a chatbot interaction to refine the candidate selection process.

---

## Part 1: Resume-Job Matching System

### Overview
- Extract key information from PDF resumes.  
- Compare resume data with job descriptions.  
- Compute similarity scores to identify the best matches.  
- Use NLP techniques and BERT embeddings.

### Document Processing
1. **PDF Text Extraction**  
2. **Information Extraction**  
   - Extract location, work experience, education, technical skills, and tools/software.  
   - Handle different CV formats with regex and NLP (spaCy).

### Semantic Analysis
- Generate BERT embeddings for each section of the resume.  
- Merge embeddings to represent the full document.  
- Compute cosine similarity with job description vectors.

### Alternative Approach: TF-IDF
- Preprocess text (lowercase, remove punctuation, tokenize, remove stopwords).  
- Vectorize CVs and job descriptions with `TfidfVectorizer`.  
- Compute cosine similarity to rank candidates.

---

## Part 2: Selection via Chatbot

### Overview
- Develop a chatbot to interact with pre-selected candidates.  
- Dynamically generate quiz questions based on candidate profile and job requirements.  
- Analyze responses to refine selection.

### Implementation
- **Service:** `services/quiz_generator.py` uses Dolphin 2.9.3 (Mistral 7B).  
- **API Endpoint:** `routes/quiz.py` (Flask) receives candidate ID, fetches CV from MongoDB, and generates a customized quiz.

### Prompt Strategy
- Each question focuses on a different skill from the candidate profile.  
- Multiple-choice questions (A, B, C, D) with one correct answer.  
- Output is a JSON list of questions only (no explanations).

---

## Other Approaches Tried
- Resume-job matching using TF-IDF and cosine similarity.  
- Preprocessing with NLTK and sklearn.  
- Comparison of semantic similarity scores to filter candidates.

---

## Technologies Used
- **React:** Frontend framework for dynamic and responsive UI.  
- **Flask:** Lightweight Python backend for API endpoints.  
- **MongoDB:** NoSQL database for storing resumes and candidate data.  
- **NLP & BERT:** For semantic analysis and similarity computation.  
- **LLM (Dolphin 2.9.3 / Mistral 7B):** For adaptive quiz generation.

---

## Conclusion
A smart and complete solution for automating candidate pre-selection by combining:  
- **NLP** for semantic matching between resumes and job descriptions.  
- **LLM-based chatbot** for adaptive quiz generation.  
- **Modern interface** for enhanced user experience.
