# Generative-AI-with-LLMs
Coursera Assignments of the course titled: "Generative AI with LLMs" offered by DeepLearning.AI and AWS

**Lab Activity 1 - Generative AI Dialogue Summarization**

**Objective:**
The lab explored dialogue summarization using the FLAN-T5 model, focusing on prompt engineering techniques to improve summary quality.

**Setup & Dependencies:**
Installed necessary libraries (Hugging Face Transformers, Datasets, etc.) and loaded the DialogSum dataset containing dialogues and human-written summaries.

**Baseline Performance:**
Without prompt engineering, the model generated incomplete or irrelevant summaries (e.g., "Person1: It's ten to nine" instead of summarizing the train hurry).

**Prompt Engineering:**

Zero-shot: Added instructions (e.g., "Summarize the following conversation") to guide the model, improving results but missing nuances.

One/Few-shot: Provided example dialogue-summary pairs (in-context learning) to help the model understand the task better, yielding more accurate summaries.

**Key Techniques:**

Experimented with prompt templates (e.g., FLAN-T5’s "What was going on?").

Adjusted generative parameters (e.g., max_new_tokens, temperature) to control output length and creativity.

**Outcome:**
Prompt engineering significantly improved summaries, but limitations remained (e.g., context length constraints). The lab highlighted the need for fine-tuning for deeper task understanding.

**Lab Activity 2 - Fine-Tune a Generative AI Model for Dialogue Summarization**

**Objective:**
Fine-tune the FLAN-T5 model (base and PEFT variants) for dialogue summarization using the DialogSum dataset, comparing full fine-tuning vs. parameter-efficient fine-tuning (PEFT/LoRA).

**Setup & Models:**

Loaded the pre-trained FLAN-T5 model and tokenizer.

Prepared the dataset by converting dialogues into instruction prompts (e.g., "Summarize this conversation…").

Evaluated baseline performance with zero-shot inference (poor results without fine-tuning).

**Full Fine-Tuning:**

Trained the entire model (247M parameters) on a subset of data.

Achieved significant ROUGE score improvements (e.g., +18.8% ROUGE-1) over the original model.

Qualitative evaluation showed better summaries (e.g., capturing key actions like "#Person1 teaches #Person2 to upgrade hardware").

**PEFT/LoRA Fine-Tuning:**

Used Low-Rank Adaptation (LoRA) to train only a small adapter (~1.4% of total parameters).

Adapter size: 14MB vs. full model’s 945MB.

Results were slightly lower than full fine-tuning but still outperformed the original model (e.g., +17.5% ROUGE-1).

**Key Metrics:**

ROUGE Scores:

Original model: ~0.23 ROUGE-1.

Full fine-tuned: ~0.42 ROUGE-1.

PEFT model: ~0.41 ROUGE-1.

PEFT traded minor performance drops for efficiency (faster training, minimal memory overhead).

**Takeaways:**

Full fine-tuning yields the best performance but requires heavy resources.

PEFT is a lightweight alternative (near-comparable results) ideal for resource-constrained scenarios.

Demonstrated the trade-off between performance and computational cost in LLM fine-tuning.
