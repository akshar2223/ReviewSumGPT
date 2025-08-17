# ReviewSumGPT: Abstractive Review Summarization using GPT-3

## Problem Statement & Motivation

In today’s e-commerce landscape, customers often face information overload when reading product reviews. Though reviews contain valuable insights, they’re often unstructured and redundant.  
This project solves that by fine-tuning a GPT-3 language model to generate concise summaries using the **Amazon Fine Food Reviews** dataset — improving the customer experience and enabling data-driven decisions.

---

## Approach & Methodology

### Data Preprocessing

- Cleaned the `Text` and `Summary` fields: removed HTML tags, punctuation, stopwords, and excess whitespace.
- Lowercased and normalized the text to reduce noise.

### Dataset Preparation

Implemented a custom PyTorch `Dataset` class within the notebook to:
- Tokenize using GPT-3 tokenizer (Hugging Face)
- Apply padding and attention masks
- Create a 75/25 train/test split

### Model Fine-Tuning

Fine-tuned GPT-3 using Hugging Face Transformers within the notebook:
- **Learning Rate:** `1e-5`  
- **Epochs:** `3`  
- **Optimizer:** `AdamW`  
- **Scheduler:** Linear Warmup  
- Trained on **10,000 reviews**

### Summary Generation

Implemented a `generate_summary()` function using:
- Beam Search (4 beams)
- Early stopping for more coherent outputs

### Evaluation

- Evaluated generated summaries using **ROUGE-1**, **ROUGE-2**, and **ROUGE-L** metrics
- Compared model summaries with actual human-written ones and saved results for inspection

---

## Results & Outcomes

| Type             | Text                                                                                      |
|------------------|--------------------------------------------------------------------------------------------|
| **Review**        | "The Fender CD-60S Dreadnought Acoustic Guitar is a great instrument for beginners..."    |
| **Actual Summary**| "Good for beginners but has tuning stability issues."                                     |
| **Generated**     | "The Fender CD-60S Acoustic Guitar is suitable for beginners, but there are reported tuning stability issues." |

- **ROUGE-1 F1 Score:** `0.77`

---

## Impact

ReviewSumGPT demonstrates how transformer-based models like GPT-3 can automate complex NLP tasks such as **abstractive summarization**.  
This end-to-end pipeline can be repurposed for other domains such as:

- Movie and game reviews  
- Hotel or Airbnb feedback  
- Customer support transcripts  

---

## Conclusion

Summarize the key findings and insights gained from training and evaluating the GPT-3 model for review summarization.

---
