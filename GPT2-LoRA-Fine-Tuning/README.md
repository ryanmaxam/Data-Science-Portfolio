# GPT-2 Fine-Tuning with Low-Rank Adaptation (LoRA)

## Overview
An experimental natural language processing project that adapts pretrained GPT-2 to generate descriptive tags for English-language quotations. It compares baseline text generation with outputs after parameter-efficient fine-tuning using LoRA.

## Tools and data
- **Python:** PyTorch, Transformers, Datasets, PEFT, Accelerate, NumPy
- **Base model:** `openai-community/gpt2`
- **Dataset:** `Abirate/english_quotes` from Hugging Face; 2,508 quotation records in the original run
- **Training:** 90/10 train/test split (seed 42), 500 optimization steps, 256-token truncation, LoRA rank 16, alpha 32, dropout 0.05

The dataset and base model are fetched at runtime. Review their upstream licenses and usage terms before redistributing model or dataset artifacts.

## Workflow
1. Load pretrained GPT-2 and the quotation dataset.
2. Format examples as `quote ->: tags` and create held-out examples.
3. Generate baseline tags from the pretrained model.
4. Attach LoRA adapters to attention projections and fine-tune.
5. Save the adapter locally and compare generated tags before and after training.
6. Inspect five held-out quotations against reference tags.

## Recorded results
The original notebook reported approximately **0.47% trainable parameters** and a final **training loss of 3.0486**. Qualitative outputs were sometimes repetitive or inaccurate; the experiment demonstrates the fine-tuning workflow rather than a validated tag classifier. These results are from the saved notebook output and have **not been reproduced in this cleaned copy**.

## How to run
1. Open `GPT2_LoRA_Fine_Tuning.ipynb` in Jupyter or Google Colab; a CUDA GPU is recommended.
2. Run the installation cell, then execute cells in order. Internet access is needed to download the model and dataset.
3. Training can take time and GPU memory; the notebook saves its adapter to `outputs/gpt2_quote_lora_adapter/`.
4. Results may vary with hardware, package versions, and upstream assets.

## Limitations and next steps
- This run does not calculate held-out tagging accuracy or validation loss.
- Language-model loss is applied to the entire quote-and-tags sequence rather than tags alone.
- Qualitative evaluation covers only a few examples and does not support production use.
- Future work: train with tag-only labels, add validation metrics, compare multiple seeds, and evaluate tag precision/recall.

## Files
- `GPT2_LoRA_Fine_Tuning.ipynb`: experiment, recorded outputs, and analysis.
- `requirements.txt`: package versions used in the original setup cell.
- `.gitignore`: excludes generated adapters, training output, and caches.
