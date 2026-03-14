## Overview
This dataset documents **10 diverse blind spots** observed when testing a recently released base model (1.2B parameters, from Hugging Face). The goal is to highlight where frontier models fail in arithmetic, translation, factual recall, reasoning, and creative tasks. Each entry includes the input, expected output, and the model’s actual output.

## Model Tested
- **Model:** oki692/LFM2.5-1.2B-Base. 
- **Size:** 1.2B parameters  
- **Release:** 2026-03-02 03:23:29+00:00 
- **Type:** Base LLM (not fine‑tuned)

## Run in Colab
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1fNgP0svg3UXXjKROXP4orgq2EP602_hj)



## Dataset Explanation

### 1. Complex arithmetic
- **Input:** Square root of 12345  
- **Expected:** ≈111.11  
- **Model output:** Produced 111.8 but then drifted into unrelated garden perimeter problem.  
- **Blind spot:** Difficulty giving accurate decimal points.

### 2. Non‑English multilingual translation
- **Input:** Translate mitochondria sentence into Japanese  
- **Expected:** ミトコンドリアは細胞の力の源です  
- **Model output:** Repeated English sentence, no translation.  
- **Blind spot:** Weakness in direct non‑English translation.

### 3. Obscure factual recall
- **Input:** Nobel Prize in Physics 1933  
- **Expected:** Erwin Schrödinger and Paul Dirac  
- **Model output:** Incorrectly listed Max Planck.  
- **Blind spot:** Poor recall of rare historical facts.

### 4. Ancient literature knowledge
- **Input:** Summarize *Epic of Gilgamesh* in 1 sentence  
- **Expected:** Gilgamesh seeks immortality after Enkidu dies…  
- **Model output:** Repeated generic description multiple times.  
- **Blind spot:** Redundancy and lack of detail in summarizing ancient texts.

### 5. Creative form constraint
- **Input:** Write a limerick about machine learning  
- **Expected:** Proper limerick with rhyme and rhythm  
- **Model output:** Gave a definition of machine learning and not rhyme and rhythm.  
- **Blind spot:** Failure to follow creative form constraints.

### 6. Ambiguous sentiment
- **Input:** “I guess I’m happy, in a sad sort of way” sentiment classification  
- **Expected:** Neutral  
- **Model output:** Repeated indecision (“not sure if happy, sad, or neutral”).  
- **Blind spot:** Struggles with mixed emotional cues.

### 7. Pattern recognition
- **Input:** Continue Fibonacci sequence  
- **Expected:** 21, 34, 55  
- **Model output:** Jumped to 55 directly, skipped intermediate values.  
- **Blind spot:** Incomplete sequence continuation.

### 8. Less common geography
- **Input:** Capital of Eswatini  
- **Expected:** Mbabane (administrative), Lobamba (royal/legislative)  
- **Model output:** Only listed Mbabane, ignored dual capital structure.  
- **Blind spot:** Missing nuanced geography facts.

### 9. Logic puzzle
- **Input:** Seating puzzle (A, B, C)  
- **Expected:** C  
- **Model output:** Ignored puzzle, switched to bacteria growth problem.  
- **Blind spot:** Context drift and failure in positional logic.

### 10. Cross‑lingual translation into ancient language
- **Input:** Translate “Hola, ¿cómo estás?” into Latin  
- **Expected:** Salve, quid agis?  
- **Model output:** Repeated Spanish input, no translation.  
- **Blind spot:** Weakness in rare language translation.

---

## How to Fix These Blind Spots
- **Arithmetic & sequences:** Fine‑tune on math problem datasets (e.g., GSM8K, synthetic numeric tasks).  
- **Translation:** Add multilingual corpora, especially non‑English and ancient languages.  
- **Factual recall:** Incorporate curated historical datasets and knowledge graphs.  
- **Creative tasks:** Fine‑tune on poetry/limerick corpora to enforce form constraints.  
- **Sentiment:** Train on nuanced sentiment datasets with mixed cues.  
- **Logic puzzles:** Include reasoning datasets with step‑by‑step explanations.  
- **Geography:** Add world knowledge datasets with dual capital and unusual facts.

---

## Dataset Size Estimate
To cover these blind spots, a fine‑tuning dataset of **50k–200k examples** across diverse domains would likely be needed.  
Balance between synthetic data (for math/logic) and curated human‑authored data (for literature, sentiment, creative forms).
